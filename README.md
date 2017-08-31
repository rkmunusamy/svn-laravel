# svn-laravel

You are going to need to type fast but I think you can do it in 4 minutes.  :) These are my notes on what worked for me on my Fedora core 6 with svn lib already installed by the package manager:

1. Create a Repository
svnadmin create /var/www/html/svnrepos

2. Create a SVN User
vi /svnrepos/conf/svnserve.conf
In that file add these three lines:

anon-access = none
auth-access = write
password-db = passwd
Create a password file:

vi /svnrepos/conf/passwd

In that file add a line for your user:

# add users in the format : user = password

tony = mypassword

3. Import Your Project

(assuming you’ve put your project files in /projects/laravel)

svn import /projects/laravel file:///svnrepos/laravel -m "initial import"

4. Start the SVN Server as Daemon

svnserve -d

Done! You should now have a svn server running with one project named myrailsproject.

Try checking it out of the repository:

svn co svn://192.168.0.2/svnrepos/myyrailsproject

Since we set anon-access to none you should be prompted for username and password which you created in the file /svnrepos/conf/passwd.

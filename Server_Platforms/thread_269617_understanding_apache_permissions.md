---
title: "understanding apache permissions"
date: 2006-10-02
forum: Server Platforms
---

### Post by goneskiing on 2006-10-02
I have my php files in a directory /var/myapp/  that are accessed from a front controller in /var/www 

to get apache to read my files I have to set them all to chmod 757 including both /var and /var/myapp folders

is this right ?  should these folders and files be exposed to all view and executing ?

---

### Post by sonic2000gr on 2006-10-02
Normally permissions should be 755 unless you want the web server to be able to write to a directory. But that should be specified explicitly. 757 is dangerous, it allows just about everyone (the other group) to manipulate all files in those directories.
The apache web server operates as user www-data
Now lets say your files are owned by your user account say, skiing and the group is users, so a random file would be:

Permissions:rwx-r_x-rwx User/group: skiing/users Filename:foo

With these permissions, clearly apache can write to the file (www-data does not belong to the users group) but so can many other unprivileged accounts.
If your web server were to be hacked, the file would be writeable!
my suggestion would be to change the owner/group of the file like:

chown skiing:www-data foo
Then set permissions accordingly, i.e. for the webserver to only read and execute:
sudo chmod 755 foo
If you want the file to be writeable:
sudo chmod 775 foo
In most cases the web server should not be able to write anywhere but in specific directories or files, and you should set these separately.
In your exact case I would do the following:

sudo chown -R skiing:www-data /var/www
sudo chown -R skiing:www-data /var/myapp
sudo chmod -R 755 /var/www
sudo chmod -R 755 /var/myapp

Then, if there is a folder say incoming in /var/www that you would like to be writeable by apache:

sudo chmod -R 775 /var/www/incoming

This would give apache (and yourself) write permissions, but will keep out anyone else. You would still have to be very careful though.

---

### Post by goneskiing on 2006-10-02
Sonic,
thks for a great, clear explanation - I have seen other posts with people struggling with permissions so perhaps it would be a good idea to add this explanation into the Apache wiki page.

---

### Post by sonic2000gr on 2006-10-02
Thanks, glad I could help.
I will consider the wiki thing.
I am already documenting a lot of stuff for myselft, so why not...

---


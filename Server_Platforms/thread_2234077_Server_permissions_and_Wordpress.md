---
title: "Server permissions and Wordpress"
date: 2014-07-12
forum: Server Platforms
---

### Post by Dragonbite on 2014-07-12
I have installed an Ubuntu Server 14.04 LAMP server and am having trouble with the permissions.   It includes Samba &  vsftpd (FTP) and I created an account (with sudo) for myself in addition to the primary one.  I installed vsftpd using these two references
[LIST=1]
[*][Ubuntu Official Documentation FTP Server]("https://help.ubuntu.com/10.04/serverguide/ftp-server.html") for installing 
[*][Ubuntu how to FTP transfer files to folder /var/www?]("http://superuser.com/questions/613857/ubuntu-how-to-ftp-transfer-files-to-folder-var-www") for adding a symlink to my /home directory to the website
[/LIST]I managed to access the /var/www/html directory via Samba and copied over a Wordpress files. I got it installed, but had to manually manipulate the files because Wordpress does not have permissions to modify anything in its directory.

How do I get it so that 
[LIST=1]
[*]I have full access to the entire website directory (Samba) to edit and update a number of site directories 
AND
[*]Enable Wordpress to modify the files in its directory 
AND
[*]Set up an FTP account that goes immediately to the /var/www directory
[/LIST]

I understand the concept of permissions and groups, but actually setting them up has not been very successful to me.  

Not to mention, I don't yet know what is a "good" setup that enables access as I need.

Thank you for your help.

---

### Post by thnewguy on 2014-07-12
Regarding questions #2

2. To allow Wordpress to modify the files in its own directory structure, change the permissions of the directory tree to match the web server's user account. Typically the web server process runs as the user "www-data". To allow Wordpress to modify its own directory, run

```

chown -R www-data /var/www/wordpress

```

Change the directory path to match the location of your Wordpress installation.

Regarding question #3, I haven't worked with vsftp specifically, but usually if you set up a user account on the system you can just specify the directory you want as the user's home directory when you create the FTP user. So, for example, let's say you created the user "FTP" on your server. Edit the /etc/passwd file, find the entry for the user "FTP" and change their home directory from "/home/ftp" to "/var/www". There are other ways to approach this, but the set up varies from one FTP program to the next.

---

### Post by Dragonbite on 2014-07-12
I don't know why, but my system runs the files in /var/www/html.  Regardless, your suggestions worked.

I ran your command to make the owner "www-data" and Wordpress worked fine.  So that was a first.

When I tried this before, I would not be able to access it via Samba but with these 2 settings it worked:
[LIST=1]
[*]My account is added to the "www-data" group
[*]Setting the permissions for the directories to 0775
[/LIST]

I was thinking about making a separate FTP account and having it point to the /var/www location but I am not sure what is the best method of creating that account and making it so it doesn't have a "/home" or it's /home is "/var/www ".  I think there is a way to set that up right in the beginning.

---

### Post by SeijiSensei on 2014-07-13
Another option in Samba is to use the "force user" directive.  If you set "force user = www-data" in the share definition for the website directory, all files created there will be owned by www-data regardless of who placed them there.

---

### Post by Dragonbite on 2014-07-14
> **SeijiSensei said:**
> Another option in Samba is to use the "force user" directive.  If you set "force user = www-data" in the share definition for the website directory, all files created there will be owned by www-data regardless of who placed them there.

Where do I set this setting?  I've heard of it, and I may have done it with an entire partition but not on a specific folder.

Is it easy to do via Command Line?  The server has no GUI installed.

---

### Post by SeijiSensei on 2014-07-14
> **Dragonbite said:**
> Where do I set this setting?  I've heard of it, and I may have done it with an entire partition but not on a specific folder.

Is it easy to do via Command Line?  The server has no GUI installed.

You need to add it to the share definition in /etc/samba/smb.conf.  If you can see the website with Windows networking, there should be a section in that file like this:
```

[website]
comment = My Website
path = /var/www/html
etc.
force user = www-data
force group = www-data

```
Then restart Samba with "sudo service samba restart".  The name "website" is arbitrary.  Just find the share associated with /var/www/html.

If you've not edited files from the command line so far, I suggest using nano for starters.
```
sudo nano /etc/samba/smb.conf
```
It has a handy menu of commands at the bottom of the screen.  The "^" represents the Ctrl- shift.  So the exit command, denoted as "^X", is executed by holding down Ctrl and hitting "X" (case insensitive).

---

### Post by Dragonbite on 2014-07-14
Using the command line I have experience with (Nano and Vi usually), but knowing what goes where is what always gets me.  At least with a GUI I can guess from the drop-down list choices or a checkbox ;)

I'll give editing /etc/samba/smb.conf a shot tonight when I get home, now that I have an idea of what the entry looks like.

Thanks.

---


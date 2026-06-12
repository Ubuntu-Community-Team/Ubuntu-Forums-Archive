---
title: "FTP and Apache, the creation of directories and files"
date: 2013-05-15
forum: Server Platforms
---

### Post by roooii on 2013-05-15
Hello folks,

I ran into a problem were Apache can't read or write newly created files by my FTP user (named roy).

I gave Apache-user and the FTP-service-user ownership to /var/www.
However when a new user logs in on the ftp, files and directories get created by this user on his own. The general group www-data also gets added, but has no read or write rights. See below what I mean and what happens if I create a folder into the /var/www/ folder.

drwx--S--- 2 roy      www-data 4096 May 15 18:21 test456

How can I fix this problem to make sure apache can read it?

Thanks in advance.

---

### Post by Lars Noodén on 2013-05-15
Welcome to the forums.

The user and group www-data exists to provide an unprivileged user for the web server to run.  So it should definitely not be used on the web server's directories.  If you want to have a group to share access to the web server's documents, then make one of your own and use that.

About being able to read the files, the directories in /var/www  should be 775 or 755 and the individual files should be 664 or 644.  Any of those grant read permission to Other, which thus includes the web server.  But again, these files and directories should not be owned by www-data nor in the group www-data, that would be unsafe.  

Speaking of unsafe, if you are running plain FTP, then your passwords, user name and data are all being transmitted across the net unencrypted.  You would be safer then to use SFTP instead.  
* [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
* [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by roooii on 2013-05-15
Thanks a lot. It's about time I started learning Ubuntu (linux). 

Anyhow I still can't seem to get it working the way I want it. If I create a folder and files with the FTP client, apache can't read them. If I create a folder or file within the console "mkdir test/" apache can read it. The permissions given by each of the methods are completely different if I look at the permissions with "ls- la". I hope you could look with me. 

So to sum up what I did now: 
* I deleted everything inside the "/var/www" folder.
* "sudo addgroup webadmins"
* "sudo usermod -a -G webadmins roy"
* "sudo chown roy:webadmins /var/www"
* "sudo chmod 755 /var/www"

Everything looks fine with "ls -la" untill I start creating maps and folders with the user "roy" via FTP.
Because roy is in the webadmins group I can create maps and folder with that user on the FTP. But apache can't read it them.

I've tried several guides on the internet, but none have worked out for me.

Thanks for the help again.

---

### Post by Lars Noodén on 2013-05-15
If you want to use group permissions to allow read and write, you can set the GID bit.

```

sudo chown -R roy:webadmins /var/www
sudo chmod -R g+ws /var/www

```

That should ensure that the group has write access to any files created in the directory.

---

### Post by roooii on 2013-05-15
Thanks again. Still if I create files within this folder after using the code you supplied apache has no read access.

Example I created a subfolder named "http".
This is what it shows me. Should apache be in the webadmins group or would that be unsafe?

drwx--S--- 2 roy webadmins 4096 May 15 21:10 http

---

### Post by Lars Noodén on 2013-05-15
Apache should be left alone, only the user (roy) that needs write access should be in the group webadmins.  You do need to find a way to grant read access to Other, so that the web server can read the pages and serve them to the public.  

```

sudo find /var/www -type d -exec chmod u=rwx,g=rwxs,o=rx {} \;
sudo find /var/www -type f -exec chmod  u=rw,g=rw,o=r {} \;

```

The directories and files need slightly different permissions.  Once you have them set correctly they should not need changing.

---

### Post by roooii on 2013-05-15
I used the code you summed up. It works perfectly, but then again newly created subfolders and files get wrong permissions:

drwxrwsr-x 3 roy webadmins 4096 May 15 21:33 .
drwxrwsr-x 3 roy webadmins 4096 May 15 21:10 ..
-rw------- 1 roy webadmins    4 May 15 19:33 index.php
drwx--S--- 2 roy webadmins 4096 May 15 21:33 test2

As you can see the first 2 lines are set correctly (parent folders set with your code). With the ftp i created index.php and test2. They both got old permissions. Why won't these file and folder get the same permissions like their parent?

I really appreciate your help. Trying to learn more about these permissions.

---

### Post by Lars Noodén on 2013-05-15
The directories are set up right.  It must be the FTP server that is overriding the permissions.  Which one are you using and how is it set up?  I only work with SFTP myself, but there are others that work with FTP servers here.

---

### Post by roooii on 2013-05-15
I will try some SFTP server then. See how that works out. Which sFTP server would you suggest? I'm using vsFTPd.

---

### Post by roooii on 2013-05-15
Looks like I found the problem in the configuration of vsFTPd.

# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022

Once I removed that hashtag it now sets permissions properly. This FTP program can also use sFTP from what I've seen so Ill continue using vsFTPd.

Thanks for your help.

---


---
title: "Apache var/www change on 12.04"
date: 2012-12-07
forum: Server Platforms
---

### Post by tomjelfs on 2012-12-07
Hi Everyone

I'm pretty new to Ubuntu and I'm tyring to move everything over on my dual booted system.  

I've set up PHP and Apache to hopefully let me carry on programming my website on Ubuntu but I've hit a road block already, I can't drag and drop my files into the var/www folder.  Now I've searched around and realise I don't have the privilege to edit this folder and based on that I've searched the web for how to do this but not found two solutions the same so far.

I understand that the way to do it is to give yourself root or administrative privileges and then to edit the Documentroot line in the Default file in the Sites-available folder but it wont let me save it based on my privileges.

Can anyone tell me the best root to go about doing this?

Thanks

Tom

---

### Post by slickymaster on 2012-12-07
By default files under /var/www are protected. To create content under /var/www you must have root privilege.

Use the sudo command and enter your password when prompted:
```
sudo cp ~/index.html /var/www/index.html
```

Or, open your file manager with root permissions and then copy your files (replace nautilus with whatever file manager you are using):
```
gksudo nautilus
```

---

### Post by tomjelfs on 2012-12-07
OK the  "gksudo nautilus" , let me edit the sites-available/default  config file and now I'm using a folder sat on my desktop instead,  brilliant.

Next problem, I got all keen and went and dragged n dropped a folder  from my XP hard drive into the new sparkly working folder but when I  open these files I get Forbidden

> 
**Forbidden**

 You don't have permission to access /acorn2012/ on this server.



I figured out that it is because of the permission settings of all the files that I dragged across.  Is there a way to change the permissions of all the files in a folder or do I have to change them individually?

Thanks again

---

### Post by slickymaster on 2012-12-07
If the problem lies in file permissions and if you want to change those permissions on all the files of a specific folder you just have to navigate to the specific folder and enter the following command

```
chmod u+w *
```

Basically that command '_chmod_', which stands for *change mode* is used to change the security permissions on files.
The arguments you're using with this command:
[LIST]'*u*' - means that you are changing the security permissions on the file(s) to the owner of the file ('u' stands for user). 
[*]'*+*' - means that you are adding a permission.
[*]'*w*' - means that you are adding write permission.
[*]'***' - means that that your chmod command applies to all the files in the folder
[/LIST]

In all cases it is advisable that you learn the basics of the command line. There are several websites where you can start.

_Here's just a few:_
[Learning The Shell]("http://linuxcommand.org/learning_the_shell.php")
[Linux Survival]("http://linuxsurvival.com/index.php")
[Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bash.html")

---

### Post by tomjelfs on 2012-12-07
OK let me take a stab at this then.

So I want to say that all the files currently in there can be:

• Read and Write by the Gwner
• Read and Write by the Group
• Read Only by Others

That seems to be the setting for newly created files.

So is the following any good (i'm gonna go with numbers cuz all the dashes in letters was frying my brain for a beginner:

```

myname@maylaptopname:~$ sudo chmod 664 * home/me/desktop/myfolderlocation

```

I don't know really.

Tom

---

### Post by slickymaster on 2012-12-07
When using chmod with octal number representing the bit pattern for the new permissions the first octal digit refers to the permissions for the owner of the file; the 2nd digit, for the group; the 3rd digit, for the rest of the world.

_In Unix, the numeric value for permissions are:_
	r="read permission"=4
	w="write/edit permission"=2
	x="execute permission"=1

So, **chmod 664**, gives the owner of the file read & write (4+2+0) permission, gives the group read & write (4+2+0) permission, and gives the rest of the world read-only (4+0+0) permission.

---

### Post by slickymaster on 2012-12-07
> **tomjelfs said:**
> 
```

myname@maylaptopname:~$ sudo chmod 664 * home/me/desktop/myfolderlocation

```


Your code is wrong. First its the path to the folder where the files are and then the files.
```
sudo chmod 664 ~/path/to/folder/*
```

---

### Post by SeijiSensei on 2012-12-07
New users often find it easier to use the symbolic method of changing permissions.  For instance,

```
sudo chmod ug+rwx,o+rx /path/to/directory
```

assigns read/write/execute privileges to the **u**ser and **g**roup, but just read and execute to **o**ther.  You can remove permissions with the minus sign.

The execute permission means different things between files and directories.  For files it has the obvious meaning, that the file constitutes an executable program.  For directories, it means that the directory may be listed.  This matters if you decide to put a web site under your home directory.  By default, only the user has rwx privileges on /home/user.  In order for Apache to read files in, say, /home/user/mywebsite, /home/user needs to have og+x (or 711) permissions.

---

### Post by slickymaster on 2012-12-08
@SeijiSensei
Just want to thank you the informative stance of your post. Not only because it is completely correct but also because most of us often in this forum when answering the questions of those who are entering the world of Linux tend to just deliver the answer to the specific doubt without framing that response in a broader instructional scope, being that I am one of those one of those that almost every time keep forgetting that.

@tomjelfs
If you consider yourself completely enlightened, don't forget to mark the thread as solved.

---

### Post by tomjelfs on 2012-12-09
I used the symbolic script that SeijiSensei suggested and it didn't seem to work, I noticed that you can Apply the Permissions to Enclosed files so I used the gksudo nautilus command to log in and hit that button after setting my preferences, that didn't seem to work.  I backed and forth for a while then it suddenly started working.  All of my files in that folder are now under the user www-data and are now working. 

So although I have my issue resolved, I'm not sure what cured it.

---

### Post by slickymaster on 2012-12-09
@tomjelfs
Your last post led me to think that rather than a permissions issue you were facing a ownership issue with those files.

The folder _/var/www_ owner is by default root:root, and when you hit the Apply Permissions To Enclosed Files in Nautilus basically what it did was to change the ownership (both user and group) of all files and directories inside of directory and directory itself.

Another way of achieving it was to run this command at a terminal window:
```
sudo chown -R youruser:youruser .*
```

---

### Post by CharlesA on 2012-12-09
> **slickymaster said:**
> @tomjelfs
Your last post led me to think that rather than a permissions issue you were facing a ownership issue with those files.

The folder _/var/www_ owner is by default root:root, and when you hit the Apply Permissions To Enclosed Files in Nautilus basically what it did was to change the ownership (both user and group) of all files and directories inside of directory and directory itself.

Another way of achieving it was to run this command at a terminal window:
```
sudo chown -R youruser:youruser .*
```
While that would work, it would be better to either use a symlink or just change the document root to a folder you have read/write access to, such as your home folder.

It would be better to go with SeijiSensei's suggestion if you don't want to mess with conf files.

---

### Post by Wim Sturkenboom on 2012-12-10
One only has to change 2 lines in apache's /etc/apache/sites-available/default to make apache read from a directory in the user's home directory instead of from /var/www.

Slightly modified from post #10 in [http://ubuntuforums.org/showthread.php?t=2070802](http://ubuntuforums.org/showthread.php?t=2070802)

Create a directory in your home directory where you want to have your website
```

testuser@VirtualBox:~$ mkdir website1
testuser@VirtualBox:~$ mkdir website1/www
testuser@VirtualBox:~$ ls -l website1/
total 4
drwxrwxr-x 2 wim wim 4096 Oct 21 10:43 www
testuser@VirtualBox:~$ 

```

Next step is to let apache use this directory instead of /var/www. For this you need to modify /etc/apache/sites-available/default and replace any reference to /var/www by /home/yourusername/website1/www. Root privileges required. So e.g.
```

gksudo gedit /etc/apache/sites-available/default

```

This is the contents of the file on my (fresh system). In red the changes; I commented out the original line by putting a '#' in front of it and added the new line.

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

[COLOR="Red"]	DocumentRoot /home/testuser/website1/www[/COLOR]
[COLOR="Red"]#	DocumentRoot /var/www[/COLOR]
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
[COLOR="Red"]	<Directory /home/testuser/website1/www>[/COLOR]
[COLOR="Red"]#	<Directory /var/www/>[/COLOR]
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Next you can restart apache
```

wim@VirtualBox:~/website1/www$ sudo service apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
wim@VirtualBox:~/website1/www$ 

```
You can ignore the warnings and test the changes by navigating to your server using a webbrowser. As there's currently nothing in the new documentroot, you will get an empty directory listing. If you now copy /var/www/index.html to /home/yourusername/website1/www and after refreshing the page in the browser, you should see the 'it works' page.

In my opinion, this is a neater solution to the permissions problem than changing ownerships and permissions on directories and files in /var/www.

---

### Post by SeijiSensei on 2012-12-10
You must have changed the permissions on /home/username at some point because the  default 0700 permissions will block the Apache user, www-data, from seeing a website in a user's home directory.  You need to use

```
sudo chmod 0711 /home/username
```

to fix that and, of course, make sure the website directory is readable by the www-data user.

---

### Post by CharlesA on 2012-12-10
I checked my home directory on my dev box and my home folder was already set for 755 permissions. ;)

---


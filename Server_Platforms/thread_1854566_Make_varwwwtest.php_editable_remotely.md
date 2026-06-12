---
title: "Make /var/www/test.php editable remotely?"
date: 2011-10-04
forum: Server Platforms
---

### Post by QwUo173Hy on 2011-10-04
I can finally view my php page from a laptop on the home network. If I could edit that file tge I could work feom it too. Is it possible for me to write to that file from my windows laptop somehow?

I think I can share the folder via samba, but what about the root permissions?

---

### Post by tomodachi on 2011-10-04
The terminal is an excellent way for you to get access to your files remotely.

running the command "aptitude install ssh" , to install a ssh server.


then start the ssh server with the command
'sudo /etc/init.d/ssh start'

you can then access your computer's terminal remotely from an ssh application for windows like the program putty.

It will require you to login with your username and password for access

This way you will have access remotely to all files on your computer not just a particular folder you share

---

### Post by collisionystm on 2011-10-04
On your server install SSH.

sudo apt-get install ssh

On your WIndows computer, install winscp

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

Check the permissions of your /var/www directory

cd /var

ls -lh

Look to see what group it belongs to. Join your user to that group.

Usermod -G groupname -a username

now do a chmod -R 774 on that your wwww folder

sudo chmod 774 www/

You can now login via your WinSCP, via ssh, using your username and password and full read and write access to your files in there. Just drag the file over to your machine, edit it, and drag it back.

---

### Post by collisionystm on 2011-10-04
Or do putty, I am not sure if you are just trying to edit text files or what

---

### Post by QwUo173Hy on 2011-10-05
Thanks guys - ssh does the job very well. I tried Putty first as I remember using it at some point in the past.

I'll also try using a Samba server so I can work more homogenously with the windows laptop, as suggested by an IT friend just now.

Thanks for getting me up and running so soon!

Jarlath

---

### Post by Lars Noodén on 2011-10-05
SSHFS is easier to set up than Samba, so you might take a look at it first.  It allows you to mount the remote system as a regular folder but the only technical pre-requisite is SSH (actually SFTP).

---

### Post by QwUo173Hy on 2011-10-05
> **Lars Noodén said:**
> SSHFS is easier to set up than Samba, so you might take a look at it first.  It allows you to mount the remote system as a regular folder but the only technical pre-requisite is SSH (actually SFTP).

Thanks  Lars. You're right - I've been finding my time slipping away reading Ubuntus Samba documentation - but I found a quick setup guide here:

[http://www.hardcode.nl/archives_147/article_548-samba-quick-setup-on-ubuntu-1004.htm](http://www.hardcode.nl/archives_147/article_548-samba-quick-setup-on-ubuntu-1004.htm)

If I don't get that up and running soon I'll look in to SSHFS as it seems to meet my needs better.

Thank you!

---

### Post by SeijiSensei on 2011-10-05
If you take the samba route, I recommend using the "force user" and "force group" directives like this:

```

[website]
path = /var/www
writeable = yes
preserve case = yes
force user = www-data
force group = www-data
valid users = (list of usernames separated by commas)
create mode = 0664
case sensitive = yes
directory mode = 0755

```

This lets all the users in the valid users list connect to the share, but all file activities at the OS level happen with user/group www-data.

---

### Post by Lars Noodén on 2011-10-06
> **SeijiSensei said:**
> If you take the samba route, I recommend using the "force user" and "force group" directives like this:

```

[website]
path = /var/www
writeable = yes
preserve case = yes
force user = www-data
force group = www-data
valid users = (list of usernames separated by commas)
create mode = 0664
case sensitive = yes
directory mode = 0755

```

This lets all the users in the valid users list connect to the share, but all file activities at the OS level happen with user/group www-data.

Maybe a different user/group would be wiser.  It may not be such a good idea for the web server to have write access to the files it will be serving.

---

### Post by SeijiSensei on 2011-10-06
I don't have an Ubuntu server instance available to check, but doesn't the www-data user already have write privileges in /var/www?  I recall that directory having 0755 permissions with user/group www-data.

---

### Post by DavidBeijer on 2011-10-06
My freshly installed Ubuntu server has www owned by root, and the default files in it (index.html and test.php) are also owned by root, as far as I can see the privileges are 0644. The group settings are also set to root only, so I guess that www-data is not the owner of those dirs.

---

### Post by CharlesA on 2011-10-06
I just checked my Ubuntu box and the /var/www/ directory is 644 for files and 755 for directories. The files/directories in question are owned by root in my case tho.

---

### Post by Lars Noodén on 2011-10-06
By default, /var/www should be owned by root, group root with permissions 755.  Files are 644.  

Adding www-data would introduce serious security concerns because then the web server could have write access to the files it is serving.

---

### Post by Lars Noodén on 2011-10-06
The way around the sharing problem is to make a new group, say webmasters, and then set /var/www to be in that group, make it group writable and set the sticky bit (chmod g=rwxs /var/www) for the group.  Then as you add accounts to the group webmasters they will be able to edit the web site.

---

### Post by QwUo173Hy on 2011-10-07
Samba would have been a very involved setup if I hadn't found these two resources:

[http://www.hardcode.nl/archives_147/article_548-samba-quick-setup-on-ubuntu-1004.htm](http://www.hardcode.nl/archives_147/article_548-samba-quick-setup-on-ubuntu-1004.htm)
[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

The only problem I had was writing to the directory /var/www - but I achieved this by making the user 'jarlath' the owner of that folder.

Many thanks for all the helpful replies!

---

### Post by bbqroast on 2011-10-08
Once you have installed the SSH (server) package (as mentioned above) you could use Notepad++ with a sftp (secure file transfer protocol) addon. What it will do is create a local cache (eg mine is in C:\web-server\ which which you can edit, when you save a file it then syncs it with the server...
Seamless and secure :)

---


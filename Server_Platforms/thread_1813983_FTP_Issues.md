---
title: "FTP Issues"
date: 2011-07-28
forum: Server Platforms
---

### Post by Brad_J on 2011-07-28
Hi, I'm currently in the process of making an HTTP web server running from home and I've run into some problems with FTP(using proftpd). I want to be able to use FTP to upload files to the website from a client like filezilla or change pages through notepad++, but I can't currently do that. I am able to connect over the local network, but I'm only able to upload anything to my home directory and I can't log in as root. When I attempt to connect through my external url or ip I get a prompt to enter my credentials, but after attempting to load for about a minute it times out.

I'm stumped, I thought it might be that my passive ports weren't being forwarded, but I changed the passive port configuration in /etc/proftpd/proftpd.conf and forwarded them through the router and I still have the same result. My actual website is accessible externally and I can ssh to it, but I can't seem to figure out ftp, please help.

-Brad

---

### Post by volkswagner on 2011-07-28
It sounds as if you have more than one issue.

Perhaps it is best to tackle one at a time.  I suggest working on uploading via LAN first.  

It appears your user is jailed to his/her home directory.  This is normal behavior, and creates a security layer.  

You can either set this user not to be jailed and have / set as default directory, or /var/www as default directory. 

 You also have the option to move your web directory to your home directory and edit the /etc/apache2/sites-available/hostfilename to point to that location.  

Another option would be to create a user with his/her home directory set to your webroot (var/www).


If you simply want to remove the jail for all users comment out the line and restart proftpd.

look for

```
# Use this to jail all users in their homes 
DefaultRoot                     ~

```

in /etc/proftpd/proftpd.conf

---

### Post by Wim Sturkenboom on 2011-07-29
> **Brad_J said:**
> ... I can't log in as root.
...You never ever want to do that over the internet; not even with secure connections.

Always log in as an unprivileged user via a secure connection (ssh, sftp/ftps).
In case of ftps/sftp, upload your files.
In case of ssh, you can elevate your privileges (e.g. sudo) to move uploaded files around

Again, never ever allow root to login directly.

---

### Post by Brad_J on 2011-07-29
> **volkswagner said:**
> It sounds as if you have more than one issue.

Perhaps it is best to tackle one at a time.  I suggest working on uploading via LAN first.  

It appears your user is jailed to his/her home directory.  This is normal behavior, and creates a security layer.  

You can either set this user not to be jailed and have / set as default directory, or /var/www as default directory. 

 You also have the option to move your web directory to your home directory and edit the /etc/apache2/sites-available/hostfilename to point to that location.  

Another option would be to create a user with his/her home directory set to your webroot (var/www).


If you simply want to remove the jail for all users comment out the line and restart proftpd.

look for

```
# Use this to jail all users in their homes 
DefaultRoot                     ~

```in /etc/proftpd/proftpd.conf
Thanks for the response. I guess I should have mentioned that users are not really being jailed to their home, they just can't edit/add files outside of the home directory. Also, according to the proftpd.conf file, this line:
```
# Use this to jail all users in their homes 
#DefaultRoot                     ~

```
is already commented out. Looking into it further, I think this is being caused by umask; I have it set to umask 22 and it says that that will prevent files from being group and world writable. How can I make it so that certain users are able to edit anything? Or maybe just allow a user to edit certain directories?

---

### Post by volkswagner on 2011-07-29
> **Brad_J said:**
> Thanks for the response. I guess I should have mentioned that users are not really being jailed to their home, they just can't edit/add files outside of the home directory. Also, according to the proftpd.conf file, this line:
```
# Use this to jail all users in their homes 
#DefaultRoot                     ~

```
is already commented out. Looking into it further, I think this is being caused by umask; I have it set to umask 22 and it says that that will prevent files from being group and world writable. How can I make it so that certain users are able to edit anything? Or maybe just allow a user to edit certain directories?

This is a little beyond my knowledge base:

I believe if you read the umask line literally, it applies to NEW files and directories.  The fact that users cant create or edit files leads me to believe you are encountering file permission problems.  If the user is not part of the group or the owner, with write permissions, then he/she won't be able to write to that file or directory.

What are the permissions of the directory you are trying to write to?

```
ls -l /var/www/directory/in/question
```

Example:
If the directory in question has group set to "www-data" and is writable by that group, you may be able to just add users to the www-data group.

---

### Post by Brad_J on 2011-07-29
> **Wim Sturkenboom said:**
> You never ever want to do that over the internet; not even with secure connections.

Always log in as an unprivileged user via a secure connection (ssh, sftp/ftps).
In case of ftps/sftp, upload your files.
In case of ssh, you can elevate your privileges (e.g. sudo) to move uploaded files around

Again, never ever allow root to login directly.

I didn't know that logging in as root was a security risk. Does that mean that it doesn't allow root to log in to ftp by default?

---

### Post by Brad_J on 2011-07-29
> **volkswagner said:**
> 
What are the permissions of the directory you are trying to write to?
```
ls -l /var/www/directory/in/question
```

I actually want to be able to add and remove files from the entire www directory. Running ls -l /var produced these results for www:
```
drwxr-xr-x  2 root root  4096 Jul 21 13:26 www
```
I am pretty new to linux and I'm not entirely sure how groups work as I haven't really had much of a reason to learn about them yet. How would I change the group of www and my account so that only I can edit www? Thanks.

---

### Post by volkswagner on 2011-07-29
I'm sorry but this has left me with no simple answer.  In fact, I have created a new thread, since I've been faced with the need to repair file permission/ownership in the past.

I hope to get some insight with this [new thread, based on Apache2 file permissions]("http://ubuntuforums.org/showthread.php?t=1814660").

---

### Post by Wim Sturkenboom on 2011-08-01
> **Brad_J said:**
> I didn't know that logging in as root was a security risk. Does that mean that it doesn't allow root to log in to ftp by default?Root is the first account that somebody will attempt to hack. Once they have access, they can modify any system file.

Not sure about defaults, I always make sure that it's disabled.

---


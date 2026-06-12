---
title: "Advice on Setting up Proper Permissions on Ubuntu 10.04 Server"
date: 2011-05-29
forum: Server Platforms
---

### Post by gary4gar on 2011-05-29
Hey,
I run a server powered Ubuntu 10.04 LTS. the software stack that I use comprises of 
[LIST]
[*]PHP fpm-fcgi Version 5.3.6
[*]Web Server:	 nginx/0.8.54
[/LIST]

To make, things like wordpress work properly. I have done *chown www-data:www-data* on my public_html folder. This was all files are easily modifiable by nginx and things like Auto Updating wordpress work as expected. 

The problem arises when I login via ftp and try to upload new files or change existing ones. Since, I use username as Gaurish & all files are owned www-data my requests are denied.

```
Response:	220 (vsFTPd 2.2.2)
Command:	USER gaurish
Response:	331 Please specify the password.
Command:	PASS ************
Response:	230 Login successful.
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Starting upload of /tmp/cachegrind.out.5513
Command:	CWD /home/gaurish
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/home/gaurish"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PORT 192,168,1,6,214,6
Response:	200 PORT command successful. Consider using PASV.
Command:	STOR cachegrind.out.5513
[COLOR="red"]Response:	553 Could not create file.[/COLOR]
Error:	Critical error
Status:	Disconnected from server
```


I need a way by which I(gaurish) & nginx(www-data) can both modify the files. Any idea how to do that?

---

### Post by lordadi on 2011-05-29
Add the user (Gaurish) to the www-data group. This will enforce the www-data group permission on the user.

---

### Post by gary4gar on 2011-05-30
thanks for reply. Adding user (Gaurish) to the www-data group worked but there is still a problem. 

If I upload some files via FTP, its default owner is user (Gaurish), which makes them unserveable by web server. so Then I have to login as root, run chown www-data:www-data on them to make them public web server. 

Any idea to default default owner & permissions?

---

### Post by SeijiSensei on 2011-05-30
If you make use Gaurish's primary group www-data, then files that user creates will be readable by the web server.  The simplest method for this is editing /etc/passwd and replacing the user's gid with 33, the gid of the www-data group.  You can also accomplish this from the command prompt with adduser, I believe, but I've always just edited /etc/passwd directly.

---

### Post by gary4gar on 2011-05-30
Thanks, I have done that.

```
# id gaurish
uid=1001(gaurish) gid=33(www-data) groups=33(www-data)
```

Tried uploading files, it got uploaded with following permissions

```

-rw-------  1 gaurish   www-data  16874 2011-05-30 12:10 html5.png
```

Which means I still have to go & manually change every file's permission to 644 to make it readable. Any idea to to set default permissions to 644?

---

### Post by lordadi on 2011-05-30
would ```
chmod 644 public_html
``` do it?

---

### Post by gary4gar on 2011-05-30
> **lordadi said:**
> would ```
chmod 644 public_html
``` do it?

That would work for existing files but NOT for new files:(

---

### Post by SeijiSensei on 2011-05-30
Somehow you have a weird umask set, I guess.  As the garuish user, what is the result of the umask command?  Normally it should return 0022 which gives the user all permissions, and read and execute permissions to group and other users.  

I don't use FTP, but perhaps vsftp has a umask setting that overrides your own?  [Yup]("http://www.google.com/search?q=vsftpd+umask").  Check vsftpd.conf and make sure umask is set properly there.

---


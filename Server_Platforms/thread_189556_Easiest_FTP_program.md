---
title: "Easiest FTP program?"
date: 2006-06-05
forum: Server Platforms
---

### Post by spelingchampeon on 2006-06-05
I'm looking for the easiest FTP program that meets average security specs. If it can be set up using GUI and no command line..I'd be **extremely** happy. I need to have this set up ASAP. I will learn the command line stuff later on. Thanks

---

### Post by mrcowcow on 2006-06-05
Vsftpd is very secure as far as ftp goes, and works very well. The only command line you would have to do is if you are doing apt-get to get it. It does take a little bit of configuration to get it off and running, but the Ubuntu server guide has a pretty good section on how to do that.

edit: this is an ftp server.

---

### Post by Slim Odds on 2006-06-05
[quote=spelingchampeon]I'm looking for the easiest FTP program that meets average security specs. If it can be set up using GUI and no command line..I'd be **extremely** happy. I need to have this set up ASAP. I will learn the command line stuff later on. Thanks[/quote]

I assume, since you didn't say, that you're talking about an FTP client program. There are lots of them. I personally prefer a command line program for this, but there are some good GUI ones also. Use the search feature in Synaptic.

Also, there is NO real security with FTP.

---

### Post by Tortanick on 2006-06-05
Why no real security? and is that downloading or uploading?

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Tortanick]Why no real security? and is that downloading or uploading?[/QUOTE]

short answer: FTP has **no** encryption. No matter which direction, all data were send "readable". Specially your login (login name and password) will be send as ASCII text.

Thomas

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=spelingchampeon]I'm looking for the easiest FTP program that meets average security specs. [/QUOTE]

what do you mean with "program"? Does program mean FTP **server** or FTP **client**?

My prefered FTP client:  ncftp  (command line - of course!)
I do prefer command line tools for many issues.

My prefered FTP server: proftpd
proftpd is very stable, real simple to configure (Apache style) and supports virtual hosts which I do need. But I also prefer to compile also this server software myself. By this way I'm able to use the very newest release asap and set all required configure options (for compiling) to fit my own needs on my production servers.

Because FTP is not secure, I do use a secure solution (FTP client sftp as part from openssh) mostly, when doing admin stuff.

Thomas

---

### Post by spelingchampeon on 2006-06-05
[QUOTE=Slim Odds]I assume, since you didn't say, that you're talking about an FTP client program. There are lots of them. I personally prefer a command line program for this, but there are some good GUI ones also. Use the search feature in Synaptic.

Also, there is NO real security with FTP.[/QUOTE]
This would be for a server. Thanks

---

### Post by LordHunter317 on 2006-06-05
I would use vsftpd myself, unless you need a feature it doesn't provide.

FTP can be made secure if you use SSL, something all the major FTP daemons support, and most major clients support it as well.  Also, the authentication issue can be resolved by using Kerberos or S/KEY.

None of the deamons worth using come with a GUI configuration tool.  But I'm of the mind if you can't figure out their configuration files (perhaps with some help and reading) you probably shouldn't be running an FTP server either.

---

### Post by spelingchampeon on 2006-06-05
I will try vsftpd.. I will only have a couple users logging in. I did have an FTP program that defaulted with Ubuntu (I think it was pureFTP), but I couldnt configure it.. caught in a quagmire with it. 

Thanks for the help everyone!

---

### Post by Tortanick on 2006-06-07
[QUOTE=linuxone]Hi,
short answer: FTP has **no** encryption. No matter which direction, all data were send "readable". Specially your login (login name and password) will be send as ASCII text.
Thomas[/QUOTE]

Not ture, PureFTPd, my favourite, has TSL support

---


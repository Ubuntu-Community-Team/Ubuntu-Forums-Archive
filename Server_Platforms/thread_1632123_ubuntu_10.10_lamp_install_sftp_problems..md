---
title: "ubuntu 10.10 lamp install sftp problems."
date: 2010-11-27
forum: Server Platforms
---

### Post by veasnak on 2010-11-27
I recently installed Ubuntu 10.10 Server as a LAMP install on my home network for website testing. Everything works great so far. I dont need the apache document root viewable from outside the network. I didnt want to install vsftpd, I just wanted to use sftp. I used this string of commands:

sudo usermod -g www-data [my username]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

but when I login using sftp via filezilla and navigate to the /var/www dir and upload files, it always gives the files 644 permissions but I want everything to have 755 (files and directories). I have pulled most of my hair out over the past few days tryig figure this one out and read almost every man page and tutorial. Can anyone offer some help? Just to clairify, I want to setup the server and only access it from my laptops and only use sftp via filezilla on my lappy, security isnt really an issue because it is behind my home network.

---

### Post by tad1073 on 2010-11-27
why don't you use nautilus?

---

### Post by veasnak on 2010-11-27
> **tad1073 said:**
> why don't you use nautilus?

Im not always using a linux box, if that helps. Im still transitioning from XP so I not completely familiar with all the details of linux sys admin.

---

### Post by windependence on 2010-11-27
WinSCP?

---

### Post by veasnak on 2010-11-27
> **windependence said:**
> WinSCP?
Nope, using Filezilla on the XP machine as well. Connecting from the remote machine, linux or win is not the problem, it the default permissions given to files that are uploaded to the /var/www using sftp.

---

### Post by windependence on 2010-11-27
In /etc/ssh/sshd_config, change the following:
[FONT=Consolas]Subsystem sftp /usr/lib/openssh/sftp-server[/FONT]
to:
[FONT=Consolas]Subsystem sftp /bin/sh -c 'umask 0002; exec /usr/libexec/openssh/sftp-server'[/FONT]
[FONT=Consolas][/FONT] 
[FONT=Consolas]-Tim[/FONT]

---

### Post by tad1073 on 2010-11-27
> **veasnak said:**
> Im not always using a linux box, if that helps. Im still transitioning from XP so I not completely familiar with all the details of linux sys admin.

you can map the ftp server as a network drive in explorer on xp

---

### Post by veasnak on 2010-11-28
> **windependence said:**
> In /etc/ssh/sshd_config, change the following:
[FONT=Consolas]Subsystem sftp /usr/lib/openssh/sftp-server[/FONT]
to:
[FONT=Consolas]Subsystem sftp /bin/sh -c 'umask 0002; exec /usr/libexec/openssh/sftp-server'[/FONT]
 
[FONT=Consolas]-Tim[/FONT]

Tim, thanks, I tried this and it didnt work. I was brave and changed it to:
[FONT=Consolas]Subsystem sftp /bin/sh -c 'umask 0002; exec /usr/lib/openssh/sftp-server'

and it worked fine for some reason.[/FONT]

---


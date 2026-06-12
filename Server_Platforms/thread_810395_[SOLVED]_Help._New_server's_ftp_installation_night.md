---
title: "[SOLVED] Help. New server's ftp installation nightmare. v8.0.4"
date: 2008-05-28
forum: Server Platforms
---

### Post by ez4me2c3d on 2008-05-28
I have taken a spin around the web, and these forums, looking for a simple answer to a simple question: "How do I setup FTP?"

I found a lot of tutorials on how to set this up, but none of them were targeted for my needs.  I ended up installing vsftpd frist via apt-get, then when that failed, I removed it, also with apt-get.  I then installed proftpd with apt-get.  I have since removed proftpd with apt-get, and attempted to reinstall vsftpd, once again, using apt-get.  That failed, as well as the proftpd install.

Here is what I see when I try to reinstall proftpd
```
root@www:/home/administrator/www# apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
The following packages were automatically installed and are no longer required:
  ssl-cert openssl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
root@www:/home/administrator/www#
```

and here is what I get when I try to remove it
```
root@www:/home/administrator/www# apt-get remove proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ssl-cert openssl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  proftpd
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
After this operation, 2552kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 22282 files and directories currently installed.)
Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@www:/home/administrator/www# 
```

I need some help from the community to get my server back to normal (P1) and get this FTP situation sorted out (P2).

I originally wanted to use the local user accounts (/etc/passwd) for FTP login, but perhaps it was this wish that got me to where I am today.  I will be open to taking instruction from the mob.

Please note some points about my setup:
1. I have Ubuntu 8.0.4 Server Edition -- So that means no GUI

2. I do not have local console access to the machine -- I use ssh over the network to access this server.  However, I do also have physical access to the server itself.

3. I am running LAMP on it currently.  That is my main role for this server, however I am trying to install joomla, and it requires an FTP service on the box.

4. This is my personal server, and it is not in a production environment.  I can do with it, whatever I please, but I do value a clean installation/configuration on my server.

Thanks to all in advance...
Anthony

---

### Post by NateMan on 2008-05-28
Have you tried the perfect server guide instead of automatically installing lamp? (if that is in fact what you did.) I'd recommend checking that out, it manually guides you through a lamp install and installs several other packages necessary to server usage, including proftpd. Check it out and try a fresh install if you feel up to it.

---

### Post by ez4me2c3d on 2008-05-28
I didn't use any guides while setting up the server, for the server installation is a guide in itself.  I probably should have had the foresight to know that I would someday need FTP services on my server, but at the time, I thought sFTP would be just fine.

I was hoping to avoid reinstalling the OS, considering I don't have a monitor keyboard and mouse for it.  But if no one else has a suggestion to what seems like a trivial problem, I suppose I shall.

thanks for being the first to respond.

---

### Post by NateMan on 2008-05-28
Its not as trivial a problem as you think. The automatic installers are not the best, manual install will always win. If this "trivial" problem pops up so quickly with a proftpd install, then I imagine that you have bigger issues that proftpd just not installing. That's why I recommend a fresh install. Fixing this problem would probably just be like putting a bandaid on a nasty cut. Besides you said yourself that you wish for a clean install, and the automated installation during your server install is very far from it. Here's a good guide. At least read through it and see what you missed by not doing it. Its an excellent entry into the world of server management.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by ez4me2c3d on 2008-05-28
I hear you.  I am saying it's trivial simply because it wasn't until I messed with the FTP portion did anything falter.  Plus, the rest of my server is still working fine.

The one thing that deos surprise me, is that you say the "tasks" I selected during the server install are no good.

I suppose I put too much faith into the people who wrote the installation program.

---

### Post by hyper_ch on 2008-05-29
why do you need ftp and why isn't sftp working?

---

### Post by ez4me2c3d on 2008-05-29
Because Joomla will only use FTP during the installation.

I was going through the setup process and it asked me for an FTP account that could write files to the web server's directory.

I suppose it was for when I upload files, and create new documents through the web interface??

I was thinking I should just install all of the options on the "perfect server" guide, and sit tight on them even if I don't use them.  This way, when the time comes for me to want...say, an e-mail server, it's already installed and ready to go.

---

### Post by hyper_ch on 2008-05-29
;) yeah, I like the falko's perfect howtos also ;)

---

### Post by jward3010 on 2008-05-30
In a terminal run:

```
sudo apt-get check
``` 

(this checks for broken packages and dependencies)

then

```
sudo apt-get autoremove
```

That might try and clean up packages that didn't install / uninstall well.

I'd love to see how this thread develops because, although I have just installed "proftpd" on my machine and on a laptop I have successfully connected to it, I'd love to know where I put the files that I want available through FTP.

---


---
title: "SSH Login Problem"
date: 2010-06-06
forum: Server Platforms
---

### Post by macmike on 2010-06-06
Hi had my server going pretty good. Two sites being hosted. wilmingtoncoc.com and mikealrhughes.com. Last night we had Thunderstorms and Tornadoes come through. While I was out Tornado chasing. We lost power here for an instant and back on. When I came in the server was off. So I booted it back up. The mikealrhughes.com site is still working good. The wilmingtoncoc.com site is giving me a Database read error, it is a WordPress site. Also I can't log into the Server using SSH. Where do I start to repair the problem? Do I reinstall SSH if so what is the command I use? Then how do I solve the WordPRess Database problem? Any and all help appreciate!! Also when I try and issue a command from the Server with sudo in front of it I get an error message that says - sudo: must be setuid root - whatever that means. I couldn't find that in any of the books I have.

Mike Hughes

---

### Post by cariboo on 2010-06-06
You probably have some corrupted files, boot from a Live CD and once at the desktop open a terminal and type:

```
sudo fsck -a /dev/sda1
```

change the partition to the one your data/web sites are on. A [ups]("http://en.wikipedia.org/wiki/Uninterruptible_power_supply") is cheap insurance to prevent the problem from happening again

---

### Post by macmike on 2010-06-06
Where can I get a live CD? True about the UPS. I have one on my other computer stuff. Will have to get one for the server. Once I run the command how do I change to the partition my server is on? I am a "Green Horn" when it comes to Linux. Most of my experience has been: DOS, Windows and Macintosh. Especially Macintosh.

Mike Hughes
A+, Network+ and MOS

---

### Post by Iowan on 2010-06-06
Ordinarily the install CD is also a Live CD.
(The Desktop, anyway. I presume the server is the same)

---

### Post by CharlesA on 2010-06-06
> **Iowan said:**
> Ordinarily the install CD is also a Live CD.
(The Desktop, anyway. I presume the server is the same)

Server CD will let you "fix a broken system" by dropping you to a root shell.

---

### Post by macmike on 2010-06-07
The $64,000 question is what do I do once I get to a shell. I don't know what command to issue to fix my broke system. Lost as a goose on this one.

---

### Post by lavinog on 2010-06-07
do a fsck as cariboo907 said.

A side note: many systems have a bios option to have the system power on after a power failure.  Also a battery backup could save you a lot of hassle in the future.

---

### Post by macmike on 2010-06-07
I have a UPC unit on this one. I tried the command that I was told. It will not take sudo without returning the error about sudo: must be setuid root.

Mike

---

### Post by linux-hack on 2010-06-07
sorry for being meen here but how can you run a linux server and not know even the basics commands in linux shell ??? how is you server security going ? first of all I strongly recommend you to learn some linux shell commands and follow some linux tutorials before administrating a linux server.

---

### Post by macmike on 2010-06-07
Sounds like the old adage don't go in the water until you learn how to swim. Circular reasoning. How are you going to learn to swim if you can't get in the water and you can't get into the water unless you learn how to swim so you never learn. 

No harm no foul. Learned DOS by doing and asking questions when getting stuck. Learned Windows an Mac the same way. Learned Microsoft Office the same way and am now MOS and on computer A+ and Network+. 

So how are you going to learn to administer a Server without jumping in there. Like I said this was going until the storm. I thought my UPC was ok. Apparently the battery needs changed out. Just want to get these errors solved. I don't know if there is a way to repair the install or not. I hate to have to format and reinstall the Server software. So I come to the forums and pick the brains of the experts. New what tutorials to read I would. Don't think I have a shell. Would love to get some program on here like Webmin so I don't have to use a command line.

Thanks for you comments though.

Dr. Mike Hughes, D.Min., Th.D. Ph.D.

---

### Post by lavinog on 2010-06-07
> **boogy9 said:**
> sorry for being meen here but how can you run a linux server and not know even the basics commands in linux shell ??? how is you server security going ? first of all I strongly recommend you to learn some linux shell commands and follow some linux tutorials before administrating a linux server.

What makes you think that he doesn't know the basic shell commands?
It looks like the OP is dealing with a corrupt system...not something basic.

---

### Post by macmike on 2010-06-08
bump

---

### Post by lavinog on 2010-06-08
> **macmike said:**
> I have a UPC unit on this one. I tried the command that I was told. It will not take sudo without returning the error about sudo: must be setuid root.

Mike

Did you do it from a live cd?

---

### Post by macmike on 2010-06-08
> **lavinog said:**
> Did you do it from a live cd?

Yes, It didn't make any difference. As a matter of fact I forgot I was on the Live CD and tried to SSH in this morning and had a different error message and thought something else happened to the Server install. When I came home and looked I realized I was still on the Live CD.

This is what I get when I try and login to SSH from a remote - Read from socket failed: Connection reset by peer


Mike

---

### Post by QuackPot10 on 2010-06-08
I can't get SSH to work either. It sucks real bad.

---

### Post by macmike on 2010-06-08
I have been searching in the forum and on the Internet for help to two of the errors I am getting on my server. 

sudo: must be setuid root 

and the - Read from socket failed: Connection reset by peer

I get when I try to use SSH from a terminal. 

I tried and at the local server to type commands that folks have used to correct these problems. I keep getting Operation not permitted. 

I even wanted to do an uninstall of openssh-server and reinstall and the same thing.

I just tried to do a apt-get php-admin 
I receive an error Could not open file /var/cache/apt/srcpkgcache.bin - open (13: permission denied)
The package lists or status file could not be parsed or opened.

---

### Post by noway2 on 2010-06-09
The first thing you probably need to fix is the inability to sudo.  From doing a little quick digging it looks like this is generally a permissions or ownership problem on /usr/bin/sudo (or the directory tree).  If you can get a live CD and run that it should let you bypass the corrupted files on your system and sudo on it.  You may also be able to try sudo -i to get a root shell prompt.  Sometimes the repair consoles will also have root access.  Undoubtedly you won't be able to do this from the server itself at the moment.

Then check the ownership and permissions of /usr/bin/sudo.  If necessary execute these commands to restore it:

chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo

---

### Post by lavinog on 2010-06-09
> **macmike said:**
> Yes, It didn't make any difference. As a matter of fact I forgot I was on the Live CD and tried to SSH in this morning and had a different error message and thought something else happened to the Server install. When I came home and looked I realized I was still on the Live CD.

This is what I get when I try and login to SSH from a remote - Read from socket failed: Connection reset by peer


Mike

So are you saying that using sudo from a live cd is giving a sudo: must be setuid root error too?

like noway2 mentioned, fixing sudo should be the priority.

---

### Post by macmike on 2010-06-09
> **lavinog said:**
> So are you saying that using sudo from a live cd is giving a sudo: must be setuid root error too?

like noway2 mentioned, fixing sudo should be the priority.

Yes

---

### Post by lavinog on 2010-06-09
Try this on the live cd:
```

sudo -i

```
does it still give an error?  If so you should make a new live cd.

---

### Post by macmike on 2010-06-09
Ok on the live CD 
sudo i 
returns to me root@ubuntu:

From the live CD how do I get down to my server installation? I tried C: and that didn't work. I know it isn't DOS.

---

### Post by macmike on 2010-06-09
> **cariboo907 said:**
> You probably have some corrupted files, boot from a Live CD and once at the desktop open a terminal and type:

```
sudo fsck -a /dev/sda1
```change the partition to the one your data/web sites are on. 

I ran the sudo fsck -a/dev/sda1 command from the root on the live CD. 
It told me that the sda1 was not unmounted correctly and had some corrupt files. 
I have search my book Ubuntu Linux Toolbox book and can't find the command to get me down to my Server1 once I do that. 

I tried from the Live CD root to issue the chown root:root /usr/bin/sudo and the
chmod 4111 /usr/bin/sudo command and it takes there.

So I rebooted the Server taking out the Live CD. I try to get to the root on the server then try and issue the sudo fsck -a /dev/sda1 command I get the error about sudo:must be setuid root.

Ok I just went into Server Rescue Mode. Was able to go down to Server1/root
I typed in sudo -i
get the following message - sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
I then issued command chown root:root /usr/bin/sudo and chmod 4111 /usr/bin/sudo
Seems to have took it.

now when I issue a sudo command I get /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting


Thanks for all your help.

Mike

---

### Post by lavinog on 2010-06-09
You so did fsck repair the drive?

You can use gparted (partition editor) from the live cd to check filesystems also.

There is no telling how corrupt your data might be.  You might want to do a fresh install instead of trying to repair it.  You should be able to backup most of your data.

If you still want to try:
When using the live cd you can mount by clicking on the drive in the places menu, and the drive will be mounted in /media
or you can mount it yourself with something like:
```
sudo mount /dev/sda1 /mnt
```

then you can do a chmod to sudoers
```

sudo chmod 0440 /mnt/etc/sudoers

```

---

### Post by macmike on 2010-06-09
That is what I thought about was do a fresh install. I wanted to some how get all the config files onto some backup like a flash Drive or a CD +R and then reinstall and put back on the configs without having to hand code everything. Especially the apache2.config and sites available and sites enable files. Thanks for the help. I will do a reinstall once I figure out how to back up the configs. I know WordPress is having trouble with its database and will not start. It tells me - [B]Error establishing a database connection 
[/B]

When I try to go to wilmingtoncoc.com

Everything I try is telling me permission denied.

Mike Hughes

---

### Post by macmike on 2010-06-09
> **lavinog said:**
> You so did fsck repair the drive?

You can use gparted (partition editor) from the live cd to check filesystems also.

There is no telling how corrupt your data might be.  You might want to do a fresh install instead of trying to repair it.  You should be able to backup most of your data.

If you still want to try:
When using the live cd you can mount by clicking on the drive in the places menu, and the drive will be mounted in /media
or you can mount it yourself with something like:
```
sudo mount /dev/sda1 /mnt
```then you can do a chmod to sudoers
```

sudo chmod 0440 /mnt/etc/sudoers

```

Ok booted with the Live CD and did all of this, shutdown and came back up into the server still getting the message when try and do a sudo that sudo: /etc/sudoers.d/README is mode 0777, should be 0440 
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting

---

### Post by lavinog on 2010-06-09
I guess you are going to need to do the chmod for each file you get that error for.

Do you have access to an external drive?
You can use the live cd to copy all of the files from the system to an external drive, then do a fresh install and use the external drive to move your files back.

You might want to start a new thread for recovering your wordpress database after a new install...I don't think I could be much help with that.

---

### Post by macmike on 2010-06-10
Ok, I did a new install of Ubuntu on to a different HD. This time I did desktop version first and then added the lamp server files to it. I tried and put the old drive back in as a slave. I can see it on the desktop but can't see the SERVER1 files to be able to bring the config, sites-enabled and website files over. 
Also I tried to do a sudo apt-get install openssh. 
Comes back with a message
E: Couldn't find package openssh

Mike

---

### Post by lavinog on 2010-06-10
it helps use tab to complete package names
the package should be openssh-server

if you type sudo apt-get install openssh[tab][tab]  it should add a hyphen with the first tab, and show you the possible choices with the second.  Then if you add an 's' then press tab again it should finish typing out 'server'

when you mount the drive, you should see an etc folder, inside that there should be an apache2 folder that contains the config files.

---

### Post by macmike on 2010-06-10
Ok I have gotten the ssh thing sorted can ftp remotely into the server ok. Got my web files on the server. But now can't see the Domains from the internet or locally. I have checked the Router everything I need to forward is forwarding. I checked the Firewall on the Server it is allowing the services in. I can't even see the Domains through Firefox locally on the server GUI. Any ideas?

---

### Post by lavinog on 2010-06-10
is the server setup for a static ip address?

---

### Post by macmike on 2010-06-10
Yes

I can see the domains now.  I have the following error when I restart apache2

 Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Jun 10 19:49:42 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Jun 10 19:49:42 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

I did manage to get my WordPress going. Had to install phpmyadmin and make a database. Once I get this last set of stuff above fixed. I am going to back up this puppy. Did get a new UPS today. Now if I can figure out how to get Webmin running!

---


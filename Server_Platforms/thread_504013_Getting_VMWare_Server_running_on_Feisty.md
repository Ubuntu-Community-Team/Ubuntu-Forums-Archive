---
title: "Getting VMWare Server running on Feisty"
date: 2007-07-18
forum: Server Platforms
---

### Post by Maxtorm on 2007-07-18
[FONT=Trebuchet MS][SIZE=3]I think I have finally been successful in getting a [/SIZE][/FONT][FONT=Trebuchet MS][SIZE=3]VMWare Server running on an ubuntu-server install (Feisty) without a gui -- the primary reason being that I wanted as little O/S overhead as possible.  [/SIZE][/FONT][FONT=Trebuchet MS][SIZE=3]Since there were a couple of hurdles, thought others doing the same might find the following helpful.

To get VMWare Server 1.0.3 up and running (all following commands are done as su):

```
apt-get install xinetd build-essential libx11-dev libXtst-dev libXt-dev libXrender-dev
apt-get install linux-header-`uname -r`
cd /usr/src
ln -s /lib/modules/2.6.20-15-server/build linux
```[/SIZE][/FONT][FONT=Trebuchet MS][SIZE=3]
[SIZE=2]* The last two lines aren't strictly necessary, but it allows you to accept the default location that the VMWare installer looks for the kernel headers.[/SIZE][/SIZE][/FONT][FONT=Trebuchet MS][SIZE=3]

Assuming you already have the tar.gz file for VMWare Server, extract it into an appropriate folder.

Download the kernel patch to get vmmon to load correctly:
```
wget http://ftp.cvut.cz/vmware/vmware-any-any-update110.tar.gz
```Remainder of instructions for patch can be found here: [http://www.kvaes.be/unix-linux/ubuntu-704-feisty-vmware-server/](http://www.kvaes.be/unix-linux/ubuntu-704-feisty-vmware-server/)
Short version: extract it and execute runme.pl.  It will fire up the VMWare installer when the patch completes.  (Keep an eye on the ftp directory at [http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/) because the version number may change as the patch gets updated.)

That's it!  You should now be able to connect remotely to the VMWare server using the VMWare Server Console.

[/SIZE][/FONT][FONT=Trebuchet MS][SIZE=3]P.S. If anyone knows of a package that provides libx11-dev libXtst-dev libXt-dev libXrender-dev without a lot of bloat, please post here.  Thanks![/SIZE][/FONT]

---


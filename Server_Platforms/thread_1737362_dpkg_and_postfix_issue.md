---
title: "dpkg and postfix issue"
date: 2011-04-23
forum: Server Platforms
---

### Post by TheFu on 2011-04-23
This morning I was performing my weekly patch management and a bunch of the 8.04.x LTS Ubuntu servers all failed to patch.

[FONT=Courier New]# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  dhcp3-client dhcp3-common postfix
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1664kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? 
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 1.
Use of uninitialized value in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 70, <$__ANONIO__> chunk 1.
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/FONT]
There is plenty of storage available.  I tried to uninstall postfix (it is a satelite system), but that failed in a similar manner. dpkg-recofigure failed too.  These systems are all single purpose and well maintained. No funny repositories, only packages for specific purposes are installed and patched weekly.

The DHCP packages are uninmportant - guess they were installed during the server install. The servers all have static IPs and are not the DHCP server for this subnet.

I believe there is an issue with the postfix package recently released.  Can someone else please confirm?

Tuned out the** file system was out of inodes.**  Use [FONT=Courier New]df -i [/FONT]to see the current amount available.  In almost 25 yrs, I've never seen a file system run out of inodes. I think EXT3 and newer file systems allocate plenty by default. This was an EXT2 setup.

---

### Post by elico on 2011-04-24
well apt-get told you a thing:
> After this operation, 4096B of additional disk space will be used.
it's not a space issue..
what you can try is using aptitute to do update and then upgrade.
and if you don't need the dhcp just purge\remove it.
and then try to install only postfix
apt-get install postfix
to upgrade only postfix.
also you can download the last postifx deb file and see if you do get any problems using the local file.

[FONT=Courier New]
[/FONT]

---


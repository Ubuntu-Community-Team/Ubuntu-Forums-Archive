---
title: "pxe booting - fails"
date: 2010-01-21
forum: Server Platforms
---

### Post by dmatusow on 2010-01-21
I have a server, which I'll call pxeserver (hp dl140), that boots off a lan.  I built a tftp server and modified my dhcpd.conf file to define this server.  So far, so good.  I see the server get the defined address, but things stop there.
 
I tested the tftp server and things work (tftp connect from another machine and both download and put work fine).
 
In this case, there seems to be some disconnect on getting the download.  See the syslog attached.  I never see the download even start.  What is wrong here?
 
I am a newbie in setting up a lan boot.  Once I get past this point (which I'm sure is something stupid), I'm not sure how to define the specific configuration to get loaded (image, packages, etc).  I see that initrd seems to be how this is done.  Any ideas on where to get intro on how to get this specified.
 
I downloaded netboot.tar and the file/directory structure is default at this point.  It appears that things are setup correctly on that side.

---

### Post by koenn on 2010-01-21
it's not a disconnect - your server is trying to serve defaul a number of default boot images, and fails.
Probably means you have not or inaccurately specified which file the clients should download from the tftp server. This is a dhcp option you (may) need to set

try this mini-howto to learn how pxe works,  [http://users.telenet.be/mydotcom/howto/linux/diskless01.htm](http://users.telenet.be/mydotcom/howto/linux/diskless01.htm)
then try to correct your dhcp conf

---

### Post by dmatusow on 2010-01-21
koenn,
 
I have already entered the dhcpd.conf entries and setup the files for bootp/pxe.  
 
In dhcp.conf, I entered:
 
allow bootp;
allow booting;
 
Within the definition for the pxeserver, I entered:
 
filename "pxelinux.0";
 
You can see it referencing the pxelinux.0 file, as well as the embedded files for the image.
 
I recopied the syslog for review.  You can see that the tftp server looks for pxelinux.0, as well as the config file, but never does seem to send it.  Not sure why.
 
I can initiate a tftp request from windows and get it just fine, so I assume that this is setup correctly.
 
The default configuration sets up a menu to allow loads as desired.  I edited the file to only have :
 
kernel ubuntu-installer/i386/linux
append vga=normal initrd=ubuntu-installer/i386/initrd.gz --
 
It is VERY possible that this will not work correctly, but it should load...and possibly fail after loading.

---

### Post by koenn on 2010-01-22
ah, OK, I must have missed that pxelinux.0 line in your log the first time. 

so, next guess is that the file is not there where your tftp server expects it, or that it's not world readable (and that you somehow correct this when you try to simply download the file)

maybe look into that, or post details  (eg output of "ls -l /ftpboot" on the server , and the parameters with which you test your tftp download from windows)

---

### Post by dmatusow on 2010-01-22
(I think I missed getting the pxelinux line over before :(
 
[FONT=Arial]-rw-r--r-- 1 david family 9705723 2010-01-22 08:43 boot.img.gz
-rwxr-xr-x 1 david family 9830400 2010-01-22 08:43 netboot.tar
lrwxrwxrwx 1 david family      32 2010-01-22 08:45 pxelinux.0 -> ubuntu-installer/i386/pxelinux.0
lrwxrwxrwx 1 david family      34 2010-01-22 08:45 pxelinux.cfg -> ubuntu-installer/i386/pxelinux.cfg
drwxr-xr-x 3 david family    4096 2009-07-08 17:19 ubuntu-installer[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]on the tftp test, nothing fancy:[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]tftp ubuntu get netboot.tar[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]completes successfully[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks for your help :)[/FONT]

---

### Post by koenn on 2010-01-22
> **dmatusow said:**
> 
[FONT=Arial]tftp ubuntu get netboot.tar[/FONT]

[FONT=Arial]completes successfully[/FONT]

ah, interesting. 
all this tests is that tftp us working. 
You should try to 'get pxelinux.0', because that's what's supposed to happen for the pxe boot



> **dmatusow said:**
> 
[FONT=Arial]-rw-r--r-- 1 david family 9705723 2010-01-22 08:43 boot.img.gz
-rwxr-xr-x 1 david family 9830400 2010-01-22 08:43 netboot.tar
lrwxrwxrwx 1 david family      32 2010-01-22 08:45 pxelinux.0 -> ubuntu-installer/i386/pxelinux.0
lrwxrwxrwx 1 david family      34 2010-01-22 08:45 pxelinux.cfg -> ubuntu-installer/i386/pxelinux.cfg
drwxr-xr-x 3 david family    4096 2009-07-08 17:19 ubuntu-installer[/FONT]
hm.
this shows that pxelinux.cfg and pxelinux.0 are in a subdirectory of ftpboot. We can assume that the links (eg pxelinux.cfg -> ubuntu-installer/i386/pxelinux.cfg) would work also, but it doesn't show that ubuntu-installer/i386/pxelinux.cfg is actually world-readable (permissions on links don't count)

simpliest way to test now is that you copy pxelinux.cfg and pxelinux.0 from ./ubuntu-installer/i386 to /tftpboot, and set them  world-readable (chmod o+r /tftpboot/pxelinux.cfg ; and likewise for pxelinux.0 ), then try again.

---

### Post by dmatusow on 2010-01-22
all worked correctly, but pxelinux.cfg in that directory is actually another directory.  Thus, the download fails, but the file below (default) works.
 
Here's the ls:
total 9592
drwxr-xr-x 2 david family    4096 2009-07-08 17:19 boot-screens
-rw-r--r-- 1 david family 7848094 2009-07-08 17:19 initrd.gz
-rw-r--r-- 1 david family 1924856 2009-07-08 17:19 linux
-rw-r--r-- 1 david family   14146 2009-07-08 17:19 pxelinux.0
drwxr-xr-x 2 david family    4096 2009-07-08 17:19 pxelinux.cfg
drwxr-xr-x 2 david family    4096 2009-07-08 17:19 pxelinux.cfg.serial-9600

---


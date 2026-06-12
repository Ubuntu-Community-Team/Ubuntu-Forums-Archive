---
title: "install HP Library &amp; Tape Tools on Ubuntu from  RHEL rpm"
date: 2011-01-19
forum: Server Platforms
---

### Post by m.ardito on 2011-01-19
Hi, 

i want to share information for who is trying to install HP LTT (library & tape tools) on ubuntu systems.
i had an old IBM x232 server (ex windows server, dismissed), on which is now instlled ubuntu 8.04 lts (the desktop version)

the system has a hw raid array (IBM serveraid x4, is really an adaptec board) and, due to the lack of open source tools to manage it (the only adaptec tools available work with newer raid controllers), i recently managed to install the IBM serveraid manager and agent (a gui java implementation), following an online guide i found here:

[http://ubuntuforums.org/showthread.php?t=597256](http://ubuntuforums.org/showthread.php?t=597256) 

(i only found minor glitches in the install bash script, mainly in the raid_aget launch script wich uses the 'cut' command extracting chars 0 to 6 from a string, and bash complains that now 'cut' char index starts from '1' and not from '0' so...i changed a "cut -b0-6" to "cut -b1-7").

then i had an external scsi ultrium drive (just to test), and started to look for some scsi/tape management tools

soon i downloaded lsscsi, via 

```
sudo apt-get install lsscsi
```and lsscsi confirmed that the tape colud be "seen" by ubuntu.

then i remembered there was an hp tool whan i used an hp autoloader on windows, and went looking for a ubuntu/debian version.

unfortunately, there are not.

somewhere on hp support sites appears that debian is (or was) supported, but if you use the web site forms to download the software,

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?pnameOID=406731&locale=en_US&taskId=135&prodSeriesId=406729&prodTypeId=12169](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?pnameOID=406731&locale=en_US&taskId=135&prodSeriesId=406729&prodTypeId=12169)

you will find only RHEL/RHL or SLES linux versions supported, aside windows, and other oses.

i also found a support forum where someone appearing to be one of this tools's mantainers said that although not supported it could (should) be compatible with debian also. This, and a basic knowledge of the guide i mentioned above, brought me to try to install the RHEL package on ubuntu, anyway. And succeeded :-) it works.

here's how:

1) go  here

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?pnameOID=406731&locale=en_US&taskId=135&prodSeriesId=406729&prodTypeId=12169](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?pnameOID=406731&locale=en_US&taskId=135&prodSeriesId=406729&prodTypeId=12169)

2) download the most recent package for RHEL (it's realy the same package for all linux variants, but i needed a rpm version). I found this HP StorageWorks Library and Tape Tools     4.11 15 Sep 2010, and got my hp_ltt411_linux.tar archive from 

[ftp://ftp.hp.com/pub/softlib/software11/COL21415/co-87453-1/hp_ltt411_linux.tar](ftp://ftp.hp.com/pub/softlib/software11/COL21415/co-87453-1/hp_ltt411_linux.tar)

on my desktop

3) then i installed (already did) fakeuser and alien packages from terminal:

```
sudo apt-get install fakeroot alien</code>

4) then i extracted tar content 

[CODE]tar -xvf hp_ltt411_linux.tar
```ending with a file, install_hpltt (of which you can forget about)
and a rpm package, ltt-4.11.0.0-4.i386.rpm

5) then i converted the rpm in deb (with scripts, option -c)
```
fakeroot alien -c ltt-4.11.0.0-4.i386.rpm
```and soon i got my ltt-4.11.0.0-4.i386.deb on the desktop

6) then i made a folder with DEBIAN subfolder
and in that folder i processed the deb with dpkg as 


```

 mkdir -p ltt-4.11.0.0-4.i386/DEBIAN
 dpkg -x ltt_4.11.0.0-4_i386.deb ltt_4.11.0.0-4_i386/
 dpkg -e ltt_4.11.0.0-4_i386.deb ltt_4.11.0.0-4_i386/DEBIAN/

```7) then i studied the scripts a bit and noted that the "ltt_4.11.0.0-4_i386/DEBIAN/preinst" script only checked for "supported" linuxes through some bash command but allowed one to "force" installation, assuming the risks.

i then decided to delete the "ltt_4.11.0.0-4_i386/DEBIAN/preinst" script fro the folder and repackage the deb

```

rm ltt_4.11.0.0-4_i386/DEBIAN/preinst
dpkg -b ltt_4.11.0.0-4_i386/ ltt_4.11.0.0-4_i386.deb

```8 ) so ltt_4.11.0.0-4_i386.deb was rebuilt from the folder, without any preinst script.

now, time to install it with dpkg:

```

 dpkg -i ltt_4.11.0.0-4_i386.deb

```9) then launch /opt/ltt/hp_ltt

```

 sudo /opt/ltt/hp_ltt

```10) ...and it works! it has a text-based ugly gui that runs in terminal, but, hey! it works!
and is able to scan my drives/tapes and query my ultrium unit! nice....


Hope it helps

Marco

---

### Post by xMaximex on 2011-01-25
Thanks ! It worked perfectly on Ubuntu Server 8.04

You just saved me alot of hassle with HP not supporting their products on Ubuntu

---

### Post by Arthemys on 2011-06-06
Using 10.10 server and it's giving me some headaches.

```


cparker@leopard:~$ sudo alien -c ltt-4.12.0.0-4.i386.rpm 
Use of uninitialized value $postinst in length at /usr/share/perl5/Alien/Package/Deb.pm line 741, <GETPERMS> line 418.
ltt_4.12.0.0-5_i386.deb generated


```
And there is no .deb file created. Any hints?

---

### Post by Arthemys on 2011-07-20
Tried again with version 4.13 and the x86_64 build, and it worked as per the directions.

---


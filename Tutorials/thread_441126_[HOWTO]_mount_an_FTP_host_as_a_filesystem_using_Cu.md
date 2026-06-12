---
title: "[HOWTO] mount an FTP host as a filesystem using CurlFtpFS"
date: 2007-05-12
forum: Tutorials
---

### Post by geco on 2007-05-12
This how-to is intended to help those who want to mount an FTP site as a filesystem using [CurlFtpFS]("http://curlftpfs.sourceforge.net/").

Yesterday I was told I could mount an FTP site as a filesystem using CurlFtpFS, but I found that on ubuntuforums it isn't well explained. So I searched around the web and the forum posts and finally I have been able to mount properly my FTP site. I decided to make this post to summarize all the information I found to help ubuntu users who want to install CurlFtpFS.

First of all, I'm using Ubuntu 6.10 Edgy Eft, but I think you can use this post also whit other Ubuntu versions. If it's the case, don't hesitate to post your problems, suggestions, etcetera.

cURLftps package isn't available in Ubuntu, so I downloaded it from Debian. Anyway you must satisfy some dependencies and so you must upgrade some other packages.

EDIT: A curlftpfs backport to Edgy is available thanks to mlind here: [curlftpfs-0.9.1-1_edgy.tar.bz2 ]("http://ubuntuforums.org/attachment.php?attachmentid=32534&d=1179099233") so now you have two ways for installing it.

EDIT: curlftpfs is available for _**Feisty**_ and **_Gutsy_**

[SIZE=4][COLOR=Red]**Installing Feisty or Gutsy packages**[/COLOR][/SIZE]

use aptitude or apt-get (I prefer the first one)
```

sudo aptitude install curlftpfs

```
then proceed to the configuration as explained in the Edgy part and in the common part of this how-to

[SIZE=4][COLOR=Red]**Installing DEBIAN packages**[/COLOR][/SIZE]

[mlind's advice]("http://ubuntuforums.org/showthread.php?t=441141") is no to use too many packages from other distribution, so if you want, you can skip this part and try to install the Edgy backport. Anyway, also the second way is a little bit tricky.

Download the following packages from [http://packages.debian.org](http://packages.debian.org) (**testing**) for your processor architecture:

libgpg-error0: [http://packages.debian.org/testing/libs/libgpg-error0](http://packages.debian.org/testing/libs/libgpg-error0)

libgpg-error-dev: [http://packages.debian.org/testing/libdevel/libgpg-error-dev](http://packages.debian.org/testing/libdevel/libgpg-error-dev)

libcurl3-gnutls: [http://packages.debian.org/testing/libs/libcurl3-gnutls](http://packages.debian.org/testing/libs/libcurl3-gnutls)

fuse-utils: [http://packages.debian.org/testing/utils/fuse-utils](http://packages.debian.org/testing/utils/fuse-utils)

curlftpfs: [http://packages.debian.org/testing/utils/curlftpfs](http://packages.debian.org/testing/utils/curlftpfs)

Install them; supposing you have put them in the folder curlftpfs do:
```

cd curlftpfs
sudo dpkg -i *.deb

```If it is all ok you can proceed to edit your /etc/fstab file.
Use the following command to append the curlftpsfs option to /etc/fstab
```

sudo echo "curlftpfs#ftpusername:ftppassword@ftp.site.address /path/to/mountpoint fuse allow_other,uid=userid,gid=groupid 0 0" >> /etc/fstab

```Where
_ftpusername_ is the username to log in the FTP site
_ftppassword_ is the password to log in the FTP site
_userid_ and _groupid_ are respectively the uid and the gid of your current user _of your computer_; 
you can discover them typing
```

id

```in a shell (this will print your user and groups IDs).

[SIZE=4][COLOR=Red]**Installing EDGY packages**[/COLOR][/SIZE]
download the Edgy backport: [curlftpfs-0.9.1-1_edgy.tar.bz2 ]("http://ubuntuforums.org/attachment.php?attachmentid=32534&d=1179099233")

be sure to meet the following dependencies: libc6 (2 2.4-1) libcomerr2 (2 1.33-3) libcurl3 (2 7.15.4-1) libfuse2 (0 (null)) libglib2.0-0 (2 2.12.0) libidn11 (2 0.5.18) libkrb53 (2 1.4.2) libssl0.9.8 (2 0.9.8b-1) zlib1g (2 1:1.2.1) fuse-utils (0 (null))

decompress the archive in an empty directory (or create a new one)
```

mkdir curlftps-edgy
tar xvjf curlftpfs-0.9.1-1_edgy.tar.bz2 -C curlftps-edgy

```install the edgy backport
```

sudo dpkg -i curlftpfs_0.9.1-1_i386.deb

```If it is all ok you can proceed to edit your /etc/fstab file.

Use the following command to append the curlftpsfs option to /etc/fstab
_note that this is different from debian packages procedure due to the different curlftpfs version_
```

sudo echo "ftpusername:ftppassword@ftp.site.address /path/to/mountpoint curlftpfs rw,allow_other,uid=userid,gid=groupid 0 0" >> /etc/fstab

```last step is to let mount recognize the filesystem type:
```

sudo ln -s /usr/bin/curlftpfs /sbin/mount.curlftpfs

```


[SIZE=4][COLOR=Red]**common part**[/COLOR][/SIZE]

Now you need your non-root user to be able to mount the FTP site without sudo.

Change the group owner of your ftp mountpoint:
```

chgrp fuse /path/to/mountpoint 

```be sure that fuse group has write permission on the directory
```

sudo chmod g+w /path/to/mountpoint

```Add your current user to fuse group:
```

addgroup username fuse

```Maybe you should logout and then login again to apply this change.

That's all, now you should be able to mount your preferred FTP site as it were an hard disk.

Thaks to:
Shinda [http://ubuntuforums.org/showthread.php?t=318824](http://ubuntuforums.org/showthread.php?t=318824)
Koybe [http://ubuntuforums.org/showthread.php?t=369895](http://ubuntuforums.org/showthread.php?t=369895)
Mlind [http://ubuntuforums.org/showthread.php?t=441141](http://ubuntuforums.org/showthread.php?t=441141)

---

### Post by geco on 2007-05-16
waiting for this post to be approved I asked for Ubuntu packges here:

[http://ubuntuforums.org/showthread.php?p=2664733#post2664733](http://ubuntuforums.org/showthread.php?p=2664733#post2664733)

as curlftpfs is available for Feisty and Gutsy you can skip the Debian Packages download part.

anyway, maybe curlftpfs will be available for Dapper and Edgy too.

---

### Post by goodtimetribe on 2007-05-18
I had to add a 

```
curlftpfs ftp://my.ftpsite.com /mount/point/
```

to my startup. I found it on the curlftpfs web site. It wasn't exactly easy, but it works wonderfully. Thanks for the howto!

---

### Post by floyd24 on 2007-05-23
For AMD64-users (like me *g*) the edgy-package won't work since it links to some 32bit-Version of libcurl.so.2. I installed it with --force-architecture, but it always brought up an error like "missing library libcurl.so.2 - No such file or directory". Trying to link to the library in /usr/lib(64) gave me an "wrong ELF" error - of course.

Anyway, it works beautifully when installed from source. Download the latest source package (in my case 0.9.1) from Sourceforge ([http://sourceforge.net/projects/curlftpfs/](http://sourceforge.net/projects/curlftpfs/)). Untar it somewhere and do the obligatory

  # ./configure
  # make
  # make install

I did a fresh apt-get upgrade beforehand and had to install libcurl3-dev and libfuse2-dev (iirc), so if configure complains, just try to install any missing fuse or curl packages for Edgy, having an special eye on the -dev ones which are needed.

The make procedure dropped the binary in /usr/local/bin which gave me an error when trying to invoke it directly

  # curlftpfs -V
  bash: curlftpfs: command not found

Maybe it was because I dpkg-installed and removed the abovementioned Edgy-Packet before. So I did a quick

  # ln -s /usr/local/bin/curlftpfs /usr/bin/curlftpfs

And now curlftpfs -V gave me some nice version information, telling me thereby that all seemed to work fine. And indeed it did, at least mounting an FTP-Host directly. Didn't try the fstab-version yet.

Hope this is of Help to anyone and thanks for the good Information on the topic so far, guys. Hope this has been a one-time-hassle for me until I upgrade to feisty.

PS: The manpage was not installed correctly here, either. But you can bring it up with 

  $ man /usr/local/share/man/man1/curlftpfs.1

---

### Post by Jonne on 2007-05-25
I'm trying this in Feisty (by adding it to fstab), but when I have to do 'chgrp fuse /media/nas' (either as root or as me) it says: 'Operation not permitted'.

Anyone know why?

i bought a nas, and i initially planned to mount it as a smb share, but smb is way too slow for this (and it hangs nautilus on folders with many files for some reason). Ftp works better (i get double the speed when i transfer files with Filezilla, so i want to be able to do this).

Are there any drawbacks to using ftp to share a folder like this, btw?

edit: i fixed the first issue, and it mounts fine, but now i get this:
```
jonne@fry:~$ cd /media/nas
jonne@fry:/media/nas$ ls
media
jonne@fry:/media/nas$ cd media/
jonne@fry:/media/nas/media$ ls
ls: reading directory .: Input/output error
jonne@fry:/media/nas/media$ 
```

media is a folder on the share, and contains 2 folders: music and video.

---

### Post by lospo on 2007-11-18
Hi, i've got a rouble mounting FTPFT with fuse (or any other commandline sw...) because my ISP (aruba.it) send me these detais:

Host : [ftp://ftp.MySite.com](ftp://ftp.MySite.com)
Login : 123456**@aruba.it**
Pass: 123456

When i try to connect with 
[PHP]
 curlftpfs ftp://123456@aruba.it:123456@ftp.MySite.com /mnt/tda/
[/PHP]

i've got this error:
[PHP]
Error connecting to ftp: Couldn't resolve host aruba.it:123456@ftp.terredegliangeli.com'
[/PHP]

Too Many "@", ithink.

If someone has a solution... let me know....

---

### Post by Knah Tsaeb on 2007-11-20
Host : [ftp://ftp.MySite.com](ftp://ftp.MySite.com)
Login : [email]123456@aruba.it[/email]
Pass: 123456

> curlftpfs [ftp://123456](ftp://123456)[COLOR="Red"]%40[/COLOR]aruba.it:123456@ftp.MySite.com /mnt/tda/

---

### Post by hencethus on 2007-12-02
This works fine for me until I try to delete a file. I get an error about a transport endpoint. Then when I try to remount I get this:
```
michael@michael-desktop:~$ sudo mount -a
fuse: bad mount point `/media/xbox': Transport endpoint is not connected
```

---

### Post by simd on 2007-12-11
> **hencethus said:**
> This works fine for me until I try to delete a file. I get an error about a transport endpoint. Then when I try to remount I get this:
```
michael@michael-desktop:~$ sudo mount -a
fuse: bad mount point `/media/xbox': Transport endpoint is not connected
```

I get the same error. Libcurl in the 7.10 repository  doesn't seem to be the latest version 7.16.4 vs. 7.17.1 from source, so it's difficult to know if it has been fixed.

I've installed libcurl from source, and curl reports it's using libcurl 7.17.1. However, curlftpfs still reports 

curlftpfs 0.9.1 libcurl/7.16.4 fuse/2.5 

I'm not sure how to make curlftpfs use the latest library I've installed to see if this resolves the problem. 

(I've seen many mentions of this across the Internet so it does seem to be a general problem for Ubuntu users who have upgraded to v7.10).

Best wishes,
David.

---

### Post by simd on 2007-12-11
> **simd said:**
> 
I'm not sure how to make curlftpfs use the latest library I've installed to see if this resolves the problem. 

(I've seen many mentions of this across the Internet so it does seem to be a general problem for Ubuntu users who have upgraded to v7.10).


OK, fixed my own problem and curlftfs is now working (or seems to be from the limited testing I've carried out). 

In short the solution seems to be:

1. Download the latest curl source (7.17.1 at the time of writing) from [http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)

2. Compile and install the downloaded version of curl.

3. Copy the new version of curl from /usr/local/lib to /usr/lib. You may need to amend the symbolic link for libcurl.so.3 and libcurl.so.4 in that folder to point at the new libcurl.so.4.0.1.

curlftpfs should now see the new version and everything should be well.

This is a workaround until Ubuntu's curl version has been updated to the latest by the maintainer, which would avoid these steps and automatically install the new version via an update.  

Best wishes,
David.

---

### Post by kpkeerthi on 2007-12-11
This is unbelievably cool. I never thought it would be possible to mount FTP host as a filesystem. Thanks a million to geco for letting me know about this wonderful tool. 

I use an ftp site that has tons of media but no search facility neither does my ftp client. With curlftpfs, I can now use regular expressions with **find ** command to search what I need (as if I'm searching a filesystem locally). Thanks again.

---

### Post by monteleo on 2008-01-28
I use kubuntu Gutsy and I have the same problem of Jonne, It mounts fine but:

> monteleo:~# cd /media/upnp/
monteleo:upnp# cd Videos/
monteleo:Videos# ls
ls: reading directory .: Input/output error
monteleo:Videos#   

how to solve the I/O read error?
Thanks for your help

---

### Post by Jonne on 2008-01-28
just FYI, I solved the problem by using smb anyway. If you're mounting a NAS or something, smb works fine. (I wanted to use FTP because of a bug in the firmware of the NAS, but that bug got fixed).

---

### Post by zzelinski on 2008-02-18
I got it to work, but I have one problem-- it doesn't mount through fstab with the rest of the drives when I boot up. I actually need to "mount -a" in order for it to show up. Any ideas?

---

### Post by haplo_dk on 2008-07-13
> **simd said:**
> OK, fixed my own problem and curlftfs is now working (or seems to be from the limited testing I've carried out). 

In short the solution seems to be:

...

Best wishes,
David.

That did the trick for me - Thank you very much ! :)
I had the same problem when trying to save/delete/rename a file it would say "transport endpoint not connected", and I could not access the mount-point anymore (the directory was listed using ls, but there was no access to it) untill I wrote
sudo fusermount -u <mount-point>
to unmount it.
But now it works - Thanks ! :)
/Anders:)
using 7.10 gutsy gibbon (32 bit version)
PS: I've also only done limited testing with this solution, but it seems to work fine.

---

### Post by mickinator on 2008-08-27
Right, I had set my mount point to be my home directory, using the nonempty option... bad idea... lost access to all my files, apart from my mounted ftp.

Won't be doing that again.

Best advice is just to use your an empty folder for your mounts.

As for the person who has to mount everytime, just add a command like

sleep 30 && mount -a to your sessions, or add the same to your /etc/rc.local

---

### Post by Crafty Kisses on 2008-08-28
Nice tutorial. :)

---

### Post by Skerit on 2008-12-05
This is my fstab line:

```
curlftpfs#login:Password,with,commas@ftp.host.com /media/host curlftpfs  rw,allow_other,uid=skerit,gid=skerit 0 0
```

It keeps giving me this error:
```
Error connecting to ftp: Access denied: 530
```

Login and password are correct (There are commas in the password, though)

If I remove the first "curlftpfs#" or if I use "fuse" instead of "curlftpfs" I get this error:

```
fuse: unknown option `MEK'
```

Edit: I tried it with a user which has NO commas in the password, and it DID work, so that must be it? Can the password be saved outside of the fstab file?

---

### Post by Jonne on 2008-12-05
have you tried escaping the commas ( \, ) or urlencoding ( %2C ) them?
as for external files, i know you can do that with smb/cifs ( ... curlftpfs credentials=/path/to/file/pwd,rw,allow,... , not sure if you can do it with ftp)

---

### Post by kevinguillorytraining on 2009-10-10
That's one of the best tutorial. Thanks

---

### Post by vhex on 2010-08-24
Skerit, for the record, you can prefix commas with double backslashes, e.g.:

```
curlftpfs -o user=xxx:yyy\\,zzz
```

---

### Post by aminix on 2011-12-12
Hi all,

sorry for my bad english in advance.

i try this tutorial. It is all OK when i mount the fstab via the terminal with the mount -a command.

But during the boot the system tell me that it is impossible to mount /media/NASF101 and to press the 'S' key to continue without mounting or 'M' for manually mount.

Actually i work with Ubuntu 10.10.

Can someone help me ?

Ciao
Flavio

---


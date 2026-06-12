---
title: "apt-get install problems (any package)"
date: 2006-08-02
forum: Server Platforms
---

### Post by michaluxa on 2006-08-02
Hi all,

I have a problem with installing ANYTHING with apt-get at the moment.

Here is one example log showing the problem:

root@server1:/home/micha# apt-get install nmap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  nmap
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/705kB of archives.
After unpacking 2437kB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/nmap_4.03-3_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `ppp': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/nmap_4.03-3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server1:/home/micha# 

The same happens with other packages, too, including apt-get upgrade (packages need updating).

My repositories in /etc/apt/sources.list look like this:

#---start---
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#--- end ---

Any idea anybody what I can do?

Cheers,

Micha

---

### Post by Paerez on 2006-08-02
do you always get:
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/nmap_4.03-3_i386.deb (--unpack):
```
or does the name of the deb file change each time? If you always get this same package, just type:
```
sudo rm /var/cache/apt/archives/nmap_4.03-3_i386.deb
```
then try again.

---

### Post by michaluxa on 2006-08-02
Thank you for your reply, Paerez.

It is not always the same package. 

For example when I do an apt-get upgrade (apt-get update works fine) I also get this error.

this is the log:

root@server1:/home/micha# apt-get upgrade

Reading package lists... Done

Building dependency tree... Done

The following packages have been kept back:

  linux-image-server

The following packages will be upgraded:

  apache2 apache2-common apache2-mpm-prefork apache2-utils libapr0 libfreetype6

6 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Need to get 1659kB of archives.

After unpacking 0B of additional disk space will be used.

Do you want to continue [Y/n]? Y

Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libapr0 2.0.55-4ubuntu2.1 [132kB]

Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main apache2 2.0.55-4ubuntu2.1 [35.8kB]

Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main apache2-mpm-prefork 2.0.55-4ubuntu2.1 [198kB]

Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main apache2-common 2.0.55-4ubuntu2.1 [786kB]

Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main apache2-utils 2.0.55-4ubuntu2.1 [91.7kB]

Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libfreetype6 2.1.10-1ubuntu2.2 [415kB]

Fetched 1659kB in 24s (68.9kB/s)

(Reading database ... dpkg: error processing /var/cache/apt/archives/libapr0_2.0.55-4ubuntu2.1_i386.deb (--unpack):

 failed in buffer_read(fd): files list for package `ppp': Invalid argument

Errors were encountered while processing:

 /var/cache/apt/archives/libapr0_2.0.55-4ubuntu2.1_i386.deb

Processing was halted because there were too many errors.

E: Sub-process /usr/bin/dpkg returned an error code (1)

It appears that it always fails when trying to install the 1st package. The download itself is fine. I have plenty of hard disk space...

Unfortunately I cannot remember when this problem first started...

Any other ideas?

---

### Post by Paerez on 2006-08-02
ok, can you run this for me?
[code]sudo dpkg -i /var/cache/apt/archives/libapr0_2.0.55-4ubuntu2.1_i386.deb[/code

hopefully that will give us some errors that will show us what is going wrong.

---

### Post by michaluxa on 2006-08-02
Thanks again, I get a similar output as when I use apt-get:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libapr0_2.0.55-4ubuntu2.1_i386.deb (--install):
failed in buffer_read(fd): files list for package `ppp': Invalid argument
Errors were encountered while processing:
/var/cache/apt/archives/libapr0_2.0.55-4ubuntu2.1_i386.deb
Processing was halted because there were too many errors.

the only 2 differences seem to be:

 (--install) instead of a (--unpack)
 the line: E: Sub-process /usr/bin/dpkg returned an error code (1) is missing

:confused:

---

### Post by Paerez on 2006-08-02
ok there are two things:
1) Reboot to the live cd and run fsck on your root file system
2) If you still have the problem, remove each package that has an error, then install it. This is a big pain but hopefully fsck will fix it.

---

### Post by michaluxa on 2006-08-02
Thanks for your suggestion.
I am not physically at the server right now (using ssh) so can't try a live CD. Will try it on Friday and let you know how I get on...

Many thanks again,

Micha

---

### Post by michaluxa on 2006-08-08
Hi again and sorry for the delayed reply.

I thought I just let you know that I have managed to get it all working again properly:

I booted from a Knoppix live CD and ran fsck.

This showed up lots of inode errors which I didn't repair to start off with.

As another clue, I have also been having weird drivestatus errors that come up every now and then. When googleing for clues, I saw lots of posts about kernels not being able to properly process harddrive status messages, so I put it down to that.

Now, having found the inode errors and obvious data corruption, I experimented with connecting to different controllers ( I have 2 SATA controllers on my motherboard, a dfi Lanparty nforce3). No change with that.

But when I changed the SATA data cable to another one, those drivestatus error messages stopped and have not reoccured since (4-5 days now). I then corrected all the inode errors with fsck and can now use apt-get again.

For the record, the drive I have is a Western Digital WD-74GB Raptor. I can only assume that the new cable that works o.k. is a shielded cable (it seems thicker and less bendy).

Thanks again for your help to point me in the right direction.

Micha

---

### Post by Paerez on 2006-08-08
No problem. Glad you got it fixed.

Just make sure that you immediately back-up data and replace the disk if the bios ever gives you HD errors. I had that happen to me but luckily I got my data off.

Of course it wasn't just the bios, the drive was making a "toothpicks in a blender" noise :D

---


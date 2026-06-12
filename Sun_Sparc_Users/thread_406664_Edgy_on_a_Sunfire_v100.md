---
title: "Edgy on a Sunfire v100"
date: 2007-04-11
forum: Sun Sparc Users
---

### Post by peskymo on 2007-04-11
hi there, 

first post here. i've just sucessfully installed edgy on a sunfire v100, and i thought i'd [share my experience]("http://ceoil.net/?page_id=110") with people here, seeing as how there's been a few posts about it. 

this wasn't my first attempt at replacing solaris on this box, i tried a few variations of debian, including sarge, etch, lenny, and ubuntu's dapper. 

it involves net booting the v100 using rarpd, tfptd, and dhcp, and then performing a http install. [pop over and have a read]("http://ceoil.net/?page_id=110") if you're having problems with it. it might not work for you, but it worked for me in the end.

---

### Post by colos128 on 2007-05-21
Could you check your link? It's not working.

 I'm been trying to get linux on a sunfire v100 for a while, but fails everytime. So I'm always looking for infomation on the matter. Thanks.

---

### Post by dmjedli on 2007-06-08
> **colos128 said:**
> Could you check your link? It's not working.

 I'm been trying to get linux on a sunfire v100 for a while, but fails everytime. So I'm always looking for infomation on the matter. Thanks.

Where have you been hanging up with your install?  I'm working on installing a couple V100s right now.

---

### Post by reidms on 2007-06-09
> **colos128 said:**
> fails everytime.

At what point in the install, or why?

---

### Post by dmjedli on 2007-06-09
> **reidms said:**
> At what point in the install, or why?

I successfully installed 6.06LTS server yesterday.  I was trying all day to install 7.04 server but it hung up at 85% (just after the update management core).  I got frustrated after 3 or 4 hang ups and switched to LTS.

The install of LTS worked great and I had no problems.  It could have been a bad image or disc for the 7.04.

---

### Post by dmjedli on 2007-06-09
Here are the basics of my V100 install...  (sorry, it's the day after and I don't have my notes)

Connect console cable (I used a Cisco console cable)

To get rid of the Time out for ARP/RARP problem I was having...

From LOM, I booted to forth (I think that's close to the right term) mode from LOM....

issued: setenv Diag_Enable?=false  (again, I think that's right.  It's at the bottom of printenv output)

issued: setenv boot-device disk (this is right)

issued: nvramrc (this should save those changes)

Back to LOM with #. and powerdown.  Then powerup.  The boot will fail at the disk (unless there's an os).  I scrubbed my disks with shred before I did this.

once you get an ok promopt... type boot cdrom

At the boot: prompt, the install image is labeled "install" so type the following:  install ide=nodma

Then everything went as normal....

---

### Post by mrtrick on 2007-07-25
I"m working through this process right now with Fiesty. The installer got past detecting network and just appears to be hung. Anyone have ideas? (This is on a Sunfire v100 as well)

---

### Post by mrtrick on 2007-07-27
Anyone else been successful on a Sunfire v100 server?

---

### Post by surlyjake on 2007-08-16
thanks, install went smoothly.

I'm getting an error when trying to boot into ubuntu:

"[   12.388167] PCI: Address space collision on region 6 [000001ff00080000:000001
ff000bffff] of device 0000:00:05.0"

.. then system freezes. any ideas?

i have seen this thread:[http://ubuntuforums.org/showthread.php?t=336241]("http://ubuntuforums.org/showthread.php?t=336241") , but none of those solutions work.

<EDIT> 
Answered my own question: when you install Linux, you must use "install ide=nodma". 

After successful install, you need to boot using "Linux ide=nodma" at the SILO boot prompt.

---

### Post by sys64738 on 2007-11-09
most your V100 install problems are caused by kernel2.6.17 and newer
use an older kernel and everything works perfect.

I haevnt ever had success with newer kernels becuase of the Davicom driver. 'modeprobe tulip' doesnt even seem to work

just use 2.6.16 and older or ubuntu 6.0.6-1 and older

---


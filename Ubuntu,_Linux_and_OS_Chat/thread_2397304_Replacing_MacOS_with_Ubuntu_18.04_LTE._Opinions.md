---
title: "Replacing MacOS with Ubuntu 18.04 LTE. Opinions?"
date: 2018-07-27
forum: Ubuntu, Linux and OS Chat
---

### Post by witcher--0 on 2018-07-27
Hi y'all!

Recently replaced my MacOS (High Sierra) with Ubuntu 18.04 LTE for the reason of learning Linux, Information Security, and programming in Python. I am an amateur with mild experience in coding. 

I was reading up on other forums about peoples opinions completely replacing the MacOS with a Linus Distro and got mixed reviews. 

I personally love the fresh taste of an open source OS and am very excited to continue to explore and learn linux. However, I saw many people saying to keep the MacOS in case anything goes wrong. **Now this has me worried a little bit because as I continue to explore I don't want to mess anything up**. But at the same time I only use my laptop to for school work and browsing.

**I am looking for opinions if I should reinstall my the Mac OS and Dual boot instead,** but I think that the best way to learn Linux is to use all the time and forget about the previous OS. 
I will eventually start coding in Python and continue to explore and teach myself the ins and outs of information security and I figured doing this is the most effective way to learn.

I am on a MacAir book Model A1466 and so far have had no problems on the newest Ubuntu distro. I will eventually explore other linux distros when I learn more. 

Is there anyone who completely switched to a linux distro and never went back? I feel as I progress in Linux I won't have to be concerned with what OS I use, as I will be knowledgeable to problem solve potential problems etc.. 

Thanks y'all! I am glad to be apart of the community

---

### Post by bodhin2 on 2018-07-27
i ran mac since osx was created.  then due to drm and other issues i went 100% linux.  i have to add that i also ran linux on another laptop while i ran mac osx.  but one day just said that is it and never went back.  have no fallback other than linux.  if you have linux running nicely then make the plunge.  you will be glad you did. 2 cents

---

### Post by &amp;KyT$0P# on 2018-07-27
> **witcher--0 said:**
> **I am looking for opinions if I should reinstall my the Mac OS and Dual boot instead,** but I think that the best way to learn Linux is to use all the time and forget about the previous OS. 
Even if you use Ubuntu exclusively, I would recommend you either dual boot Mac OS or have an external installation of Mac OS available on hand.  In my experience with Ubuntu on Apple hardware, you never know when you might need Mac OS.  I've needed it for troubleshooting and for various hardware things like setting up graphics.

---

### Post by witcher--0 on 2018-07-27
So I could put MacOS on an external SSD then as a backup in case I ever need it? Makes sense to me. Is it basically the same as trial testing Ubuntu from a thumb-drive?

---

### Post by &amp;KyT$0P# on 2018-07-28
> **witcher--0 said:**
> Is it basically the same as trial testing Ubuntu from a thumb-drive?
I think you would need to do a full install of Mac OS to the external drive.

(It wouldn't hurt to backup your existing Ubuntu installation before doing this.)

---

### Post by mastablasta on 2018-07-30
the easiest and safest way to dual boot is to use a virtual machine (for example virtualbox). 
here are a couple of guides: 
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[https://www.lifewire.com/run-ubuntu-within-windows-virtualbox-2202098](https://www.lifewire.com/run-ubuntu-within-windows-virtualbox-2202098)
[https://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/](https://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/)

you leave the original system as it is and independently run the other OS. and unless you need the OS to do some graphically intensive tasks (games, video editing...) it is a good way to try out the os and to learn. since you can mess it up completely and have the previous state restored in a couple of seconds (snapshots feature). 

with enough hard disk space you can also run multiple OS at once. 

there are also premade images available so you can just import the file & create virtual machine, select the password, and you are good to go (bitnami stack, turnkey linux). i use these for tests servers.  for example Bitnami:  [https://docs.bitnami.com/virtual-machine/get-started-virtualbox/](https://docs.bitnami.com/virtual-machine/get-started-virtualbox/)

i run various test machines on WindowsXP single core PC. i wish i had multiple core PC and more RAM, so they would run more fluently. but even so i don't have issues with lighter distros and server images.

---


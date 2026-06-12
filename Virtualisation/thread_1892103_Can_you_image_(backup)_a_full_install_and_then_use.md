---
title: "Can you image (backup) a full install and then use it in a virtual machine?"
date: 2011-12-07
forum: Virtualisation
---

### Post by gjwebber on 2011-12-07
Hi all,

Title says it all really. I have Ubuntu 11.10 installed on my home machine with various code libraries, programs, etc working properly now (it is installed on a partition on my main HDD). 

Is it possible to take an image of that whole install/partition, and then put it on a virtual machine?

Thanks for any help,
Gareth

---

### Post by lukeiamyourfather on 2011-12-07
Probably not, but there's a small chance it might. Since the virtual machine "hardware" will be different than the actual physical hardware in a machine there will likely be issues. It would be like putting the hard disk into another computer with different hardware, it won't have the drivers for the new hardware and will try to load the drivers for hardware that doesn't exist anymore.

---

### Post by CharlesA on 2011-12-07
You can try it, and it may work. I've done it before and it has worked, but I have had to tweak some stuff such as editing the file:

```
/etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by josephmills on 2011-12-07
> **gjwebber said:**
> Hi all,

Title says it all really. I have Ubuntu 11.10 installed on my home machine with various code libraries, programs, etc working properly now (it is installed on a partition on my main HDD). 

Is it possible to take an image of that whole install/partition, and then put it on a virtual machine?

Thanks for any help,
Gareth

Hello there 
there is a great tool out there called remastersys
what it does is takes everything that you have and makes a iso of it that you can then install or run live on your system. 
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)


there is also a different tool called live-build this is a little harder to use but there are far more options then remastersys 
[http://live.debian.net/manual/html/index.en.html](http://live.debian.net/manual/html/index.en.html)

then there is a main line that ubuntu uses  that you could alter the source code 
[https://code.launchpad.net/~cjwatson/ubuntu-cdimage/mainline](https://code.launchpad.net/~cjwatson/ubuntu-cdimage/mainline) 

I hope that this helps in some way :)

---

### Post by haqking on 2011-12-07
YES.

I do it all the time.  I use clonezilla to take an image then clone it back into the VM

Done

There may be some issues encountered and some config changes but for the most part it works fine, Linux clones tend to work much better than Windows clones

---

### Post by haqking on 2011-12-07
> **lukeiamyourfather said:**
> Probably not, but there's a small chance it might. Since the virtual machine "hardware" will be different than the actual physical hardware in a machine there will likely be issues. It would be like putting the hard disk into another computer with different hardware, it won't have the drivers for the new hardware and will try to load the drivers for hardware that doesn't exist anymore.

actually the fact that the hardware is virtualised IMO makes it easier than a different machine with differing real hardware

---

### Post by gjwebber on 2011-12-07
Thank you for all of the replies so far!

Remastersys looks like it should do the job nicely. How is it different from Clonezilla, and which do you think will work best and be easiest? (I'm a Linux noob)

I'm at work now, but will give these a try when I get home in a few hours. I'll let you know how I get on.

The VM I will be using is VMWare Player, on XP or 7, if that makes any difference at all.

Thanks again,
Gareth

---

### Post by haqking on 2011-12-07
> **gjwebber said:**
> Thank you for all of the replies so far!

Remastersys looks like it should do the job nicely. How is it different from Clonezilla, and which do you think will work best and be easiest? (I'm a Linux noob)

I'm at work now, but will give these a try when I get home in a few hours. I'll let you know how I get on.

The VM I will be using is VMWare Player, on XP or 7, if that makes any difference at all.

Thanks again,
Gareth

Not sure how VMware player will work with remasterysy or clonezilla, it does allow you to create a VM but there are better applications such as workstation or virtual box for this purpose IMO.

Best thing is to try it to be honest, though i would go with vbox myself.

---

### Post by gjwebber on 2011-12-08
I had a go with remastersys last night and it couldn't have been any easier. It took about 10 minutes from start to finish. Great little tool.

I installed the latest version of VirtualBox and was up and running. The only thing wrong was that the display was staying far too small, and also wouldn't go full screen. After a bit of googling I found a package that was required:
```
sudo apt-get install virtualbox-ose-guest-utils
```After doing that and taking another image it worked perfectly :)

Thanks for your help,
Gareth

---

### Post by haqking on 2011-12-08
> **gjwebber said:**
> I had a go with remastersys last night and it couldn't have been any easier. It took about 10 minutes from start to finish. Great little tool.

I installed the latest version of VirtualBox and was up and running. The only thing wrong was that the display was staying far too small, and also wouldn't go full screen. After a bit of googling I found a package that was required:
```
sudo apt-get install virtualbox-ose-guest-utils
```After doing that and taking another image it worked perfectly :)

Thanks for your help,
Gareth

cool, glad you got it sorted, you are welcome.

Make sure you have the extensions pack also to enhance things like USB in the VM.

Cheers

---


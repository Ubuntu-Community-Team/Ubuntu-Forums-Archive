---
title: "installing Windows on Virtualbox"
date: 2010-03-18
forum: Virtualisation
---

### Post by tjanzen on 2010-03-18
I currently have Ubuntu installed on my Dell laptop, and am trying to install the original Windows 2000 OS using Virtualbox. I get to the point where it mounts the cd, but returns the error message 'This Software is licensed for use on Dell Systems only'. 

All I have is the Dell Product Recovery CD which came with the laptop. Will this not work on Virtualbox?

---

### Post by blur xc on 2010-03-18
OE install disks are only linsenced to be installed on the OE hardware, and won't work in a VM.  Thank you MS EULA telling you what you can or can not do with your software!  That's because it's not YOUR software, it's theirs, and you just use it w/ their permission if you agree to their terms and conditions...

end rant

So, I friend of mine once said you might be able to use a program called nlite to modify your install disks, and make a new iso that might get you around this limitation, but I think that only works for XP, and would still make you into a cyber-criminal.

BM

---

### Post by tjanzen on 2010-03-18
So even though the virtual machine is running on the correct hardware, the install disk doesn't know it?  I'll now stop pulling out my hair, and give up on the install.

thanks.

---

### Post by howefield on 2010-03-18
> **tjanzen said:**
> So even though the virtual machine is running on the correct hardware,

The virtual machine isn't seeing your hardware, it is only seeing what Virtualbox is telling it to see, via the Virtualbox drivers.

So it isn't running on the correct hardware, so to speak.

---

### Post by jermf810 on 2010-03-18
I have a similar setup as you tjanzen and installed Windows on my VirtualBox. I followed this tutorial and it worked for me: [http://klikit.pbworks.com/How-to-install-Windows-in-VirtualBox](http://klikit.pbworks.com/How-to-install-Windows-in-VirtualBox) Hope this helps!

---

### Post by bpalone on 2010-03-18
Just did a quick Google and found this: [http://www.thetechguide.com/forum/index.php?showtopic=6555]("http://www.thetechguide.com/forum/index.php?showtopic=6555")

It might be of some help.

---


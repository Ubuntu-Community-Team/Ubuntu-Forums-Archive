---
title: "grub2 re-install"
date: 2009-12-18
forum: System76 Support
---

### Post by brusegadi on 2009-12-18
Hello, 

My Pangolin was not booting properly, so I was advised to attempt a GRUB2 re-install.  I followed the instructions here:[html]  http://ubuntuforums.org/showthread.php?t=1195275[/html]Under "Reinstalling GRUB 2 from LiveCD",    the following did not work: ```
sudo mount /dev/sda1 /mnt
```  so I had to say: ```
sudo mount -t ext3 /dev/sda1 /mnt
``` and then, when running the grub-install command, I got the following error message: 
"This msdos-style partition label has no post-MBR gap.....GRUB can only be installed in this setup by using blocklists."
"grub-setup error: cannot read `/grub/core.img' correctly"
 
See: [[html]http://wiki.archlinux.org/index.php/GRUB2[/html]]("http://wiki.archlinux.org/index.php/GRUB2")   
(under "msdos-style error message"; section)  Should I try blocklists?  I have a Pangolin, on karmic, with an ssd (perhaps the ssd uses the blocklists?)  
Thanks so much, and sorry for my poor formatting,

 B

---

### Post by thomasaaron on 2009-12-18
Since I was helping you via email on this one, it's probably best that you respond to the email with your output.

I have to go through both email and forums, and so it causes the flow of data to be a bit disjointed when you shift venues.

---

### Post by brusegadi on 2009-12-18
So, I loooovvveee this machine.  This seems to be a very rare Karmic thing.  My question is, should I just try all the stuff that I have managed to find online, and if nothing works, just re-install?  Also, If I post this in the more general Ubuntu forum, would the community look down on me for double posting?  Thanks everyone!

B

---

### Post by gamerchick02 on 2009-12-18
I'd give what you have a try.  If that doesn't work, a reinstall is in order.

How was it not booting properly?  Did you get a specific error?  

Amy

---

### Post by oldfred on 2009-12-19
When you tried to reinstall it you said sda1 which is the partition boot or PBR. Grub2 does not like the partition but can be forced to install there, so you can chainboot from another boot loader. You probably want to install to the MBR or sda (not sda1). sda1 may be where your install is but grub needs to be in the drive's MBR.

---

### Post by brusegadi on 2009-12-19
At boot, I would get an alert about the root partition not responding.  It would dump me into busy box (this was when doing a recovery boot... a nor mal boot would not boot at all.)  I'll keep you posted.  Thanks for your response.

---

### Post by brusegadi on 2009-12-19
I am super happy, I tried using --force in the command I had issued, and it did not work.

Then I tried "Method 2" and "Method 3" at"

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


and Method 3 did the job (gave me warnings but ultimatly, no errors.)  everything looks fine.  I'll mark the thread as solved.  Thanks!!!!!!!!!!!!!!!

---


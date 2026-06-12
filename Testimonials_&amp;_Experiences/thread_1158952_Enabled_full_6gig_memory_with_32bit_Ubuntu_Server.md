---
title: "Enabled full 6gig memory with 32bit Ubuntu Server"
date: 2009-05-14
forum: Testimonials &amp; Experiences
---

### Post by 73ckn797 on 2009-05-14
Much has been said on the forums about using the server edition to have full memory use over 4GiB. 

I was performing an experiment to have a 32bit Ubuntu utilize the 6GiB ram on my system. I have loaded 9.04 64bit but was not impressed by any speed increase. The new ext4 file system did help things seem slightly faster. I wanted to enable PAE (Physical Address Extension). The server edition has it enable by default. I had noticed by enabling PAE under Windows XP that the system was very fast. It was much, much faster than I have ever had a Windows system run. From that I assumed Ubuntu could have the same speed increase which it does seem to have now.
My procedures were as follows:

Step 1: I installed 9.04 32bit Server but did not install all of the server packages. I was not going to use it as a server.

Step 2: When the server loaded and I was at the command line I entered:
```
sudo apt-get gnome-desktop-environment
``` as had been recommended in previous posts. That worked just fine. It does take some time to install.

Step 3: I then entered:
```
sudo apt-get ubuntu-desktop
```Reading info in Synaptic suggested this package would allow for full support and upgrades. Not support in the way of being an officially recognized Ubuntu but so that regular updates could be available as usual. At least that was how I read it.

Rebooted system and I have Ubuntu 9.04 32bit with 5.9GiB of 6.0GiB RAM being recognized.

The system runs very fast and very responsive. It seems to be much faster than the 64bit Ubuntu. That I realize is because the 64bit requires more memory than the 32bit. My system will only allow a max 8GiB memory.

I may not have had to perform step 2 since step 3 was the Ubuntu desktop. I did notice that "ubuntu-desktop" installed OO and many other of the usual programs beyond what "gnome-desktop-environment" installed.  Either way I now have a faster system than I have ever had with Ubuntu. I think I will keep it as my primary OS configuration.

):P

---

### Post by 73ckn797 on 2009-05-24
My previous steps to install the server kernel failed. It was my attempt to have a 32 bit system with PAE (Physical Address Extenson) enabled to utilize the 6GiB memory installed. I wanted to see if it could work.

The problem was that upon a first or sometimes second reboot, resulted in getting "xserver" not starting and also the GDM not being able to start. The system would take me to the server CLI prompt then, in a semi graphical mode would ask to reconfigure xorg.conf. That would only work the one time until a reboot. I attempted a couple of other solutions ( will not get into that ) which all failed on subsequent reboots and would bring me back to the prompt. These problems always occurred after trying to install the restricted Nvidia 180 driver.

I believe that I have finally resolved the problem.

This time I first installed Ubuntu 9.04 and then from Synaptic I installed the server kernel only. The first step after the initial Ubuntu install was to allow updates to install and then enabling the restricted driver. I have not experienced any problems with the system starting up into the Ubuntu desktop and 5.9GiB of 6Gib are recognized.

It seems that the system is running a bit more quicker than my install of 9.04 64bit. This install is also using ext4.

Time will tell whether this success will last. So far, so good after multiple reboots.

---

### Post by HappyFeet on 2009-05-25
How come you just didn't use the 64bit mini iso (10mb) and build it up? I'm sure it would have been lightning quick.

---

### Post by 73ckn797 on 2009-05-25
> **HappyFeet said:**
> How come you just didn't use the 64bit mini iso (10mb) and build it up? I'm sure it would have been lightning quick.

I was not aware of the mini iso.

This was more an experiment to see what would happen. The 9.04 64 runs great. I do have the benefit of 3 hard drives and can experiment using one of those. I have another computer I use just for messing around with. The 9.04 64 with ext4 is really quite good and seems to have good speed. I am not one who is trying to squeeze out every bit of speed. A few seconds is not much to get bent out of shape over. I currently do not have 64 with ext4 installed due to several issues recently which turned out to be a failing hard drive. I have replaced that drive and will probably reinstall with ext4.

The PAE really made a difference with Windows XP and that result made me want to see how it would work with Ubuntu 32 bit. I still prefer Ubuntu and only keep windows for one aspect of my work. There is one web site that I have to use IE to upload photos with. I have not had the chance to use the "User Agent Switcher" in Firefox to accomplish this task. I can do everything else on the web site in Ubuntu but upload photos.

I know there are many who only have 32 bit systems and might benefit from the PAE. I really do not see that the hassle of what I have done is really making a big difference over 9.04 64 with ext4 to speed the system up. 9.04 32 with ext4 does a good job even without PAE enabled.

---

### Post by HappyFeet on 2009-05-25
Btw, [here]("https://help.ubuntu.com/community/Installation/MinimalCD") are the mini iso's for future reference. You need a wired internet connection for the installs.

---

### Post by 73ckn797 on 2009-05-25
> **HappyFeet said:**
> Btw, [here]("https://help.ubuntu.com/community/Installation/MinimalCD") are the mini iso's for future reference. You need a wired internet connection for the installs.


Thanks.

I have book marked that link for future use.

---


---
title: "Starting from ZERO after kernel updates"
date: 2009-01-31
forum: Testimonials &amp; Experiences
---

### Post by marcgh on 2009-01-31
I am running Intrepid 8.10 .
After the initial struggle of the first days I got my system running stable for the pas 6-7 weeks (I am a new user).

I could browse, mail, RSS, encode and burn my DVD's, relax with some games and had a nice Cube desktop running

I have a ATI Radeon 4850 with 2 LCD screens (17" and 20") and despite all what I read on this forums I did not have any major issue.

Yesterday evening I updated the whole proposed list (I am technically unable to know what is what and what I need on my system) after the expected download and install time I was asked to restart my system.

On restart I got 1 blank screen and one blue screen nothing further. I had no choice than to restart the hard way (power off).

I tried to repair broken packages....no help.
I reset the X server...and I could log in.
What I got is **DISASTER**:
- ATI driver can no more work - Catalyst is dead!
- Max. resolution on 1 screen = 800x600
- 2nd screen blank with one small orange square.
- no more cube.
- no more wireless ( I have now a loose cable running thrue the living room - CHILDREN BE CAREFUL NOT TO HOOK PAPA'S CABLE).
- any .avi file I play is flickering.

I know, I will probably find a way to fix it (I did it in the initial install period) but I am really reluctant to spend my W-End sorting things out.

I will NEVER again update anything unless I read a 1,000 threads that this time the software guy's did it in a more serious manner. I have the feeling that anybody can just put anything as an update - and let's see how it works out!

I know this is free put I still expect a flawless update or an update with some kind of 'security barrier' build in to avoid users like me to have this kind of CATASTROPHIC FAILURE.

Don't think you got rid of me, I'm still Ubuntu and will be back with my machine in full glory hopefully by Sunday.

Marc

---

### Post by armandh on 2009-01-31
I'de be upset too. [and have been in the past]

but I have had better luck with less complex graphic cards.

once when my son [the gamer] upgraded to pcie buss and I got his old machine. the unrecognized graphic card had only the basic vga without working drivers. I set it aside to use a known working AGP card. a month later I tried it and a request for restricted drivers poped up. then it just worked. [GTX with nvidia chip]

PS the GRUB start screen should show the earlier kernels
click down to one that works then use a grub editor to select as default. 
[I like the KDE grub editor]
after some time try the newer kernels and look for newer drivers

finally a pitch to use open source drivers when ever possible
restricted drivers increase the chance of upgrade failure.

---

### Post by cjnkns on 2009-01-31
> 
I know this is free put I still expect a flawless update or an update with some kind of 'security barrier' build in to avoid users like me to have this kind of CATASTROPHIC FAILURE.

+1 I coudn't agree with you more.

---

### Post by Tamlynmac on 2009-01-31
You might enjoy this thread.

[http://ubuntuforums.org/showthread.php?t=1055367](http://ubuntuforums.org/showthread.php?t=1055367)

---

### Post by wolfen69 on 2009-01-31
my suggestion is to do a fresh install and do all updates immediately before configuring anything. set up your pc, then turn off all updates. 

i myself, have never had any problems with any updates. i just did 3 kernel updates in 2 days, and it still runs great. but that's because ubuntu loves me more than you.  ;)

---

### Post by Tamlynmac on 2009-01-31
> wolfen69
i myself, have never had any problems with any updates. i just did 3 kernel updates in 2 days, and it still runs great. but that's because ubuntu loves me more than you. :wink:

There is a fine line between "Love & Hate". One never knows what tomorrow may bring.:smile:
However, I must agree, as I've never had a problem with an update. I suspect it directly relates to hardware compatibility and learning the OS.

---

### Post by solwic on 2009-01-31
Call me Captain Obvious...but if you're having trouble with kernel updates, shouldn't you not update the kernel?  

Just a thought.  

Good luck.  :)

---

### Post by marcgh on 2009-01-31
First of all, many thanks for the tips.

I got my system back running after nearly a day work (somehow also joy!). Wireless is working and dual screens are ok. (ATI has new driverversion). Left with some minor problems: skype sound and webcam, but that will be for tomorrow.

To all of you in this timezone: good night / to the others: have a nice day.

Wolfen 69: Blessed are the loved ones!

---

### Post by dasunst3r on 2009-01-31
I got two questions for you:
1. How did you install your graphics card driver?  Did you install it through the Restricted Hardware Manager, EnvyNG, or manually?  If you did it through the first two methods, the kernel module fglrx should have been registered in DKMS (Dynamic Kernel Module System) and rebuilt for you automatically.
2. Who manufactured your wireless card and what is its model?  If you had to perform some procedure to get it working, what was it?

*Edit*: Also, I appreciate your patience in starting again even after things borked up for you that bad.

---

### Post by marcgh on 2009-01-31
[QUOTE=dasunst3r;6653147]I got two questions for you:
1. How did you install your graphics card driver?  Did you install it through the Restricted Hardware Manager, EnvyNG, or manually?  If you did it through the first two methods, the kernel module fglrx should have been registered in DKMS (Dynamic Kernel Module System) and rebuilt for you automatically.

I installed the driver as how I did it the first time + this time I had to remove any former driver.

This is the link : [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I have to say that I wasted a lot of time and removed and reinstalled because:
a) in the how to install pdf from ATI they are still referring to the former version name.
b)I did not realise immediately that a restart was needed for ATI catalyst control center to work.



My wireless card is a PCI TP-LINK 108M model: TL-WN650G/TL-WN651G.
For this part of the problem I am myself a bit confused about how I fixed it. I did so many 'things' without taking notes that it's, for me, close to a miracle that it finally works.
My problem was not that Ubuntu did not see my card but how to set up the encryption and key - even now I could not do that!
Luckely my router has a function where I can allow only specific MAC adresses. So I removed the wireless encryption and allowed only the 2 MAC adresses from my PC and laptop. I'll google a bit around tomorrow to see if this is a safe situation.

Thanks for your reaction,
Marc

and also thanks for your appreciation but after the Panic it somehow enjoyed it.

---

### Post by Crafty Kisses on 2009-01-31
Just don't to the kernel updates, and if you feel you need a kernel update, compile it on your own, that's just the way I feel.

---

### Post by dasunst3r on 2009-01-31
It's good that you're back up and running again.  On the next release upgrade, you should definitely take advantage of the Hardware Drivers deal as it'll make your job a whole lot easier.  You can find it by going to System -> Administration.

According to community-contributed documentation, your card should work out of the box: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link)

It is a VERY BAD idea to run your wireless network without any form of encryption.  A MAC filter will take just a few seconds to crack.

---

### Post by 3rdalbum on 2009-01-31
Use the Hardware Drivers program to install drivers, unless you absolutely definitely need to do it the manual way (the way you did it).

On Linux, drivers need to be built for the specific version of the kernel, or they might not work. This isn't a problem if you use the Hardware Drivers program, because whenever there's a new kernel update Canonical will also push out a new driver that will work. If you install the ATI driver manually, however, you would need to reinstall it each time the kernel gets updated.

---

### Post by hyper_ch on 2009-02-01
> **dasunst3r said:**
> It is a VERY BAD idea to run your wireless network without any form of encryption.
why?

---

### Post by marcgh on 2009-02-01
> **3rdalbum said:**
> Use the Hardware Drivers program to install drivers, unless you absolutely definitely need to do it the manual way (the way you did it).

On Linux, drivers need to be built for the specific version of the kernel, or they might not work. This isn't a problem if you use the Hardware Drivers program, because whenever there's a new kernel update Canonical will also push out a new driver that will work. If you install the ATI driver manually, however, you would need to reinstall it each time the kernel gets updated.

When I installed Ubuntu for the first time some 2 months ago I used this method and ended with a 800x600 resolution. So I just did not try it again finding my way ....but I will try it later the way you suggested.

If I use only access by specific MAC address, can my neighbours crack, connect and use my internet?

---


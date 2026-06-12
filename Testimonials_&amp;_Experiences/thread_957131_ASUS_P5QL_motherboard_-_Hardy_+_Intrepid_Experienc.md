---
title: "ASUS P5QL motherboard - Hardy + Intrepid Experiences."
date: 2008-10-24
forum: Testimonials &amp; Experiences
---

### Post by Roasted on 2008-10-24
Note - These experiences were with Hardy Heron 64 bit + Intrepid 64 bit. Intrepid was used in its Beta state, one week prior to official release.

Hardy:

This board doesn't seem to like IDE Legacy mode. I had to run this system in AHCI (SATA) mode in order to get things running. This wasn't a problem, considering I have all SATA drives, but I realized I didn't have the SATA driver pre-installed for support with XP Pro. So, I had to make my own copy of XP Pro using my already existent XP Pro CD. Using nLite, I slipstreamed SP3 and the SATA drivers required. Then, I installed XP Pro + Ubuntu Hardy just fine in AHCI mode. 

My onboard ethernet card made by Atheros was not supported out of box. I heard a rumor that drivers were available and functional, but I never got them to work. I resorted to a PCI LAN card I had laying around.

In a nutshell - No support for onboard Atheros LAN, and you have to run in AHCI (SATA) mode to run Ubuntu.



Intrepid:

 I used AHCI mode from the get-go, so I have no idea if Intrepid yielded any difference with IDE Legacy mode or not. However, AHCI works perfectly, as expected.

And now? My onboard Atheros LAN works out of box. Wooo! 

Up until now, I have not had any other issues worth noting about this motherboard with Ubuntu Intrepid (beta) 64 bit 8.10.

Note - I have not tested the onboard audio in Intrepid, since I have a PCI sound card (Turtle Beach Montego DDL 7.1, which works fine btw). But it worked in Hardy, and I'm almost positive it would work in Intrepid as well.

For the sake of knowing, here are the specs of the rest of my system:
Q8200 Intel Quad Core 2.33ghz
4GB DDR2 800 RAM (2x2gb) G. Skill
Nvidia GeForce 9600GT 512mb 256bit PCIEx16 2.0 with 177 hardware drivers
Two 500gb SATA Seagate's, Two 250gb SATA WD's.

---

### Post by bluewind on 2008-11-12
This about Hardy 32 bits with an ASUS P5QL PRO.

I also needed to switch the disk to AHCI otherwise it was not recognised.

A LAN driver for Linux (arl1e for Atheros AR8121/AR8113) can be downloaded from the AsusTEK support site for P5QL PRO at 
[Downloads for P5QL PRO]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5QL%20PRO")

I had a difficulty when compiling the driver (some story about CFLAGS and EXTRA_CFLAGS) which required an option to be passed to modify an environment variable :
sudo KBUILD_NOPEDANTIC=1 make install

Now everything is fine. I prefer to stick to Hardy because of LTS.

---

### Post by rogueninja on 2008-12-06
Hi, I am a total newbie to Linux & Ubuntu, and I was wondering if you could help me out. I installed Ubuntu Studio Intrepid Ibex 64 Bit earlier this week, and it wouldn't connect to the internet. I have the P5QL PRO as well, and I tried downloading the driver from the ASUS site after I found that the Linux driver included on the motherboard DVD wouldn't work. Ubuntu recognizes that the driver is installed, but still won't connect. I can't get at my router either so I would imagine that the LAN driver is still somehow at fault. I also combined your advice with another post's ([http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)) and ran

sudo insmod ./atl1e.ko

at the end of it all, when no internet connection was happening yet. The error I received at that point was 

insmod: error inserting './atl1e.ko': -1 File exists

which I would take a stab in guessing it means it won't install it because it's already there.

I am not very savvy when it comes to networking at the best of times, so please does anybody know if there's something obvious I'm doing wrong? I have been spending all my free time for the last three days trying to get a connection. I know there's no hardware issue because the connection is fine when I boot into Vista instead.

I did find that my motherboard has the Atheros L1E60 included, if that's any help.

Thanks so much!!

---

### Post by Roasted on 2008-12-07
Are you sure it has the Atheros L1E60?

I googled "Atheros L1E60" and got 1 result... this thread...

EDIT - is the "Atheros L1E60" the name of the driver?

I don't know what else to tell you. Mine works out of box... Is it for some reason disabled?? Can you find out within Vista what LAN chip Vista detects? Maybe it's an edition slightly different than what I have in my P5QL Pro. BTW - is your P5QL a "Pro?"

---

### Post by hellokitty889 on 2008-12-07
GOOD Writing! The Combat [Formula thread.](http://www.runescapecoin.net) This is a recreation of the previous combat formula thread. In this thread, we discuss the formula that calculates one's combat level, using the levels in the combat skills. This formula is not exact, but it does have a very high accuracy. Our goal is to improve it so that it becomes exact. The formula can help you calculate your combat level, for any combination of [combat skills](http://www.runescapemoney.ws) you like. INTERESTING NEWS: Jagex puts up a Wallpaper containing something that appears to be an estimate of the combat formula. Our data suggests that it is not the actual formula, but it does seem to confirm bits of our formula. Feel free to discuss it here in this thread Want to buy [rs gold](http://www.rsgold.info/) pls check it~~keep working!

---

### Post by bluewind on 2008-12-07
What happened to you is surprising Rogueninja, as the experience of Roasted shows that the LAN driver for the LAN of P5QL PRO is already included in Intrepid (while it is not in Hardy).

Please be more specific about what you have been trying to do. A few questions the answers to which might help :
1. Is your router configured for DHCP or do you have to set an IP address ?
2. What is the output of "sudo ifconfig" (this will describe the detected network interfaces)
3. After loading the driver did you try a "sudo /etc/init.d/networking restart" to reinitialise the network service?
4. I put that fourth but it should have been first : you should not have to use "./atl1e" to designate the driver to be loaded. If the installation worked properly "atl1e" is enough because insmod will in that case look for the module in its proper place in /lib/modules/etc..., not in the folder where you compiled
(and by the way it is supposedly better to use "sudo modprobe atl1e" instead of insmod)
So perhaps we should go back to your compilation/installation process. Did everything go well ? No error diagnostic ?

---

### Post by rogueninja on 2008-12-07
Thank you both for responding so soon!

You're right, Roasted. I had the name of the driver, not the hardware. As far as Vista will tell me, the hardware is an Atheros AR8121/AR8113/AR8114 PCI-E ethernet controller. My motherboard is the P5QL PRO.

Bluewind - yes actually I had an issue in the installation process. It told me that it couldn't detect an ethernet card (or something to that effect) and that if I wanted to load it, I'd have to go back to the network setup step... I tried going back but all it gave me was the same error and no options. I didn't know what else to do to make it see the card from there so I just continued the installation. After the first time I couldn't get the network running, I uninstalled Ubuntu, found my motherboard DVD, re-installed the drivers (for Vista) just in case that would help it "see" the card there, and installed Ubuntu again. It didn't help.

My router has DHCP turned on. However when I try to access the router's setup from Firefox in Ubuntu, it can't find the router's IP.

I tried running the line of script you gave me as #3 and it seems to have worked in the terminal but it didn't do anything for the connection.

When I ran sudo ifconfig I got:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10048 (10.0 KB)  TX bytes:10048 (10.0 KB)

Which means nothing to me, hopefully it's clearer to you :)

Thanks!!

---

### Post by Roasted on 2008-12-07
Yeah... your ethernet card doesn't appear to be detected. AR8121 is what my ethernet card is. And mine works! I didn't do a darn thing to it to get it running.

That's very odd... 

You're positive you're running Ubuntu Intrepid 8.10? I don't mean to question your assurance on the matter, but with somebody like myself having the same exact motherboard and it working flawlessly, coupled with the fact your board works fine in Vista, I'm completely lost as to why YOU are having issues... and it's not like you could have done anything wrong, to be honest. Mine worked out of the box!

But hey, do this... I just did this and I'm not sure if it will help your case or not...


In the upper right corner, there's two computers side by side near your clock. It's your networking icon. With it disabled, I pull this information after entering ifconfig in terminal:

```
jason@jason-intrepid:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3876 (3.8 KB)  TX bytes:3876 (3.8 KB)

```

With it enabled, I pulled this:

```
jason@jason-intrepid:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:22:15:74:c6:44  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe74:c644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3237818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1941199 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:4372682242 (4.3 GB)  TX bytes:171448808 (171.4 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3876 (3.8 KB)  TX bytes:3876 (3.8 KB)

jason@jason-intrepid:~$ 

```

eth1 is your ethernet connection. lo is your loopback. Ignore your loopback... it's not your "connection." As you can see, mine disappears when it is disabled. When it's enabled, it shows up...


I'm wondering if your networking is even enabled... I find it hard to believe it'd be disabled, but let's look at the facts...

-Vista works. We know the hardware is good.
-Mine works under Intrepid 8.10 64 bit. We know the OS supports it.
-Yours doesn't work... but... why? 

Check that out and get back to me... I check these forums several times a day, so I'll help best I can. But I have to admit, I'm stumped here if something isn't accidentally disabled.

---

### Post by rogueninja on 2008-12-08
My networking skills are tenuous, so I am not going to discount user error... I didn't do anything to turn networking *off*, but I also haven't been able to find a thing that will allow me to turn it *on*. My belief that it's somehow the ethernet driver comes from the fact that I can't access my router's settings from my browser, combined with the error I had while installing that it couldn't detect network hardware.

I had to add the networking icon to the bar at the top to try to carry out your experiment. Alas, I was foiled again. Is there supposed to be something in the Connection Properties window that it brings up to allow me to turn on the network? I don't know where to go or what to do to try to initialize it :(

I double-checked and when I open Firefox it says Welcome to Ubuntu 8.10. It *is* the Studio release, however, with its own theme and backgrounds and a selection of multimedia software included... but that shouldn't make any difference, should it?

Thanks for your patience!

---

### Post by Roasted on 2008-12-08
In the upper right corner by those two computers I spoke about... right click on that icon.

Do you see "enable networking" ???

If so, is there a check by it?

If not, click on it once so there IS a checkmark there... 

See if that takes you anywhere.

---

### Post by bluewind on 2008-12-08
ifconfig returning only a description of the lo (local) interface means that your LAN card is not detected. As long as ifconfig does'nt mention an eth* interface it's nou use trying to establish networking, it cannot work.

The LAN card not being recognised probably means that the driver is not properly installed. The driver for your chipset is atl1e. Let's do first things first : what do you get when you pass the command "sudo modprobe atl1e" ?

---

### Post by Roasted on 2008-12-08
How would that ever make sense though, Bluewind? Think about it.

-Vista works. Meaning the hardware works.
-Mine works out of box. No driver installation needed.
-His doesn't work out of box, or at all for that matter.
-Yet, we know several things reassuring the fact that everything "SHOULD" work.

---

### Post by rogueninja on 2008-12-08
Oddly, when I right-click the networking icon, the only options it gives me refer to how I want to move the icon around... there is no option to network at all.

I tried "sudo modprobe atl1e" and nothing happened. It asked for my password, but then no script came up, nothing. I ran the sudo from the directory of the atl1e driver as well as from the main directory.

It occurred to me this morning that when my friend installed my motherboard, he may have installed only the bare bones necessary to make it run with Vista. I found that Express Gate wasn't installed yet. Installing it didn't affect Ubuntu at all, but I'm thinking that maybe if I uninstall Ubuntu and reinstall with Express Gate running, it might make a difference. I will let you know how it goes later tonight...

---

### Post by Roasted on 2008-12-08
I hate to do this, but I have express gate disabled.

I don't know what it does or how to install it, but I kept getting an error right around the BIOS splat screen that it wasn't installed. It was annoying, I had no idea what it is, how it works, how to install it, etc... so I disabled it in BIOS...

---

### Post by rogueninja on 2008-12-08
Oh wow. Well that ends my troubleshooting process, I am at a complete loss for ideas now! Maybe I should just give the main release of Ubuntu a try and put aside my Studio version for now. If I download a Live CD is it possible it would give me the same problem just because its a Live CD and not the installed O/S?

---

### Post by Roasted on 2008-12-08
If your hardware is supported "out of box", it'll work on the LiveCD.

AKA - Download Ubuntu 8.10... burn to CD as image... boot to it... try firefox. See if it works.

---

### Post by bluewind on 2008-12-09
Yes, trying the Live CD is a good idea.

Going back over the discussion I realise that
a/ there was an atl1e driver since it is included in Intrepid
b/ you compiled and intalled nevertheless another one over the existing driver.
I don't know, but perhaps this messed up the referencing of the driver in the system.

If it is the case, the Live CD should work.  
Then, you can either do a complete reinstall or try to clean the system yourself with the following steps :
- remove anything that carries the name "atl1e" in the drivers directory. That is /lib/modules/[your kernel reference]/kernel/drivers/net/
- do "sudo depmod -a" (to remove all references to atl1e in the system
- go to the directory where you have the driver source
- do "sudo make clean" (to remove all residue from former compilation)
Then start again from scratch
- compile and install
- "sudo modprobe atl1e" (if that says nothing, it means it worked ; you can verify by doing "lsmod | grep atl1e" which will give a line with atl1e if the module is correctly loaded and a blank line if it not)
- "sudo /etc/init.d/networking restart"

If that does not work I don't know what to suggest.

---

### Post by Roasted on 2008-12-09
bluewind - just to bounce some ideas around here, what's your knowledge on Ubuntu Studio? I would think they'd be running the same kernel as the regular Ubuntu line... I can't imagine it'd be different.

---

### Post by bluewind on 2008-12-09
I don't erally know. The kernel is perhaps a bit different. But it's an 8.10 Interpid Ibex nevertheless. I can't imagine that they would remove some of the drivers that are in the standard version !

---

### Post by rogueninja on 2008-12-09
Well I don't know what to tell you! I ran regular Ubuntu (not Studio) from the Live CD and the network worked immediately. I went ahead and installed it last night. I think that maybe during the installation of Studio when it was unable to detect the network hardware, it disabled networking in the installation, because I didn't have the option at all under the networking icon to enable networking. The default interface setup in Studio is different than this one, and the install interface is different too. I think I will poke around and see if I can find a Live CD version of Studio, although I seem to recall reading that it's just too big with all the software included - the install image file needs a DVD.

For curiosity's sake, I'll keep you posted if I find out anything useful about how to get Studio running... and whether that really was the problem or *what* the heck I did.

Thanks for all your help!!

---

### Post by Roasted on 2008-12-09
rogue - I'm glad to hear we at least came to SOME sort of consensus. If it wasn't for the fact my Ubuntu machine with the ASUS motherboard in question is maxed out in hard drives, I'd go ahead and give it a shot with that computer.

But then again, and maybe some of you can help me here... can you install Ubuntu to an external USB hard drive? I'm so very tempted to get Ubuntu Studio on my main computer for the sake of trying to iron out this confusion... if I can install to a USB hard drive, I'm sure I can figure something out as to why it wasn't working for rogue.

I'm pretty sure I can boot to a USB device, so that shouldn't be a problem. It's just a question as to whether or not I can install...

Another question - Can't you install the "Studio" packages on Ubuntu? To therefore give Ubuntu users the added applications and whatnot that Ubuntu Studio users would have?

---

### Post by rogueninja on 2008-12-09
I was thinking the same thing today, actually! I have a laptop hard drive with a USB case/connector that I think I am going to experiment with and see if I can get Studio to play nice. I don't know how installable it is on external media. I've read that the regular release can be done.

You can definitely install the whole list of Studio-included software onto regular Ubuntu. The Studio page - and Wikipedia for that matter - has a nice handy list of them. I just started with Studio because it seemed to be easier to start with them all installed so I could play with them right away! It looked like a good plan on paper, anyway! :)

---

### Post by Roasted on 2008-12-09
Well, the important thing is you got Ubuntu working and online.

I don't mean to stab at you with this, but I really can't see what would be different between Ubuntu and Ubuntu Studio to cause any conflict networking wise. I mean, they both run on the same kernel, don't they?? If so, they should be equally supported.

---


---
title: "Video Card Drivers in Virtualbox"
date: 2010-04-26
forum: Virtualisation
---

### Post by Twitch04 on 2010-04-26
Hello, everyone. 

I'm running Ubuntu 9.10 on Sun Virtualbox, my host computer is Windows XP Pro, though I suppose that doesn't matter too much. 

I was wondering if there was some way, because I know virtual machines are different, to get propriety drivers. I know I managed to get some before [on my Ubuntu partition on my actual hard drive. They weren't totally awesome, but they worked]. 

The reason I ask is because 1024x768 is just i think a LITTLE too small for my liking, even though it's perfect in Windows. Things are a tad bigger in Ubuntu. XD

Anyway, just wondering. I know Virtualbox handles things differently... I think. I'm not actually sure what all of my hardware it DOES detect. O_o

EDIT: I know it seems like a stupid question, it's more about whether or not the propriety drivers would matter because it's VirtualBox, not a legitimate machine, or whatever.

---

### Post by mickie.kext on 2010-04-27
You can not install graphic driver for host hardware on to VirtualBOX guest. VirtualBox emulates its own graphics hardware, and to get full acess to it, you need to install VBoxLinuxAdditions package to guest Linux OS.

You can do that y starting you Ubuntu VM, and then going to Devices --> Install Guest Additions in the menu. 

Now you will get VBox additons icon on desktop of your guest OS. From here you need to to start terminal and type 

cd /media/VBOXADDITIONS_x.xx 

where xx is verison of VirtualBox you are using. You can do only cd /media/VBOX and then tab to autocomplete. Once you are there, type **sudo sh VBoxLinuxAdditions-x86.run** and wait for installer to do its job. Affter that, restart VM and you should have larger resolution available.

PS: I assumed that you are ruining 32-bit ubuntu guest. If it's 64-bit, then replace x86 with AMD64.

---

### Post by Twitch04 on 2010-04-27
Yes, that's correct, it's 32-bit. However, I already did install the guest additions. XD. It was the first thing I did when I booted up the virtual machine the first time. That did allow me to go from 800x600 to 1024x768, but that's as high as she goes.

It's not really a big deal, but I wasn't sure really how VirtualBox works as far as drivers for... well, everything. It's totally different. I mean, I needn't drivers for my modem [which were VERY hard to find for the partition that's actually on my hard drive] because if I connect to the internet [yes, I'm on dial-up] before I boot VirtualBox, it's just recognized as automatically being online.

So I suppose it's also just more of a general question about the whole thing than specifically video card drivers. 

Thank you for the help, though, sir. Love this community.

---

### Post by Shazaam on 2010-04-27
Twitch04...
You can resize the VBox window using the menu (at the top of the window), then hover your pointer over one of the corners and drag it. I have to do this every time as I've not found a way yet to make it happen automatically. VBox will scale the window contents nicely.
I am on dialup also and my host machine has to already be connected to the internet to be able to surf using the virtual machine. You are not alone.

---

### Post by mickie.kext on 2010-04-27
> **Shazaam said:**
> Twitch04...
You can resize the VBox window using the menu (at the top of the window), then hover your pointer over one of the corners and drag it. I have to do this every time as I've not found a way yet to make it happen automatically. VBox will scale the window contents nicely.
I am on dialup also and my host machine has to already be connected to the internet to be able to surf using the virtual machine. You are not alone.

^Yeah, that should be solution. If that does not work, then you exit VM and go to "display" setting of you VM in VBox. There you can increase you virtual video memory from 12Mb to some bigger amount. Set it at 64Mb for example. Then do again what **Shazaam** told you, and it should now work.


Good luck.

---

### Post by Twitch04 on 2010-04-27
No, I don't think you guys are quite understanding. At least partly. I already installed VirtualBox Additions, so I can just hit hostkey+F to make Ubuntu full-screen, 1024x768. So that part's fine. It's just that I wanted to try a slightly HIGHER resolution than 1024x768, but I suppose it's not possible in Virtualbox.

I'll try seeing how much of my video card's memory is allocated for VBox next time I turn it off, though [I'm using it right now]. My video card has 1024 mb of memory, so I should be fine upping it a bit.Haha.

---


---
title: "Should I install Linux?"
date: 2017-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by 1jarwolf on 2017-10-26
Alright, I just purchased a new laptop...well...it's refurbished but new to me. Anyhow, I purchased a Panasonic Toughbook CF-29 MK4 Intel Pentium M - 1.2GB ram, and 60gb hard drive and it is supposed to have Windows 7 Professional. So...I think it may be kind of slow. Should I keep the Windows 7 or install Linux over it? Also, I don't trust really using the OS that is on there, never know if there is a hidden keylogger or trojan. I like Windows 7 though. I don't know... I wanted to ask for your opinions.

---

### Post by RobGoss on 2017-10-26
My personal opinion would be to install Linux / Lightweight distribution on that machine but that's just me, I don't see how they would have** Windows 7** installed on that machine with only **60-GB** of storage and the low amount of Ram, I'm sure it will be very slow and not very responsive. Best of luck with what OS you choose

---

### Post by mastablasta on 2017-10-26
win7 is supported until 2019. you should add more ram to it (if you can), but on the other hand you will start running out of disk space as well. the laptop was made for WindowsXP.

some Pentium M are 32 bit only. not some beast of a computer, so you might benefit form using Lubuntu or similar light desktop on it.

i am not sure if Linux works on it, but live session should reveal how good it works. with Lubuntu you will definitely have more ram available.

after that it depends on what you plan to use it for. for running windows apps it is best to use windows OS.

---

### Post by sudodus on 2017-10-26
> **mastablasta said:**
> i am not sure if Linux works on it, but live session should reveal how good it works. with Lubuntu you will definitely have more ram available.


+1

Try Lubuntu live. I suggest that you start by trying Lubuntu 16.04.1 LTS **live** according to this link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

You may need the boot option **forcepae** (depending on the version of the Pentium M processor).

---

### Post by 1jarwolf on 2017-10-26
Indeed. I do believe it is 32 bit. I just want an OS that will not be slow. I kind of wanted Ubuntu as for the most part, I get no errors and I like the looks of it compared to other Linux distributions. I guess I will have to install an Linux OS, I'm not sure if Ubuntu will be slow or not on it. I also don't really know what to even get for the ram if there is that I can get for it. I will try the Lubuntu first. The sad thing is, I don't have a Windows OS at the moment to be able to create a bootable USB. On another note, what can I upgrade on this PC, such as the HDD, and ram and what exact items should I get if upgrade-able? I took a hardware class in College about eight months ago but my professor did not really go into depth except show us how to take a computer tower apart and put it back together so, I have a general knowledge of what these hardware items are, but I don't know what to get that is compatible and all of that. I have a feeling this last part should be a different thread to avoid getting off topic.

What is forcepae and how do I install it?

---

### Post by sudodus on 2017-10-26
**forcepae** is a boot option, that activates a latent feature of some Pentium M and Celeron M processors. These processors have PAE capability, but they do not flag for it.

See this link, that describes how to use it.

[Pentium M and Celeron M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by 1jarwolf on 2017-10-26
@sudodus So, the forcepae is all because it doesn't have enough ram? I have read the website you have linked and I am kind of confused. I am getting that it causes a fake-pae in the system to gain a higher amount of ram to work around with when actually booted up.

---

### Post by sudodus on 2017-10-26
No, forcepae is because the current 32-bit versions of Ubuntu and flavours of Ubuntu use a PAE kernel, and look for the PAE flag.

---

### Post by ian-weisser on 2017-10-26
> **1jarwolf said:**
> Should I keep the Windows 7 or install Linux over it? 

Should you? No.

Install whatever OS will make you most comfortable.

Only install Linux on personal equipment if you *want *to.

---

### Post by mörgæs on 2017-10-26
> **1jarwolf said:**
> I don't have a Windows OS at the moment to be able to create a bootable USB.

I thought the computer was running Windows now. 

It may not be young enough to boot from USB so you may need a DVD.

Try a live boot of Lubuntu, one way or another. If everything works you don't have to worry about PAE.

---

### Post by Autodave on 2017-10-26
Xubuntu should also work well on there. It is lighter than Ubuntu, but a little heavier than Lubuntu.

---

### Post by RobGoss on 2017-10-26
Start with the lighter version and see how it goes. Upgrading the Ram will be the least expensive and should make Linux run much better

Trying to change any other hardware components might be costly. I have a few older machines and most if not all, have at least 4 GB of Ram just to make things run smoothly

I try to stay away from the 32-bit ISO's seeing there's talk about it being dropped

---

### Post by leunam12 on 2017-10-26
> **RobGoss said:**
> My personal opinion would be to install Linux / Lightweight distribution on that machine but that's just me, I don't see how they would have** Windows 7** installed on that machine with only **60-GB** of storage and the low amount of Ram, I'm sure it will be very slow and not very responsive. Best of luck with what OS you chooseI sell a lot of mini computers with Windows 7 and only 60 to 64 Gb storage. Windows 7 does not require a lot of space. Windows 10, on the other hand, requires a lot more because it keeps downloading huge files every time it upgrades and if you don't delete those "previous version" files it can fill up your HDD in no time. My personal laptop has a 32GB SSD and it runs Windows 8.1 just fine.

---

### Post by Mark Phelps on 2017-10-26
For many years, I used an old laptop that came with Windows XP installed and I put Ubuntu 8.04 on it -- and it worked great!

Then, changes were made to the Linux kernel and newer versions of Ubuntu, and any other distro I tried, would not work the screen buttons anymore, and since it was a convertible, that eliminated the key feature under Linux -- so I restored XP to it.

The best performance upgrade was replacing the memory sticks with ones with larger capacity -- and it worked well, up until an eventual Win7 upgrade.

If yours runs slow under Win7, it will under Ubuntu, as well -- so the advice of using a lightweight Linux distro is the way to go.

In my case, the only thing that made the Win7 performance good was swapping in an SSD to replace the HDD.

So, if you want good performance, I would consider using an SSD in it.

---

### Post by mörgæs on 2017-10-26
> **RobGoss said:**
> 
I try to stay away from the 32-bit ISO's seeing there's talk about it being dropped

[https://ubuntuforums.org/showthread.php?t=2312451&page=7&p=13691370&viewfull=1#post13691370](https://ubuntuforums.org/showthread.php?t=2312451&page=7&p=13691370&viewfull=1#post13691370)

---

### Post by 1jarwolf on 2017-10-26
The seller says he/she is going to ship he a CF-30 3GB Ram and 250 HD. Man, I hope that is true. I won't know if it boots up into USB until I get it. Alright guys, I will have to wait a week before I can try all of this.

---

### Post by wildmanne39 on 2017-10-26
*Thread moved to **Ubuntu, Linux and OS Chat for a better fit **.*

---

### Post by 1jarwolf on 2017-10-26
I'm not sure if the Windows 7 will work or not. I guess I will have to wait until I get it. If it's slow and whatnot, I will see about installing either Xubuntu or Lubuntu. Which out of the two would you prefer? Do they both have forcepae already in the OS it's self? Sadly this computer I am getting is 32 bit.

---

### Post by ian-weisser on 2017-10-26
Try them both and see if there's a difference.
That's what LiveUSBs are for.

---

### Post by mörgæs on 2017-10-27
> **1jarwolf said:**
> Do they both have forcepae already in the OS it's self? Sadly this computer I am getting is 32 bit.

All Buntus can use the forcepae option but forget about it for now. Chances are that you don't need it at all. 

There is nothing sad about a 32 bit operative system except that Chrome is unavailable. I recommend people to install 32 bit if they run low performing but 64 bit capable hardware.  

As others have mentioned: Try the live boot. There is no point in guessing before you have hands-on experience.

---

### Post by 1jarwolf on 2017-10-27
Okay. I will try out the live USB OS'es. Thank you all for the advice. I was not sure what to do when I get this older computer. Thank you all for your support!

---

### Post by RobGoss on 2017-10-27
> **1jarwolf said:**
> Okay. I will try out the live USB OS'es. Thank you all for the advice. I was not sure what to do when I get this older computer. Thank you all for your support!

You're very welcome you would be surprise how well Linux runs on older machines, I have about 8 machines and they run GREAT

---

### Post by kurt18947 on 2017-10-27
I will second those who advise installing a lighter distro if you go that route. I have a Thinkpad X61 tablet with a low/midrange core2 duo and 3 GB RAM. It will run Ubuntu mainstream 17.10 but is 'happier' with something lighter. One big issues is that the display is only 1024X768. I had Xubuntu 16.04 running on it and that worked very well. Another lighter weight distro derived from Lubuntu is LXLE. Lubuntu comes with less mainstream apps - abiword, gnumeric etc. There are other ubuntu derivatives such as Mint though the current Mint series has some things I don't care for.

---

### Post by 1jarwolf on 2017-10-27
I just want to know what ram I can get for my computer, like an upgrade ram that is compatible. I didn't get a model number for the pc but if I do I can just go to [https://promotions.newegg.com/memory/17-5198/index.html#/](https://promotions.newegg.com/memory/17-5198/index.html#/) , so I guess I solved my own question, but opinions are always wanted! :D

---

### Post by ian-weisser on 2017-10-27
Every reputable online store has some kind of easy-memory-finder.

---

### Post by 1jarwolf on 2017-10-28
Hmm. Does Xubuntu have more mainstream apps / programs?

---

### Post by 1clue on 2017-10-28
I would recommend that you max out the RAM. That said, the product sheet says max is 1.5g, but it may work with more. The product sheets are generally made when the system is new, and then never updated. I would ask on the panasonic forum about maximum usable ram for this model.

The good thing about old equipment is that the memory is very cheap to max out and it has a huge impact on performance.

lxde (Lubuntu) is probably the lightest weight *buntu, but xfce (Xubuntu) is not much different and I like xfce better than lxde.

---

### Post by 1clue on 2017-10-28
Xubuntu, Lubuntu and Ubuntu and a lot of other *buntus all use the same software repository.

Each version has a different default window manager and the apps may either be different or may be compiled with different options.

Ubuntu is for newer mainstream hardware and has more bells and whistles. Xubuntu and Lubuntu are made for older hardware or newer lower-powered CPUs (like atom or i3 or ...).

---

### Post by mörgæs on 2017-10-28
> **1jarwolf said:**
> I just want to know what ram I can get for my computer, like an upgrade ram that is compatible. I didn't get a model number for the pc but if I do I can just go to [https://promotions.newegg.com/memory/17-5198/index.html#/](https://promotions.newegg.com/memory/17-5198/index.html#/) , so I guess I solved my own question, but opinions are always wanted! :D

Again: Wait with these considerations until you have hands-on experience. Opinions serve no purpose if you don't have the hardware for testing them.

---

### Post by techguru30 on 2017-10-28
> **1jarwolf said:**
> Alright, I just purchased a new laptop...well...it's refurbished but new to me. Anyhow, I purchased a Panasonic Toughbook CF-29 MK4 Intel Pentium M - 1.2GB ram, and 60gb hard drive and it is supposed to have Windows 7 Professional. So...I think it may be kind of slow. Should I keep the Windows 7 or install Linux over it? Also, I don't trust really using the OS that is on there, never know if there is a hidden keylogger or trojan. I like Windows 7 though. I don't know... I wanted to ask for your opinions.

You should be able to run Ubuntu 32bit version on your laptop. It should run better than Windows 7 with low specs. I would recommend to upgrade your ram if possible on your hardware.

---

### Post by sports fan Matt on 2017-10-29
My experience is similar to Mark's.  Started with 7.10 and havent looked back on my spare system.  I still run Windows on my main for a few day to day softwares.  Use what you are comfortable with. :)

---

### Post by jpberes on 2017-10-29
Dear,
In fact there are 2 flavours of Ubuntu you can try, since (and I did test and try) there is fairly no difference in resource usage between these two.
It is like mentioned several times within the answers Lubuntu (= Ubuntu with LXDE desktop environment) OR Xubuntu (Ubuntu with XFCE desktop environment).
I personally prefer the XFCE version (so Xubuntu) since it is very customizable ...
With all the customizations I did made, it only uses 354Mb of RAM (fully workable) !
Hereby an example of my Xubuntu 17.10 version
Regards, JP
[ATTACH=CONFIG]277333[/ATTACH]

---

### Post by 1jarwolf on 2017-10-31
Alright, I am running Xbunutu on this laptop that I have gotten through the mail. I like it so far no problems or lag!

---

### Post by ulysses77 on 2017-10-31
Definitely would be better off with a lightweight Linux distro.

---


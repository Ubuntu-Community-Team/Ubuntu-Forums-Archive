---
title: "drivers: system76 vs. ZAreason"
date: 2013-07-07
forum: System76 Support
---

### Post by rybnik on 2013-07-07
Why is there a "System76 Driver" but no "ZAreason Driver"?  
Is the linux kernel alone enough to get all of the hardware on a zareason machine to work?  If so, is that the reason?
Thanks.

---

### Post by 3Miro on 2013-07-07
The System76 "driver" is somewhat mislabeled. The Linux kernel has all the needed modules, what the S76 driver provides is a bunch of automatic setup scripts to adjust power management and some other options. It is a nice and convenient thing to have, but it is not necessary.

I don't know if ZaReazon have their own scripts.

PS: In the past, the System76 driver would also install the proprietary Nvidia drivers from the Ubuntu Software Center, basically just run the appropriate terminal command. Nvidia video cards were the only piece of hardware to require a module outside of the kernel.

---

### Post by rybnik on 2013-07-07
[quote=3Miro]The System76 "driver" is somewhat mislabeled. The Linux kernel has  all the needed modules, what the S76 driver provides is a bunch of  automatic setup scripts to adjust power management and some other  options. It is a nice and convenient thing to have, but it is not  necessary.[/quote]
That's good news.

[quote=3Miro]I don't know if ZaReazon have their own scripts.[/quote]
As they give the option to ship a machine without *any* OS pre-installed, it would seem that they don't.  And the fact that they give that option in the first place was what made me think that they chose their hardware more carefully than sys76 did.

I can't understand why having an OS pre-installed is seen as desirable.  To have control over certain things that I would think most linux users would want control over (like having a separate partition for /home), you need to do the installation yourself anyway.

I don't mean to turn this into a thread for complaining about sys76, but even if you wanted Ubuntu and wanted it pre-installed, they still don't give you the choice of the current release or the LTS release--only the former is available.

[quote=3Miro]In the past, the System76 driver would also install the proprietary  Nvidia drivers from the Ubuntu Software Center, basically just run the  appropriate terminal command. Nvidia video cards were the only piece of  hardware to require a module outside of the kernel.[/quote]
I remember reading about Torvalds's "Nvidia, f*** you!" remark.  lol!  He makes for a good BDFL.  Yeah, I noticed that sys76 doesn't have nvidia cards anymore.  (good thing, I presume)

---

### Post by rorschachwalter on 2013-07-07
System76 machines do require a number of tweaks to get them working.

Brightness keys? Need to be setup. Display toggle key? Needs setup.

Also, the wireless *and even the ethernet port* require non-free firmware. I couldn't get Debian to work with the wireless in my System76 machine. I bought it because it was supposed to be compatible with Linux. Turns out it's only compatible with Ubuntu, and that still requires tweaking.

---

### Post by 3Miro on 2013-07-08
System76 supports Ubuntu and Ubuntu only. Other distros work simply because they are Linux.

System76 does tweak the BIOS, I don't think ZaReazon does anything Linux special on their machines. In fact, System76 is a lot more conservative in their choice of hardware, ZaReazon would be as bold as to offer machines with Nvidia Optimus (that was a few months back).

System76 laptop Bonobo Extreme does come with Nvidia video card.

---

### Post by rybnik on 2013-07-08
[quote=rorschachwalter]System76 machines do require a number of tweaks to get them working.

Brightness keys? Need to be setup. Display toggle key? Needs setup.

Also, the wireless *and even the ethernet port* require non-free  firmware. I couldn't get Debian to work with the wireless in my System76  machine. I bought it because it was supposed to be compatible with  Linux. Turns out it's only compatible with Ubuntu, and that still  requires tweaking.[/quote]
That is quite startling.

I was under the impression that the advantages of buying from system76/ZaReason were:
(1) not having to support Microsoft
(2) hardware that "just works" without having to mess with drivers

But from your post, it seems that (2) isn't the case.

Right now I use kubuntu on a Dell laptop, and the only driver that I had to install manually was for the wifi.  Everything else "just worked"--including the brightness keys and the ethernet port.  Granted, it's old hardware that I'm using, but if a dedicated linux vendor is worse than Dell when it comes to linux-compatible hardware, then... that's really something!

---

### Post by rybnik on 2013-07-08
[quote=3Miro]I don't think ZaReazon does anything Linux special on their machines.  In fact, System76 is a lot more conservative in their choice of hardware[/quote]
Sorry, but could you clarify what that means?  I don't think I understand.

Thanks for your replies.

---

### Post by rorschachwalter on 2013-07-08
I've had great experiences with Dells and compatibility. In fact, I have an Inspiron 17R SE sitting here right now that has working ethernet, wireless, and brightness keys. The only problem is that its touchpad is recognized as a PS/2 mouse instead of a touchpad, but aside from the lack of gestures (which I don't care for anyway), it actually runs better as a PS/2 than after you install the (single-command) ALPS driver for it.

So yeah, compared to Dell, System76 is actually less compatible. It's very, very, very disappointing. I might send my Gazelle back except I'd lose ~$80 shipping.

---

### Post by 3Miro on 2013-07-08
> **rybnik said:**
> Sorry, but could you clarify what that means?  I don't think I understand.

Thanks for your replies.

System76 build machines with custom BIOS and they guarantee compatibility with Ubuntu. I don't think Zareazon does anything of the sort, they just sell the default BOIS.

For System76 + Ubuntu you don't have to make any tweaks or adjustments. You need two clicks to install the System76 "driver" and everything works.

For other distros, you you don't have to make anything more special than you would on any other machine. The point of System76 is that you can make their machines work, if you happen to buy incompatible hardware from someone else, then you are in big trouble. Someone like Dell sells a ton of machines, you are guaranteed that many will not work well with Linux. Why take a gamble?

---

### Post by rorschachwalter on 2013-07-08
> **3Miro said:**
> Someone like Dell sells a ton of machines, you are guaranteed that many will not work well with Linux. Why take a gamble?

In the first week since having my new Gazelle, I've discovered:

[LIST]
[*]touchpad doesn't respond to changes in Mouse & Touchpad settings
[*]BIOS low battery alarm setting doesn't work -- my laptop continues to make loud, annoying beeps on low battery
[*]I have to plug in an external microphone before the internal microphone works
[*]HDMI audio stops working after suspend
[*]even with the System76 Driver, my display toggle (F7) isn't working
[*]the keyboard constantly misses strokes because of poor design
[/LIST]

Also, the logo on my machine was placed off-center. Not artistically off-center, just I-don't-care-about-my-work off-center.

Why take a gamble? Because it seems Dell doesn't have as many problems as this System76 has been giving me. I spent ~$1000 for a compatible machine, and System76 doesn't seem interested in taking it back, telling me "We'll figure it out" instead.

---

### Post by screaminj3sus on 2013-07-08
> **rorschachwalter said:**
> System76 machines do require a number of tweaks to get them working.

Brightness keys? Need to be setup. Display toggle key? Needs setup.

Also, the wireless *and even the ethernet port* require non-free firmware. I couldn't get Debian to work with the wireless in my System76 machine. I bought it because it was supposed to be compatible with Linux. Turns out it's only compatible with Ubuntu, and that still requires tweaking.

It really depends on the model...All the hardware in my system76 lemur ultra (lemu4) works out of the box, perfectly, in pretty much any distro that has kernel 3.8 or newer. I currently run arch linux on it.

Wireless? Out of the box
Ethernet? Out of the box
Sound? Out of the box
Card reader? Out of the box
Brightness keys? Out of the box

I did need a few tweaks when I first got it, just for the brightness keys and card reader (which the system76 driver obviously did automatically for *buntu), on other distros I just needed to add one line to my grub config to get the brightness keys, and install the dkms driver for the realtek card reader. But since kernel 3.7 the brightness keys work out of the box and since 3.8 the card reader does too. Right now this laptop is the best linux experience I've ever had. It just works in every distro I try.

I did run debian on it for a while too. Obviously there were a few issues with debian, but thats just because debian uses a ridiculously old kernel and has strict policies about including non-free firmware... After installing kernel 3.8 in wheezy everything was fine (And I'm pretty sure kernel 3.9 is now in the official wheezy backports repo). And you can easily get the non-free wireless and ethernet firmware during the debian install, its documented on the debian wiki. Copy the firmware files to a usb stick, plug it in during install, and the installer will automatically find and use them. I'm going to guess that you have intel wireless. Even though intel wireless does have non-free firmware, its still typically some of the best supported wireless in linux, and debian is a definite outlier (and its not even that hard to get it to work using the procedure outlined above) when it comes to intel wireless out of the box, 90% of distros will work out of the box with intel wireless...

---

### Post by rorschachwalter on 2013-07-08
I upgraded Debian to 3.9. Stuff still didn't work. I tried putting firmware onto the USB stick, but not only was it difficult to find, but the wireless firmware wouldn't get picked up by the installer. I got ethernet working, but even after getting the wireless to see a network and ask for the key, it would appear connected without giving any actual throughput.

And regardless of kernel, HDMI audio out has issues, brightness keys didn't get picked up automatically, etc.

And even on *Ubuntu* HDMI audio out won't work after suspend, dispay toggle is borked, touchpad doesn't respond to settings changes, wireless has issues, etc.

I guess it's the model. But for a company making machines that are supposed to be flawless OOTB, they certainly missed the mark with the newest Gazelle.

---

### Post by screaminj3sus on 2013-07-08
Yeah I've definitely had no issues with hdmi audio, suspend/resume or brightness keys here. That model does sound a bit disappointing, but typically these types of issues should be resolved in future kernel updates though (and kernel development moves quite fast these days), sometimes running linux on bleeding edge hardware can be a bit rocky because the kernel support isn't fully there yet. I got my lemu4 a bit later in its life time.

---

### Post by 3Miro on 2013-07-08
> **rorschachwalter said:**
> In the first week since having my new Gazelle, I've discovered:

[LIST]
[*]touchpad doesn't respond to changes in Mouse & Touchpad settings
[*]BIOS low battery alarm setting doesn't work -- my laptop continues to make loud, annoying beeps on low battery
[*]I have to plug in an external microphone before the internal microphone works
[*]HDMI audio stops working after suspend
[*]even with the System76 Driver, my display toggle (F7) isn't working
[*]the keyboard constantly misses strokes because of poor design
[/LIST]

Also, the logo on my machine was placed off-center. Not artistically off-center, just I-don't-care-about-my-work off-center.

Why take a gamble? Because it seems Dell doesn't have as many problems as this System76 has been giving me. I spent ~$1000 for a compatible machine, and System76 doesn't seem interested in taking it back, telling me "We'll figure it out" instead.

In the past couple of years I have purchased two laptops and one desktop from System76. I also used to own a System76 laptop back in 2009. I have never experienced anything even remotely similar to what you describe and I have never had anything by fast and to the point response. I am very surprised about your experience and problems.

---

### Post by rybnik on 2013-07-08
[quote=3Miro][COLOR=#000000]System76 build machines with custom BIOS and they guarantee compatibility with Ubuntu. I don't think Zareazon does anything of the sort, they just sell the default BOIS.[/COLOR]

[COLOR=#000000]For System76 + Ubuntu you don't have to make any tweaks or adjustments. You need two clicks to install the System76 "driver" and everything works.[/quote]
Thanks for explaining.

======================[/COLOR][COLOR=#000000]======================[/COLOR][COLOR=#000000]======================[/COLOR][COLOR=#000000]
@rorschach  That all sounds awful!  But to be honest, I haven't really encountered any stories similar to yours about system76.  As you said that even in ubuntu with the s76 Driver installed, things still don't work, maybe your machine's hardware is defective?
======================[/COLOR][COLOR=#000000]======================[/COLOR][COLOR=#000000]======================[/COLOR][COLOR=#000000]

[quote=3Miro][/COLOR][COLOR=#000000]In the past couple of years I have purchased two laptops and one desktop from System76. I also used to own a System76 laptop back in 2009. I have never experienced anything even remotely similar to what you describe and I have never had anything by fast and to the point response. I am very surprised about your experience and problems.[/quote]
Did you run various OS's on it or just *buntu's?  (just curious)[/COLOR]

---

### Post by 3Miro on 2013-07-09
> **rybnik said:**
> 
Did you run various OS's on it or just *buntu's?  (just curious)[/COLOR]

On the desktop I am running Xubuntu, which probably doesn't count and on the Pangolin with Sandy Bridge I used to try different variant (Fedora, Gentoo, Arch ... ). I would run into occasional need to tweak some settings (i.e. do the work of System76 driver manually), but for the most part everything worked fine.

With my other machines I was either too much of a noob to mess with it, or needed too much of low maintenance and stability to change the officially supported Ubuntu.

---

### Post by screaminj3sus on 2013-07-10
> **rorschachwalter said:**
> 
[*]touchpad doesn't respond to changes in Mouse & Touchpad settings

Come to think of it i'm pretty sure this is not a system76 specific issue, rather its a long-running bug with gnome's touchpad settings. I have two older non-system76 laptops (one with a synaptics touchpad, and one with an elantech touchpad), and gnome/unity's touchpad sensitivity settings have no effect on either of them.

---

### Post by rorschachwalter on 2013-07-10
> **screaminj3sus said:**
> Come to think of it i'm pretty sure this is not a system76 specific issue, rather its a long-running bug with gnome's touchpad settings.

Yeah, I'm not sure if it's a GNOME issue or an Ubuntu issue, but it seems it's not the hardware's fault. I only noticed now because my other laptops have had better touchpads, and this is the first one I've wanted to change settings on to make it function better.

---

### Post by rybnik on 2013-07-12
^What about a different settings manager?  Like kde's "system settings"?

---

### Post by TheCraiggers on 2013-07-15
> **screaminj3sus said:**
> It really depends on the model...

So basically what you're saying is that we're no better off than buying a Dell or Lenovo. This is rather disappointing as I had my eye on System76's new Galago due out this month, and the first thing I would likely do is install Arch.

---

### Post by isantop on 2013-07-15
It's much better than with a Dell or Lenovo. The WiFi, ethernet, display, and chipset MUST work out of the box with no modifications from a vanilla Ubuntu installation, or we won't sell it (basics like the keyboard/mouse are a given). Furthermore, if a system requires *any* kernel replacements for all of the hardware to work properly, we won't sell it (this includes non-vanilla, or unreleased kernels; new modules or kernel boot parameters are fine). For everything that doesn't work out of the box, our driver is open source python code; it's not hard to figure out what it's doing in Ubuntu and apply the same fixes.

---

### Post by rybnik on 2013-08-04
Thanks for your reply, isantop.  That's good to hear.

---

### Post by bonesTdog on 2014-04-06
[**[COLOR=#AEA79F]rorschachwalter[/COLOR]**]("http://ubuntuforums.org/member.php?u=1161705") - This is concerning. It has been quite a while since this post - how did your story end? Were they (or you) able to get your machine working properly, did you return it or are you just dealing with the issues?

---

### Post by jaylittle on 2014-04-07
I would recommend ignoring rorschachwalter.  He is an ex-System 76 customer that has an axe to grind with the brand and spends his time here sh*tting on everything of theirs.  I'm on my third System 76 machine and I couldn't be happier.  All three machines are still in service (panp9, bonx6, gazp9) and not a single one of them has had any major issues.

---


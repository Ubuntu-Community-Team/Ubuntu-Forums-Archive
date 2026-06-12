---
title: "Installing a different distro on a System76 laptop?"
date: 2011-02-22
forum: System76 Support
---

### Post by gunit888 on 2011-02-22
Just wondering if anyone has had experience in doing this, either with a whole wipe or a repartition and multiboot.  I'm strongly considering getting a System76 laptop and I'm wondering about the limits of what I can install on it.  Nothing against Ubuntu, I'm just curious about exploring other distros.  Biggest concern to me would be hardware support and salvaging the prebundled drivers from the Ubuntu install, if that can be done.  

If it matters, I'm looking at picking up either a Serval or a Gazelle, the differences between the two seem fairly minor.

---

### Post by isantop on 2011-02-22
I can't speak directly for other distros, but the only thing we fix for those in Ubuntu would be the Suspend, as it's broken by default due to USB 3. You'll probably want to go with the Intel Wireless as well, as it has better general Linux compatibility.

---

### Post by gunit888 on 2011-02-22
Very good to know, thank you!  Are the hardware drivers in general portable to other distros?  I would have to have such a beast of a laptop and not have drivers.

---

### Post by isantop on 2011-02-22
The driver itself does not run on anything other than Ubuntu. However, it is distributed as python, and it should be readily available under /opt/system76/src/. Additionally, you can extract the source code from the Debian package and use that.

---

### Post by Noah0504 on 2011-02-22
I am now using Debian Squeeze on my Pangolin P6.  Everything has been working flawlessly.  I am loving it!

---

### Post by msrinath80 on 2011-02-22
I'll second that. I'm on a Lemur (lemu1) with Debian squeeze... Hellooo stability :-)

---

### Post by marshmallow1304 on 2011-02-22
PanP5 with Gentoo here.  Configured the kernel myself and all the hardware works with in-kernel drivers plus the nVidia binary.  Suspend/resume still breaks the ondemand CPU governor, but everything else is flawless.

---

### Post by gunit888 on 2011-02-23
Thanks for the replies, it seems that Debian Squeeze works flawless without any modification (aka no driver mining afterwards?).  That's good to hear.  Also, can someone explain what the P# (where # is a number) means?

@marshmallow1304, have you checked what isantop posted regarding suspend?  I'm not sure what 'ondemand CPU governor' exactly means.

It's really good to know I have at least 1 other distro option I can take without worrying.  Often, the option of choice is more important than the requirement of choice.

---

### Post by tlroche on 2011-02-23
> **isantop said:**
> System76 Pangolin Performance - panp7

> **Noah0504 said:**
> I am now using Debian Squeeze on my Pangolin P6.

> **marshmallow1304 said:**
> PanP5 with Gentoo here.

> **gunit888 said:**
> can someone explain what the P# (where # is a number) means?

P==Performance, part of the name of the (now apparently deceased? no longer on the website) "Pangolin Performance" laptop line. Its model#s included panp5, panp6, panp7 (apparently the last). The PanPs were (IIRC) intermediate between the Lemurs and the Gazelles (pricewise, anyway).

---

### Post by bill516 on 2011-02-25
I have an older PanP4 and I run a variety of distros successfully.  Currently Ubuntu 10.4, Debian 6.0 and aptosid 2011-1 all reside on my main drive.  I have Mint LMDE, SalineOS and antiX all running from an external drive.

Several conclusions:

Running a live CD usually can tell me if critical hardware, especially wireless, is going to work.  Note:  With certain distros you may need to install firmware. Check their forums and follow along.

HP printers generally will print, scanner/copiers are iffy.  I cannot comment on other brands.

Power management is inconsistent.  Suspend/Hibernate work fine with Ubuntu and Debian, You will need to test with each distro.  Suspend is a better bet than hibernation.

Desktop interfaces come and go as does desktop artwork (some of which I genuinely admire!), but the actual applications do not vary that much.  Open Office is Open Office, etc.

I finally gave up on KDE after trying to like it.  Too much "Kthis 'n Kthat", clumsy (though powerful) configuration tools, needlessly complex power management and a wireless manager that does not work from the command-line, necessitating something like wicd or ceni.  All in all just a nuisance with no compelling virtues.  So I run Gnome or Xfce.  (My apologies to KDE folks!)

That said if you are a photographer put up with all the dependencies and load DigiKam.  Easily the best set of image maniplation tools I have found this side of GIMP.

Conclusion:  Do cut liveCDs and test-drive.  Do settle on ONE distro as your "go-to" system.  In my (limited) experience an Ubuntu LTS or Debian stable are not bad choices.  Let one of these control your Grub2 installation.  Then go exploring. Linuxland is an interesting place.

One (really) last thought:  While I have settled on Debian-based systems do not ignore Suse.  If I were going to leave apt-ville I probably would go there.  Mandriva is lovely but I think it is in deep mud.

---

### Post by bean2 on 2011-03-01
I am running Fedora 14 on my panp7. I had to download the drivers source code for the realtek wireless card, but it compiled w/o issues. Everything else worked out of the box.

---

### Post by Roush 427r on 2011-03-01
I am actually downloading Mandriva right now, I'll let you guys know how it goes :D

---

### Post by Welly Wu on 2011-04-05
I plan on buying a Serval Professional with all of the top of the line hardware upgrade options. I plan to install OpenSUSE with the Tumbleweed repository. I was wondering if anyone has already done this and if he or she would be so kind to reply with their experiences. Thank you.

---

### Post by isantop on 2011-04-05
I'm not sure how that will work, but you're free to have a go at it. Let us know how it goes!

---


---
title: "Ubuntu Customization Kit questions"
date: 2010-12-03
forum: The Cafe
---

### Post by nolag on 2010-12-03
I want to make a custom Ubuntu.  I want the disk to make some changes that I have made, other than just packages.  If anyone knows how to do the following for the custom disk please reply :).
 
1) change distributor-logo (I will be doing so on my comp soon, and I want that to stay on my disk)
 
2) I changed some of the setting in about:config in firefox, I want those changes to stay
 
3) Themes, I want to change the default and installed ones (to add more)
 
4) Defaults for programs

---

### Post by Oxwivi on 2010-12-03
I think modifying to however you want it on a default install and then using remastersys to make a installer out of your system (with all your settings) is the solution for all of the above.

---

### Post by nolag on 2010-12-03
> **Oxwivi said:**
> I think modifying to however you want it on a default install and then using remastersys to make a installer out of your system (with all your settings) is the solution for all of the above.
 
Yeah, I tried remastersys and had problems.  Maybe I will try it agian.  I want to create a custom like distro, because I want people to be able to install it and not have my own saved stuff.  Will remastersys allow my changes that I mentioned?

---

### Post by Oxwivi on 2010-12-03
Yes, you can create installer without your settings and personal files, though I'm not sure if it's selective or not. I'd recommend taking the latest remastersys for a spin.

---

### Post by nolag on 2010-12-03
> **Oxwivi said:**
> Yes, you can create installer without your settings and personal files, though I'm not sure if it's selective or not. I'd recommend taking the latest remastersys for a spin.
 
I want it to be selective.  My system has too much on it for me to create a cd (I think), and I don't want to make it a dvd.  Also there are some programs that I have included that I am not sure if it would be legal to distribute preinstalled (sun java?), since they have terms that the user would need to agree to.

---

### Post by Oxwivi on 2010-12-03
You should simply review the licenses of all the programs you plan include, if you're planning to create your flavour of Ubuntu. On the other hand if you're just planning to use it by yourself or friends or family, I don't think it'd matter much.

---

### Post by cariboo on 2010-12-03
Have a look [here]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"), you can create a custom Live CD from scratch.

---

### Post by nolag on 2010-12-03
> **cariboo907 said:**
> Have a look [here]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"), you can create a custom Live CD from scratch.
 
Thanks, but I think the tools are easier.  Also I still don't see anywhere in anything that addersses my 2 of problems :'(.  Granted I think reconstructor/remastersys will fix the others.


I changed some of the setting in about:config in firefox, I want those changes to stay.

Themes, I want to change the default and installed ones (to add more).
 
Also I may decide to download chrome as well and make changes (if I have space for it).  Finnaly does anyone know if it is legal to put sun's (now oracal's) java as a default package?  It is GPL now anyways, so I would assume not but I am not 100% sure...

---

### Post by cariboo on 2010-12-03
I think you better look at java's license agian, according to this [page]("http://java.sun.com/j2se/1.5.0/source_license.html"), it uses Sun's BCL license, which has nothing to do with the GPL.

---

### Post by 101011010010 on 2010-12-03
Hello.
You need to look at the /etc/skel folder. Here's a good tutorial that's linked to from the website called "[SIZE=1]Remastersys - Gnome Customization".
[/SIZE]
[http://klikit.pbworks.com/w/page/7315112/Remastersys%20-%20Gnome%20Customization](http://klikit.pbworks.com/w/page/7315112/Remastersys%20-%20Gnome%20Customization)

I hope this helps.


[B][SIZE=1]
[/SIZE][/B]

---

### Post by nolag on 2010-12-05
> **cariboo907 said:**
> I think you better look at java's license agian, according to this [page]("http://java.sun.com/j2se/1.5.0/source_license.html"), it uses Sun's BCL license, which has nothing to do with the GPL.

Yeah, I reread the page on wikipedia, I misunderstood.  I will give it a read over and see if I can include it in my customization

> **101011010010 said:**
> Hello.
You need to look at the /etc/skel folder. Here's a good tutorial that's linked to from the website called "[SIZE=1]Remastersys - Gnome Customization".
[/SIZE]
[http://klikit.pbworks.com/w/page/7315112/Remastersys%20-%20Gnome%20Customization](http://klikit.pbworks.com/w/page/7315112/Remastersys%20-%20Gnome%20Customization)

I hope this helps.
[B][SIZE=1]
[/SIZE][/B]

Thanks, I will give it a look over :D.

---

### Post by Mike_tn on 2010-12-06
What if you just want a graphics deb-package, like nVIDIA current, on the install disk so it get's installed immediately, because you are installing Ubuntu to an offline PC with an nVIDIA chipset. Am doing this so there is no need to attempt to remove and install graphics drivers post-install and offline, which can be a nightmare even online. So Ubuntu would detect and install the right driver from the start.  The rest of the customization possibilities I don't care about. No need to customize much, just one tiny fix that the remastersys might help with. Would that be a good idea?
(Don't mention APTonCD that thing fails)

---


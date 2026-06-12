---
title: "The Ubuntu/Linux Dilemma"
date: 2010-03-14
forum: Testimonials &amp; Experiences
---

### Post by unueco on 2010-03-14
Let me start off by saying that I in general support the Linux movement or in fact *ANY* movement that is designed to free a User from the strangle hold of Microsoft.

But having said that, I find myself facing a dilemma.

It seems that the strong points of Ubuntu and other modern linux flavors is also its weakness and possible downfall: the migration towards being more and more "user-friendly".

There is an old adage from the Early developmental days of "computing for the masses": As systems become more user-friends, users will become more system ignorant.

In the past, the one-liner description I often heard for describing Linux (especially vis-a-vis comparison to Windows) was:
"You have to make it do everything.....but you can get it to do anything."

Back in the old days, installing and running linux was an excersize in learning to master the "logic" of the system. Once you understood, how things were organized...combined with some command-line and scripting skills....you could pretty much customize your system however you liked. That was a benefit to the experience user...but a barrier to the inexperienced.

In an attempt to bring Linux to the masses, later systems have been designed to lower this barrier. System installation is a breeze! But the result seems to also have been that a lot more is taking place "under the hood" without givng the user the ability to affect or modify it.....

......just like with Windows. 

Just a few examples that I have run into so far:

1) The shutdown menu option pulls up a announcement window saying the system will go down in 60 sec. I'd like to modify this time parameter to 10 sec. Seemsit should be a matter of locating the command script referenced by the window and editting it. But can't seem to find out where or how to do that. So I'm stuck with accepting the pre-set parameters.....just like with Windows.

2) The file browser does not seem to display hidden files -- I noticed this when trying to debug a problem I was having with OpenOffice. I'd like to modify the file browser to correct this....but can't figure out how....finally had to go over to the Windows side of my dual-boot and examine the directories. 

3) Recently I've started to get a slew of boot messages scrolling up my screen when I boot-up. So far my system seems to still be running fine. But I'd sure like to know what those messages are. In the old days I'd just look iin /var/message/boot or something similar. But seems this is not longer active in Ubuntu. No idea why.

So it seems there is a danger that by trying to become more user-friendly to the masses, Linux is becoming more and more like...and suffering from more and more of the problems of the Micro$oft Windows systems it is seeking to replace.

Unfortunately, I cannot complain about  this too vociferously. This is my thrid iteration at attempting to migrate away fron Windows to Linux. If Linux had remained as it was in the past, then I probably wouldn't be smart enough to use it.

---

### Post by woodmaster on 2010-03-14
> 
1) The shutdown menu option pulls up a announcement window saying the system will go down in 60 sec. I'd like to modify this time parameter to 10 sec. Seemsit should be a matter of locating the command script referenced by the window and editting it. But can't seem to find out where or how to do that. So I'm stuck with accepting the pre-set parameters.....just like with Windows.

Ubuntu Tweak app let me modify this

> 2) The file browser does not seem to display hidden files -- I noticed this when trying to debug a problem I was having with OpenOffice. I'd like to modify the file browser to correct this....but can't figure out how....finally had to go over to the Windows side of my dual-boot and examine the directories. 


I have an option in nautilus to show hidden files.  Again, I think I enabled it with Ubuntu Tweak
> 3) Recently I've started to get a slew of boot messages scrolling up my screen when I boot-up. So far my system seems to still be running fine. But I'd sure like to know what those messages are. In the old days I'd just look iin /var/message/boot or something similar. But seems this is not longer active in Ubuntu. No idea why.


Don't know about this one.  I see them too, but the error messages have all gone away since I fixed my graphics problems.  I can "see" most of it if I pay attention though there has to be a better way.

---

### Post by steindor2 on 2010-03-14
> **unueco said:**
> 
2) The file browser does not seem to display hidden files -- I noticed this when trying to debug a problem I was having with OpenOffice. I'd like to modify the file browser to correct this....but can't figure out how....finally had to go over to the Windows side of my dual-boot and examine the directories. 


control+h

---

### Post by ajgreeny on 2010-03-14
At the moment gdm for karmic is still in its infancy, and is therefore not very configurable.  I suspect that will change over the next few versions to give back the theming and other configurations that were possible in previous gdm versions.

To enable hidden files to show there is always a way in the preferences of the file browser you are using, or a simple temporary view option in the window you have open at that moment (Ctrl+H in nautilus).

I can't help with the text messages at boot time, as I don't see any after grub.  In my case it goes straight to the white ubuntu logo, then to my own version of the login screen, instead of the grey brown version that appears by default.  I did this by renaming the /usr/share/images/xsplash/bg_2560x1600.jpg as a backup and adding a jpg version of my desktop and renaming it to the same as the original /usr/share/images/xsplash/bg_2560x1600.jpg.  Now I get a smooth transition from the white logo to my desktop background which lasts through the login procedure.

---

### Post by leclerc65 on 2010-03-14
> 2) The file browser does not seem to display hidden files -- I noticed this when trying to debug a problem I was having with OpenOffice. I'd like to modify the file browser to correct this....but can't figure out how....finally had to go over to the Windows side of my dual-boot and examine the directories. 

Edit/Preferences/Show Hidden & Backup Files
Actually with the Side panel (display with Trees) it's much more usable than Win Explorer. I miss program Total Commander though.

---

### Post by coffeecat on 2010-03-14
> **unueco said:**
> 2) The file browser does not seem to display hidden files 

Apart from the keyboard shortcut and changing the default in preferences that other posters have mentioned, it's there in the file browser menu:

View > Show Hidden Files

---

### Post by samh785 on 2010-03-15
> **leclerc65 said:**
> edit/preferences/show hidden & backup files
actually with the side panel (display with trees) it's much more usable than win explorer. I miss program total commander though.
+1

---

### Post by mastablasta on 2010-03-15
i miss it too. but it seems there is plenty alternatives.:
 
[http://168hours.wordpress.com/2008/08/18/10-total-commander-alternatives-for-linux/](http://168hours.wordpress.com/2008/08/18/10-total-commander-alternatives-for-linux/)
 
Total commander site suggests Krusader. haven't tried them yet, but i know now what i will do over the weekend. :-)

---

### Post by unueco on 2010-03-18
> **woodmaster said:**
> Ubuntu Tweak app let me modify this.........Again, I think I enabled it with Ubuntu Tweak

1) Where does one find this app?

2) If you need to use a pre-canned app to make these tweaks, it still is in-line with the general spirit of my original post in that it is not something that can be done by directly accessing whatever command file or script or paramater table. Instead the tweaks are limited to the range of whatever "tweaks" are offered by the app.

And I stil do not understand the elimination of boot messages from /var.

---

### Post by uRock on 2010-03-18
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by armandh on 2010-03-19
yes but

for those that would return to win without OOTB linux
and then stay to learn a bit of the CL....

getting a working OS is a must.

I gave up on linux several times
but when XP became greatly disabled
I found ubuntu, the first distro that just worked for me.

now I do a little copy/paste to terminal
but mostly I just use the OS rather than muck around with it

---

### Post by Simian Man on 2010-03-19
If you want an easily hackable, transparent system, using Ubuntu with Gnome is one of the worst combinations you could choose as both try to make everything as easy and comfortable as possible - at the expense of being a bit more opaque.  Grab Arch, Slackware, or Gentoo then install Fluxbox, Openbox or dwm if you want "transparent and hackable".


> **unueco said:**
> Unfortunately, I cannot complain about  this too vociferously. This is my thrid iteration at attempting to migrate away fron Windows to Linux. If Linux had remained as it was in the past, then I probably wouldn't be smart enough to use it.

I don't understand your thinking at all.  You want it to be too hard for you to use?  Or you'll just wait until you're comfortable and *then* start complaining vociferously?  That's like the idiotic attitude that many Americans have towards immigration.  Once *they're* family is in, everyone else can just go back where they came from.

---

### Post by kaldor on 2010-03-19
"So it seems there is a danger that by trying to become more user-friendly to the masses, Linux is becoming more and more like...and suffering from more and more of the problems of the Micro$oft Windows systems it is seeking to replace."

[www.slackware.com](www.slackware.com)
[www.gentoo.org](www.gentoo.org)
[www.wolvix.org](www.wolvix.org)
[www.archlinux.org](www.archlinux.org)

Maybe those would make you happier if you have the  time to learn. It seems like your computer skill level is higher than average, so maybe you'd rather use a "Total control" distro. 

I have to agree with you in what you are saying though. Ubuntu is progressing fast and becoming more "user-friendly", but it sometimes becomes too basic in some aspects. 

At least you're trying and not complaining about how your Windows programs don't work in Ubuntu. I see those too often. :)

---

### Post by MarcusW on 2010-03-19
> **unueco said:**
> 1) Where does one find this app?

2) If you need to use a pre-canned app to make these tweaks, it still is in-line with the general spirit of my original post in that it is not something that can be done by directly accessing whatever command file or script or paramater table. Instead the tweaks are limited to the range of whatever &quot;tweaks&quot; are offered by the app.

And I stil do not understand the elimination of boot messages from /var.

You don't need Ubuntu Tweak to show hidden files, nautilus can handle that, and it's not hard to find. You can do what Ubuntu tweak does by yourself as you would in any other distribution, but if you can't even find "Show hidden files" I'd use the GUI. :P

---

### Post by unueco on 2010-03-20
> **Simian Man said:**
> 
I don't understand your thinking at all.  You want it to be too hard for you to use?

Essentially, yes! 

If it s too hard for me to use....then I need to learn and grow in order to be able to use it. A process that...while at times frustrating...in the end is of greater benefit than just sitting back, being lazy, and letting the system do it all for me.

Of course, as ideal as this theory is, the flip-side is that in reality, we all have other things to do in our lives and cannot take the time to put in to learn.

So therein lies the dilemma.....

---

### Post by uRock on 2010-03-20
I guess I see your point. I spend a lot of time breaking installs so that I can learn to fix them.

---

### Post by unueco on 2010-03-21
> **Simian Man said:**
> If you want an easily hackable, transparent system, using Ubuntu with Gnome is one of the worst combinations you could choose as both try to make everything as easy and comfortable as possible - at the expense of being a bit more opaque.........

Thank you! After doing a little more research I find that that is the point exactly.....

Quoting from [http://wiki.archlinux.org/index.php/Arch_Compared_to_Other_Distributions](http://wiki.archlinux.org/index.php/Arch_Compared_to_Other_Distributions)

'Arch is designed for users who desire a do-it-yourself approach, whereas Ubuntu provides an autoconfigured system which is meant to be more of a distribution for 'all'."

---


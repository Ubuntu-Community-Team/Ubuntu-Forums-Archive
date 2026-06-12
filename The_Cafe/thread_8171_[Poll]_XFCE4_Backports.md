---
title: "[Poll] XFCE4 Backports?"
date: 2004-12-14
forum: The Cafe
---

### Post by jdong on 2004-12-14
The new 4.2 looks cool.... so.... who wants it??

---

### Post by oddabe19 on 2004-12-14
I actually installed it via their graphical installer, and it worked great....

i just need to add it to my gdm sessions menu...

but other then that, it is really nice...

---

### Post by Daniel G. Taylor on 2004-12-14
I voted yes (although I use Hoary, I know others that would love the updated XFCE4), but I thought that you were going to stay away from desktop environments and stick with desktop user programs like Firefox and such.

---

### Post by TravisNewman on 2004-12-15
It looks very slick, but it may be too much for the backports. I'm ambivalent.

I used it for about 10 minutes, didn't bother cusomizing/configuring, but it's NICE.

---

### Post by poofyhairguy on 2004-12-15
[QUOTE=jdong]The new 4.2 looks cool.... so.... who wants it??[/QUOTE]

count me in, it looks cool enough to try. Plus with that I could talk a stubborn friend of mine into trying Ubuntu. :p

---

### Post by jdong on 2004-12-15
[QUOTE=Daniel G. Taylor]I voted yes (although I use Hoary, I know others that would love the updated XFCE4), but I thought that you were going to stay away from desktop environments and stick with desktop user programs like Firefox and such.[/QUOTE]

Yeah, but XFCE is in Universe, so I think I'm in the clear!

P.S. 4.0.5 comes with Hoary -- not 4.2 RC2!

P.P.S I'm about halfway done... By 9:00pm EST tonight, i should have a full set of testing stuff!

---

### Post by Lovechild on 2004-12-15
I don't personally use or like XFce4, but doesn't some of the nicer features rely on the composite extension in the newer X.org - so if we want full XFce someone has to backport X.org as well?

---

### Post by jdong on 2004-12-15
Well, the composite stuff can wait for Hoary!

XFCE is very nice for older systems that can't handle GNOME too well, but are not so old as to rely on Flux. I'm thinking of the 200-400MHz range as good candidates for XFCE.

---

### Post by Rancoras on 2004-12-15
I would wait for final, but that's just me.

---

### Post by jdong on 2004-12-15
[QUOTE=Rancoras]I would wait for final, but that's just me.[/QUOTE]

What's this 'patience' thing you speak of? ;)


Progress-wise, I'm about 75% done.. I project I'll finish around 5:00 EST.

---

### Post by jdong on 2004-12-15
ok, it's **DONE**! XFCE 4.2 RC2 is in warty-backportstaging.

I'm using it right now, and it appears working.


Please test!

---

### Post by flibblesan on 2004-12-15
[QUOTE=jdong]ok, it's **DONE**! XFCE 4.2 RC2 is in warty-backportstaging.

I'm using it right now, and it appears working.


Please test![/QUOTE]
 I've installed XFCE 4.2 using the os-cillation installers. But I guess the packages are good :D

---

### Post by flibblesan on 2004-12-15
[QUOTE=flibblesan]I've installed XFCE 4.2 using the os-cillation installers. But I guess the packages are good :D[/QUOTE]
 I've installed your backport on my main machine and theres a problem. When I click the filemanager it says rox is not found. How can I get rox?

---

### Post by jdong on 2004-12-15
[QUOTE=flibblesan]I've installed your backport on my main machine and theres a problem. When I click the filemanager it says rox is not found. How can I get rox?[/QUOTE]

Oops, left it out! I'm building a package for rox right now!

---

### Post by jdong on 2004-12-15
ok, it's uploaded.
EDIT: Need leafpad too.... getting that packaged, also.

---

### Post by flibblesan on 2004-12-15
[QUOTE=jdong]Oops, left it out! I'm building a package for rox right now![/QUOTE]

excellent :)

---

### Post by flibblesan on 2004-12-15
[QUOTE=jdong]ok, it's uploaded.[/QUOTE]

whoah that was quick! 
 \\:D/ 

thank you!

EDIT: Excellent! XFCE4.2 works a treat and Rox-filer is happy, thank you. I've checked out this Leafpad. Its a Notepad clone, quite cool too.

---

### Post by jdong on 2004-12-15
Seems like I left out xfce4-toys too -- it's not in the dependencies ! LOL

I'll get that uploaded. Also, I'll check the source tree more carefully this weekend. XFCE won't get into the stable backports tree until probably next Wednesday (when I leave for a vacation).

---

### Post by adbak on 2004-12-15
I originally voted "I dont use XFCE", but I remember that I'll be installing Ubuntu on my parents' old 350mhz cpu.  I forget how much ram, but it's most likely very low.  That CPU only has a 7gb hard drive!

---

### Post by jdong on 2004-12-15
Ack, guess what? I left out even more XFCE stuff! LOL. I got the following taken care of:

xffm4_4.1.1099.2+cvs.20041211-1-4.10ubp1_i386.deb
xfce4-trigger-launcher_4.1.99.2+cvs.20041211-1-4.10ubp1_i386.deb
xfce4-systemload-plugin_0.3.4-2-4.10ubp1_i386.deb
xfce4-showdesktop-plugin_0.4.0-2-4.10ubp1_i386.deb
xfce4-notes-plugin_0.9.7.xfld-2-4.10ubp1_i386.deb
xfce4-netload-plugin_0.2.3-2-4.10ubp1_i386.deb
xfce4-minicmd-plugin_0.3.0-2-4.10ubp1_i386.deb
xfce4-diskperf-plugin_1.5-2-4.10ubp1_i386.deb
xfce4-datetime-plugin_0.3.1-2-4.10ubp1_i386.deb
xfce4-clipman-plugin_0.12.0.xfld-2-4.10ubp1_i386.deb
xfce4-battery-plugin_0.2.0.xfld-2-4.10ubp1_i386.deb


--NOTE: XFFM has a NASTY HABIT of putting stuff in the GNOME Applications menu (right in the root, too!). You can use applications:/// to get rid of them.

I'll continue to investigate the repository.

---

### Post by jdong on 2004-12-15
Update: I got EVERY FRICKIN package backported from that repository! Turns out I was missing quite a number of plugins! LOL. I have the full list in the ubuntu-bp SF project news.


One thing I want you guys to test:

xnetcardconfig wants to install pump as the DHCP client as opposed to Ubuntu's dhclient. Functionality-wise, they should be exactly identical! Can you guys test if networking works after installing xnetcardconfig? Thanks!

P.S. Please, guys, be intelligent... **Don't try installing xnetcardconfig on an important computer then tell me I screwed up your Ubuntu install...**  :-({|=

---


---
title: "My own remastering Ubuntu 10.04.1 for low memory"
date: 2011-02-27
forum: The Cafe
---

### Post by dioramayuanito on 2011-02-27
I've created my own remastering Ubuntu 10.04.1 LTS coz i want to learn UCK for my old 
PC (P4 memory 512Mb - low memory)

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...

i only add 1 file at /etc/gconf/gconf.xml.default/%gconf.xml

does anybody also need this iso? i called it Bobun (Boring-Ubuntu)

if we run it via livecd = 122MiB memory usage (system-monitor)
if we run it from hdd = 97-100MiB memory usage (system-monitor)

thx

---

### Post by hyperdude111 on 2011-02-27
Getting it down to 100mb is quite impressive, if you want to go further you can try to remove gnome and replace it with fluxbox or openbox (they are a bit ugly thought).

I'm afraid I wont really need it (4gb RAM) but good feat to really cut down the ram usage.

---

### Post by Hur Dur on 2011-02-27
No offense, but:

1.) 512mb RAM isn't that low, really. Ubuntu will fly on a system with 512mb RAM on default settings. I know this, because I tried ubuntu on my old netbook about a month ago.

2.) Lower RAM usage doesn't mean that performance will improve.

3.) You can get Ubuntu to use less than 90mb RAM by simply installing Fluxbox.

Overall, it's a good experiment, but you should roll out a distro with performance tweaks, and low resource programs.

---

### Post by stmiller on 2011-02-27
> **dioramayuanito said:**
> 

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...



That's some good stuff. How about services though? Services are more of a hit on resources. Bluetooth, CUPS, saned, ppp stuff are all running by default in Ubuntu. Bah - I hate it with a passion.


At one point you arrive at Debian...  :)

---

### Post by dioramayuanito on 2011-02-27
> **Hur Dur said:**
> No offense, but:

1.) 512mb RAM isn't that low, really. Ubuntu will fly on a system with 512mb RAM on default settings. I know this, because I tried ubuntu on my old netbook about a month ago.

2.) Lower RAM usage doesn't mean that performance will improve.

3.) You can get Ubuntu to use less than 90mb RAM by simply installing Fluxbox.

Overall, it's a good experiment, but you should roll out a distro with performance tweaks, and low resource programs.

1. Yes, but sometime i need NetBeans and Eclipse to run on my old PC, you know "Java bloatware" eats memory more and more :)

2. Yes you're right, but to get "good performace", i disable Compiz and others Animation mechanism in gconf, it works... just like my old Win95 Desktop :)

3. Yes you're right, FluxBox is very very Good on old PC. But my wife already learn GNOME :) ahh you know "women"...

Thanks for your suggestion...

---

### Post by dioramayuanito on 2011-02-28
> **stmiller said:**
> That's some good stuff. How about services though? Services are more of a hit on resources. Bluetooth, CUPS, saned, ppp stuff are all running by default in Ubuntu. Bah - I hate it with a passion.


At one point you arrive at Debian...  :)

Haha! I still need it, because i use bluetooth modem to connect to inet.

Debian is very impressive at "memory usage". I knew it, i learn Debian at College, some of my friends are debian-zealot, debian-minded persons :)

---

### Post by dioramayuanito on 2011-02-28
> **hyperdude111 said:**
> Getting it down to 100mb is quite impressive, if you want to go further you can try to remove gnome and replace it with fluxbox or openbox (they are a bit ugly thought).

I'm afraid I wont really need it (4gb RAM) but good feat to really cut down the ram usage.

Yes sir, you're right, i use ordinary Ubuntu 10.04 in my T400 4Gb :)
Ubuntu + AWN Panel

---

### Post by dioramayuanito on 2011-02-28
> **dioramayuanito said:**
> I've created my own remastering Ubuntu 10.04.1 LTS coz i want to learn UCK for my old 
PC (P4 memory 512Mb - low memory)

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...

i only add 1 file at /etc/gconf/gconf.xml.default/%gconf.xml

does anybody also need this iso? i called it Bobun (Boring-Ubuntu)

if we run it via livecd = 122MiB memory usage (system-monitor)
if we run it from hdd = 97-100MiB memory usage (system-monitor)

thx

i forgot the pics...

---

### Post by Dustin2128 on 2011-02-28
Yeah, I agree that 512MB isn't even close to low. Good work though, getting it down to ~100.

---

### Post by dioramayuanito on 2011-02-28
> **Dustin2128 said:**
> Yeah, I agree that 512MB isn't even close to low. Good work though, getting it down to ~100.

Dear Dustin,
what is exactly "Low Memory PC" in Linux community, i mean how much RAM ...

just for my couriosity :)

Thanks...

---

### Post by Hur Dur on 2011-02-28
> **dioramayuanito said:**
> Dear Dustin,
what is exactly "Low Memory PC" in Linux community, i mean how much RAM ...

just for my couriosity :)

Thanks...
It's subjective. Although, I do believe that the latest kernel requires 16mb RAM. Some people say 1GB is low, some say 128, some say 64, etc. Personally, if a distro uses more than 40mb RAM at boot, then I simply don't use it.

---

### Post by NightwishFan on 2011-02-28
> **dioramayuanito said:**
> Debian is very impressive at "memory usage". I knew it, i learn Debian at College, some of my friends are debian-zealot, debian-minded persons :)

Yeah, I have always been interested in Debian, recently though I got into using it full time.

> **Hur Dur said:**
> It's subjective. Although, I do believe that the latest kernel requires 16mb RAM. Some people say 1GB is low, some say 128, some say 64, etc. Personally, if a distro uses more than 40mb RAM at boot, then I simply don't use it.

I can understand, programs today are a bit lazy with keeping things trim. I got out of using Ubuntu since it usually runs with 700-800mb of ram on my machine, though to be honest it is not slow, and would run with less. However I struggle to run Ubuntu on anything less than 512mb, where Debian does fine. I prefer being a little bit conservative, so I still recommend it to beginners.

---

### Post by dioramayuanito on 2011-02-28
> **NightwishFan said:**
> Yeah, I have always been interested in Debian, recently though I got into using it full time.
I can understand, programs today are a bit lazy with keeping things trim. I got out of using Ubuntu since it usually runs with 700-800mb of ram on my machine, though to be honest it is not slow, and would run with less. However I struggle to run Ubuntu on anything less than 512mb, where Debian does fine. I prefer being a little bit conservative, so I still recommend it to beginners.

The most annoying things in GNOME : Nautilus, metacity and gnome-session are too smart to do anything :)

---

### Post by Jagoly on 2011-02-28
isn't this the purpose of xubuntu?
it ran on 256mb ram ps3 (so long ago...)

---

### Post by aeiah on 2011-02-28
if you want to cut it further, get rid of GDM and gnome. openbox is fine, and you dont really need a session manager. i just have ```
su - username -c startx
``` in /etc/rc.local for auto-login instead of gdm etc.

anyone who says openbox doesn't look good is blind. the look of a desktop is really about gtk anyway.

---

### Post by Dustin2128 on 2011-02-28
> **dioramayuanito said:**
> Dear Dustin,
what is exactly "Low Memory PC" in Linux community, i mean how much RAM ...

just for my couriosity :)

Thanks...
ay.... Not sure about everyone else, but I call a PC low memory if it has less memory than my first video card, 64Mb :D
Though in all fairness, I've run a system with 1Gb up until recently as my main desktop.

---

### Post by Shining Arcanine on 2011-02-28
> **dioramayuanito said:**
> I've created my own remastering Ubuntu 10.04.1 LTS coz i want to learn UCK for my old 
PC (P4 memory 512Mb - low memory)

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...

i only add 1 file at /etc/gconf/gconf.xml.default/%gconf.xml

does anybody also need this iso? i called it Bobun (Boring-Ubuntu)

if we run it via livecd = 122MiB memory usage (system-monitor)
if we run it from hdd = 97-100MiB memory usage (system-monitor)

thx

Replace glibc with uclibc, recompile the software with -Os instead of -O2 and strip out all of the debugging information from the binaries. That should make it use even less memory.

---

### Post by MarcusW on 2011-02-28
> **Hur Dur said:**
> Personally, if a distro uses more than 40mb RAM at boot, then I simply don't use it.

Why? ^^

---

### Post by Hur Dur on 2011-02-28
> **MarcusW said:**
> Why? ^^

I have a low memory complex, I guess. I used to have an old computer with 64mb RAM, so I always kept things low. Now, even with 3GB RAM, and a dual-core, I still have the habit of keeping things to a minimum. I use Dillo instead of Firefox, Geany instead of Office, etc. I don't even need the extra memory, as I barely ever hit 100mb of memory usage.

@Jagoli: Xubuntu is pretty bloated now. You would be better off with Debian or Arch with XFCE.

---

### Post by dioramayuanito on 2011-02-28
> **Shining Arcanine said:**
> Replace glibc with uclibc, recompile the software with -Os instead of -O2 and strip out all of the debugging information from the binaries. That should make it use even less memory.

This is why i love Linux Community, you guys are more informative than my government is :)

Thanks alot for your suggestion

---

### Post by Jagoly on 2011-03-01
> **Hur Dur said:**
> I have a low memory complex, I guess. I used to have an old computer with 64mb RAM, so I always kept things low. Now, even with 3GB RAM, and a dual-core, I still have the habit of keeping things to a minimum. I use Dillo instead of Firefox, Geany instead of Office, etc. I don't even need the extra memory, as I barely ever hit 100mb of memory usage.

@Jagoli: Xubuntu is pretty bloated now. You would be better off with Debian or Arch with XFCE.

**Jagoly**
are you typeing on an iphone? (it auto-corrects my nickname)
Plus i suppose. It ran slower than Win XP on my little brothers VERY OLD Pc (1999)

---

### Post by Lucradia on 2011-03-01
> **dioramayuanito said:**
> I've created my own remastering Ubuntu 10.04.1 LTS coz i want to learn UCK for my old 
PC (P4 memory 512Mb - low memory)

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...

i only add 1 file at /etc/gconf/gconf.xml.default/%gconf.xml

does anybody also need this iso? i called it Bobun (Boring-Ubuntu)

if we run it via livecd = 122MiB memory usage (system-monitor)
if we run it from hdd = 97-100MiB memory usage (system-monitor)

thx

I hope you don't run Firefox or chrome, or anything with flash support.

---

### Post by Spice Weasel on 2011-03-01
Why bother keeping GNOME if you want low memory usage? Even if you need an easy to use interface there are window managers like JWM and IceWM with an interface similar to Windows <Vista.

Even if you absolutely need a DE, LXDE is much better option.

FVWM can look and behave exactly like GNOME but with less CPU + memory usage, but you have to be prepared to fiddle with configuration files and do a bit of reading.

---

### Post by Hur Dur on 2011-03-01
> **Spice Weasel said:**
> Why bother keeping GNOME if you want low memory usage? Even if you need an easy to use interface there are window managers like JWM and IceWM with an interface similar to Windows <Vista.

Even if you absolutely need a DE, LXDE is much better option.

FVWM can look and behave exactly like GNOME but with less CPU + memory usage, but you have to be prepared to fiddle with configuration files and do a bit of reading.

Exactly. I'm a huge IceWM fan, I like it even more than GNOME. You can get a nice, light-weight desktop using IceWM and ROX. You can even add some eye candy to it, and keep it light.

@Jagoly: Yeah, I was typing from my iPod.

---

### Post by IWantFroyo on 2011-03-01
Wow, that's good!
I'm going to have to try to do something like this at some point...
I agree that if you continue, you might want some Debian elements. Someone once said that if they looked hard enough, they could find a version of Debian that would run on their watch. I forgot who said it, though.

---

### Post by Lucradia on 2011-03-02
Debian would be a better choice for starting a low-memory spin actually. A lot of things there aren't in Ubuntu, specifically, a bunch of packages that require gnome depends here, don't over there.

I'd suggest SLiM or LXDM as a login screen.

---

### Post by dioramayuanito on 2011-03-02
> **IWantFroyo said:**
> Wow, that's good!
I'm going to have to try to do something like this at some point...
I agree that if you continue, you might want some Debian elements. Someone once said that if they looked hard enough, they could find a version of Debian that would run on their watch. I forgot who said it, though.

I don't know, after using other OS in a few days, and/or other Desktop (XFCE, IceWM, FVWM etc), i always come back to Ubuntu default settings... is this a LOVE ?

:lolflag:

---

### Post by opodaniel on 2011-03-04
I have one laptop with Intel Pentium M 1.7GHz and Gnome is a little to much for it. I installed openbox, fluxbox, icewm and I kinda like the simplicity of them. In Gnome I like very much Docky  a docking bar similar to the one you find in Mac OsX.
Pls help me with the following:
- dock station so that I can easily switch from one program to the other using the mouse
- How to make the wi-fi autostart for the windows managers I installed 
- How to have access to all the programs installed in gnome?

BR

---

### Post by Lucradia on 2011-03-04
> **opodaniel said:**
> - How to have access to all the programs installed in gnome?

Install **menu** package. This is usually required by low-end WMs / bars / etc. if gnome-menu isn't around. But keep in mind, some programs that you install aren't coded to update the menu, and rather just update xfce menu, gnome menu, etc. It is the responsibility of the program's developer to add such support, otherwise, you must do it all manually.

If you install openbox, you WILL need these too: obmenu, obconf

And if you want a glitzier openbox: murrine-themes and openbox-themes

If you want wi-fi to autostart, openbox will probably be the easiest to do it in, as it uses a user-able-to-read text-compatible file that you can edit with your favorite text editor. I suggest leafpad for a text editor by the way. If you need a low-end media player that's compatible with gstreamer, you should try parole, it requires some xfce things, however. If you need to change the appearance of GTK, you can search for the gtk-theme chooser.

Google is your friend, search **autostart openbox**

If you can bear the very few features it has, I suggest Midori over any big browser. You can get flash running in it, but I *definitely* would not recommend flash. If you need help on midori, or need to report bugs, go to twotoasts.de. Like chrome and opera; Midori supports userjs, but has no Greasemonkey API, some scripts that require the Greasemonkey API, will not work.

**install <package> --no-install-recommends is your ultimate friend** << Do this if you *must* install firefox, it will force ubufox to not install, which is a good thing.

---

### Post by Jagoly on 2011-03-05
Maybe this is surpassed to be a low memory **GNOME** spin. 
If it works on the computer it was designed for, why make it less memory intensive? You wouldn't reduce the graphics quality on a game running at full speed just because it would use less memory.

---

### Post by dioramayuanito on 2011-03-05
> **Jagoly said:**
> Maybe this is surpassed to be a low memory **GNOME** spin. 
If it works on the computer it was designed for, why make it less memory intensive? You wouldn't reduce the graphics quality on a game running at full speed just because it would use less memory.

Aha ! "Low Memory GNOME Spin" ! Thanks ! :popcorn:

---

### Post by Lucradia on 2011-03-05
If you want a low-memory GNOME Spin, you must install it ground up from debian, not ubuntu. (Somehow, Ubuntu's gnome core features take more memory, in the long run, than Debian's.)

You need Debian's mini.iso for that, and install gnome package. (You need a network connection, sadly.)

---

### Post by MasterNetra on 2011-03-05
Anything under 1GB is low (OS not factored) 1GB itself is borderline low as far as I'm concerned, 2GB is good and 4GB+ is awesome. ;) But yea Ubuntu Vanilla handles 512MB of ram like a champ, granted your unlikely to be doing any high resource gaming of course. 

Side note, I'm reminded of my first computer with a GUI, A packard bell with windows 95, had I think about 600MB of hard drive space or somewhere in that area. Don't remember ram or video, wasn't that knowledgeable at that time to even check it. Had a Pentium Processor if I recall correctly. And oh how I frequently KOed the OS, can't remember how many times I had to do a fresh install...good times, good times...kinda.

---

### Post by Fraoch on 2011-04-18
> **dioramayuanito said:**
> I've created my own remastering Ubuntu 10.04.1 LTS coz i want to learn UCK for my old 
PC (P4 memory 512Mb - low memory)

No dual-panel, only 1 panel at bottom
No Compiz
No Animation
No Additional Package(s)
No Removal Package(s)
No GDU-Disk-Notification at session startup
No Evolution-Alarm at session startup
No Remote-Desktop at session startup
No User-Folder-Update-to-Locale at session startup
No Visual-Assistance at session startup
No tty3-tty6
etc etc...

i only add 1 file at /etc/gconf/gconf.xml.default/%gconf.xml

does anybody also need this iso? i called it Bobun (Boring-Ubuntu)

if we run it via livecd = 122MiB memory usage (system-monitor)
if we run it from hdd = 97-100MiB memory usage (system-monitor)

thx

There's a good wiki entry here:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Using the instructions there, the low memory usage winner that I considered to be usable and attractive enough was Openbox + fbpanel.  With conky running the entire OS consumes ~35 MiB.

IceWM came a close second, just a few MiBs more.

Fluxbox is by far the easiest to configure and the most attractive.  It boots at around 40 MiB in this minimalist configuration IIRC.

Other things in the wiki and found elsewhere which turned out not as good:

- perlpanel.  It's really nice but it pushes the Openbox install to about 55 MiB

- FVWM-Crystal.  65 MiB.

- fspanel.  Way too primitive!

- hpanel - much like fspanel

- pypanel (uses an older version of Python which doesn't seem to be available)

- gnome-panel - really needs a full-blown GNOME desktop to be usable

- xfce4-panel - really needs a full-blown XFCE desktop to be usable

- tint2 works well but doesn't provide a menu.  I've seen standalone menu apps mentioned but couldn't find any.

- JWM, couldn't get it to work at all

- currently trying Window Maker, seems to be heavier on resources and I haven't gotten application menus to work on it yet

In regards to file managers, I haven't tried them all but:

- XFE: light on resources but I find it quite ugly

- PCManFM: I almost settled on this one, light and works well

- Thunar: I've settled on this right now, as light or lighter than PCManFM but seems to be snappier overall, plus automounting CDs works better.

Web browsers - I didn't even attempt Firefox, it's gotten way too heavy over the years.  Dillo's no longer in the repos.  I tried another one, I forget which one though.  I settled on Epiphany-webkit.

I'm still playing around with low-memory installs but it's becoming very hard to beat Openbox and fbpanel at 35 MiB.:P

---


---
title: "Wow cant patch!"
date: 2009-10-28
forum: Wine
---

### Post by Cakeguy on 2009-10-28
Hello! I have reinstalled Wow on Wine Ubuntu 9.04. Now that I'm starting Wow Launcher, it just doesnt patch. And yes I've tried downloading the patches manually but that doesn't work neither. And it feel like I've googled around enough not to find any good results. Care to share any information? ;)

---

### Post by pedro_orange on 2009-10-29
> **Cakeguy said:**
> Hello! I have reinstalled Wow on Wine Ubuntu 9.04. Now that I'm starting Wow Launcher, it just doesnt patch. And yes I've tried downloading the patches manually but that doesn't work neither. And it feel like I've googled around enough not to find any good results. Care to share any information? ;)

I'd ask the same from you. What do you mean "it won't patch"? 
What happens when you download the patch manually and run it from a terminal? Does it say anything as to why it's not running?
Have you tried running WoW.exe directly and ignoring the launcher?

---

### Post by Cakeguy on 2009-10-29
> **pedro_orange said:**
> I'd ask the same from you. What do you mean "it won't patch"? 
What happens when you download the patch manually and run it from a terminal? Does it say anything as to why it's not running?
Have you tried running WoW.exe directly and ignoring the launcher?


1. When you recently have installed Wow and when you start the game, then it usually should come up downloading patches and so on. 

2. Haven't tried that, cause I'm a Ubuntu-noob, and I got the game to work before I reinstalled it.

3. Can try that.

---

### Post by sunfire on 2009-10-30
Are you patching saying "Waiting for files to close.." and don't do nothing ? 
If, it does. Then do:

Start "Winecfg" in terminal and change Windows Version to "Windows NT". After installing all patches change it back to normal.
Worked on TBC and WotlK so far.

---

### Post by Cakeguy on 2009-11-14
> **sunfire said:**
> Are you patching saying "Waiting for files to close.." and don't do nothing ? 
If, it does. Then do:

Start "Winecfg" in terminal and change Windows Version to "Windows NT". After installing all patches change it back to normal.
Worked on TBC and WotlK so far.

Sorry I've been inactive. I'll check out if it says so.

And I got a question. What works best with Wine? Downloading Wow fron wow-europe or installing from DVD's?

---

### Post by Cakeguy on 2009-11-15
Okay... I got a bigger problem now. I installed Wrath Of The Lich King to see if it would patch then. But now I cant even start WoW. When I'm trying to start WoW this happens:


[IMG]http://up2this.com/upload/b272f1d3c77baa0c96b47f441f306b1f.png[/IMG]



And if I choose to browse c:/driver with Wine and I open programs and so on the WoW folder looks like this:

[http://up2this.com/upload/3c9b5fc99ee4694a5505f2904522f531.png](http://up2this.com/upload/3c9b5fc99ee4694a5505f2904522f531.png)


And when I try to open the folder this happens:

[IMG]http://up2this.com/upload/695cd3635ca206132d13c960bc7b16cf.png[/IMG]


The weird thing about this picture is that I am a adminstrator on this computer. XD

Sorry if I am noobish. I just wanna get it to work.

---

### Post by 8Kuula on 2009-11-15
For some reason Launcher.exe changes install directory permissions, removes any permisions from user level. To way go around it, hmm... don't have that yet :]

Wine 1.1.33, ubuntu 9.10

[http://bugs.winehq.org/show_bug.cgi?id=20643](http://bugs.winehq.org/show_bug.cgi?id=20643)

---

### Post by Alatar1 on 2009-11-18
Browse on over to home/yourusername/.wine/c_drive/program file/world of warcraft

if theres an X on the folder right click, it go to properties, change the permissons(or you can do the sudo chown in terminal if you like, as long as you unlock the folders first,BUT you do NEED to browse to the world of warcaft directory under /c_drive/program files!!!), Now in that world of warcraft directory, launch WoW via using "WoW.exe" once in the login screen, un-click the box that says "show launcher" to not use the launcher when you run WoW , should fix that permission denied error right up, DO NOT USE THE WOW LAUNCHER IT WILL LOCK YOU OUT EVERYTIME
__________________

---

### Post by alphasoup on 2010-03-26
Launcher.exe changes permissions for entire directory where WoW is located.
I run this script:

wdir="$HOME/.wine/drive_c/Program Files/World of Warcraft"

if [ ! -x "$wdir/Wow.exe" ]; then
   echo "the launcher locked wow, unlocking..."
   chmod +rx -R "$wdir"
   find "$wdir" -type d | xargs chmod +w
   echo "wow unlocked"
fi

Also the beta version 1.2 of wine prevents successful patch update (at least for latest WoW 3.3.3 patch).
Reverting wine to supported version 1.0.1 fixed the patch load problem after the laucher permission fix above was applied.

---


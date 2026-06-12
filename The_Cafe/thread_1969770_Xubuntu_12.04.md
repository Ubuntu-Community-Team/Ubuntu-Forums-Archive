---
title: "Xubuntu 12.04"
date: 2012-04-30
forum: The Cafe
---

### Post by BrokenKingpin on 2012-04-30
With all the discussion going on about Ubuntu 12.04 I though I would start a thread for Xubuntu 12.04, as it is another great release.

This version of Xubuntu is not all that much different from the last release, it is just a bit more polished and fixed a few issues. It fixed a touchpad issue I was having (kernal update) and added the option to configure it in the Xfce control panel. It also has better sound configuration for PulseAudio. This combined with all the visual and theme updates it just comes off as a really polished released.

I have always really liked Xubuntu as it strikes the perfect balance between performance and usability. So is anyone else really enjoying Xubuntu 12.04 thus far?

---

### Post by mips on 2012-04-30
I installed it today and really like it, they did a great job!


That said for me it has way to much apps & services loaded by default and it eats resources as I think it could be leaner and faster.

So what I'm gonna do is reinstall from my alternate cd performing a base install and then I'm gonna add bog standard xfce v4.10 without all the stuff that gets pulled in with the xubuntu-desktop. Did a similar thing with 11.10 & 4.8

This is just personal preference though and no reflection on the quality of Xubuntu. Out of all the Ubuntus flavours I like it the most by a long shot!

---

### Post by pqwoerituytrueiwoq on 2012-04-30
aside from the broken stock themes it is good the sensors applet needs nvidia support i want to know my gpu's temp

---

### Post by samwyse on 2012-04-30
Things are working fine except I had to recompile VICE myself, because the Ubuntu package doesn't have Pulseaudio support and using ALSA freezes the emulator a lot. 

Also I had to install Audacious from a PPA, because the official version has a bug with SID files. Still I don't know why you can't configure the SID-plugin from the GUI when I could do it in Debian.

Third thing, trash doesn't work for me from a non-home partition. It just prompts the permanently delete dialog.

Fourthly, CD ripping with Asunder takes a lot longer than in Debian. Must be doing more error checking or something.

I went from Debian 6 to Xubuntu 12.04 a couple of week ago.

---

### Post by Linuxratty on 2012-04-30
I downloaded it and ran it live this weekend...VERY nice indeed!
I need to know if Compiz runs ok with it?

---

### Post by keithpeter on 2012-04-30
> **mips said:**
> So what I'm gonna do is reinstall from my alternate cd performing a base install and then I'm gonna add bog standard xfce v4.10 without all the stuff that gets pulled in with the xubuntu-desktop. Did a similar thing with 11.10 & 4.8

Hello mips

Let us know what packages you use on top of a command line install. Font rendering is important to me (Ubuntu's is really good, keeps me coming back) but I guess it is for you as well.

Xubuntu 12.04 runs really nice and relatively light on my Samsung Netbook (NC10) and I have not had to install any of the Samsung ppa stuff yet (Voria's ppa). Must be in the kernel now.

---

### Post by LewisTM on 2012-04-30
Don't know what they did to their kernel or drivers but 12.04 Compiz runs as smooth as in 10.10.
So after spending some months with Xfwm4, I'm going back to Compiz for the nice effects and features.
The cube flashing bug is still there but whatever.

Other than that, so far so good. Fast and bug free. Waiting for 4.10 for some fresh meat.

Cheers!

---

### Post by LillyDragon on 2012-04-30
It's the best Ubuntu flavor I ever tried! :'D Plan on re-downloading an Ubuntu ISO encase I need to reinstall it, except I'll grab the Xubuntu version instead. (Saving myself time spent on downloading and installing Xfce.)

This DE has come a long way since I last gave it a spin in 2009, and now it's more user friendly than Gnome 2 was! I loved it already because of how much easier fullscreen stuff was and the snappier speed, but now I don't have to edit text files written in unfamiliar syntax to even change my panel background or color, ah. 8) Changing the color of window borders with a GUI is still out of the question, but version 4 is still an impressive upgrade overall; the Xfce devs, and the guys integrating it into Ubuntu for easy installation, are doing wonders for my desktop!

---

### Post by Marzata on 2012-04-30
We upgraded to Xubuntu 12.04 LTS. This is very stable and stylish distro. Much more responsible and nicer than the old Gnome2 Ubuntu. Thank you, Xubuntu community and congratulations for the great LTS release! Indeed, the best Linux distro around!

---

### Post by Gremlinzzz on 2012-04-30
> **Linuxratty said:**
> I downloaded it and ran it live this weekend...VERY nice indeed!
I need to know if Compiz runs ok with it?

compiz runs smooth with Xubuntu 12.04 i followed this sites advice the thing i had to do was put the command in [sessions and startup] you will find in settings/settings manager
compiz --replace   put it in application autostart

[http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot)

just realized that the site has 2 pages one shows how to put the command in  application autostart.

---

### Post by neu5eeCh on 2012-04-30
Just downloaded [Voyager 12.04]("http://voyager.legtux.org/"), a re-spin of Xubuntu 12.04 --  beautifully themed and dolled up with a touch of French. I tried Ubuntu 12.04 from Beta 1 through the final release, but find myself returning to Xubuntu (having used Xubuntu for about a year now). It just feels cleaner, more customizable and more efficient in every sense; though the biggest improvement, to me, is the ability to view thumbnails on the desktop. That's _huge_.

kiethpeter: [I]Font rendering is important to me (Ubuntu's is really good, keeps me coming back) but I guess it is for you as well.

[/I]I've noticed that if you install the XFCE Desktop or Xubuntu on top of Ubuntu, the font rendition is awful in XFCE. There's some kind of bug, same as there used to be (or still is?) when installing KDE alongside Ubuntu. A fresh install of Xubuntu, so far, is the surest solution.

For those of you who have installed Compiz, have any of you installed Emerald?

---

### Post by Gremlinzzz on 2012-04-30
No, not recently but found a site:popcorn:
going to try
[http://ubuntuforums.org/showthread.php?t=1870792](http://ubuntuforums.org/showthread.php?t=1870792)

---

### Post by BrokenKingpin on 2012-04-30
> **Linuxratty said:**
> 
I need to know if Compiz runs ok with it?
Um... why? Xfwm is part of what makes Xfce so good. It is light and configurable, but still has a built is compositing manager. To me replacing Xfwm with Compiz defeats the whole purpose of running Xfce. But hey, to each their own.

---

### Post by OpenSourceRules on 2012-05-01
The last time I ran Compiz was the old Ubuntu, back when it needed just 384MB of RAM.  I value the balance between performance and functions, so I don't use excessive things anyway.

---

### Post by mips on 2012-05-01
> **keithpeter said:**
> 
Let us know what packages you use on top of a command line install. Font rendering is important to me (Ubuntu's is really good, keeps me coming back) but I guess it is for you as well.

Sure thing, I will start a thread about my endeavours for others to follow. I'm just waiting for the PPA to be populated with XFCE 4.10.


> **VTPoet said:**
> I've noticed that if you install the XFCE Desktop or Xubuntu on top of Ubuntu, the font rendition is awful in XFCE. There's some kind of bug, same as there used to be (or still is?) when installing KDE alongside Ubuntu. A fresh install of Xubuntu, so far, is the surest solution.


I honestly don't recall that happening to me with 11.10 where I did a base install from a Ubuntu alternate cd.

This time round I'll be doing a base install from a Xubuntu alternate cd. Just in case I will back up my existing font configs/folder I have now in Xubuntu 12.04.

My font's in 12.04 don't look any different to what I had in 11.10, unfortunately I wiped my 11.10 install so can't do a side by side objective comparison.

---

### Post by keithpeter on 2012-05-01
> **VTPoet said:**
> I've noticed that if you install the XFCE Desktop or Xubuntu on top of Ubuntu, the font rendition is awful in XFCE. There's some kind of bug, same as there used to be (or still is?) when installing KDE alongside Ubuntu. A fresh install of Xubuntu, so far, is the surest solution.

I'm glad you said that. I noticed exactly that on the PC with Xubuntu on top of an Ubuntu base install. On this netbook, which is a Xubuntu install, the font rendering is ace. I was putting it down to incompatibility of Xubuntu with the graphics/driver on the PC (nvidia/gt520 card with current nvidia restricted drivers).

Now, how about a review of that coffee shop distro of yours? :twisted:

Seriously, I think people here might be interested in Voyager Linux and a bit of description and your views before downloading might be welcome. That guy has done a lot of work with his conky dodads looking at the video.

@mips: font rendering is same on 11.10 and 12.04 when it is working properly; it is this thing that VTpoet found that when you install along side Ubuntu the font settings seem to change.

---

### Post by rajuvembala on 2012-05-01
Voyager is very good looking but its not for the underpowered computers such as netbooks. I have an s10-3s , downloaded voyager yesterday and after using it for 4 hours I felt that stock xubuntu is much peppier. So I gladly returned to xubuntu.

---

### Post by SlugSlug on 2012-05-01
This is my first use of Xubuntu, I moved due to not liking the unity stuff


Found it fantastic tbh, but I have had to install nautilus, and replaced Thunar  (after weeks of holding off!)

---

### Post by neu5eeCh on 2012-05-01
> **rajuvembala said:**
> Voyager is very good looking but its not for the underpowered computers such as netbooks. I have an s10-3s , downloaded voyager yesterday and after using it for 4 hours I felt that stock xubuntu is much peppier. So I gladly returned to xubuntu.

That's strange. 

Not that I doubt you but, Voyager is Xubuntu. They're the same thing. All voyager has done is to add Conky and AWN. Other than that, the themes and icons aren't going to slow you down. Anyway, you can always pop in the live CD and copy over the themes if you like them. Then you'll have Voyager minus Conky & AWN.

@ kiethpeter:  [I]Now, how about a review of that coffee shop distro of yours? :twisted:

[/I]Sir. I take umbrage and while I'm taking that umbrage, I'll have a latte. :???:

@ Slugslug: [I]but I have had to install nautilus, and replaced Thunar

[/I]It's the first thing I do in all my Xubuntu installs.The next stop is [here]("https://launchpad.net/%7Enae-team/+archive/daily").

---

### Post by Luffield on 2012-05-01
Another Xubuntu convert here. I tried to like Unity -- I really did try hard -- but I just can't. Same with Gnome Shell. Cinnamon is better but still needs some polish IMHO. Tried LXDE and it's nice but a bit limited for my needs. And KDE has always been my least favorite Linux desktop and every time I check it out I still can't stand it.

So I tried Xubuntu and I just loved it. Switched 3 computers already and I'm very happy with this desktop. It's a huge step forward comapred to Xfce 4.6.

However, I'm not a fan of most of the default applications in Xubuntu, so I'm using Nautilus, Gnome-terminal, LibreOffice, gedit, gThumb... It just works great.

---

### Post by The Cog on 2012-05-01
Re broken themes:
I always used to like Clearlooks, but some things look really bad in the Clearlooks that ships with Xubuntu now. I found that Clearwaita is a very good replacement:
[http://gnome-look.org/content/show.php?content=145210](http://gnome-look.org/content/show.php?content=145210)
Just copy the zipfile contents to /usr/share/themes.

I notice that with Xubuntu 12.04, Unreal Tournament 2004 occasionally loses scrollwheel motion which means it doesn't always change weapons as it should. I haven't seen this on any previous version of Xubuntu.

Otherwise, it's looking good. I always install gnome terminal because xfce4-terminal doesn't scroll with the scroll wheel in **less** or **man** pages.

---

### Post by neu5eeCh on 2012-05-01
For all Xubuntu users who may not know it, XFCE 4.10 has a PPA and can be installed on 12.04. 

For the "preview" (the following being from [here]("https://plus.google.com/u/0/112064450121097287690/posts/8Z5jnh8cRb1")) do this:

> Would you like to try **Xfce 4.10pre2** ? Are you running **Xubuntu 12.04 beta/pr**? In case of 2 positive answers, you are only one PPA away from your goal.

**-** *use your terminal to type:*

**sudo add-apt-repository ppa:mrpouit/ppa**
**sudo apt-get update**
**sudo apt-get dist-upgrade**

**-** *if you decide to remove **Xfce 4.10pre2**, type these:*

**sudo apt-get install ppa-purge**
**sudo ppa-purge ppa:mrpouit/ppa**

*(Note:  Keep in mind that this is not a final/stable Xfce 4.10 release, but a  preview release 2 - also, you would be testing a Preview Release in a  Beta... so, if you do proceed, do so with caution! & expect some  rough edges)*The launchpad PPA is located [here]("https://launchpad.net/%7Emrpouit/+archive/ppa").



And the following is for the stable version (which isn't yet populated):

[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10]("https://launchpad.net/%7Exubuntu-dev/+archive/xfce-4.10")

I installed 4.10 on top of Voyager 64bit, and most everything (which *I* tried) worked beautifully except for the suspend and hibernate options, which were grayed out (a bug for which a fix has already been committed). Shutting down requires using the "log out" option in the menu.

---

### Post by Linuxratty on 2012-05-01
> **LewisTM said:**
> Don't know what they did to their kernel or drivers but 12.04 Compiz runs as smooth as in 10.10.
So after spending some months with Xfwm4, I'm going back to Compiz for the nice effects and features.
The cube flashing bug is still there but whatever.

Other than that, so far so good. Fast and bug free. Waiting for 4.10 for some fresh meat.

Cheers!

Excellent..I don't even use the cube.

---

### Post by Linuxratty on 2012-05-01
> **Gremlinzzz said:**
> compiz runs smooth with Xubuntu 12.04 i followed this sites advice the thing i had to do was put the command in [sessions and startup] you will find in settings/settings manager
compiz --replace   put it in application autostart

[http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot)
.

Ok,good deal.
Thank you!!!

---

### Post by mips on 2012-05-01
> **VTPoet said:**
> For all Xubuntu users who may not know it, XFCE 4.10 has a PPA and can be installed on 12.04. 

For the "preview" (the following being from [here]("https://plus.google.com/u/0/112064450121097287690/posts/8Z5jnh8cRb1")) do this:

The launchpad PPA is located [here]("https://launchpad.net/%7Emrpouit/+archive/ppa").

People might wanna hold off a wee bit, mr_pouit is busy packaging the 4.10 final release and it should be ready shortly. Once it's in his PPA it will also be moved to the official PPA.

---

### Post by Marzata on 2012-05-01
Nope. We will stick to what is stable in 12.04 LTS. We are old school.

---

### Post by neu5eeCh on 2012-05-01
> **Marzata said:**
> Nope. We will stick to what is stable in 12.04 LTS.

Not me. I like to live on the edge - me, my skateboard, snowboard, or laptop, as the case may be.

---

### Post by Gremlinzzz on 2012-05-01
Did anyone ever get parole plugin too work. I always end up installing totem.:popcorn:
A site like this didn't work with parole but works with totem.

[http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)

---

### Post by M_Mynaardt on 2012-05-01
I've upgraded to Xubuntu 12.04 and I have noticed a couple of problems that are more of a nuisance than anything else:

First; *AbiWord* isn't working quit right.  It won't scroll unless you grab the slider on the side of the screen, and many hot keys don't seem to work very well, or not at all, in *AbiWord*.  It's also prone to doing a screen grab and move when I highlight a block of text.  I don't use *AbiwWord* a lot, but these are annoying little problems.

Second; *gedit* isn't quite right either.  For some reason, it will not highlight the current line of text, even though I have selected that option.  It will darken the current line's number, if the line numbers are showing, but it won't darken the line itself as it did before the upgrade.

Are these just oddities of those apps under 12.04?  I haven't yet run across any other problems since upgrading Xubuntu to 12.04...

---

### Post by marzzbar on 2012-05-05
I've had the same problems you describe with AbiWord, so I've switched to LibreOffice writer for the time being. I don't use gedit though.

---

### Post by M_Mynaardt on 2012-05-06
> **marzzbar said:**
> I've had the same problems you describe with AbiWord, so I've switched to LibreOffice writer for the time being. I don't use gedit though.

Actually, I had a chance to use Lubuntu (what I run my laptop with) today.  I noticed the same little problems with AbiWord and gedit on Lubuntu too.  So I think these might be a couple of minor glitches with Precise Pangolin on the whole.

I don't know if these are problems with just those two apps or not, but I've only noticed with those two.  These are just minor issues, though.  Those apps both work well enough, but just a wee bit off from before.

I have noticed some improvements with Precise Pangolin, though.  In particular, the shutdown is noticeably faster than before.  And the start up seems to be a wee bit faster too.

---

### Post by samwyse on 2012-05-06
> **samwyse said:**
> Third thing, trash doesn't work for me from a non-home partition. It just prompts the permanently delete dialog.

The root of the partitions need a ".Trash-1000" directory that is user writable. I found the solution here: [http://forum.xfce.org/viewtopic.php?id=6910](http://forum.xfce.org/viewtopic.php?id=6910)

---


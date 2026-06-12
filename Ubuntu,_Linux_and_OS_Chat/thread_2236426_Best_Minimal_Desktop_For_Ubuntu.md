---
title: "Best Minimal Desktop For Ubuntu"
date: 2014-07-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Priyanshu_Sharma on 2014-07-26
Hi, I am seraching for best minimal desktop environment to use in Ubuntu 14.04. I know term 'best' is too relative to answer sharply but here's a thing, i have already tried Xubuntu and Lubuntu, see I migrated from Windows and hate every bit of it(specially UI/UX) the start menu type interface in xfce freshens my old 'not-so-good' memories with windows :p . Please suggest a minimal interface. Thanks in advance.

---

### Post by deadflowr on 2014-07-26
Perhaps something like Enlightenment.
It should be in the repos, aka the software center.

---

### Post by grahammechanical on 2014-07-26
Please explain what you mean by the word "minimal." Most user interfaces that claim to be minimal have that same look as Xubuntu and Lubuntu which you apparently do not like that much.

I have used Ubuntu + Unity 3D since it first came out. I have the launcher set to autohide and I know I can make the top panel almost transparent. I use a 20 inch wide screen TV/monitor. So, my desktop work environment is a wide photograph quality background image without any icons in sight and just the top panel on show. Now, that is what I call minimal.

What do you call minimal?

Regards.

---

### Post by vasa1 on 2014-07-26
> **grahammechanical said:**
> ...
What do you call minimal?
...
No desktop at all? But looks like OP has a problem with the "tree" substructure of the menus that most DEs come with. (Not just DEs, but most applications.) So even if Unity seems to avoid the dreaded tree, most of the apps in existence will have them internally. I don't know how popular HUD is as a solution.

Anyway, this doesn't look like a support question. Better off in Chat.

---

### Post by buzzingrobot on 2014-07-27
Research Openbox.

---

### Post by bapoumba on 2014-07-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by mastablasta on 2014-07-28
i3 or xmonad definitelly

---

### Post by frankmorris2 on 2014-07-28
Hello,

I don't know if it is the best, but my OpenBox setup is very light.

Here is my laptop setup:

Installed Ubuntu 12.04 Server (my installation is not new) without any GUI.

Then, I added a few packages:
```
sudo apt-get install openbox menu obmenu obconf xserver-xorg-core xinit xfce4-terminal
```

This installed very simple window manager, without any bells and whistles: no menu bar, no desktop icons, no widgets.
All the applications are available with a right-click.

I suppose the packages names on 14.04 are highly similar.

Have a nice day.

---

### Post by mooreted on 2014-07-30
> **frankmorris2 said:**
> Hello,

I don't know if it is the best, but my OpenBox setup is very light.

Here is my laptop setup:

Installed Ubuntu 12.04 Server (my installation is not new) without any GUI.

Then, I added a few packages:
```
sudo apt-get install openbox menu obmenu obconf xserver-xorg-core xinit xfce4-terminal
```

This installed very simple window manager, without any bells and whistles: no menu bar, no desktop icons, no widgets.
All the applications are available with a right-click.

I suppose the packages names on 14.04 are highly similar.

Have a nice day.

I prefer tint2

sudo apt-get install openbox obmenu obconf nitrogen tint2

---

### Post by mooreted on 2014-07-30
Anyway, I like OpenBox when I want to go minimal because I can design it however I want. It's truly a blank palette.

---

### Post by mooreted on 2014-07-30
> **frankmorris2 said:**
> Hello,

I don't know if it is the best, but my OpenBox setup is very light.

Here is my laptop setup:

Installed Ubuntu 12.04 Server (my installation is not new) without any GUI.

Then, I added a few packages:
```
sudo apt-get install openbox menu obmenu obconf xserver-xorg-core xinit xfce4-terminal
```

This installed very simple window manager, without any bells and whistles: no menu bar, no desktop icons, no widgets.
All the applications are available with a right-click.

I suppose the packages names on 14.04 are highly similar.

Have a nice day.

I prefer tint2

sudo apt-get install openbox obmenu obconf nitrogen tint2

---

### Post by vasa1 on 2014-07-31
> **mooreted said:**
> I prefer tint2

sudo apt-get install openbox obmenu obconf nitrogen tint2

What do you use nitrogen for? Managing the background image?

I use tint2 but I need lxpanel as well for a CPU usage monitor.

---

### Post by vasa1 on 2014-07-31
> **frankmorris2 said:**
> ...
All the applications are available with a right-click.
...
I set things up so that I can access the right-click menu from the keyboard as well. There's [a thread here]("http://ubuntuforums.org/showthread.php?t=2173126") in case someone has something to contribute.

---

### Post by patrikmellq on 2014-07-31
Read this topic [http://ubuntuforums.org/showthread.php?t=2234261](http://ubuntuforums.org/showthread.php?t=2234261) and you will install minimum Ubuntu system from scratch with no window manager.

Then after you basic Ubuntu install from scratch you can pick any window manager you want - i would recommend Fluxbox.

Fluxbox work out of the box and are in the same area as Openbox.

Cheers

---

### Post by mooreted on 2014-07-31
> **vasa1 said:**
> What do you use nitrogen for? Managing the background image?

I use tint2 but I need lxpanel as well for a CPU usage monitor.

Yes, Nitrogen is for the wallpaper and you can make it remember your wallpaper choice in the the autostart.sh script with:

nitrogen --restore &

---

### Post by umrku on 2014-08-14
How about Openbox and Razor?

---

### Post by walterorlin on 2014-08-14
Razor ended up merging with LXDE and now makes LXQt.

---

### Post by Tar_Ni on 2014-08-15
> **Priyanshu_Sharma said:**
> but here's a thing, i have already tried Xubuntu and Lubuntu, see I migrated from Windows and hate every bit of it(specially UI/UX) the start menu type interface in xfce freshens my old 'not-so-good' memories with windows :p

The thing is, a 'minimalistic' or lightweight Linux desktop will not look like Windows 8.1 or OS X 10.9. For better performance on older machines and so for the system to use less ressources, you have to sacrifice all the bells and whistles. A startup menu is for the convenience of the users to quickly acess apps, may it be at the bottom or above the screen. Lubuntu and LXDE default settings looks visually similar to XP in my view, though it's even more efficient. It runs like joy on my 1GB RAM desktop computer. What's interesting is that both LXDE and XFCE are *highly* customizable DE and you can make them look whatever you want them to be like with Cairo-Dock, Docky or Conky and by creating your own taskbar with the icons you want.

---

### Post by pizzalover1974 on 2014-08-15
Well I just installed Ubuntu Studio on my Media Center PC that is connected to the TV. It has a special low latency kernel for sound I just found out. Which explains why my 2.1 wooden speakers I got in a 50% off sale for £100 sound so damn good now. I can hear every tiny audible noise on each note of the music i'm playing today. AWESOME QUALITY.

PLUS its using XFCE as standard. So its all set up right from the get go. Not the lightest Window Manager. But its amongst the lightest of the complete feature rich window managers non roll your own types. ( I know Enlightenment is lighter still but its a bit Frankenstein in looks).

Perfect for watching movies and listening to music, which is what I do on this pure install media PC. Plus as a trained graphic designer ex-student, that decided not to take up the career, it has all the apps I love pre-installed.

As one reviewer stated "The minimum memory requirement for Ubuntu Studio is 512 MB of memory. It  is highly recommended that you have 2GB, or more, as some applications  use up a lot of RAM." 
If you need less your looking at Enlightenment or Openbox if you really need that speed or have a very old system.

A+

PS: It has a a dock pre-installed too. That auto hides when you mouse off it.

---


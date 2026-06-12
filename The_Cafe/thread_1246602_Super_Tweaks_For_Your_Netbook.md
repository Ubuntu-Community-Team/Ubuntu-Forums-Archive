---
title: "Super Tweaks For Your Netbook"
date: 2009-08-21
forum: The Cafe
---

### Post by Bungo Pony on 2009-08-21
Hey all, I figured this would be a good idea for a thread. Please share some tweaks that you did to make your netbook nicer to work with. Here's what I did with mine:

- Wipe Suse off the hard drive and install Xubuntu :)
- Eliminate one task bar and put all "must haves" into one bar
- Make the task bar 'auto hide'
- Change the zoom in Opera to 90% instead of 100%
- Install the 'eeePC' skin in opera to reduce clutter
- Instead of having long descriptions of the open windows, have icons of the windows open (sorry, I don't remember the names of the taskbar apps)
- Reduce size of icons on the desktop

Anyone got more ideas?

---

### Post by gletob on 2009-08-21
Ubuntu Netbook Remix!!

---

### Post by Regenweald on 2009-08-22
Soon as i get a netbook, I'll hook you up :) i'm a tweak freak....

---

### Post by rafita on 2009-08-22
Use the Tree Style Tab in firefox, to put the tabs to the left.

---

### Post by joebodo on 2009-08-22
Ubuntu Netbook Remix (modified theme)
Guake for terminal
Eikon (icons)

Firefox Plugins
All-in-One Sidebar
Tab Mix Plus
Hide Menubar
Personas

[http://img191.imageshack.us/img191/4583/screenshot4h.png]("http://img191.imageshack.us/img191/4583/screenshot4h.png")

[http://img196.imageshack.us/img196/166/screenshot5k.png]("http://img196.imageshack.us/img196/166/screenshot5k.png")

---

### Post by Luca_turicci on 2009-08-22
-Eliminated bottom bar.
-Dimminished the size of fonts and icons.
-Installed the smallest skins and icons I found on gnome-look website
-CUSTOMISED KEYBOARD SHORTCUTS!!!

I'll try Firefox plugins, thanx for the ideas.

---

### Post by 3rdalbum on 2009-08-22
I used to have XFCE set up with two panels - one on either side of the screen. Currently-running programs and services (like battery and wireless monitors) on the left panel, and application launchers on the right panel. The right-panel was an auto-hiding one too.

Because there's much less height than width on most netbook screens, it makes more sense to put panels on the sides rather than on the top.

---

### Post by bodyharvester on 2009-08-22
> **joebodo said:**
> [http://img196.imageshack.us/img196/166/screenshot5k.png](http://img196.imageshack.us/img196/166/screenshot5k.png)

how in the name of the man-god of Holy Tera did you do that? does anybody know?

---

### Post by kerry_s on 2009-08-22
> **bodyharvester said:**
> how in the name of the man-god of Holy Tera did you do that? does anybody know?

**sudo apt-get install ubuntu-netbook-remix**

log out & back in

---

### Post by imbjr on 2009-08-22
On my son's EEE-PC:

. I use elevator=noop as a kernel parameter in the menu.lst GRUB file:

[http://blogs.zdnet.com/perlow/?p=9190](http://blogs.zdnet.com/perlow/?p=9190)

The above link also mentions the use of noatime, which I also use.

. I mount /tmp, /var/log and a few other directories onto the tmpfs system, which places them in RAM - reducing writes to the SSD. This means that logs will not be saved on reboot and the log reader will sometimes complain about missing logs when fired up, but I find it's a small inconvenience.

---

### Post by frrobert on 2009-08-22
I use open box.

Not really a tweak but a cool command line utility to use with your netbook when using an external display. xrandr is a command line utility that allows you to configure the use of an external display.  I found if I used the hot key it would lock my system or cause some other unexpected results .  xrandr has always worked great for me.

Here is an short post I wrote on how to use it

[http://www.batushkas.com/desktop-tips/58-xrandr-and-multiple-displays.html](http://www.batushkas.com/desktop-tips/58-xrandr-and-multiple-displays.html)

---

### Post by speedwell68 on 2009-08-22
> **gletob said:**
> Ubuntu Netbook Remix!!

I was using UNR on my Acer One A150, but have recently replaced it with Xubuntu 9.04.  Xubuntu is faster, uses less memory/disk space and has increased the battery life by at least 20% with no extra tweaking.  Another good tip is to replace the default network manager with WICD, it is smaller, has more functionality than the default network-manager and does away with the need for the keyring applet.  WICD is in the repos on Jaunty, or has it's own repo available.  WICD can also be downloaded as a deb.

---

### Post by Bungo Pony on 2009-08-23
> **speedwell68 said:**
> Another good tip is to replace the default network manager with WICD, it is smaller, has more functionality than the default network-manager and does away with the need for the keyring applet.

I tried WICD. It worked well for a day, and then it quit retrieving the IP address. An apt-get remove restored my wireless to its full functionality.

---

### Post by Warpnow on 2009-08-23
Screenshot of my Acer Aspire One: [http://www.kuki.me/wp-content/gallery/our-users-screenshots/brinson.png](http://www.kuki.me/wp-content/gallery/our-users-screenshots/brinson.png)

---

### Post by cody7002002 on 2009-08-23
This may be a dumb question but, I'm looking to clean up my desktop like yours Warpnow, but how do you access the main menus "Applications, places, system"?

---

### Post by Warpnow on 2009-08-23
The XFCE logo in the top left spawns the ubuntu menu.

---

### Post by Bungo Pony on 2009-08-23
> This may be a dumb question but, I'm looking to clean up my desktop like yours Warpnow, but how do you access the main menus "Applications, places, system"?

You can change the settings so that you'll get the menu when you right click on your desktop.Goto Settings -> Desktop, under the 'behavior' tab, check off 'show desktop menu on right click'

---

### Post by Bungo Pony on 2009-08-23
Here's a couple screenshots of mine

edit: I just got rid of that bar on the bottom of Opera :)

---

### Post by Warpnow on 2009-08-23
I wish instead of autohide I could bind a panel to the useless windows key. Actually, I wish hitting the windows key just brought up the applications menu as if you were right clicking on the desktop.

Then I wouldn't even need a panel at all. Switch between apps using alt + tab.

---

### Post by kerry_s on 2009-08-23
> **Warpnow said:**
> I wish instead of autohide I could bind a panel to the useless windows key. Actually, I wish hitting the windows key just brought up the applications menu as if you were right clicking on the desktop.

Then I wouldn't even need a panel at all. Switch between apps using alt + tab.

doesn't the menu key bring up the desktop menu?

---

### Post by Warpnow on 2009-08-25
> **kerry_s said:**
> doesn't the menu key bring up the desktop menu?

Only if I'm hovering on the background.

---

### Post by kerry_s on 2009-08-25
> **Warpnow said:**
> Only if I'm hovering on the background.

try-> **alt+f1**
it brings up the menu on mine, i'm using jaunty 9.04 unr.

in the keyboard shortcuts that can be changed.

my bag, i just saw your screenshot, your using xfce4.

---

### Post by alienclone on 2009-08-31
not sure of the relevancy but here is a thread i found interesting, the first few posts are a bit comfuzing (as the posters also noticed) but once you read through it culminates into a very interesting "tweak" so to speak.

[http://ubuntuforums.org/showthread.php?t=1104061](http://ubuntuforums.org/showthread.php?t=1104061)

---


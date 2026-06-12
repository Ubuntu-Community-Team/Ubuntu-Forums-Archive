---
title: "Just got a new rig, I can't stand xfce, how do I switch to Gnome?"
date: 2016-07-30
forum: Ubuntu Studio
---

### Post by helios16v on 2016-07-30
Okay, little background, I've been doing professional video editing on a Windows machine for years, I've always been a Linux lover at heart but the need for Adobe After Effects and Premiere kept me using Windows for my workstation, I've been reading into Blender and Lightworks and they seem to be pretty close to par now with how far they've come along so now that I just got my new workstation today, I did some quick Googling research on best distros for video editing so I can start this new machine off using Ubuntu Studio, I did not know it uses XFCE and I'm an eye candy *****, so this for me is not working and I need to be on GNOME but I'm not sure how I uninstall XFCE and install GNOME 3.20.

I found some tutorials on how to upgrade Ubuntu GNOME from 3.18 to 3.20 but I'm not sure if this method is the same for switching from XFCE to GNOME and then removing XFCE all together to keep it as light as possible, not that I need to keep anything light on this power house, just kind of my OCD to remove everything that will not be used.

Any suggestions?

EDIT
I also wasn't sure if this should be in this section as it's regarding Ubuntu Studio, or Desktop Enviroments because the issue is between XFCE to GNOME, sorry in advance if this isn't where this should be posted.

---

### Post by helios16v on 2016-07-31
I've figured out most of it so far, but I'm still getting some issues, everything seems to be "working" but not fully. I'll explain

First I installed GNOME 3.20 according to the guide for updating GNOME 3.18 using 
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt update
sudo apt install gnome gnome-shell
reboot
```

After rebooting, nothing changed, found out I needed to logout, select the session I want, log back in, and it seemed to fix this and I was using GNOME3 with all of it's eye candy glory.

I now noticed that while booting it hangs in the GRUB menu for some reason so I used
```
sudo gedit /etc/default/grub
```
and changed "#GRUB_HIDDEN_TIMEOUT=0" to "GRUB_HIDDEN_TIMEOUT=0". After saving, I used
```
sudo update-grub
reboot
```

Now I was back to booting normally and booting straight into GNOME3 without issues, however the OCD bug inside me of knowing that XFCE was still installed was bothering me, I removed it using
```
sudo apt-get remove xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xfwm4-themes xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers
```
which was posted by SuperFreak in another thread, however it was posted for Ubuntu 12.04 so some of the code came up with errors as not being found (most likely removed in newer XFCE builds since then)

and finally, I installed the Paper-GTK theme using
```
sudo add-apt-repository ppa:snwh/pulp
sudo apt-get update
sudo apt-get install paper-gtk-theme && paper-icon-theme
```

After opening Tweak Tool and changing the theme over to that and enabling Global Dark Theme, I was "done"

However now when I open terminal, it is not themed, and I'm getting these warning messages.
```
(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:3209:17: The 'icon-shadow' property has been renamed to '-gtk-icon-shadow'

(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:6352:23: The '-gtk-image-effect' property has been renamed to '-gtk-icon-effect'

(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:6362:15: The 'icon-shadow' property has been renamed to '-gtk-icon-shadow'

(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:6412:13: The 'icon-shadow' property has been renamed to '-gtk-icon-shadow'

(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:6525:16: The 'outline-radius' property has been renamed to '-gtk-outline-radius'

(gedit:5347): Gtk-WARNING **: Theme parsing error: gtk-dark.css:6548:52: The :prelight pseudo-class is deprecated. Use :hover instead.

** (gedit:5347): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
```

So far I have not been able to find a fix for this after the last hour of searching and reading countless threads. Does anyone know what this means or how to fix it so everything is themed properly using the Paper-GTK theme?

I use a Ubuntu Gnome install on my laptop, came with GNOME 3.18, updated to 3.20, and I use the Paper-GTK theme on it without any issues, this is solely a Ubuntu Studio issue with GNOME 3.20 and I can't figure it out.

---

### Post by sudodus on 2016-07-31
It might be easier to get a system that works well for you, if you start by installing Ubuntu Gnome from its iso file, and after that install the application programs, that you want (video editing tools etc).

---

### Post by helios16v on 2016-07-31
That was my original plan as it has always worked out of the box for me, however when reading about distro's suited for general media editing, a lot of websites strongly suggested Ubuntu Studio as it comes with a lot more than just added software, there are additional drivers, libraries, packages, all of which I haven't looked into what I need and what I don't, which is why I felt this would be a fail safe as I can get everything at once and see what I need to keep in the future. At this point though, I'm kind of learning towards what you've suggested as I've been "setting up" this install for the last 4 hours, where as a fresh install of Ubuntu Gnome would take around 15-20 minutes and then just playing which drivers or libraries I need on the fly as I need them, it's more work in the long run but at least I know I'll have stability of everything working for the time being.

I'm going to wait this one out until tomorrow to see if anyone knows why I'm getting these warning messages as this is so far the last issue I've been having, if this is fixed, it's done and I can feel confident loading all 6tb of backed up footage on here to start editing with blender and lightworks

---

### Post by sudodus on 2016-07-31
Often you can ignore warning messages - as long as the software can do what you want it to do. For example, you can redirect gedit warnings to a log file or to "cyberspace's black hole", **/dev/null**.

```
gedit 2> ~/gedit.log
```

That way you get a clean terminal window, when you run the application program, that spams warnings. You can create an alias, so that it is enough with a short command to run it, for example

```
alias ged='gedit 2> ~/gedit.log'
```

If you store the alias in **~.bashrc** near the other aliases, it will be invoked automatically whenever a terminal window is started.

-o-

The easiest alternative is to get used to XFCE and run Ubuntu Studio as it is - after all, many people like it, are even enthusiastic about it. For example, I like the medium light XFCE, but my ageing computers want Lubuntu with the ultra light LXDE to play HD video well.

---

### Post by helios16v on 2016-07-31
> **sudodus said:**
> ```
gedit 2> ~/gedit.log
```
This got rid of the warning messages, however Terminal is still not themed

> **sudodus said:**
> The easiest alternative is to get used to XFCE and run Ubuntu Studio as it is - after all, many people like it, are even enthusiastic about it.
Don't get me wrong, XFCE is extremely resource friendly and I completely understand why Ubuntu Studio uses it so more system resources can be directed toward processing power, but I also can't get over how dated it looks, it just reminds me of a really old build of Ubuntu like 4.10, while it can be themed, the themes just aren't as in depth, they don't change enough to get that aesthetic I can easily achieve in GNOME3.

Another huge downfall for me is being able to just push the mouse to the top left corner and start typing to find all the programs that match, I use that more than anything and on XFCE I need to click, click search, and then start typing, while that doesn't sound like much, it extremely slows down productivity for me over time.

I've used many of these before as dailys on my laptop, always finding myself back at GNOME to fit my needs.

I've decided to try and make a list of all the codecs, libraries, packages, programs, what have you and try to implement that into Ubuntu GNOME for the day and see if that gets me to where I need to be easier than figuring out this theming issue

---

### Post by helios16v on 2016-07-31
I figured out a solution that works significantly better than what I was trying before, I installed Ubuntu GNOME again, and found the packages for Ubuntu Studio, I found a link that said for upgrading from Ubuntu to Ubuntu Studio, use

```
sudo apt-get update && sudo apt-get install [s]ubuntustudio-desktop[/s] ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

Obviously I didn't use ubuntustudio-desktop which allows me to keep the stock GNOME3 desktop of Ubuntu GNOME while adding everything from Ubuntu Studio.

Thanks for your help, and you suggestion to try and get this working with Ubuntu GNOME rather than trying to convert Ubuntu Studio to GNOME3, this was a LOT easier and only took about 45 minutes including making the USB and fresh install of Ubuntu GNOME

---

### Post by sudodus on 2016-08-01
Congratulations, and thanks for sharing your solution :KS

---

### Post by sudodus on 2016-08-01
Hi again helios16v,

I just started to think about the kernels. You may want the ***lowlatency*** kernel, which is often offered as an alternative, when installing Ubuntu Studio. See this link,

[UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

Maybe the lowlatency kernel came with the audio package, but I suggest that you check if you have it.

---


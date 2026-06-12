---
title: "LXAppearance - New GTK+ Theme Switcher"
date: 2008-03-28
forum: The Cafe
---

### Post by PCMan on 2008-03-28
LXAppearance - Feature-rich and desktop-independent GTK+ theme switcher.

Project page:[http://www.gnomefiles.org/app.php/LXAppearance](http://www.gnomefiles.org/app.php/LXAppearance)
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

Please see the screenshot. If you don't use gnome or xfce, this is a must-have for you.

[IMG]http://lxde.sourceforge.net/screenshots/lxappearance.png[/IMG]

With this handy tool, the users can:

1. Choose their favorite gtk+ theme
2. Choose their favorite icon theme
3. Install new icon theme
4. Choose their favorite font
5. Choose toolbar style

All changes done by the users can be seen immediately in the preview area. After clicking "Apply" button, the settings will be automatically written to gtkrc, and all existing programs will be asked to reload their themes.

LXAppearance is a new GTK+ theme switcher originally developed for project LXDE ([http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)), but it's totally desktop-independent and requires GTK+ only.

---

### Post by SunnyRabbiera on 2008-03-28
I have seen this around, seems interesting.

---

### Post by dashnak on 2008-03-29
I've installed it, since I'm using now lxpanel, pcmanfm, lxsession and openbox...
This doesn't really work, but looks promising...

---

### Post by PCMan on 2008-03-29
> **dashnak said:**
> I've installed it, since I'm using now lxpanel, pcmanfm, lxsession and openbox...
This doesn't really work, but looks promising...
Which part of this program doesn't work?
Run it from console and see if there is any error message, please.
It did work on my box.

---

### Post by chris4585 on 2008-03-29
it didnt work under gnome, but it worked under lxde session as far as i know

---

### Post by PCMan on 2008-03-29
> **chris4585 said:**
> it didnt work under gnome, but it worked under lxde session as far as i know
Then that means, it works well.
Gnome and XFCE use their Xsettings daemon, so GTK+ ignores gtkrc. Other desktop environments don't have settings daemon, so gtkrc is used. LXAppearance works like a charm under other desktop environments.

---

### Post by urukrama on 2008-03-29
It works fine on this computer, but I get the following error message in the terminal:

>  The program 'lxappearance' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 19549 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I've also written about this application on [my blog]("http://urukrama.wordpress.com/"). Thank you very much for this application. It is great.

---

### Post by spupy on 2008-03-29
Thank you! I am generally very skeptical about this kind of programs, because they often lack much needed options. This program has them - font selection and toolbar style.

---

### Post by dashnak on 2008-03-29
> **PCMan said:**
> Which part of this program doesn't work?
Run it from console and see if there is any error message, please.
It did work on my box.


Oops, sorry... I forgot to unload gnome-settings-daemon from my lxsession, I'm an idiot...
It works great!! Thanks!!

---

### Post by boomtisk on 2008-03-29
Is it possible to change the color of widgets and title bars with this like you can in more recent versions of GNOME? If yes, I might use this to replace the default Xubuntu GTK theme chooser.

---

### Post by webaake on 2008-04-04
Works great! Thx!

---

### Post by timjohn7 on 2008-04-04
I am a newb and have installed LXDE.  I now have PCMan under System Tools and GPicViewr under Graphics, but how do I change the Desktop to LXDE.  I saw that in another post you say Select it from gdm, but I don't know where that is or how to do it.

Also, since installing last night, I have lost my Home Network connection (wireless from my laptop to my Desktop PC; wireless from laptop to my router is still fine). Could PCMan or LXDE have affected these settings?  I've rebooted a couple of times, but no joy.

---

### Post by webaake on 2008-04-04
In order to start an LXDE session you have to logout (no reboot), then choose from menu LXDE as session. When logging in again you'll get the question if you want to use this permantely or not. Just try it temporarily and see how it works. You can later on make LXDE the default session.

Sry, can't help you with the wireless.

---

### Post by timjohn7 on 2008-04-04
I've logged out, but the system returns to the login screen as per normal... no option to select LXDE.  I also don't see any reference to LXDE in Startup Sessions or Current Sessions.  Is it perhaps not installed correctly?  In Synaptic, I have 4 LXDE modules installed.

---

### Post by dashnak on 2008-04-04
When I installed it, LXDE never showed up by default in the session selector, I had to follow this:
[http://www.gnomefiles.org/app.php/LXSession](http://www.gnomefiles.org/app.php/LXSession)

---

### Post by webaake on 2008-04-04
Yup, the above link should fix it!

Good luck!

---

### Post by herbster on 2008-04-04
How can one get this program to sort themes alphabetically? I really like it, it's much more complete than gtk-chtheme.

---

### Post by dustigroove on 2008-05-30
[FONT=Garamond][SIZE=2][COLOR=Black]Nice little program, it does its job well without fluff and fuss.

*[FONT=Arial Black][SIZE=1][COLOR=Red](EDIT - the below repo is outdated, please see the updated entries a couple of posts down.)[/COLOR][/SIZE][/FONT]*

Figured that I'd also note that they have a repo we can add:
```
deb http://people.linux.org.tw/~pcman/ubuntu/ ./
```Cheers,[/COLOR][/SIZE][/FONT]

---

### Post by eriqjaffe on 2008-05-30
> **dustigroove said:**
> [FONT=Garamond][SIZE=2][COLOR=Black]Nice little program, it does its job well without fluff and fuss.

Figured that I'd also note that they have a repo we can add:
```
deb http://people.linux.org.tw/~pcman/ubuntu/ ./
```Cheers,[/COLOR][/SIZE][/FONT]Heh.  I just posted in another thread...that repo is out of date.

[http://ubuntuforums.org/showthread.php?t=805334](http://ubuntuforums.org/showthread.php?t=805334)

---

### Post by dustigroove on 2008-05-30
Here's the updated repo info to save clicks...   :)

> **PCMan said:**
> Hi all, we have new apt repository for LXDE now.
There is no update in my personal apt repository for quite a long time because I don't have ubuntu anymore. Ubuntu 8.04 performed poorly on my laptop, and there are a lot of unresolved problems, so I removed ubuntu, and switched to ArchLinux recently.
Fortunately, we found another package maintainer - michael r < [EMAIL="michael.r@spamfreemail.de"]michael.r@spamfreemail.de[/EMAIL]>. He built up a new repo on Launpad PPA of LXDE for us.

For Ubuntu 8.04 hardy
```

deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```For Ubuntu 7.10 gutsy
```

deb http://ppa.launchpad.net/lxde/ubuntu gutsy main
deb-src http://ppa.launchpad.net/lxde/ubuntu gutsy main
```Just do this, and you'll get the latest LXDE (lightweight X11 desktop environment) for Hardy.
```
sudo apt-get update
sudo apt-get install lxde
```From now on, our official ubuntu repo will be moved to Launchpad PPA service.
Currently, i386, amd64, and lpa packages of the latest LXDE are provided for Hardy. Please upgrade now!!

Alternatively, you can use the repository provided by Ubuntulite project.
This is a lightweight branch of Ubuntu. They switched to LXDE in Ubuntulite 0.8 release.

Cheers!!

---

### Post by eriqjaffe on 2008-06-03
Alright, I'm having some troubles with lxappearance:

[[IMG]http://img88.imageshack.us/img88/9471/48zu4.th.png[/IMG]](http://img88.imageshack.us/my.php?image=48zu4.png)

No matter what I do, the fonts are huge and the theme is stuck on Clearlooks.  The really confusing thing is that I don't have lxappearance installed, yet it still runs:

```
eriq@eriq-desktop:~$ sudo apt-get remove lxappearance
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package lxappearance is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
eriq@eriq-desktop:~$ lxappearance &
[1] 20212
eriq@eriq-desktop:~$ 
(lxappearance:20212): Gtk-WARNING **: Unable to locate theme engine in module_path: "rezlooks",
```

I'm able to use gtk-chtheme without issue (which is how I got the aeterna theme working in the first place), but that's not as feature-packed as lxappearance...does anybody have any idea what's going on with this?

---

### Post by dustigroove on 2008-06-03
> **eriqjaffe said:**
> ... The really confusing thing is that I don't have lxappearance installed, yet it still runs ...

Try a reinstall of LXappearance and then purge it. If that doesn't work you may have to hunt down the files/folders that are getting left behind and prune them manually.

```
sudo apt-get install lxappearance

sudo apt-get remove --purge lxappearance
```Cheers,

---

### Post by Mark76 on 2008-06-23
I seem to be having the same problem with lxappearance. It was working fine and then it just stopped changing themes.

Incidentally, I can't do what Dustigroove suggested above as I installed it from a tarball.

---

### Post by eriqjaffe on 2008-06-24
> **dustigroove said:**
> Try a reinstall of LXappearance and then purge it. If that doesn't work you may have to hunt down the files/folders that are getting left behind and prune them manually.

```
sudo apt-get install lxappearance

sudo apt-get remove --purge lxappearance
```Cheers,Sorry, forgot to report back.

It didn't help, the behavior persisted.  I actually went ahead and transitioned from my Wubi install to a dedicated install from the ground up (although I transferred my /home directory to a new partition and kept it).  LXAppearance has worked fine on the new setup so far.

---

### Post by nami on 2008-11-02
How do I add more themes to LXAppearance or how do I remove themes from LXAppearance?

---

### Post by SomeGuyDude on 2008-11-02
> **nami said:**
> How do I add more themes to LXAppearance or how do I remove themes from LXAppearance?

Well you can either put the folder in /usr/share/themes or ~/.themes, or you can just have the .tar.gz somewhere and hit "install" in LXAppearance itself.

This thing's great, by the way, since it lets you preview things without starting/restarting X and unlike gtk-chtheme it doesn't pull my icon theme out of my .gtkrc file. Every time I switched through gtk-chtheme I had to open the damn rc file and put my icon theme back in there.

---

### Post by RiceMonster on 2008-11-02
Using this with openbox is perfect. I love it.

---

### Post by Mark76 on 2008-11-02
I like it too.

If it had a cursor theme changer option it'd be perfect. Especially as gcursor doesn't want to work for me

---

### Post by bzwl on 2009-06-29
After clicking "Apply" button, the settings will be automatically written to gtkrc,

which and where is the "gtkrc"?  I can't  find it

---

### Post by Mark76 on 2009-06-30
It's a hidden file in your home folder. Just click on View  on the menu bar and then on show hidden files

---

### Post by bzwl on 2009-06-30
> **Mark76 said:**
> It's a hidden file in your home folder. Just click on View  on the menu bar and then on show hidden files

Thx very much!
There is a ".gtkrc-2.0" in my home folder, but after clicking "Apply" button, the file doesn't change! 
Then I delete the ".gtkrc-2.0", and after clicking "Apply" button, there is no such file at all!
I remembered that this file was generated by "gtk-chtheme" (I installed it before), 
Is there any conflict between "gtk-chtheme" and "lxappearance"???

---

### Post by Mark76 on 2009-06-30
Uninstall gtk-chtheme.

You don't need them both

---

### Post by bzwl on 2009-06-30
yes, I uninstalled it, but there is a new problem.

when I choose the default gnome desktop, the ".gtkrc-2.0" can be  automatically generated and changed by "lxappearance", but the windows can't  reload the new theme after clicking "Apply" button.

when I choose the LXDE, the situation goes opposite, the windows can reload the new theme but the ".gtkrc-2.0" can not be generated or changed...

---

### Post by bzwl on 2009-07-01
HaHa, I find out the file!!!

It is ~/.config/lxde/config, it change automatically after switching a theme, it's the file I want!

I am so happy! Thanks Mark76 for replying! :p

---

### Post by Mark76 on 2009-07-01
Yes. I thought it might be either hidden in a subfolder or called something different. Or, in this case, both.

---

### Post by HandyAndy on 2009-11-26
I'm running Ubuntu 9.10 and Fluxbox 1.1.1. I can't get LXAppearance to change my icon theme. It lists my installed icon themes, but clicking on them does nothing. Previewing and changing themes works fine.
I've uninstalled gtk-chtheme, deleted gtkrc-2.0 and stopped the gnome-settings-daemon in case they were interfering with it in some way, but to no avail.
Any ideas?

---

### Post by Ernie S. on 2010-04-28
-deleted-

---


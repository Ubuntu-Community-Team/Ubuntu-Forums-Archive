---
title: "Terminal stopped working after upgrading to 22.04"
date: 2022-10-14
forum: Ubuntu/Debian BASED
---

### Post by mksundaram2 on 2022-10-14
Recently I upgraded to Ubuntu 22.04. after upgrading my terminal stopped working.
Terminal is installed and I can see it in my favourites also in application section, but when I try to open it shows on activities and then does nothing, I mean it fails to open the terminal.
In my application window this is what I got: a terminal app and below it this set of information: 
" Soyombo Terminal Mark-1 U+11AA1, []: Soyombo Terminal Mar... Soyombo Terminal Mark-1 U+11AA2, []: 
Soyombo Terminal Mar..." the square brackets is actually a square box. 
I couldn't figure out the reason and what does this mean. 
 I tried to open the terminal by right click and open in terminal and it opens. (any folder),  but fails to open directly by clicking the icon or via keyboard keys (ctrl+alt+T).

---

### Post by TheFu on 2022-10-14
I'll through out a few ideas .... 

There are lots of different terminal programs.  Try some others to see if the issue is with 1 program or the entire desktop.  I've been using xterm and xrvt for decades.  

Some programs may have lost support between releases, so those wouldn't make it into the next release.  

Also, create a new useraccount on the system, logout, then login using the new user account. Does the terminal program you want work or not?  This tests whether it is a system-wide or an individual user account issue.  Basically, incompatible settings between releases a usually the issue.

May check if Wayland or Xorg is being used.  Try the other display server, see if that helps.  If it were me, I'd do this testing with the new user account to avoid other config issues.

Lastly, I've made it a habit to see if there's a snap package issue involved.  Is the terminal being used shipped as a snap?  There have been really odd issues due to that.

---

### Post by mksundaram2 on 2022-10-15
Thanks for reply. 
I tried installing other terminal packages, tilda and xterm both runs smoothly(as of now). 
I also tried to open new user account and tried to login as you asked to, even in that case the terminal(original) failed to open.
Sorry, I don't know what Wayland or Xorg is as I am not proficient in computers. 
One thing which I want bring to notice is that the original terminal opens/runs when I open folder/file as open in terminal(right click and chose the option), but it fails to open when I tried from the desktop(right click and open in terminal) and also when directly launching from the applications.
Hopes that help to understand the issue.

---

### Post by vanadium on 2022-10-15
So your terminal can run. Also try starting it directly from e.g. tilda with the command "gnome-terminal". If it starts, you know it is not the terminal application. What remains is the desktop launcher, but I would be surprised that that is the culprit: you would need to change it to break it.

Try to run the launcher from the terminal:

```

gtk-launch org.gnome.Terminal

```
Does it run now?

Eventually post the contents of your default system launcher:

```

cat /usr/share/applications/org.gnome.Terminal.desktop 

```

---

### Post by TheFu on 2022-10-15
I'm guessing that during the upgrade, you allowed old programs that didn't have replacements to be retained?   That can happen when an program isn't supported any longer.  You could try installing the package again (or reinstalling it), but if my guess is correct, since the upgrade process didn't do that, it probably won't install.  The next choice is to find a PPA with the program for 22.04, set that up and install the package.

Xorg and Wayland are the display server options - everything that uses the mouse, keyboard or GUI uses them on all Unix/Linux desktops.  Xorg has been used for 40+ yrs, but in 17.xx, Canonical decided to try forcing Wayland onto us.  It wasn't ready back then and was quickly pulled as the default.  They tried again in 20.04.  Lots of people didn't have problems with it and have been using it since then. In 22.04, at initial release time, Wayland was the default display manager ... but within 2 weeks, it was found that Wayland and nvidia GPUs didn't work well together, so a fix was put into place to make it so Wayland was only default if AMD GPUs were used.  For nvidia, Xorg is still used.

X11 (aka Xorg) has always been network aware. Running commands over the network and using them locally on the same physical device both use the network stack. There's overhead and security considerations in doing that.  OTOH, it is very flexible.  This has worked well over 30 yrs.  I've been using these capabilities since the early 1990s as part of my daily use.  I'm using it right now.  

Wayland doesn't use the network by default. This was a key decision for a number of reasons, but mainly for security and performance.  At least that's the theory. They aren't dumb.  They knew people like me and all X/Windows programs (there are over 100K X/Windows programs), use expect the X API to be available and some crazy people like me would want to run programs on different machines, but have the user interface  'window' displayed locally.  For that Xwayland was created.  However, it isn't working perfect yet.

To an end-user, 99% of the time, Xorg or Wayland shouldn't matter. They should both work.  However, screen capture and desktop image capture tools were created for Xorg and don't work with Wayland, except 1-2 which were specifically coded just exactly the way Wayland requires.  Sadly, those tools aren't mature, crash, and don't have all the capture options that the Xorg options do.  Also, for test and desktop automation, Xorg allows inserting keyboard and mouse events into the event queue just like they were typed. The programs cannot tell the difference.  Wayland doesn't allow this, though we can send some events, not the full set.  This means testing tools all need to be rewritten to support whatever Wayland supports and other automation tasks don't work with it.  These 2 aspects break by workflows - captures and automation, so I specifically don't use Wayland and probably will not until Xorg is removed.  If history is any guide, it takes about 10 years from the first "stable" release before something non-trivial is actually production ready.  We've seen that with Pulse Audio, SystemD, and now we are seeing it with Wayland.  So, sometime in 2032 is when I expect Wayland to be ready for my use with all the needed support programs and other tools finally updated to use it.  

You can read more about both topics on Wikipedia.  They will do a better job than me.

Oh ... almost forgot.  I think in 22.04, both Wayland and Xorg are installed by default.  The way to toggle between them can only happen BEFORE login.  There is a 'gear' icon somewhere on the login screen. Click that and look for "XXXXXX on Xorg", where XXXXXX is your desired desktop environment. Pick that and see if it doesn't have the terminal you want working. Can't hurt too much.  If you have an nvidia GPU, it should already be the default, but it doesn't hurt to look.  The gear may not show up until some or part of the password for the userid is entered, but before "login" is selected.  I really don't know, as I don't login very often. I leave my systems running 24/7/365 and really only login directly on the hardware for 2 systems after a kernel update, which happens once every few weeks.  I'm doing my weekly patching now and see a new kernel, so later today, I'll reboot a number of machines, perhaps even this desktop.

---

### Post by mksundaram2 on 2022-10-15
sundaram@mks:~$ gtk-launch org.gnome.Terminal
sh: 1: exec: gnome-terminal: not found

[COLOR=#000000]contents of my default system launcher:[/COLOR]
Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;cmd;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=org.gnome.Terminal
Type=Application
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
StartupWMClass=Gnome-terminal
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity;
Actions=new-window;preferences;
X-Ubuntu-Gettext-Domain=gnome-terminal


[Desktop Action new-window]
Name=New Window
Exec=gnome-terminal --window


[Desktop Action preferences]
Name=Preferences
Exec=gnome-terminal --preferences

---

### Post by mksundaram2 on 2022-10-15
Thanks for the time spend on the topic and trying to explain me, truly appreciate the efforts taken by you, but frankly it would take time to sink in with the subject. 

Thanks again.

---

### Post by vanadium on 2022-10-16
You see that the program, gnome-terminal, is not found. Thus, it may not or incorrectly be installed, or the PATH variable may not be set correctly. Check the path with the command

Remove and reinstall Gnome Terminal:

```

sudo apt autoremove --purge gnome-terminal
sudo apt install gnome-terminal

```

Reboot. If it still does not launch, check your PATH:

```

printenv PATH

```

---

### Post by mksundaram2 on 2022-10-16
" [COLOR=#000000][FONT=&quot]sudo apt autoremove --purge gnome-terminal[/FONT][/COLOR]sudo apt install gnome-terminal"

Remove and reinstall "Gnome Terminal worked.
Now my terminal is launching.

Thanks for your time and patience. Truly appreciate. Thanks again.

---


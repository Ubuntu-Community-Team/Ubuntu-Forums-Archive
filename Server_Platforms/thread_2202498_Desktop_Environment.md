---
title: "Desktop Environment"
date: 2014-01-29
forum: Server Platforms
---

### Post by thault on 2014-01-29
I'm looking at installing a desktop to manage some software that's easier to work with via graphical interface. What GUI would you suggest for light use. Also I don't need the GUI all the time, just occasionally. How would I go about making sure the GUI only boots when I need it? Thanks.

---

### Post by Bashing-om on 2014-01-29
thault; Hi !

I follow that precept. I use xfce4 for that GUI .
Much depends on what your base install is. Do you now boot to a terminal ?

[INDENT][INDENT]simple is better
[/INDENT][/INDENT]

---

### Post by lykwydchykyn on 2014-01-30
LXDE is light but otherwise pretty complete.  If you just want something really light and barebones that will let you pull up the application, jwm, icewm, or openbox might be good choices.

If you don't install a display manager (e.g. lightdm, gdm, kdm, xdm), then you won't get the graphical login and the GUI won't start automatically.  You could start it as needed by logging in to the terminal and running "startx".

(to avoid installing a display manager, don't install any of the "desktop" metapackages, e.g. ubuntu-desktop, lubuntu-desktop, xubuntu-desktop, etc.  Just install xorg and whichever environment you want to use (lxde, xfce, jwm, etc)).

---

### Post by nerdtron on 2014-02-01
What do you need a GUI for?
Navigating between files and folder?

It would be a lot easier if you just use your desktop file manager, Nautilus, Dolphin, Thunar, etc. and use them to connect via the sftp protocol to your server. Added bonus is you can instantly drag files between your computer and server for easy copying.

---

### Post by thault on 2014-02-06
> **lykwydchykyn said:**
> LXDE is light but otherwise pretty complete.  If you just want something really light and barebones that will let you pull up the application, jwm, icewm, or openbox might be good choices.

If you don't install a display manager (e.g. lightdm, gdm, kdm, xdm), then you won't get the graphical login and the GUI won't start automatically.  You could start it as needed by logging in to the terminal and running "startx".

(to avoid installing a display manager, don't install any of the "desktop" metapackages, e.g. ubuntu-desktop, lubuntu-desktop, xubuntu-desktop, etc.  Just install xorg and whichever environment you want to use (lxde, xfce, jwm, etc)).

To use LXDE I had to download initx, now when I boot it boots into LXDE. I would prefer to have the server boot into terminal and only use lxde when i need to. How do i change this back?

---

### Post by Bashing-om on 2014-02-06
thault; Hey ,

One way would be to boot with the boot parameter "text" :
Make a back up copy of grub before editing.
Edit the grub file at /etc/default/grub with your favorite text editor and remove the terms "quiet splash" insert "text".

Save the file and;
Execute the terminal command
```

sudo update-grub

```

for the change to take effect.

[INDENT]though more than one path leads to an end
[/INDENT]

---

### Post by lykwydchykyn on 2014-02-07
> **thault said:**
> To use LXDE I had to download initx, now when I boot it boots into LXDE. I would prefer to have the server boot into terminal and only use lxde when i need to. How do i change this back?

Never heard of initx or had to install it.  Can you remove it?

EDIT: I just searched the repositories for "initx"; I don't find such a package.  Can you double check what it was you installed?

---

### Post by Bashing-om on 2014-02-07
thault; Hey ,

See lykwydchykyn's last:

In that respect, are you actually referring to something like ".xinitrc" ?
In my case (xfce4) :
> 
sysop@1310mini:~$ cat .xinitrc
#!/usr/bin/env bash
#started creation of this file 23may2013
#
#
echo "starting the X session, Billy" >&2
export XAUTHORITY=/home/sysop/.Xauthority
exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1
#end
sysop@1310mini:~$ 

Here I manually start my GUI. Be aware I am trouble shooting a niggly little intermittent startup issue -> echo, and export.
I manage my desktop manually and have no need of a DM. For my use case it workie great.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by thault on 2014-02-21
The program is xinit not initx. but No matter what I'm doing lxde is still booting.

---

### Post by 1clue on 2014-02-22
Back in the day, this was easy.  You edited /etc/inittab and there was a line that said what default runlevel to go.  5 was X, 3 was command line.

Actually, back when I got into this, no rational Linux nerd would start directly to X because XFree86 wasn't stable yet.

If you were doing it that way, you would set your default runlevel to 3 and then when you wanted x you would type **startx.**

Obviously I've been out of the loop for a bit. I need to figure out how boot/init works in Ubuntu.  And others.

---

### Post by lykwydchykyn on 2014-02-22
> **1clue said:**
> 
Obviously I've been out of the loop for a bit. I need to figure out how boot/init works in Ubuntu.  And others.

Well, it's about to change once again, so don't put too much effort into it.

---


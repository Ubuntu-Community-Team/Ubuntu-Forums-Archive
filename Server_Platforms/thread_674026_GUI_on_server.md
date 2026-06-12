---
title: "GUI on server"
date: 2008-01-21
forum: Server Platforms
---

### Post by InfoTech on 2008-01-21
I installed GUI on Ubuntu 7.10 server, hoping it will help me solve some installation issues easier. In the end, I managed to fix everything from CLI. But now, when I reboot server, it loads to GUI.

Is 

sudo apt-get remove ubuntu-desktop

sufficient to get rid of this thing?

Thanks.

---

### Post by commonplace on 2008-01-21
I think you can just remove gdm:

> sudo apt-get remove gdm

That will leave the GUI intact, but it will boot into the CLI instead of the GUI (then you could run 'startx' if you wanted to get into the GUI). But if you want to remove the whole GUI, then what you proposed should work, too.

I should note that I'm not 100% on this, though, so you may want to await confirmation. :)

/Kevin

---

### Post by gtdaqua on 2008-01-22
if u removed gdm or kdm - then effectively u r removing the gui. if u typed 'startx' there wont be any desktop manager to be loaded because u have removed kdm.

ubuntu-desktop will remove all native GNOME-based apps as well.

---

### Post by HermanAB on 2008-01-22
No, don't uninstall anything.

Just change the server run level to level 3:
[http://ubuntuforums.org/showthread.php?t=231335](http://ubuntuforums.org/showthread.php?t=231335)

Basically, you edit file /etc/inittab and set level 3 (No X, no graphics).

Cheers,

Herman

---

### Post by InfoTech on 2008-01-22
Thanks.

---

### Post by MJN on 2008-01-22
> **HermanAB said:**
> Basically, you edit file /etc/inittab and set level 3 (No X, no graphics).

Is this Gutsy-specific?

Certainly on Dapper (admittedly this could be a Kubuntu-ism) runlevels 2-5 are almost identical, and certainly all include starting a window manager.

Are you thinking of RedHat? Certainly my old install started X in 5, but not in 3 (which was otherwise identical).

Mathew

---

### Post by koenn on 2008-01-23
> **gtdaqua said:**
> if u removed gdm or kdm - then effectively u r removing the gui. if u typed 'startx' there wont be any desktop manager to be loaded because u have removed kdm.

ubuntu-desktop will remove all native GNOME-based apps as well.
this is wrong, and commonplace was right
```

n@knix:~$ sudo apt-get -s remove gdm
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  gdm ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv ubuntu-desktop [0.120]
Remv gdm [2.14.10-0ubuntu1.1]

n@knix:~$ sudo apt-get -s remove ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv ubuntu-desktop [0.120]
n@knix:~$
```

gdm only manages GUI log-in, removing it means you'll log in at a command prompt, and run 'startx' to start X (+ window manager / desktop environment)
removing ubuntu-desktop is no problem, because it's an empty package, it only exists of dependencies and recommends. 
as long as you don't force removal of dependencies (with autoremove or through aptitude, i think, never done it), it's save to remove.

---


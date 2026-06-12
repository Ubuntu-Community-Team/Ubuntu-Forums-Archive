---
title: "System Monitor issues"
date: 2018-03-20
forum: Ubuntu Development Version
---

### Post by exploder on 2018-03-20
System Monitor no longer works from the shortcuts I have in Activities or the one I placed in the launcher. The command "gnome-system-monitor" will launch it and it will work as expected. There is one more thing though, the version I launch from the command line is 3.28.0. If I run the command "snap list" version 3.26.0 displays in the list. Synaptic shows 3.28.0 installed. I am seeing this on two machines with fully updated installs.

---

### Post by corradoventu on 2018-03-20
I have the same problem but also the command "gnome-system-monitor" has unespected result:
 ```
corrado@corrado-p13-bb-0319:~$ snap list
Name                  Version    Rev   Tracking  Developer     Notes
core                  16-2.31.2  4206  stable    canonical     core
gimp                  2.8.22     30    stable    snapcrafters  -
gnome-3-26-1604       3.26.0     53    stable/&#8230;  canonical     -
gnome-calculator      3.26.0     75    stable/&#8230;  canonical     -
gnome-characters      3.26.2     50    stable/&#8230;  canonical     -
gnome-logs            3.26.2     23    stable/&#8230;  canonical     -
gnome-system-monitor  3.26.0     31    stable/&#8230;  canonical     -
corrado@corrado-p13-bb-0319:~$ gnome-system-monitor
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)
corrado@corrado-p13-bb-0319:~$ 
```
same with gnome-calculator:```
corrado@corrado-p13-bb-0319:~$ gnome-calculator 
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-calculator:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)

``` and I have Gnome 3.28.0  why should install gnome-3-26-1604?```
corrado@corrado-p13-bb-0319:~$ inxi -S
System:    Host: corrado-p13-bb-0319 Kernel: 4.15.0-12-generic x86_64 bits: 64
           Desktop: Gnome 3.28.0 Distro: Ubuntu Bionic Beaver (development branch)
corrado@corrado-p13-bb-0319:~$ 

```
I opened a problem on: [https://forum.snapcraft.io/t/gnome-calculator-problem/4579](https://forum.snapcraft.io/t/gnome-calculator-problem/4579)
I opened also a bug: [https://bugs.launchpad.net/ubuntu/+source/0ad/+bug/1757073](https://bugs.launchpad.net/ubuntu/+source/0ad/+bug/1757073)

---

### Post by corradoventu on 2018-03-20
[https://forum.snapcraft.io/t/gnome-calculator-problem/4579](https://forum.snapcraft.io/t/gnome-calculator-problem/4579) says
snapd 2.32+18.04~pre5 is known to be broken, an update is being prepared (it should be available later today).

---

### Post by exploder on 2018-03-20
corradoventu, thank you!

---

### Post by kerry_s on 2018-03-20
did you run the commands?

snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

same goes for calculator, follow the instructions it says right there in terminal.

---

### Post by exploder on 2018-03-20
The output says the snaps are already installed.

---

### Post by kerry_s on 2018-03-20
run the second command:
 snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

---

### Post by exploder on 2018-03-21
System Monitor now launches but it launches the 3.26.0 version. If I launch from the terminal version 3.28.0 comes up. I am not sure why I would need two different versions pf the same thing? Seems more like a mistake to me.

---

### Post by kerry_s on 2018-03-21
yeah, i don't have version 3.28.0 on my system.
i installed from a daily about 4 days ago.

maybe just purge version 3.28.0

it's most likely other apps will change as well, since they decided to use snaps in place of regular apps.

---

### Post by exploder on 2018-03-21
I took your advice and removed the 3.28.0 version, now everything works right again. Even starting system monitor from the terminal now brings up the same version the shortcuts do. Thanks!

---

### Post by exploder on 2018-03-21
kerry_s, you hit the nail on the head! Everything listed using the "snap list' command except for gnome-calculator had a 2.26.0 version and a 2.28.0 version. Removing the ones that were regulr packages seems to have taken care of everything.

Edit: On my other machine I had to run "snap refresh" to get all the snap apps working.

---

### Post by corradoventu on 2018-03-21
problem solved with last uodates```
corrado@corrado-p13-bb-0319:~$ snap version
snap    2.32+18.04~pre6
snapd   2.32+18.04~pre6
series  16
ubuntu  18.04
kernel  4.15.0-12-generic
corrado@corrado-p13-bb-0319:~$ 


```

---


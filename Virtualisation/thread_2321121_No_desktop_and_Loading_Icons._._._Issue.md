---
title: "No desktop and Loading Icons. . . Issue"
date: 2016-04-20
forum: Virtualisation
---

### Post by tom229 on 2016-04-20
I've recently installed Ubuntu 15.10 onto a virtual machine, however after logging in there is no icons or anything on the desktop, just the cursor and the background. I have looked online however am unable to find a working solution.
I thought I found one here:

[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

However after running this command "[COLOR=#111111][FONT=Consolas]DISPLAY=:0 ccsm"
[/FONT][/COLOR]The console becomes stuck on saying "Loading icons. . ." The actual machine itself is not frozen, it's just that it will spend hours on that without changing.

The system specifications are:
2gb of RAM
12MB of VRAM
8GB of Storage

The host's specifications are:
16GB of RAM
2GB of VRAM
500GB of Storage


This shows that it is not an issue with the host, and should not be an issue with the virtual machine itself.

Any suggestions would be greatly appreciated.

---

### Post by DuckHook on 2016-04-21
**Moved**

You will have a better chance for a response in the virtualisation forum.

---

### Post by DuckHook on 2016-04-21
Welcome to the forums tom229:> **tom229 said:**
> The system specifications are:
2gb of RAM
12MB of VRAM
8GB of Storage
...This shows that it...should not be an issue with the virtual machine itself......not necessarily true. 12MB of VRAM is simply not sufficient to run Ubuntu. At all. You need minimum 128 MB. You can actually push it up to 256 MB, but this must be done manually:```
vboxmanage modifyvm name_of_VM --vram 256
```Replace "name_of_VM" with the name of your virtual machine. Also make sure guest additions is installed.

---

### Post by MAFoElffen on 2016-04-21
Which virtualization host software did you install into? Which version? 

If it was VirtualBox, do you have the optional Oracle Extentsion pack installed for that version?

---

### Post by DuckHook on 2016-04-21
> **MAFoElffen said:**
> Which virtualization host software did you install into?My bad. Should not jump to the conclusion that it is vbox. Naughty :redface:

It was getting late...

---


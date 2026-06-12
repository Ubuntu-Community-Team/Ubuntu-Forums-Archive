---
title: "PLEASE help me through this all sorts of errors"
date: 2008-04-02
forum: Windows
---

### Post by rolledthatho on 2008-04-02
Hey all, here was my problem, i got a computer with a load of viruses (on windows) i didnt have a windows disc, so my friend gave me a copy of this linux ubuntu and i loaded it on there.  its horrible on this comp. i now have a windows disc and want to load it, but here is my problem:

my keyboard is usb and it dosent light up and cut on until AFTER my chance to "hit any key to boot from disc" so i got a old school style keyboard, wired with the old plug in, and apparently my plug jack is all messed up, 5 keyboards later i need to try a diff route, case closed i cannot re-start and boot from disc by pressing a button. 

now for problem 2 when i load the disc, click on the icon and try to run the "setup"  on the desktop, i get this archive manager crap everytime it looks like this

[IMG]http://i32.photobucket.com/albums/d45/rolledthatho1/Screenshot.png[/IMG]

people have directed me to run a terminal but even that fails, can someone possibly guide me through this, its about to drive me insane

thanks in advance.

---

### Post by kesman on 2008-04-02
So what disk are you trying to load there? Also, install the updates that it's asking you to install, they are usually quite important for stuff to work. It's the red start next to GAIM-trayicon there.

---

### Post by rolledthatho on 2008-04-02
its a windows xp disc.  also thats another problem ive tried that too, heres what i get. 

[IMG]http://i32.photobucket.com/albums/d45/rolledthatho1/Screenshot-1.png[/IMG]

im in the process of running that terminal and trying again. brb



and of course... heres what i get

brittdodia@brittdodia-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  sun-java6-bin sun-java6-jre
0 upgraded, 0 newly installed, 2 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 14.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
105578 files and directories currently installed.)
Removing sun-java6-jre ...
Removing sun-java6-bin ...
brittdodia@brittdodia-desktop:~$

after it came back to that at the end, i tried again to run updates and its doing the same thing

---

### Post by kesman on 2008-04-02
Have you tried to open synaptic package manager from system -> administration  as it asks you to? Also consider running the given command in terminal.

---

### Post by kesman on 2008-04-02
In any case, you won't benefit anything trying to run windows install cd in ubuntu. You can't really do anything with it.

---

### Post by kesman on 2008-04-02
Run these in terminal to repair your software sources:

```

sudo apt-get update
sudo apt-get install -f

```

---

### Post by rolledthatho on 2008-04-02
i dont really know anything about ubuntu, im in syn package manager, but i dont really know where to go from here.

so as long as ubuntu is on my comp the only way i can put windows on here is to "press any key to boot from disk" at startup up??

thanks for your help btw

ok i ran both of those, i guess that is lettting me update "downloading package files now"

then what?

---

### Post by kesman on 2008-04-02
Yeah, you can't install windows from ubuntu, the only way is to boot from the windows disk. What you could do, is to download the latest ubuntu version, 7.10 or upgrade to it from your update manager, and start using it instead.
Also, have you tried to connect your usb keyboard to your pc with an usb -> ps/2 adapter? Usually there's always one with an usb-keyboard just in case the user doesn't have any usb ports.

---

### Post by rolledthatho on 2008-04-02
damn well thats discouraging. ive already got the disk, as for the adapter thing, i do have this adapter that my usb plugs into, that the other end plugs into the old style keyboard port on the back on the tower. is that what your talking about? i think its something to do with that plug in

---

### Post by kesman on 2008-04-02
Yeah that's the adapter I'm talking about it. Can you use it to connect your usb-keyboard to the old-school keyboard port?

---

### Post by rolledthatho on 2008-04-02
ive tried, i think there is something wrong with the port back there its self, do they ever come lose or un soldered or whatever they are

sorry im pc illiterate

---

### Post by Ptero-4 on 2008-04-02
Your problem is that the PS2 card (or chipset) is fubar. If that's your issue then I guess that you'll need to stick to ubuntu until you can get ahold of a new PS2 card (or a new motherboard if it's a chipset in your current one).
In the end ubuntu can't be that bad.

---


---
title: "VMware Player installation help"
date: 2009-10-18
forum: Virtualisation
---

### Post by Rhetoric Camel on 2009-10-18
Alright I've looked all over to instructions on how to install VMware Player in Ubuntu. I'm not having any luck with it at all. I'm using Ubuntu 9.04 and VMware-Player-2.5.3-185404.i386.bundle

I've found instructions on how to install it from this page [http://johnsonyip.com/wordpress/2009/07/05/installing-vmware-player-with-bundle-installation-files-in-terminal-command-prompt-for-ubuntu-9-04-and-starting-a-virtual-machine/](http://johnsonyip.com/wordpress/2009/07/05/installing-vmware-player-with-bundle-installation-files-in-terminal-command-prompt-for-ubuntu-9-04-and-starting-a-virtual-machine/)
I just can't get anywhere with it though.

I did:
```
sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel
```
and everything installed except the devel but it seems that's what happened to the person who did the instructions.

I then do this:
```
gksudo bash ./VMware-Player-2.5.2-156735.i386.bundle
```
and I get this message:
```
bash: ./VMware-Player-2.5.3-185404.i386.bundle: No such file or directory
```

The file is on the desktop. I also right clicked it went to properties and made it executable. I heard that it must be in the /usr directory, so I moved it there and tried it with the same issue. I also tried typing ```
gksudo bash ./home/rhetoriccamel/Desktop/VMware-Player-2.5.3-185404.i386.bundle
and I tried
gksudo bash ./usr/VMware-Player-2.5.3-185404.i386.bundle
```

and keep getting the same error message.

Anyone know whats going on? I can't get this to install for the life of me. I even tried just double clicking on VMware-Player-2.5.3-185404.i386.bundle on the desktop and run in terminal and the terminal pops up for a quarter of a second and disappears.

---

### Post by mikewhatever on 2009-10-18
Try right clicking the file, select 'Open with other application...', then select 'Use custom command' at the bottom, and type in 'gksudo bash'.

---

### Post by Rhetoric Camel on 2009-10-18
thank you very much that got it up and running. Now the hard part. Figuring out how to use my EXISTING Windows XP in the Virtual Machine. I don't have a windows disk or anything like that. I bought this computer from Dell and they sent me a recovery cd but not an installation cd.

---

### Post by mikewhatever on 2009-10-18
You can't do that with VMplayer. In fact, I am not quite sure there is a free visualization product that lets you use existing installations. I remember having read VMwork station may have that feature, but it's a rather expensive commercial product.

---

### Post by kevinrogers1977 on 2009-10-18
I have sucessfully installed vmplayer on ubuntu 9.04

1. download the .rpm for linux

2. from terminal, apt-get install alien

3 cd Desktop (navagate to you desktop or wherever you downloaded the .rpm)

4 sudo alien --scripts (name of rpm.rpm)

5 . double click on .deb packedge alien created
 you done hope this works

tip: to use any .iso on vmplayer download a blank.vmx and attached the iso to it.
:P:P:P :Pope this helps

---


---
title: "ssh protocal works, but where do i go from there? (windows -&gt; linux networking)"
date: 2006-02-27
forum: Server Platforms
---

### Post by Mangelo on 2006-02-27
im using ubuntu (debian..kernel 2.6.xxx i forget exact numbers). and im setting up a server for a windows based lan (w/ an ubuntu box as the fserver).   can connect via putty, and ssh, but how do i configure the windows domain controllers (is that what i need to fix?) in order to have windows recognize it as a network drive.

i followed [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) to the letter, and it still isnt working..i ultimatly want to set it up so all i have to do is either go to my computer, or network places (in windows) and i can browse into my  /home/shares/allusers without using a third party protocal like ssh (i actually found winsc3p which works perfect for what i want to do...browse the directory of my linux box and transfer files in and out...now i just want to do it without the third party protocal of the winsc3p...

btw: the only thing i INTENTIONALLY skipped in the howto was setting up quota's, cause i want everyone on the lan (my immediate family and each member's respective computer, all windowsxp based) to have full access to the HD w/o limited storage space...

any help would be greatly appreciated!! a point in the right direction...which document i should be looking at..or man pages..or anything... i dont really know much of the networking protocal, but i think the fact that ssh works means i'm one step away from realizing my hopes and dreams...i just dont know where to proceed from here.


worse comes to worse i know i can use winsc3p to fulfill my needs...but then my the rest of my computer illiterate family wouldnt really be able to make use of the file server, they want the ease and convenience of simply "browse to the h: drive"

any thanks is greatly appreciated!

---

### Post by Glut on 2006-02-28
Once you've finished the setup that you've linked to, you should have a nice little samba server. All you should need to do is map the h: drive to \\*servername*\allusers. What happens when you try to connect to the smb share (by exploring to \\*servername*\allusers)?

---


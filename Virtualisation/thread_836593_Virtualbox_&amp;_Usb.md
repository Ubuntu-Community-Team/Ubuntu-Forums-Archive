---
title: "Virtualbox &amp; Usb"
date: 2008-06-21
forum: Virtualisation
---

### Post by kdm on 2008-06-21
Hi,

Has anyone succeeded in getting USB to work in Virtualbox under Hardy Heron ?
I have read lots of different forums and it seems unclear whether this actually works !
I am running XP Pro in VB  - All for 2 main reasons...
1)  Itunes - Yes, I hate it too, but nothing else seems to manage my Ipod CLASSIC successfully.
2)  Lexmark 4530 - I understand that wireless is too much to hope for in Ubuntu - but I would settle for USB standard printing !
So will it eventually work - Or am I wasting my time ???
Thanks

---

### Post by maybeway36 on 2008-06-21
Are you installing VirtualBox from virtualbox.org (the Sun version?) Only that one has USB.

---

### Post by kdm on 2008-06-21
Yip,
I installed the version from...
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by Ev1L on 2008-06-21
for me it partially work.
i followed a guide saying to uncomment some lines of a file (somethingmount.sh, sorry but i can't remember right now).
so the support to usb is activated.
then you go to the settings of the VM and enable usb and add to the list the devices that you want to be recognized by the guest OS.
not much more to say, something works, most of the rest not :)

---

### Post by kdm on 2008-06-22
Oops !

Bit of a rookie mistake this one !
I just needed to add the devices rather than creating new filters !!

So for the benefit of any other newbies out there – this is what you do...

Press and hold the button where the highlighted dot is in the attached screencap and your devices will appear !
Its as simple as that !

---

### Post by bodhi.zazen on 2008-06-22
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help [INDENT]... and users looking for solutions.[/INDENT][]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")
[uwiki]UnansweredPostsTeam/SolvedThreads[/uwiki]

---


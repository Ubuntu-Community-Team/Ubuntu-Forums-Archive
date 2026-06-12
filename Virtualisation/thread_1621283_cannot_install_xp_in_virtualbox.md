---
title: "cannot install xp in virtualbox"
date: 2010-11-14
forum: Virtualisation
---

### Post by aghora on 2010-11-14
[SIZE=4]i want to run windows xp in ubuntu .i tried with virtualbox.
i  installed new virtual xp machine.
when i treid to install ,it is showing like this[/SIZE]
**"Fatal: no bootable medium found! System Halted"**

[SIZE=4]how to resolve it?[/SIZE]

---

### Post by mosaic2s on 2010-11-14
What are the steps that you went thru on the ubuntu? Pl give more details like - 
which ubuntu, which virtualbox you have loaded. then what settings you gave to virtual machine in terms of hard disk space, ram, video ram etc.
and did you actually install windows xp using the CD rom?

---

### Post by aghora on 2010-11-14
[SIZE=3]i use ubuntu 10.04LTS version,i installed oracle vm virtualbox 3.2.10,for xp virtual machine i gave 512 gb of ram,15 gb of harddisk space,and then i pressed the start button to install,it gave that fatal error[/SIZE]

---

### Post by mosaic2s on 2010-11-14
at that point, you will have to keep a bootable CD in the CD rom. And define boot order  in the settings as CD, hard disk in that order.

---

### Post by aghora on 2010-11-14
i inserted xp cd before pressing start,still it is showing same error.
may be boot order is wrong,once i will check,
but i selected it to boot from cd rom.
thanks for your suggestion :)

---

### Post by aghora on 2010-11-14
i gave 512 mb of ram that is a mistake,i wrote gb instead of mb

---

### Post by mozkill on 2010-11-16
You need to get a hold of a different image/iso  of your XP install cd and mount that one instead.  I bet it would work.

---


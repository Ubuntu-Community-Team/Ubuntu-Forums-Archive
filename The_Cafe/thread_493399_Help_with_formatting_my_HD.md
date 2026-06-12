---
title: "Help with formatting my HD"
date: 2007-07-05
forum: The Cafe
---

### Post by blakcode on 2007-07-05
Hello everyone I am new here. I have recently downloaded Ubuntu and I think it's awesome. But thats not really what I am here to talk about.

Atm I am using Windows Vista (because I am more comfortable with it and I don't know how to use the Linux partition tool) and I want to know somthing about partitioning my drives. 

Well when I installed Ubuntu I Just shrunk my C: drive.. well now my C drive is allmost out of space and I want to use my D: (data drive (it all came preinstalled on my ASUS A7F notebook)) and make it smaller and put some of that free space onto my C: drive and even install a new OS (I was thinking about trying Solaris).

My problem is that when I shrunk my C: I got black unallocated space (wich is what I want), my D: drive is for some reason in a green box call (extended partition). When shrink it I don't get black unalocated space, I get green free space.. this is not really what I am after. 

So can you guys shed some light on this for me? It will probably help me understand how things work better too. 

Thanks,
**ßÎâ&#269;&#1220; &#986;&#1147;Ð&#441;**

---

### Post by FoolsGold_MKII on 2007-07-05
A hard drive had two types of partitions - primary and logical.

There's a limit to how many primary partitions a drive can have, but no real limit to logical partitions. A common way to order a drive (like you've got) is to have a primary partition and a logical partition.

However, to create a logical partition you have to create what's known as an "Extended" partition, which isn't really a partition as such but simply a **container** to hold individual logical partiitons. The extended partition doesn't actually define partitions, it's just a holding area for logicals.

So, when you shrunk the D drive (which is a logical partition), you increased the amount of available space in the exdended partition container. To use this space, right click in the green box and create a new logical partition to fill up the remaning green area.

---

### Post by blakcode on 2007-07-05
Ok thanks :) is there a way to be able to take some of my D drive space though and add it to my C drive?

---

### Post by blakcode on 2007-07-05
Oh and while I am here I might add.. I am getting a GRUB error 17 *sigh* I hope there is a way to fix this without reinstalling Ubuntu cus I just got it awesome looking :D

Could you please help me! I only just started getting it.

---

### Post by init1 on 2007-07-05
> **blakcode said:**
> Oh and while I am here I might add.. I am getting a GRUB error 17 *sigh* I hope there is a way to fix this without reinstalling Ubuntu cus I just got it awesome looking :D

Could you please help me! I only just started getting it.
You need to reinstall grub
```
grub-install /dev/yourdevicehere
```

---


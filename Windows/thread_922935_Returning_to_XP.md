---
title: "Returning to XP"
date: 2008-09-17
forum: Windows
---

### Post by Solais on 2008-09-17
I installed Ubuntu only, but my dad needs xp cause he is a lil slow at learning, so I guess I have to install xp again but it wont detect my hard drive, its a SATA Hard Drive, and my xp cd cant recognize the hard drive idk why, what can I do? :(

---

### Post by tuxxy on 2008-09-17
It may not be recognizing it as I think you would need to install the SATA drivers for your mobo

---

### Post by Solais on 2008-09-17
> **tuxxy said:**
> It may not be recognizing it as I think you would need to install the SATA drivers for your mobo

mobo? oh and my cousin told me that about installing drivers but idk how lol:confused:

---

### Post by tuxxy on 2008-09-17
Sorry, mobo is a motherboard, the SATA driver does not come in the Windows XP installation, you need to add it yourself.

Heres a guide for you, to [install XP to SATA drive]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml")

---

### Post by Solais on 2008-09-17
thank you ever so much ^^, now i have to wait till the weekend so i can borrow my friends portable hard drive, i have 98gb on stuff :popcorn:

---

### Post by nickgaydos on 2008-09-17
I'm not entirely sure, but I think you can slip-stream the drvers using nLite.

---

### Post by lazyart on 2008-09-17
or pull your data off, set the sata controller into compatibility mode via setup and install without needing drivers.

---

### Post by crispy_420 on 2008-09-17
Simple answer: drivers on floppy drive and use when prompted during initial load (F8 to load third party drivers?)

---

### Post by Solais on 2008-09-17
> **nickgaydos said:**
> I'm not entirely sure, but I think you can slip-stream the drvers using nLite.

Heard of this before, but not 100% sure on how it goes.

---

### Post by Solais on 2008-09-17
> **crispy_420 said:**
> Simple answer: drivers on floppy drive and use when prompted during initial load (F8 to load third party drivers?)

My computer those not have a floppy drive :???:

---

### Post by jaqie on 2008-09-17
Cross-posting is a no-no.

[http://ubuntuforums.org/showthread.php?t=921938](http://ubuntuforums.org/showthread.php?t=921938)

---

### Post by Solais on 2008-09-17
I'm reading the info tuxxy gave me.I'll have to print this too, heard so many ways on doing this yet still have to wait for my cousin's portable hard drive :lolflag:

---

### Post by Solais on 2008-09-17
> **jaqie said:**
> Cross-posting is a no-no.

[http://ubuntuforums.org/showthread.php?t=921938](http://ubuntuforums.org/showthread.php?t=921938)

Hey lol, thanks for the link, I forgot to bookmark that yesterday, fell alseep after posting it :lolflag:, ty :)

---

### Post by College_Trained on 2008-09-17
Is it the XP cd that's not recognizing the hard drive?
I know that Windows doesn't recognize the Linux EXT3 file system.

---

### Post by aimpau on 2008-09-18
Make sure your BIOS is set to boot FIRST from the CD. Don't run Linux and run the XP-CD using wine.

---

### Post by wenuswilson on 2008-09-18
> **College_Trained said:**
> Is it the XP cd that's not recognizing the hard drive?
I know that Windows doesn't recognize the Linux EXT3 file system.

I had this problem a while back --I gave up so no help. BUT Windows won't find ext3's this is true AND gparted (with something in Synaptic allowing ntfs part's to be created) it doesn't find those either. 

Nothing important, just my two cents over the things I've tried and failed.

---

### Post by Louis de Broglie on 2008-09-18
I think the problem is XP does not recognize ext3 drive. But it does recognize SATA drives. Because it did for my case . I have 160GB SATA hdd. And it just works .:) But you will need service pack 2 for it. Maybe you are trying only XP( without any service pack ) try SP2 .

---


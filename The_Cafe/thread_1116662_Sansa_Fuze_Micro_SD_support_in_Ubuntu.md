---
title: "Sansa Fuze Micro SD support in Ubuntu"
date: 2009-04-05
forum: The Cafe
---

### Post by casbahdk on 2009-04-05
I just purchased a Sansa Fuze 8GB with radio. I have already run out of room and need to get a Micro SD for the Fuze. Does the Micro SD mount as a separate hard disk when the Fuze is connected to a Linux box? I understand that the Fuze supports Micro SD cards up to 16 GB. Does this size work with Ubuntu?

Cheers

---

### Post by Mr_Bumpy on 2009-05-30
I'm not sure about the max size you can use, but the Micro SD card will show up as a separate device if you use the Fuze in MSC mode.

---

### Post by mamamia88 on 2009-05-31
my brother has one and i'm pretty sure it does.  if you are worried you can always get a card reader for cheap and use that to add music

---

### Post by SomeGuyDude on 2009-05-31
I'm 99% sure all micro-SD cards come with an adapter that turns it into a full-size card, so if your laptop has the slot you can just throw it in there for purposes of putting music on 'er.

---

### Post by casbahdk on 2009-05-31
Cheers. Unfortunately my IBM/Lenovo laptop doesn't seem to have one.

---

### Post by The Toxic Mite on 2009-05-31
> **casbahdk said:**
> Cheers. Unfortunately my IBM/Lenovo laptop doesn't seem to have one.

You can get card readers from electronics retailers, you know. ;)

---

### Post by gnomeuser on 2009-05-31
Set the Fuze in mtp mode and when you plug it in Banshee will merge the two volumes when it represents the device, thus I now have a 16gb Fuze device (8 + 8). However there is a bug where the device doesn't reserve enough space on the internal partition for generation of the database (filed naturally).

---

### Post by casbahdk on 2009-06-02
Thanks for all of the advice.

---

### Post by rossmoore on 2009-06-24
Hey - have you got your Sansa fuze working with banshee in mtp mode properly? I'm in Jaunty and have had real issues getting this working smoothly and quickly, and have now reverted to MSC mode.
Incidentally, isn't it annoying that banshee syncs the whole music database, not a user-defined list of playlists... or am I missing a trick?

---

### Post by Mr_Bumpy on 2009-06-24
MTP mode has been shaky for me as well using a Sansa Fuse with Amarok 2 on Kubuntu 9.04.  MSC mode works great, though, and for my collection, having my own folder structure actually works better, so I'll probably keep it this way.

---

### Post by rossmoore on 2009-06-25
Glad I'm not alone with the shaky MTP support. I didn't think Amarok 2 had MTP support built in yet, just Amarok 1.4?

Playlist syncing on linux seems to be a real issue not properly tackled by any of the major music players.

---

### Post by starcannon on 2009-06-25
> **casbahdk said:**
> I just purchased a Sansa Fuze 8GB with radio. I have already run out of room and need to get a Micro SD for the Fuze. Does the Micro SD mount as a separate hard disk when the Fuze is connected to a Linux box? I understand that the Fuze supports Micro SD cards up to 16 GB. Does this size work with Ubuntu?

Cheers

I mount microSD cards using a microSD to SD converter and popping the thing into a regular old usb SD card reader on a regular basis. You should have no problem.

---

### Post by rossmoore on 2009-06-25
I can confirm that if you put the micro SD card into the Sansa, and plug the Sansa into you machine then, in MSC mode, Ubuntu (and Macs and Windows) will recognise two memory cards - one the size of your Fuze, one the size of the micro SD card.

If you connect your Fuze in MTP mode it will be recognised as one big space (although MTP mode doesn't seem to be quite fully functional in Linux at the moment).

There shouldn't be any problem with recognising a 16Gb card, although I haven't tried one that big yet.

---

### Post by Mr_Bumpy on 2009-06-25
I'm using Amarok 2.1 (along with KDE 4.3 beta2), so it looks like they've added MTP support.

---


---
title: "Wanna pass to Edgy...but difficult back up"
date: 2007-01-02
forum: The Cafe
---

### Post by Gargamella on 2007-01-02
I wanna pass to edgy (already burned the edgy install cd),but i have about 10 GB of songs and 5GB of movies...

How would you back up this ? On dvds?

---

### Post by Lord Illidan on 2007-01-02
yep.

---

### Post by jethro10 on 2007-01-02
> **Gargamella said:**
> I wanna pass to edgy (already burned the edgy install cd),but i have about 10 GB of songs and 5GB of movies...

How would you back up this ? On dvds?

Do you mean on windows or Ubuntu?

both to DVD certainly, and easily.
I have a USB hard disk for my backing up as well.

J

---

### Post by Rhubarb on 2007-01-02
If you've got a spare 20GB on your hard drive and you're currently running Ubuntu Dapper, you could do a :-
```
sudo apt-get install gparted
```
Shrink your current partition, create a new partition (say 20GB for your music and video), mount the new partition, then copy your documents, music and video to the new partition.
When you go to install Edgy, open up gparted on the live cd and delete your old ubuntu partition, your old swap file partition, everything but the 20GB partition you created for your documents.
Then in the Edgy installer, tell it to install into the empty space on your hard drive.

That should be it, you may have to re-mount your 20GB partition in Edgy, I'm not sure.

Certainly if you've got access to another (usb) hard drive / Blank DVDs and you're a bit un-confident about all of what I've said above, do it the "easy" way and use a USB drive / burn to DVDs.

---

### Post by Gargamella on 2007-01-02
> **jethro10 said:**
> Do you mean on windows or Ubuntu?

both to DVD certainly, and easily.
I have a USB hard disk for my backing up as well.

J

I am in Dapper

and I have a Usb HD 60GB

but it is now almost full

---

### Post by insane_alien on 2007-01-02
y'know what, i think this is a good chance to treat yourself to a new harddrive. or an external one, they come in really handy every now and again.

---

### Post by maniacmusician on 2007-01-02
yeah. SATA drives totally rock in terms of performance. get one of those, you'll never go back to IDE!

---


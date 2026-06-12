---
title: "GParted or Palimpsest"
date: 2010-01-10
forum: The Cafe
---

### Post by ubudog on 2010-01-10
Which is better in your opinion?

---

### Post by blueshiftoverwatch on 2010-01-10
I've never even heard of Palimpsest. It doesn't even have it's own Wikipedia page.

---

### Post by gsmanners on 2010-01-10
It would probably help if it was referred to by its more well-known name: Gnome's "Disk Utility".

[http://library.gnome.org/users/palimpsest/stable/index-info.html.en](http://library.gnome.org/users/palimpsest/stable/index-info.html.en)

---

### Post by Old Marcus on 2010-01-10
I tried to use it and found I couldn't resize or move partitions (i was attempting to resize my windows partition), and on the whole, found it very basic. I feel that playing around with partitions is a very techy thing in the first place, so at least give them the tools and keep gparted.

---

### Post by gnomeuser on 2010-01-10
The two aren't really comparable.

GParted is intended for partition creation and deletion primarily. It's a standalone application with no decernable design for allowing data exposing or logic functionality embedding. In other words it is an impenetrable functionality fortress which isn't very useful on a desktop.

Palimpsest on the other hand presents a set of APIs and widgets that can be used to embed or call useful functionality in the desktop. E.g. how you can add partition formatting or checking in nautilus. Additionally it acts as an early warning system monitoring your devices' supported services such as SMART and emit a warning message if you harddrive is at risk of failure. Aside the utterly silly name udev-disks and palimpsest present an open and easy to use agora of functionality and exposes relevant information to the desktop in meaningful ways that serve the user.

Which is best? All that GParted does is a mere subset of what Palimpsest offers, at that it offers it in a manner that isn't helpful to evolving the desktop nor takes advantage of current technology to ensure data stability. 

GParted could be implemented using udev-disks/Palimpset. Easily. With a nicer UI.

Progress thine name is udev-disks.

---

### Post by k64 on 2010-01-10
It would be much more interesting to see them as they are ported to GNOME 3. Oh, and it sucks to see GNOME 3 delayed to September.

---

### Post by BrokenKingpin on 2010-01-11
GParted here. Disk Utility does have its uses though.

---

### Post by Psumi on 2010-01-11
Neither, because I don't use GNOME anymore.

---

### Post by gnomeuser on 2010-01-11
> **Psumi said:**
> Neither, because I don't use GNOME anymore.

Then udev-disks is definitely for you, given it's design you could easily write an application using your toolkit of choice for maximum consistency of the experience or embed the desired functionality in your existing application bank.

---

### Post by joehosch on 2010-01-11
Palimpsest doesn't work well on smaller Screens. I have a screen with 1024*768 and P has no scollbar, so I can't see the bottom of the window.

---

### Post by Paqman on 2010-01-11
Both. Gparted is good for managing partitions, Palilpsest/Disk Utility is good for monitoring disk health through SMART.

---

### Post by gradinaruvasile on 2010-01-11
I found Palimpsest quite useful - it presents an easy to understand image of the devices on the system, allows for some basic partition setup. But i found that it doesnt do the partitioning job right every time. But for the other functions i quite like it. Also, its predecessor (pysdm or "Storage Device Manager) was quite useful too on mounting partitions that werent in fstab.

Gparted on the other hand scares me - some times it wasnt able to do its work - partitioning. Couldnt finish operations etc. I lost my faith in it.

So i learned fdisk for partitioning.

---

### Post by ubudog on 2010-01-11
> **Paqman said:**
> Both. Gparted is good for managing partitions, Palilpsest/Disk Utility is good for monitoring disk health through SMART.

I agree.  GParted is great for managing partitions.

---

### Post by Dark Aspect on 2010-01-11
GParted

GParted is probably on my top ten most favorite pieces of software although cfdisk has its uses.

---

### Post by yurx cherio on 2010-03-22
I have been using GParted for a while until I had to manage software RAID. GParted failed even to detect all RAIDs, it could only find the 1st one out of 3.

Palimpsest on the other hand detects all 3 and provides very easy way to manage disks. It looks like the tool is evolving quickly. I haven't tried it /w LVM but I wouldn't be surprised if it could handle LVM as well.

I still use GParted sometimes to do simple partitioning though now my focus has shifted to Palimpsest as a primary disk management tool.

---

### Post by ratcheer on 2010-03-22
GParted - I can't even say "Palimpsest". ;) But, really, I use GParted all the time.

Tim

---

### Post by Psumi on 2010-03-22
> **gnomeuser said:**
> Then udev-disks is definitely for you, given it's design you could easily write an application using your toolkit of choice for maximum consistency of the experience or embed the desired functionality in your existing application bank.

Too bad I don't code, nor know how. Nor do I want to know how.

---

### Post by koleoptero on 2010-03-22
> **ratcheer said:**
> ....I use GParted all the time.

Your hard drives must hate you. :lolflag:

---

### Post by ratcheer on 2010-03-22
> **Paqman said:**
> Both. Gparted is good for managing partitions, Palilpsest/Disk Utility is good for monitoring disk health through SMART.

Very true.

Tim

---

### Post by ratcheer on 2010-03-22
> **koleoptero said:**
> Your hard drives must hate you. :lolflag:

Probably. I am a tester and I have to reinstall Lucid at least once per week.

Tim

---


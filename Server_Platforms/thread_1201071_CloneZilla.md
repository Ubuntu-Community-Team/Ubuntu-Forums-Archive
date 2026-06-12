---
title: "CloneZilla"
date: 2009-06-30
forum: Server Platforms
---

### Post by sickdude on 2009-06-30
Howdy folks,

Ok i just read a article on lifehacker where they discussed CloneZilla.

Which perfectly fits my needs. Well at least i think. I own 2 Mac's, a Macbook pro and a Imac, on which i use Time machine to back up. This works perfect. On my new Macbook pro i restored from a back up i made of my Imac to restore settings/preferences etc. 

Now i want something similar to Time machine and i think that CloneZilla will work for me.

**So my question is,** are there people around here that back up their servers using CloneZilla? If yes, does it work like i would expect it to work? And is there a nice guide for Ubuntu servers that i could follow?

Is this maybe something for the Ubuntu team to use on both desktops and servers in the future as a equivalent to Apple's Time machine? Ubuntu is all about user friendlyness and this might improve that a whole bunch, since i really love the Time machine feature on my Mac's.

PS.
I searched around the forum for a thread that had clonezilla in the comments but most of them die after the "Use clonezilla!" comment, unfortunately.

---

### Post by Boondoklife on 2009-07-03
I personally love clonezilla and have a network boot setup going.
I have a WesternDigital NAS that I have tftp installed on that makes the PXE version of clonezilla available. From there I just boot the pc/laptop/whatever with a wired connection and then backup or restore from the network booted clonezilla app. I have it saving to the samba share the is available on the NAS which is a 750GB Mirror Raid.

---

### Post by Aearenda on 2009-07-03
Clonezilla is great for taking disk image backups - and they are given date-based names by default. But unless it has progressed a long way since I last looked, I don't think it is a Time Machine equivalent.

---

### Post by Boondoklife on 2009-07-04
Well I personaly just use a script to have it create backups with custom names but hey =). As mentioned though, it is a great PXE option so no need for a live cd etc. Just plug in the network and off you go. And how can ya beat replacing a hard drive and then siply plugging in and restoring the pc, No looking for a cd or boot disk or usb stick etc.

---

### Post by windependence on 2009-07-04
Most likely Clonezilla won't work for your Macs. Macs are funny animals, you can't even clone them using dd for some reason. The only thing that works for me on Macs is SuperDuper or Carbon Copy Cloner.

-Tim

---

### Post by Boondoklife on 2009-07-04
Well acording to the clonezilla site it does work with macs, but I would like to know if someone has tested it [LINK]("http://clonezilla.org/")

---

### Post by sherl0k on 2009-07-04
I used the experimental builds (which are based off of the Ubuntu kernel) to clone servers that use the ext4 partition. If Ubuntu can read HFS+ partitions (not sure if it can or not) You can use the built-in partclone utility in Clonezilla to create some pretty small compressed images. I was able to fit Clonezilla-live and an pre-configured Ubuntu install on a 4 gig USB drive, not sure how big OSX would be.

If all else fails, Clonezilla can DD any drive no matter the filesystem, and then compress it. You may end up with a hefty file size though.

---

### Post by windependence on 2009-07-05
Heh, I thought the same thing, been using dd for years but it will NOT clone a mac drive for me. I have never heard of anyone using Clonezilla to do it either.

I did forget to mention that the built in Disk Utility in OS X will clone for you just fine also.

-Tim

---

### Post by sickdude on 2009-07-06
Well as i said i am not looking for something to make back ups from my Mac but a Ubuntu server.

I work at a ISP in the Netherlands and im checking this as a back up option for important servers, like nameservers, mailservers and all that good stuff.

And of course my own Ubuntu server, which is web, mysql etc. but it would be awesome to make a full back up every month, in case a hdd fails.

CloneZilla isnt in the apt repository i guess, is this because of its experimental state?

---

### Post by Boondoklife on 2009-07-06
> **sickdude said:**
> Well as i said i am not looking for something to make back ups from my Mac but a Ubuntu server.

I work at a ISP in the Netherlands and im checking this as a back up option for important servers, like nameservers, mailservers and all that good stuff.

And of course my own Ubuntu server, which is web, mysql etc. but it would be awesome to make a full back up every month, in case a hdd fails.

CloneZilla isnt in the apt repository i guess, is this because of its experimental state?

Well I would think it is not in there because it is not an app so to say, you have to boot it so you can get full access to the HD without anything changing. There are usb/cd/pxe bootable versions on the site.

---


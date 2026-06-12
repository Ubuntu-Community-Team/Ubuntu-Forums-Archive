---
title: "Samba Server Help"
date: 2006-12-01
forum: Server Platforms
---

### Post by madmorpheus on 2006-12-01
Hi all

I upgraded from Mandiva to Edgy LAMP Server.  I share my music using the Samba server configured on my Edgy server.

here's the funny thing:

I can view open and play anything and everything from my Windows XP laptop clients.  No Problems at all

But, I can't open music or video directly from my samba share on my Edgy laptop.  I can do everything else, open docs, images, other files directly from the share when I mount on my Edgy laptop, but when I try to play any music or video I get this:

"Totem could not play 'smb://hollywood;morpheus@145.1.1.2/public/Music/ - 13 - GROOVY.mp3'.
could not read from resource"

This happens for Realplayer, Rhythmbox or Mplayer

Any help on this issue would be greatly appreciated.
I was able to do this before with my old Mandriva server.

---

### Post by Beernut on 2006-12-02
You need to mount the samba share in order for the music to play for some reason.  Have a look at this thread I was experiencing the same issue along with many other people.

[http://www.ubuntuforums.org/showthread.php?t=273206&highlight=samba+rythmbox]("http://www.ubuntuforums.org/showthread.php?t=273206&highlight=samba+rythmbox")

In addition to this script you can automatically mount the share by editing your fstab file.  Unfortunately I can't help you with this yet all the example I have tried so far from the forums have not worked but I know it is probably something I am doing wrong.

---


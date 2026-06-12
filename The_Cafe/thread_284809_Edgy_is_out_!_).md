---
title: "Edgy is out ! :)"
date: 2006-10-26
forum: The Cafe
---

### Post by ubuntu_demon on 2006-10-26
Edgy is out! :)
[https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)
[http://fridge.ubuntu.com/node/611](http://fridge.ubuntu.com/node/611)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by slimdog360 on 2006-10-26
Finally, Ive been checking it all day.

---

### Post by Bezmotivnik on 2006-10-26
Torrents?

Download is bogging down already.  Nearly all the sites 404 on the .iso....

---

### Post by miceagol on 2006-10-26
This is great. :D I see some good upgrades there. I like the upgrade to the splash, and the rounded corners on the windows looks really neat.

I'll upgrade this weekend, but I'm not looking forward to the problems with ndiswrapper. It got messed up last time I did an upgrade of Ubuntu.

---

### Post by slimdog360 on 2006-10-26
Mines going max, but Im downloading the server install form a Western Australia Server. Probably about 4 people using it.

---

### Post by detgar on 2006-10-26
> **Bezmotivnik said:**
> Torrents?

Download is bogging down already.  Nearly all the sites 404 on the .iso....

Here's the release anouncement [https://wiki.ubuntu.com/EdgyAnnouncement](https://wiki.ubuntu.com/EdgyAnnouncement)
it contains links to torrents and files.

---

### Post by PriceChild on 2006-10-26
/me has been running edgy a couple of months already ;)
 
He he i love the madness of everyone wanting it the first day :)

---

### Post by Bezmotivnik on 2006-10-26
> **PriceChild said:**
> 
He he i love the madness of everyone wanting it the first day :)
Chalk it up to my touching and childlike faith that all the bugs will be out of it before they *release* it. ;)

---

### Post by wishyjr on 2006-10-26
aw, now i have to rebuild my system again! :( 

..before i do, can anyone confirm that there have been any improvments to 'dist-upgrading'? I find that every time i try it it really breaks my system. thanks.

---

### Post by beerfan on 2006-10-26
> **wishyjr said:**
> ..before i do, can anyone confirm that there have been any improvments to 'dist-upgrading'? I find that every time i try it it really breaks my system. thanks.

I too would like to know if upgrading is smooth or if a reinstall is recommended. Are there any upgraders that can comment?

---

### Post by raublekick on 2006-10-26
the best part of waking up is a new ubuntu release in your cup!

so glad i don't have any classes today. 

downloading via bittorrent, but for some reason i never get good speed in bittorrent anymore :(  uploading at 80-90KB/s but only downloading at 20-30KB/s

---

### Post by raublekick on 2006-10-26
> **beerfan said:**
> I too would like to know if upgrading is smooth or if a reinstall is recommended. Are there any upgraders that can comment?

I can't really say either way as I've never done it that way before. I do plan on testing it out today but I am gonna do a fresh install afterwards anyways. 

I can offer this though: [http://jaraub.good-evil.net/jaraub/scripts/mybackup.py](http://jaraub.good-evil.net/jaraub/scripts/mybackup.py)

It's a quick-'n'-dirty backup script I wrote that will backup all of your home directory. xorg.conf, fstab, blacklist, and your sources.list. If you have an external storage device to store it on, this is a good solution when it comes time to reinstall, because you can just untar it right back into your home. Create a folder called "backups" in your home directory.

Use the following flags:

-x makes a dated backup of your xorg.conf and sends a copy to your home dir

-f makes a copy of your fstab to your home

-b copies blacklist to your home (i need this because i have to blacklist my internal audio stuff)

-s backs up sources to your home

-h backs up everything in your home except the following ~/backups, ~/mp3, ~/ISOs, ~/.Trash, ~/.local/share/Trash  if you need other folders excluded you can easily add them in the source file.

So basically just run the following to enable full capabilities:
```
python mybackup.py -x -f -b -s -h
```

It will also prompt for your password because it needs sudo for anything outside of home.

beware though, the source is preeeeetty sloppy :)

---

### Post by DoctorMO on 2006-10-26
oooh I'll need new alt-covers and disk printable materials

---

### Post by d3v1ant_0n3 on 2006-10-26
I was one of the excitable people who booted up my comp first thing this morning and ran updates to upgrade to edgy final. Got nothing. Read a little. Realized I've already GOT edgy final since my last round of updates yesterday.:D 

Me wants Feisty!!! NOW!

---

### Post by nami on 2006-10-26
is it easier to get compiz\xgl working on 6.10?

---

### Post by tseliot on 2006-10-26
> **nami said:**
> is it easier to get compiz\xgl working on 6.10?
you can use AIGLX which is included in the xserver by default

---

### Post by LaserJock on 2006-10-26
update-manager is the recommended way to upgrade to edgy instead of apt-get dist-upgrade. I've done it a few time already for 6.10 and it works pretty well. No real problems. I just had to run it a couple time to make sure everything got upgraded and removed properly.

AIGLX is enabled by default in 6.10. You just need to install compiz or beryl and change a couple settings in Xorg.conf . It literally took me about 1 min. to get to a wobbly windowed state ;-)

-LaserJock

---

### Post by hoagie on 2006-10-26
> **LaserJock said:**
> update-manager is the recommended way to upgrade to edgy instead of apt-get dist-upgrade. I've done it a few time already for 6.10 and it works pretty well. No real problems. I just had to run it a couple time to make sure everything got upgraded and removed properly.

AIGLX is enabled by default in 6.10. You just need to install compiz or beryl and change a couple settings in Xorg.conf . It literally took me about 1 min. to get to a wobbly windowed state ;-)

-LaserJock

Like what kind of settings?

---

### Post by d3v1ant_0n3 on 2006-10-26
I think personally I had to add 3 entries to my Xorg.conf. One of which should have probably been there the whole time anyway.

---


---
title: "Finally found a use for all that memory"
date: 2010-06-16
forum: The Cafe
---

### Post by eriktheblu on 2010-06-16
So last night I decide to import my work Outlook e-mail archive into Evolution.

[IMG]http://i29.photobucket.com/albums/c292/eriktheblu/screenies/Screenshot-archivepstProperties.png[/IMG]

Yes, it's a 7.3 GB email archive. I wasn't really thinking about it, and it spans 5 years of email.

Couple hours into it, I decide to leave it running and go to bed.

This morning I wake to find this

[IMG]http://i29.photobucket.com/albums/c292/eriktheblu/screenies/Screenshot-SystemMonitor.png[/IMG]

The culprit (in case anyone hadn't guessed)

[IMG]http://i29.photobucket.com/albums/c292/eriktheblu/screenies/Screenshot-SystemMonitor-1.png[/IMG]

After restarting Evolution, it is of course now behaving and only eating 56.8 MB.

Pretty pointless thread, but thought I'd share.

---

### Post by Sealbhach on 2010-06-16
You have a big swap partition. 5.7GB :shock:
.

---

### Post by eriktheblu on 2010-06-16
The swap space is unintentional. I wanted a 2G partition on each HDD, but it rounded up. I don't need the space (I actually have deliberately unformatted sections) so I haven't bothered with it.

---

### Post by Bucky Ball on 2010-06-16
Why a swap on each hdd? Are you running two installs of OS?

---

### Post by Barrucadu on 2010-06-16
If both are mounted with the same priority, Linux can swap to the two devices simultaneously, effectively doubling the (write) speed.

---


---
title: "Frustration (Rant)"
date: 2008-07-16
forum: The Cafe
---

### Post by Dragonbite on 2008-07-16
Don't you hate it when you are working on a presentation for a couple of weeks (days actually) and the computer you have the files in decides to crap-the-bed?

I have a Linux Special Interest Group meeting tonight and the subject I am going to cover is Digital Photography. I was going to go over F-Spot and digiKam for sorting, editing  and organizing pictures before moving on to using Gimp and possibly Krita.

I have my notes, as well as selected pictures on the hard drive. This morning I tried to boot it up quickly so I could copy the notes (OpenOffice.org writer, saved as a MS Word doc file) and go over them during lunch at work.

So I booted it up, put in the encryption passphrase and took a shower.

The HAL daemon is dying. It gets stuck on that.  The hard drive "clicks" make a rhytmic 4-5 clicks and the repeats... over and over and over...!

Normally it would be "LiveCD to the rescue!" except that the hard drive is encrypted so  I *should* not be able to get the files off of it (otherwise the encryption is worth nothing)!

Luckily I have other avenues for the meeting, just without notes and hoping the pictures are available on my USB (otherwise I'll have to find the link to the Flickr album I got them from and download them again).

It always seems to happen at the last minute! Argh!

(looks like I'll be taking Fedora 9 off this hard drive and replace it with something else. Experiment done.)

---

### Post by Rhubarb on 2008-07-16
A hard drive that makes regular clicks is not a healthy hard drive.
There's a chance the heads may be stuck, in which case percussive maintenance may help.

If you haven't already, it may be a good time to review your backup procedures / habits.

I hope at the least your presentation goes well :D

---

### Post by fiddledd on 2008-07-16
> **Rhubarb said:**
> (...)

If you haven't already, it may be a good time to review your backup procedures / habits.

(...)

I was actually going to post something similar, but thought better of it. I figured now wasn't the time. :)

Incidentally, I'm almost paranoid about Backup, I have at least 4 copies of everything. I use USB Sticks and spare HDDs for backup.

---

### Post by Dragonbite on 2008-07-16
Thanks.. I'll try "percussive maintenance" on it. ;)

Luckily this laptop hard drive is or was supposed to be exclusively for the computer club demonstrations so most of the files I have on it came from the server I'm still trying to set up.

Ideally, when the server is up and running, I'm going to keep a directory or something of the files for this laptop and synch them up so if anything like this happens my files are elsewhere plus when I'm at the desktop I can also get to the files.

The only reason for trying Fedora in the first place is because it includes full-disk encryption and somebody in the club wants to explore encryption on Linux. Otherwise I would go with a more stable distro.

---

### Post by gn2 on 2008-07-16
Unless there's a need for encryption, you dont need encryption. \\:D/

---

### Post by HermanAB on 2008-07-16
On a laptop, encryption is a must.  Laptops gets stolen/lost in which case encryption is the only thing between you and a whole lot of banking blues.

---

### Post by x0as on 2008-07-16
> **Dragonbite said:**
> 
Normally it would be "LiveCD to the rescue!" except that the hard drive is encrypted so  I *should* not be able to get the files off of it (otherwise the encryption is worth nothing)!


You know the passphrase though, if you're using LUKS you can boot of a recovery livecd & mount the encrypted partition easily.

---

### Post by Foster Grant on 2008-07-16
A clicking hard drive is a hard drive that needs to be replaced.

Encryption is a *must* only if you leave your laptop unattended a lot, in which case there are ways to secure it using a cable lock, or if you have a lot of confidential/classified data, in which case you should *not* be leaving your laptop unattended because the federal Fan Belt Inspectors (or your nation's equivalent) are known to disapprove of that sort of thing. ;)

(If you are married and have a largish pr0n collection, encryption *may* be necessary in that instance as well. :lol: )

---

### Post by Dragonbite on 2008-07-16
> **x0as said:**
> You know the passphrase though, if you're using LUKS you can boot of a recovery livecd & mount the encrypted partition easily.
How would I go about this?

I believe Fedora 9 uses LUKS, but where do I have to get the recovery livecd (from Fedora, or does LUKS provide one)?

This would be a perfect exercise for the next meeting where I was going to work with Encryption for that person who is interested!

---

### Post by x0as on 2008-07-16
SystemRescueCd has everything you need if Fedora is using LUKS.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If the partition you want to mount is /dev/sda2, from the livecd

```
cryptsetup luksOpen /dev/sda2 encfs
mount /dev/mapper/encfs /mnt/whatever
```

Copy what ever you want somewhere else, then

```
umount /mnt/whatever
cryptsetup luksClose /dev/mapper/encfs
```

encfs can be whatever you want to call it.

---

### Post by Barrucadu on 2008-07-16
And that is why I don't use encryption. If I have some files that MUST be encrypted, I either encrypt the file with GPG (such as my passwords file), or tar them and encrypt that with GPG (such as my collection of scanned bank statements).
Then, nobody can read the files without having a copy of my secret key, and the password, which of course only I know, is not written down anywhere, and is fairly long.

---

### Post by Dragonbite on 2008-07-16
> **x0as said:**
> SystemRescueCd has everything you need if Fedora is using LUKS.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If the partition you want to mount is /dev/sda2, from the livecd

```
cryptsetup luksOpen /dev/sda2 encfs
mount /dev/mapper/encfs /mnt/whatever
```

Copy what ever you want somewhere else, then

```
umount /mnt/whatever
cryptsetup luksClose /dev/mapper/encfs
```

encfs can be whatever you want to call it.
This opens up a whole possibility for the next meeting, to demonstrate how you cannot get to the encrypted hard drive with a regular live CD (like Ubuntu) and then how you can get to the drive with the right tools!

I think I'm going to leave it as-is and see about incorporating it with next month's meeting.

Since the hard drive is older (from a Pentium I w/MMX laptop era, now in a Pentium M @ 1.4GHz ) it may not be able to calibrate itself from the temperature fluctuations (warmer when it was last on, cooler this morning when I tried). A co-worker mentioned this so I'll have to see if it works when I get home (and is presumably warmer than it was this morning).

Doesn't help with looking over my notes during lunch, but at least it may work.

---

### Post by madjr on 2008-07-16
the approach of 1 encrypted "**private**" folder is the best approach for Ibex, no one needs to encrytp all their mp3, pr0ns or a simple presentation (like in your case)

the clicking sound means that you have **turn off** the computer **forcedly** by pressing the power button without shutting it off or reseting it lots of time over it's lifetime.

it could die at any moment.

---

### Post by Dragonbite on 2008-07-16
> **madjr said:**
> the approach of 1 encrypted "**private**" folder is the best approach for Ibex, no one needs to encrytp all their mp3, pr0ns or a simple presentation (like in your case)

the clicking sound means that you have **turn off** the computer **forcedly** by pressing the power button without shutting it off or reseting it lots of time over it's lifetime.

it could die at any moment.
I don't know how good the original owner was to it, but it has locked up a number of times on me since installing Fedora (the other distro's have been MUCH better than Fedora).

---

### Post by NxZDr on 2008-07-16
what happened to long and cryptic passwords at login?

---

### Post by madjr on 2008-07-16
> **Dragonbite said:**
> I don't know how good the original owner was to it, but it has locked up a number of times on me since installing Fedora (the other distro's have been MUCH better than Fedora).

yea 2 of my disks died after they started doing that (western digitals)

anyway you could still use it **for a while**, as a external disk in one of those external thingies and keep unimportant stuff on it.

**Do not install another OS in that disk**, so go and purchase a new HDD ASAP

---


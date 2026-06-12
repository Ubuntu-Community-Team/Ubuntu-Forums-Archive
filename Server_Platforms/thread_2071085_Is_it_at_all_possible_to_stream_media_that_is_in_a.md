---
title: "Is it at all possible to stream media that is in another OS? Aka in /media/[USER]/OS?"
date: 2012-10-14
forum: Server Platforms
---

### Post by duodecillian on 2012-10-14
I'd like not to have to copy/paste all of my movies into my Ubuntu partition to get streaming to work, however in any streaming client with a web interface (Mediatomb, squeezebox) It doesn't list it. Or in the case of MiniDLNA (What I am using) it tells me "permission denied".

---

### Post by darkod on 2012-10-14
Is the other OS windows or linux?

If it's windows usually you should be able to read it, but even in this case it's far from recommended since windows doesn't want other OSs to touch its system partition. If we are talking about media in your default user folder in windows, that means it's the system partition.

If it's linux and they are in the default location, the Home folder of a user, it will probably refuse access to other users.

Fow media you want to use cross platforms the usual would be to save them in specific shared location, not in any Home (Users) folder. That should give it easy access from other OSs and machines.

---

### Post by duodecillian on 2012-10-14
The other OS is Windows 7, I wasn't aware that there was even such a thing as a shared location.

You said that it should be able to read it, but here is the error message I receive when trying.

 minidlna.c:474: error: Media directory "/media/duodecillian/OS/Users/Ed/Videos/Movies" not accessible! [Permission denied]

---

### Post by darkod on 2012-10-14
And what if you try to open the location yourself manually from Nautilus?

And are you mounting this win7 partition (location) in /etc/fstab or not?

---

### Post by duodecillian on 2012-10-14
Opening the location via nautilus is fine.

I also just edited fstab to automount the OS, unfortunately I still got the same error.

---

### Post by darkod on 2012-10-14
If opening in nautilus is fine, that means minidlna is trying to access in some different way (user). But I don't know details how minidlna works.

---


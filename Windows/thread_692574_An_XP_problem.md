---
title: "An XP problem"
date: 2008-02-09
forum: Windows
---

### Post by jtsemrah on 2008-02-09
Hello, I am a long time reader, first time poster. I have a little problem with Window$ XP. Don't ask me why I came here, I guess I just exhausted all other resources. So please don't yell at me about asking for Window$ help on a Linux forum.

Anyway, I was needing more space in my XP partition so I popped in a GParted LiveCD. I shrank my Ubuntu partition and grew my XP partition, figuring that this would probably be fine. The process took about 36 minutes, and when it was done I booted into XP.

Here's where the problems start. It boots to the point just before the welcome screen, where the cursor and logo appear. Then it just hangs. The cursor can move, but it doesn't load any further. First I tried booting into safe mode, but the same thing happened there. So I popped in my XP disk and ran CHKDSK. No help there.

I tried the check function in GParted. It started trying to grow the filesystem to fill the volume, but then errored and said it couldn't continue because of something with not shutting down Window$ properly. This is a problem, because I *can't* shut down Window$ properly. If I push the power button after I try to boot up it doesn't do anything.

There are a lot of people on Google Groups with similar problems, all after doing something with their partitions. I'm not sure where to go from here, and want to avoid reinstalling XP, though that may be my only choice at the moment. Any help is appreciated.

Thanks,
jtsemrah

---

### Post by PmDematagoda on 2008-02-09
Moved to the Windows Discussions section.

---

### Post by mrsudo on 2008-03-05
betcha xp is toast!
still beats vista anyday though!

---

### Post by LaRoza on 2008-03-05
Does Ubuntu load?

Does GRUB show everything correctly?

---

### Post by rickyjones on 2008-03-05
Did you defragment the drive from Windows before expanding the partition? If not then your best bet is that several required files are now corrupted. Easiest fix would be a repair installation of Windows.

-Richard

---

### Post by sgt.splatters on 2008-03-08
For the record, the idea of running GParted over an active partition terrifies me. Especially when one OS is Winbl0ws...

---


---
title: "64 bit and add on programs"
date: 2008-02-11
forum: System76 Support
---

### Post by richieboy on 2008-02-11
hi.  i read here that system76 is now using the 64 bit version of ubuntu.  can i still run 32 bit programs under a 64 bit os?  programs like streamtuner, nethack, tomenet, scid chess database, jose chess are very important to me and i dont wan't to lose them.
thanks, 
rich

ps:  i am still very much a noob.

---

### Post by thomasaaron on 2008-02-12
I see nethack and scid in the repos. I don't see the rest of them there.
Did you download all of them from the repositories or are some from a 3rd party repo somewhere?

---

### Post by Vadi on 2008-02-12
Yeah, you can - I run 32bit games just fine.

---

### Post by greg_g on 2008-02-12
FYI: 
1)It looks like streamtuner is in the 32bit Gutsy Universe repo

2)There is no "tomenet" but there is a "tome" a "single-player, text-based, dungeon simulation game." in gutsy 32bit Multiverse repo.

3)I couldn't find anything with the word "jose" in the title using packages.ubuntu.com

For packages already in Ubuntu (#1 and 2) it should be as simple as requesting a rebuild (filing a bug against the package in Launchpad with the words "Please package 64bit version").  That is of course assuming that all of the required depencies of the programs are already compiled for 64bit.

Richieboy, if you didn't understand that last sentence, no worries.  It just means that it may take a while for them to provide a 64bit version of some programs.

Hope that helps,

greg

---

### Post by greg_g on 2008-02-12
> **Vadi said:**
> Yeah, you can - I run 32bit games just fine.

Well, there is your answer I guess.

Wouldn't hurt to have them rebuilt for 64bit systems though (if that is possible).

---

### Post by Vadi on 2008-02-12
I don't think there's a difference between a 32 and a 64 bit app unless the 64bit one actually makes threads to utilize both cores. Because even programs that I installed that were packages for 64bit were using only half of each core (I got two) in intensive task.

While that does leave the two other halves of the cores to their own things, it would be better if they actually used both of them!

(on that note, I really love "make -j 2" now)

---

### Post by richieboy on 2008-02-12
thanks for all the answers, everyone.  i didn't know that i could request 64 bit builds.  jose chess and tomenet are third party programs so i'll have to research them some more.  i really appreciate the help.  as soon as my refund is direct deposited i'll be on the phone ordering my laptop.

thanks,
rich

---


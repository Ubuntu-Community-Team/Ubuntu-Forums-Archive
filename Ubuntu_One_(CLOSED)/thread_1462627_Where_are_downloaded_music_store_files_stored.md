---
title: "Where are downloaded music store files stored?"
date: 2010-04-25
forum: Ubuntu One (CLOSED)
---

### Post by tricomp on 2010-04-25
Does anyone know where the files downloaded from the Ubuntu One Music Store are stored? They are not in the Music folder or anywhere else in my home folder that I can determine, yet Rhythmbox sees them. I noticed that in the Rhythmbox preferences I can no longer specify one specific folder as a watch folder (it defaults back to "Multiple Locations Set"). I'd like to transfer the files I bought to a flash drive, but cannot find them. Makes me feel pretty stupid. Anybody?

---

### Post by StephenDavison on 2010-04-26
Try ~/.ubuntuone/Purchased\ From\ Ubuntu\ One

Or ~/.local/share/ubuntuone/Purchased\ From\ Ubuntu\ One
which is a symbolic link to the former.

---

### Post by StephenDavison on 2010-04-26
Also, the library locations appear to be specified in
~/.gconf/apps/rhythmbox/%gconf.xml

---

### Post by tricomp on 2010-04-26
Thank you very much. Don't know why they have to stash it in a hidden directory but
I do appreciate your help.

---

### Post by stuartlangridge on 2010-04-27
> **tricomp said:**
> Does anyone know where the files downloaded from the Ubuntu One Music Store are stored? I'd like to transfer the files I bought to a flash drive

The easiest way to do this is to drag the songs directly from Rhythmbox to your flash drive. You don't need to rummage around on the filesystem to find them; just use Rhythmbox, it's easier :-)

---

### Post by tricomp on 2010-04-27
Thanks, always good to have multiple ways of doing things I think. I do prefer to have the
files already in the appropriate folder though, laziness on my part. Perhaps you can provide some insight on why it way decided to set things up so that someone like me does 
have to "rummage around on the filesystem to find them". I have used ITunes, Emusic, Amie Street, the
Amazon downloader, and the Napster store, and all make it very easy to locate purchased files - the default is to put them in the Music folder in the Home directory, but putting them in the Ubuntu One folder would make just as much sense to me. I'm sure there was a good reason for doing it this way, perhaps you can share it with us?

---

### Post by joshuahoover on 2010-04-27
> **tricomp said:**
> Thanks, always good to have multiple ways of doing things I think. I do prefer to have the
files already in the appropriate folder though, laziness on my part. Perhaps you can provide some insight on why it way decided to set things up so that someone like me does 
have to "rummage around on the filesystem to find them". I have used ITunes, Emusic, Amie Street, the
Amazon downloader, and the Napster store, and all make it very easy to locate purchased files - the default is to put them in the Music folder in the Home directory, but putting them in the Ubuntu One folder would make just as much sense to me. I'm sure there was a good reason for doing it this way, perhaps you can share it with us?

There is a reason we chose to store the files this way. :) You can read about in this FAQ: [https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?](https://wiki.ubuntu.com/UbuntuOne/FAQ#Why%20are%20downloaded%20music%20files%20stored%20in%20a%20hidden%20directory?)

Thank you,

Joshua

---

### Post by tricomp on 2010-04-27
You know, I actually read that FAQ at some point but must have skipped the end. My bad, especially since I know you are very busy at present. Thanks for taking the time to redirect me to what I should have already read. Please don't take away my Ubuntu decoder ring (or make me go back to Windows!) for being such a twit.

---

### Post by serd on 2010-04-28
The .ra format allows *files* to be *stored*  in a self-contained fashion,i think so

---

### Post by joshuahoover on 2010-04-29
> **tricomp said:**
> You know, I actually read that FAQ at some point but must have skipped the end. My bad, especially since I know you are very busy at present. Thanks for taking the time to redirect me to what I should have already read. Please don't take away my Ubuntu decoder ring (or make me go back to Windows!) for being such a twit.

Not a problem! I have a hard time keeping all the info straight myself and I work on the project. :)

Joshua

---


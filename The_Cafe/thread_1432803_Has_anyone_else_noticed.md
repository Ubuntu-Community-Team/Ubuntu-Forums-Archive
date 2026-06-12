---
title: "Has anyone else noticed?"
date: 2010-03-18
forum: The Cafe
---

### Post by jayze on 2010-03-18
Ubuntu downloads from Windows based PCs can be slightly larger than those downloaded using an Ubuntu system....anyone care to comment?

---

### Post by corney91 on 2010-03-18
Huh? Are you sure you're downloading the same file?

---

### Post by gnupipe on 2010-03-18
Could you be more specific? (Because I don't get it)

---

### Post by Giant Speck on 2010-03-18
I have absolutely no idea what you're talking about.

---

### Post by dmizer on 2010-03-18
If the file size is different, you should run a checksum on it. They should be the same exact size.

How to checksum in Windows: [http://www.brunolinux.com/01-First_Things_To_Know/Checksum_in_Windows.html](http://www.brunolinux.com/01-First_Things_To_Know/Checksum_in_Windows.html)

---

### Post by spupy on 2010-03-18
* deleted *

---

### Post by the yawner on 2010-03-18
There are possibly two explanations:

- Windows adds a couple more bytes here and there while you download it.
- The 1MB interpretation is different on Windows and Ubuntu.

---

### Post by descendent87 on 2010-03-18
Are you on lucid? Could be to do with this [http://ubuntuforums.org/showthread.php?t=1429062](http://ubuntuforums.org/showthread.php?t=1429062)

---

### Post by Psumi on 2010-03-18
> **descendent87 said:**
> Are you on lucid? Could be to do with this [http://ubuntuforums.org/showthread.php?t=1429062](http://ubuntuforums.org/showthread.php?t=1429062)

Uh, the thread opener states that the BIGGER ISO is on Windows, and that the SMALLER ISO is on ubuntu.

Your link says that the BIGGER ISO is on ubuntu.

---

### Post by descendent87 on 2010-03-18
Sorry didn't check the link just knew it was something to do with file sizes being shown differently

---

### Post by Tibuda on 2010-03-18
I think it has something to do with how much bytes is in 1 KB: 1000 x 1024. Not sure.

---

### Post by rottentree on 2010-03-18
They put in bloat for windows users in order to ease the transition for them  \\:D/

Now seriously I haven't noticed it going to check it out now!

Eh both seems to be 690MB

---

### Post by ratcheer on 2010-03-18
the yawner's first explanation is correct concerning text files. Each line of a text file ends with a newline char in UNIX-type systems or a carriage return character and a newline character in Windows. Therefore, a 10-line text file would be 10 characters larger on Windows than on Linux.

Binary files that are downloaded in binary format should be identical on both platforms.

Tim

---

### Post by whiskeylover on 2010-03-18
Most probably its because of the way an MB or GB is represented in Windows and Ubuntu. Check the size in bytes. It should be identical.

Windows - File/Properties/General tab - shows size in bytes.
Ubuntu - ls -l - shows size in bytes.

---

### Post by mickie.kext on 2010-03-18
> **the yawner said:**
> 
- The 1MB interpretation is different on Windows and Ubuntu.

That's the thing.

It is old 1000 vs 1024 issue.

---

### Post by Simian Man on 2010-03-18
It could also be the fact that files on Windows are always stored in 4K blocks on the hard drive.  Perhaps he is looking at the size on disk vs. the actual size.

---

### Post by jayze on 2010-03-18
Big Hi and TY to you all......so how many ice creams have I gotta buy this time?....But this still doesnt explain why if I formatt with a download from Windows I have a windows network that wont go away...but if I use an Ubuntu download I can jigger and poke til I get rid of Windows...anyway...I'm done worrying about it....think I might even have an ice cream myself....what flavours guys?;)

---

### Post by standingwave on 2010-03-18
> **dmizer said:**
> If the file size is different, you should run a checksum on it. They should be the same exact size.I always run md5sum, especially considering that I usually down the iso from bit torrent as it's much faster than using the official servers.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RabbitWho on 2010-03-18
> **the yawner said:**
> There are possibly two explanations:

- Windows adds a couple more bytes here and there while you download it.


Bytes of what? where is it getting them? surely they must be errors then?

---

### Post by the yawner on 2010-03-18
Sorry. I was just making it up. D:

---

### Post by jayze on 2010-03-19
:frown:Righto...well I guess we need a new thread then> Can "I Was Just Making it Up" be classified as anti-social behaviour on Ubuntu Forums

---


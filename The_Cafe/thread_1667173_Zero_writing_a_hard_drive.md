---
title: "Zero writing a hard drive?"
date: 2011-01-14
forum: The Cafe
---

### Post by Captain Smiley Pants on 2011-01-14
Hey guys, I've gotten a new computer lately and don't need my old one. I just saw a posting on a local board for a group that needs computers, and I'd be more than glad to give my old one to them.

One thing though; I want to make sure my HD is completely wiped before giving it out. I used that computer for financial needs and, I'm not pointing fingers at specific people, but one HD can go from someone to another to... someone malicious. Better safe than sorry.

Are there any Linux options I can use? I think the drive is formatted NTFS, if I need to format again for it to work then I'm sure I could work that out.

---

### Post by pl@yer on 2011-01-14
zeroing it like you subject says should do it /dev/zero
assuming /dev/hda is the drive you want to zero
```

dd if=/dev/zero of=/dev/hda

```

---

### Post by WthIteh on 2011-01-14
> **Captain Smiley Pants said:**
> Hey guys, I've gotten a new computer lately and don't need my old one. I just saw a posting on a local board for a group that needs computers, and I'd be more than glad to give my old one to them.

One thing though; I want to make sure my HD is completely wiped before giving it out. I used that computer for financial needs and, I'm not pointing fingers at specific people, but one HD can go from someone to another to... someone malicious. Better safe than sorry.

Are there any Linux options I can use? I think the drive is formatted NTFS, if I need to format again for it to work then I'm sure I could work that out.
1. You could never be sure that data could not be recovered.
2. You could reduce its probability as much time as you spent on it.
3. You could use
```
sudo dd if=/dev/urandom of=/dev/sda1 bs=1G
```
to wipe /dev/sda1 device with random bytes (however it's very time consuming).
4. You could run above command N times to make it very harder to recover.
NOTE: One time running of it will require a good lab for recovering :)

---

### Post by Captain Smiley Pants on 2011-01-14
Oh cool, so I could just mount the drive under another Linux machine and run that command for the drive needing zeroing? Neato!

---

### Post by RiceMonster on 2011-01-14
> **pl@yer said:**
> zeroing it like you subject says should do it /dev/zero
assuming /dev/hda is the drive you want to zero
```

dd if=/dev/zero of=/dev/hda

```

Indeed, and just to answer the second part of the OP's question, that won't require any formating.

---

### Post by mips on 2011-01-14
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)
MHDD & Victoria can invoke the same ATA command from DOS.

For Linux you can use hdparm [https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by Paqman on 2011-01-14
There's also [DBAN]("http://www.dban.org/").

---

### Post by Captain Smiley Pants on 2011-01-14
Sorry for all the posts. Think the forums crapped itself in that specific period of time.

Thanks for all the suggestions thus far. I'm going to try the command first off, and then see where I am down the line. Again, thanks!

---

### Post by Barrucadu on 2011-01-14
Before you run the `dd` command, *make sure you're using the right device node*. Otherwise you'll zero the wrong HDD and feel like an idiot (after the gut-wrenching "omfg what have I done?" moment) :P

---

### Post by Paqman on 2011-01-14
> **Barrucadu said:**
> Before you run the `dd` command, *make sure you're using the right device node*. Otherwise you'll zero the wrong HDD and feel like an idiot (after the gut-wrenching "omfg what have I done?" moment) :P

Hence why dd is known as "destroy drive". Potentially a very dangerous command.

---

### Post by Gremlinzzz on 2011-01-14
I use [http://en.wikipedia.org/wiki/DBAN](http://en.wikipedia.org/wiki/DBAN)
[http://www.dban.org/](http://www.dban.org/)

---

### Post by mips on 2011-01-15
> **Captain Smiley Pants said:**
> Sorry for all the posts. Think the forums crapped itself in that specific period of time.

Thanks for all the suggestions thus far. I'm going to try the command first off, and then see where I am down the line. Again, thanks!

Just to add that Secure Erase is the fastest method of zeroing a drive. There is nothing faster.

Secure Erase does not actually use your os/cpu, it relies on a internal hard drive ATA feature. It's supported by most drives from 2000 onwards.

---

### Post by CharlesA on 2011-01-15
I kinda wonder if that SecureErase thing would work with external USB drives. From what I read on hdparm, it's not working with USB drives.

I tried running dban on a 1.5TB external and it crashed with a kernel panic. I've also had problems with it when having stuff like memory card readers hooked up.

This latest time I use badblocks -w to overwrite the drive, but I think that dd would be more efficient in doing that.

*shrugs*

---

### Post by mips on 2011-01-15
> **CharlesA said:**
> I kinda wonder if that SecureErase thing would work with external USB drives. From what I read on hdparm, it's not working with USB drives.


Probably not as the USB controller will see the drive as inactive and try to reset it.

---

### Post by CharlesA on 2011-01-15
The end would probably be a bricked drive. At least there is a disclaimer.

---

### Post by CharlesA on 2011-01-15
The end would probably be a bricked drive. At least there is a disclaimer.

---

### Post by Captain Smiley Pants on 2011-02-22
Thought I'd get back to this thread to let people know what I used.

I only have a 10.04 CD around and didn't have the means to really download anything like DBAN (maybe will try it later).

I ended up running the Live CD, mounting the hard drive, and using the [shred](http://en.wikipedia.org/wiki/Shred_%28Unix%29) command.

I think it was something like *shred /dev/devicename *[I]-f -v -z

[/I]I reinstalled an OS for this girl who's just gotten out of vocational rehab and needs to finish school. Just gave it away.

So thanks for your input guys!

---

### Post by Lucradia on 2011-02-22
DBAN can force erase everything, even make it unrecoverable and like new (erases all bad sectors, etc.) But since DBAN isn't written to handle certain SATA Drives, it may make the drive corrupt.

It also will void your warranty, and can be reported as an illegal act to cover up incriminating evidence (as I've been told many times on many communities), no matter if you have any or not.

---


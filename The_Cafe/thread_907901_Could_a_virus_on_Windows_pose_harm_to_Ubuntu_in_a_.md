---
title: "Could a virus on Windows pose harm to Ubuntu in a dual-boot config?"
date: 2008-09-01
forum: The Cafe
---

### Post by diablo75 on 2008-09-01
All I'm wanting to know is:

Hypothetically speaking, could a virus running on Windows corrupt things like partition tables on a hard drive and cause you to lose access to your Ubuntu machine.  Might it be possible for a virus to erase all the data on your Ubuntu ext3 partition?

---

### Post by Vitamin-Carrot on 2008-09-01
:confused:

ummmmmmm

Possible

---

### Post by steveneddy on 2008-09-01
Doubtful

---

### Post by EnGorDiaz on 2008-09-01
hmmm i dont think so alot of ppl wouldnt make a virus for it to infect the GRUB bootloader most just target at microsoft programs although its possible

take this example
[http://antivirus.about.com/library/weekly/aa032801a.htm](http://antivirus.about.com/library/weekly/aa032801a.htm)

---

### Post by ~LoKe on 2008-09-01
I'm sure it's possible to do some damage to the partition, but likely?  No, not really.

---

### Post by Twitch6000 on 2008-09-01
Well it depends on where you placed grub.

If its in the MBR.

Then yes it can mess up Linux somewhat,but not like it would Windows.

The worst it would do is make both Oses unbootable.

---

### Post by zmjjmz on 2008-09-02
Most viruses don't attack MBRs --
Killing your host **before** you reproduce? Bad idea.

---

### Post by EnGorDiaz on 2008-09-02
> **zmjjmz said:**
> Most viruses don't attack MBRs --
Killing your host **before** you reproduce? Bad idea.

your exactly right but not exactly attack what im saying it can implant itself into another form of memory other than the hard disk

---

### Post by zmjjmz on 2008-09-02
Hm, I see what you mean.
Supposing Windows is still unable to write ext3, you should be fine.

---

### Post by kevin11951 on 2008-09-02
> **zmjjmz said:**
> Hm, I see what you mean.
Supposing Windows is still unable to write ext3, you should be fine.

well, using this program ([http://www.fs-driver.org/](http://www.fs-driver.org/)) i can write (and read) to/from my Ubuntu partition... just to let you know :)

---

### Post by zmjjmz on 2008-09-02
> **kevin11951 said:**
> well, using this program ([http://www.fs-driver.org/](http://www.fs-driver.org/)) i can write (and read) to/from my Ubuntu partition... just to let you know :)

That was dumb.
So long as you run in Limited User with suDown you should be fine though.

---

### Post by EnGorDiaz on 2008-09-02
> **zmjjmz said:**
> That was dumb.
So long as you run in Limited User with suDown you should be fine though.

huh! rootkits roflcopter

---

### Post by sonofusion82 on 2008-09-02
> **kevin11951 said:**
> well, using this program ([http://www.fs-driver.org/](http://www.fs-driver.org/)) i can write (and read) to/from my Ubuntu partition... just to let you know :)

i think the virus dont even need such a driver, they can do serious damage by just writing garbage in to the entire harddisk.

---

### Post by zmjjmz on 2008-09-02
> **sonofusion82 said:**
> i think the virus dont even need such a driver, they can do serious damage by just writing garbage in to the entire harddisk.

But they wouldn't be able to write to ext3.
Believe me, the last thing a virus wants to do is destroy a user's hard disk.

---

### Post by diablo75 on 2008-09-02
So far, it seems like the answer is "yes...hypothetically speaking".  It makes sense that designing a virus to destroy your host right off the bat would be dumb, but still possible.

---

### Post by Trail on 2008-09-02
As the above posters have said, it is very unlikely that damage to an ext3/whatever filesystem would occur.

---

### Post by gn2 on 2008-09-02
I have a dual boot of Vista and Ubuntu, I use the FS Driver to read ext3 from Vista, but no way would I allow Vista to write to my precious ext3 partitions.
Fortunately during the FS Driver set-up process you can deny it write access and have it as read only,otherwise I would not use FS Driver.

Here's a question I wondered about, Windows always causes bad fragmentation, so would using Windows and FS Driver cause fragmentation on an ext3 drive/partition?

---

### Post by EnGorDiaz on 2008-09-02
> **gn2 said:**
> I have a dual boot of Vista and Ubuntu, I use the FS Driver to read ext3 from Vista, but no way would I allow Vista to write to my precious ext3 partitions.
Fortunately during the FS Driver set-up process you can deny it write access and have it as read only,otherwise I would not use FS Driver.

Here's a question I wondered about, Windows always causes bad fragmentation, so would using Windows and FS Driver cause fragmentation on an ext3 drive/partition?

no becuase most of it would be read only even when you transfer files i bet the program doesnt use the same slack type to write to the partition seemings as the program writer himself would use a type of unix or linux

---

### Post by EnGorDiaz on 2008-09-02
the program would basicaly write the slack type of ext3 and not of windows famous ntfs

althought this makes me relise there is more possibly a chance a virus could direct the slack type to do some damage

---


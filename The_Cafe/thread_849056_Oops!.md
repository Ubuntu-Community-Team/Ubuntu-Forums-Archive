---
title: "Oops!"
date: 2008-07-04
forum: The Cafe
---

### Post by wannadumpwindows on 2008-07-04
You know that evil command? The one that everyone says never use? Well, there's another way.

I was trying to erase and overwrite an external hard disk the other day. I was using the "Shred" command. Let me tell you what, with the right options, it will toast your disk in a heartbeat. LoL. 

Accidentally hit the enter key before you type the entire device path, and POOF your install is toast. I can tell you I won't be letting that happen again.

Just thought I'd throw that out as a little warning for the rest of you. Don't do it. LoL.

---

### Post by JT9161 on 2008-07-04
In comparison I think Shred is even more powerful as you know what just deletes, Shred overwrites data with random  1s and 0s.

---

### Post by wannadumpwindows on 2008-07-04
Yeah, shred is brutal. But I got lucky. I caught it right away with the good old <ctrl+c>. All that it wiped out was the EULA and my initrd. I reinstalled the kernel I was running at the time, and it was pretty much back to normal. 

I hadn't upgraded to hardy yet at that point anyways. So it sounded like a good time to upgrade. So I guess it all worked out in the end. Other than the fact that I can't get my wireless working for anything right now.

I think it's still network-manager messing with me again. Here I come again WICD. LoL.

P.S. I still liked Gutsy better.

---

### Post by wannadumpwindows on 2008-07-04
All I can say, is thank god it overwrites 26 times. It gave me time to catch it before much was gone!

---

### Post by thschiavo on 2008-07-04
... O.o... Didn't know...

---

### Post by wannadumpwindows on 2008-07-04
> **thschiavo said:**
> ... O.o... Didn't know...

I knew, and I still screwed it up . LoL.

---

### Post by beercz on 2008-07-04
You [SIZE=4]**DO**[/SIZE] have a backup don't you?

---

### Post by lisati on 2008-07-04
> **beercz said:**
> You [SIZE=4]**DO**[/SIZE] have a backup don't you?
What's that? :):):):)

---

### Post by Barrucadu on 2008-07-04
dd can be brutal too, don't use that on the wrong disk ;)

---

### Post by RATM_Owns on 2008-07-04
Yeah. Like...
(I'll change it a little to prevent accidental copying and pasting)
```
[dd] if=/dev/urandom (.Dont.Try.) of=/dev/hda
```
Overwrites the data with completely random characters.

---

### Post by wannadumpwindows on 2008-07-06
> **RATM_Owns said:**
> Yeah. Like...
(I'll change it a little to prevent accidental copying and pasting)
```
[dd] if=/dev/urandom (.Dont.Try.) of=/dev/hda
```
Overwrites the data with completely random characters.

Also good to know. 

And yes, I have multiple backups. Gotta love the sbackup with a remote server holding on to everything for me. :)

---


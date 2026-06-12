---
title: "Acorn Archimedes emulation"
date: 2008-08-07
forum: The Cafe
---

### Post by Ozor Mox on 2008-08-07
Has anyone tried to emulate the Acorn Archimedes? I have been trying for the last few days so I can play a classic game called Cataclysm that I used to love, and have got nowhere. I've tried ArcEm, Arculator and Red Squirrel under Ubuntu and also under Windows in a VM, and it just doesn't want to work. The closest I have got is ArcEm under Ubuntu, which booted up RISC OS, but won't read floppy or hard disk images.

If anyone can share their wisdom on the subject, that would be great!

---

### Post by Ozor Mox on 2008-08-09
Bump!

I got my friend to try this on his Windows XP machine, and apart from crashing it several times, he couldn't get it to work with any of the emulators either!

I don't know much about emulation, maybe someone else does?

---

### Post by FranMichaels on 2008-08-09
My curiosity is piqued, will take a look. ;)

P.S. Maybe this thread should be moved to Gaming and Leisure section?

Update: This emulator looks good, and was easy to compile

[http://beebem-unix.bbcmicro.com/](http://beebem-unix.bbcmicro.com/)

Here is a screenshot running the welcome disk (under Ubuntu 8.04)

I'm at a bit of a loss on how to use the system, f11/f12 brings up a menu to load tape or discs. The PRINT command works as I'd expect, but no idea how to use RUN etc... (Experience with C64 helps, but I'm more spoiled with emulators that can easily attach and run tape images from a double click... :lolflag: )

Update 2: I stand corrected, it can auto load and plays fine! 

Update 3: Looking at [wikipedia]("http://en.wikipedia.org/wiki/Acorn_Archimedes"), it seems you are trying to run a much later model of the Archimedes correct? :popcorn: That's what I get just looking for Acorn... Oh well, good luck either way, and it was interesting for me either way... :D

---

### Post by Ozor Mox on 2008-08-09
Wow, thanks for your research FranMichaels! I may well take a look at that BBC emulator too, since that was my very first computer, right before the Acorn Archimedes...ahh, nostalgia! :)

But yes, I am trying to run a newer version, I think the operating system is RISC OS 3. Here's a good idea of what it looks like:

[IMG]http://toastytech.com/guis/riscosoldlook.gif[/IMG]

The game I am trying to get working on it:

[IMG]http://b-em.bbcmicro.com/arculator/cataclysm.gif[/IMG]

[http://www.youtube.com/watch?v=VMlZ2MwYvuA](http://www.youtube.com/watch?v=VMlZ2MwYvuA)

Since I have tried three different emulators though and none of them have worked, I'd have thought it was something I'm doing wrong, which is why I was hoping someone would be able to help me.

---

### Post by FranMichaels on 2008-08-10
Nostalgia means a lot to me. ;)

Anyway, looking at the [arculator]("http://b-em.bbcmicro.com/arculator/download.html") page, there is rpcemu, GPL'd, and has a linux version. It was also an easy compile (but there were no permissions, so I had to do sh configure or make it executable...)

[http://b-em.bbcmicro.com/arculator/download.html](http://b-em.bbcmicro.com/arculator/download.html)

I was looking at a games database (contains no games, just reviews) [http://www.acorn-gaming.org.uk/index.php3?p=Database/DB6](http://www.acorn-gaming.org.uk/index.php3?p=Database/DB6)
Cataclysm looks pretty darn fun, but more importantly, it needs a RISC3 OS, which rpcemu can handle.

I haven't tested more, due to lack of certain files, will likely play around a little tomorrow or another day... 
:popcorn:

---


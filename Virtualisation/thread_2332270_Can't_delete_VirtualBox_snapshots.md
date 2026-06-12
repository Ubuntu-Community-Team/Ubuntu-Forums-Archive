---
title: "Can't delete VirtualBox snapshots"
date: 2016-07-29
forum: Virtualisation
---

### Post by 1clue on 2016-07-29
Hi.

Ubuntu 16.04.

I have a VirtualBox image that has 2  snapshots.  I don't want it to have any.  I want the disk to be exactly  like it is when I run the VM, with the latest changes.

As I  understand it I should be able to delete the two snapshots and have it  be the way I want.  I don't ever want to go back to those snapshots.

I can't delete the snapshots.

According to the docs, I can go to the main screen and click the snapshots button and from there delete my snapshots.

I can click the button and it appears to operate like a button (the graphic changes) but it doesn't do anything.

I found Virtual Media Manager, I can see the still-attached snapshot but when I right click on it I can't do anything.

There's an "Action" menu in the window title bar, but everything is disabled except "refresh."

Can somebody tell me what I'm missing?

Thanks.

---

### Post by DuckHook on 2016-07-29
[LIST=1]
[*]Is your VM still running when you try to delete?
[*]Is your VM not completely shut down but instead saved as a machine state?
[/LIST]
Either of these conditions will prevent you from deleting a snapshot.

---

### Post by 1clue on 2016-07-29
My VM is not running.  According to docs it should work either way, but instead it doesn't work in any way.  I've verified that there is no virtualbox in the process list. (ps axf | grep -i virtual)

I've saved a machine state so I know what you're talking about.  That's not it.

It looks like a repeat of this old bug from 3 years ago:  [https://www.virtualbox.org/ticket/12118](https://www.virtualbox.org/ticket/12118)

I'm using VirtualBox 5.0.24_Ubuntur108355

Thanks.

On the gui neither the details button nor the snapshots button work.

I tried going into the .vbox file and chopping the snapshots out of the xml but that led to an unbootable vm.  I backed it up of course.

---

### Post by DuckHook on 2016-07-30
Try the CLI method using the following template (substitute your own labels where appropriate):```
vboxmanage snapshot name_of_VM delete "Snapshot 1"
```

---

### Post by 1clue on 2016-07-30
I deleted the last snapshot, but I'm a bit nervous to try the other one as it was still windows 7 and I had only downloaded the updates.  If I do it wrong and wind up at this point I've lost my windows 10 upgrade

Let me verify:

If I delete a snapshot, nothing happens to anything that happened after that snapshot was taken, right?

Thanks.

---

### Post by 1clue on 2016-07-30
OK I got them both deleted.

The command line tool helped because I got the error there wasn't enough room on the filesystem.  I grew that and it all deleted fine.

Thank you for your help.

---

### Post by DuckHook on 2016-07-30
You're welcome. :)

The solution to this problem is a good demonstration of why command line tools are often more helpful than insisting on a GUI that blinds us to what's really going on behind the scenes.

---

### Post by 1clue on 2016-07-30
I hear that.  I got heavily into Linux back before XFree86 was stable enough to use regularly. I'd installed X occasionally when I was bored but never really used it for much until years later.

This whole project has been because of the need to get GUI-oriented people able to use VirtualBox so I didn't even know there were command-line utilities to use.

When I get back to the command line it's like coming home.

---

### Post by DuckHook on 2016-07-30
> **1clue said:**
> …I didn't even know there were command-line utilities to use…vboxmanage has no man page, but you can get a summary of its commands with:```
vboxmanage -help
```You will also find the following wiki link very useful: [https://www.virtualbox.org/manual/ch08.html](https://www.virtualbox.org/manual/ch08.html)

Happy Ubuntuing!

---

### Post by 1clue on 2016-07-30
Ya I can rtfm if I know there's a fm to r.

Your post made me less antagonistic to VirtualBox.

Thanks again.

---

### Post by MAFoElffen on 2016-07-31
> **DuckHook said:**
> vboxmanage has no man page, but you can get a summary of its commands with:```
vboxmanage -help
```You will also find the following wiki link very useful: [https://www.virtualbox.org/manual/ch08.html](https://www.virtualbox.org/manual/ch08.html)

Happy Ubuntuing!
I also refer to that wiki page in the VirtualBox Doc's. vboxmanage is sort of like the many options of mdadm. Their are too many sections and subsections in the options to get a jist of in a --help screen. With that, you only scrtath the surface of what it can do.

---


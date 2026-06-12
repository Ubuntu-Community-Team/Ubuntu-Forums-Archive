---
title: "Ubuntu Netbook 64-bit"
date: 2010-12-03
forum: The Cafe
---

### Post by Oxwivi on 2010-12-03
Is it available? Or even possible? Just a quick question, would appreciate a quick reply for now.

---

### Post by Spice Weasel on 2010-12-03
Aye, just install 64-bit Server or use the Minimal CD and then install Unity.

---

### Post by Oxwivi on 2010-12-03
I wish. I'm facing [these problems]("http://ubuntuforums.org/showthread.php?t=1627217") with minimal installs.

---

### Post by NightwishFan on 2010-12-03
Try this method, unless this is not just a 'minimal iso' but a 'debian installer' bug. Just use the Ubuntu Desktop Alternate Install CD. Press f4 and choose install command line system. This usually works better than the minimal iso, and installs a more full system. Then run sudo apt-get install ubuntu-netbook.

If that is a problem, just install ubuntu desktop, then install ubuntu-netbook, and remove a few of the desktop packages you do not want. It is very nearly the same thing.

---

### Post by Oxwivi on 2010-12-03
As a matter of fact, all of my attempts were from my alternate CD, however I don't understand why it'd be better from the alternate.

I'll review ubuntu-netbook packages before trying it.

---

### Post by NightwishFan on 2010-12-03
There are subtle differences to the installer. I find the alternate one a bit more usable. This must just be in general a "debian installer" bug then. The second way works quite well, you can build and strip a system quite efficiently post install if you become proficient with synaptic. In fact, the software center works fine remove most desktop programs. It will leave a few libs, however they will not be used.

---

### Post by Oxwivi on 2010-12-03
Bah, if I install ubuntu-netbook, it will install whatever is in a normal install, which I do not desire. I'll be back to step one, and redo all the removals I do in a normal install. I use a very slim portion of the regular install, so the rest of the programs are, in my eyes, a kind of bloat.

---

### Post by NightwishFan on 2010-12-03
I am not sure what you mean. The Netbook is not much removed from Ubuntu Desktop. Off the top of my head I can not think of much that it misses at all.

Edit: I get it, you want something more minimal. Well to be honest I think it is a bit of a waste of time, just remove what hogs memory from the main install. (Such as "cups" if you do not use it, or some daemons.) Bloat (terrible word, I refuse to call any operating system bloated, even if it is), is just unused programs, the worst they do is take a few hundred mb of disk space, if that is a priority, Just remove a few of them manually. It does not take long and packages such as Ubuntu-Desktop and Ubuntu-Netbook can be removed. Generally just reinstall them before a full upgrade. (Most people fresh install anyway).

---

### Post by Oxwivi on 2010-12-03
Yes, well, that's why I said 'a kind of' bloat.

Well anyway, I selectively installed a very few packages from ubuntu-netbook or ubuntu-desktop. I suppose if I want x64 Netbook, I gotta install minimal, yet experience anything but minimal. :(

---

### Post by 3rdalbum on 2010-12-03
There's no 64-bit Ubuntu Netbook Edition because there are very, very few 64-bit capable netbooks.

---

### Post by Oxwivi on 2010-12-03
I suppose so. I want to install it on a notebook.

---

### Post by CharlesA on 2010-12-03
So you just want the netbook interface?

Just install the netbook version then, there really isn't *that* much difference between x86 an x64 versions.

---

### Post by Oxwivi on 2010-12-03
Speaking of which, Netbook Edition on CD doesn't work. Don't have a USB either, I'm at a dead-end on my quest for Netbook Edition on notebook. Guess I'll stick to Deskop Edition for now...

---

### Post by NightwishFan on 2010-12-03
I do not understand what you mean. The netbook edition is 99% the desktop edition. It is not lighter.

---

### Post by Oxwivi on 2010-12-03
I know it's not lighter, I do no want to install netbook edition for it's lightness. But I was trying minimal install I mentioned for it's lightness. Sorry for the confusion.

---


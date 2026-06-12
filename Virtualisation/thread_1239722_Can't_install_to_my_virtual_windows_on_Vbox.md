---
title: "Can't install to my virtual windows on Vbox"
date: 2009-08-13
forum: Virtualisation
---

### Post by ROY.G.BIV on 2009-08-13
So I made a VM with windows XP Pro as my guest. I've gotten it all working, minus one detail: I can't install anything. The drive picks up the disc, but upon trying to install, I get a screen saying that I don't have enough space to make the download... yet, on the same screen, it clearly shows that I do have enough space. See attachment, I'll show you...

I was told that it was possible to mount more space on my XP? I see how to *** more hard drive space... so I made another 25 GB as primary slave... but when I boot it doesn't show up under drives or anywhere else that I can tell.

Help? What do I do? If I can't install stuff, then this is useless....

edit: Solved.

---

### Post by aesis05401 on 2009-08-13
Hello, 

Is this the first attempted installation of the software on this VM?

I have seen this error thrown by numerous installers... usually when there is an incompletely removed previous version of the software on the machine.  HP print driver installers did the same thing for number of years. 

If this is the first install then maybe something strange occurred during installation. Could it be that you are logged in as a user that does not have write permission to the local disk space?

---

### Post by ROY.G.BIV on 2009-08-13
Sorry, I meant to mark this as solved...

The problem was that the space just wasn't big enough... even though I did technically have enough. I made a new image and made it 30Gb, instead of 10. That solved the problem. However, since VB doesn't offer 3G support, its no good for me... I get nothing under "Host interface" nor "bridged connection".

Which brings me to my next question: do you, or anyone else, know if VmPlayer does offer 3G support?

---


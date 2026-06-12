---
title: "Installing 10.04 broke my wireless ..."
date: 2010-05-27
forum: System76 Support
---

### Post by Eyore15 on 2010-05-27
and I can't figure out how to get it back.  I have played with the little button on the lower right-hand corner of the machine and rebooted until I am blue in the face.

The wireless is up (confirmed on another system).

I've read a whole lot of stuff about the subject on-line and now am so confused I don't know which way is up.

Con someone point me to an "easy-to-understand" how to that will get my wireless back up?

tnx

mcm

---

### Post by vttay03 on 2010-05-27
The fix that's been floating around for this is as follows (this was posted by thomasaaron):

Please establish a wired connection. Then open a terminal and run this command...

```

sudo apt-get install build-essential

```

Then run your System76 Driver again.

Then reboot.

---

### Post by Eyore15 on 2010-05-27
armed with the information from [http://ubuntuforums.org/showthread.php?t=1492608](http://ubuntuforums.org/showthread.php?t=1492608) about doing the build, I solved the problem.  I still don't get why is this is a known issue, that the driver hasn't been propoerly integrated in a driver from the 19th, why are we still struggling to find the solution?

---


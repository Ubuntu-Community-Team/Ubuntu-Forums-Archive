---
title: "Viewer"
date: 2016-08-31
forum: Virtualisation
---

### Post by stockpimp on 2016-08-31
I have a mining rig (Zeus Thunder 3) that I wish to run with a R Pi 3 using Ubu Mate.  I have loaded Mate and all seeme to be runing fine however my next issue is that where I have the miner I do not have a monitor.  My thoughts were if I could set up the R Pi for remote access I could control it from my desktop and that would take care of the issue but it's proving to be a pain.  I installed Vino on the Pi and my DskTp but have yet to successfully get it to connect.  is there a better way to do this?

Cheers

---

### Post by sudodus on 2016-08-31
I have connected to RPi via ssh - but it was running Debian. You can run remote sessions with ***ssh*** (text mode) or ***ssh -X*** (also GUI applications), and you can transfer files with sftp (or via the file browser).

I think [openssh-server](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) should be available for RPi also in Ubuntu MATE.

```
sudo apt-get install openssh-server
```

---

### Post by stockpimp on 2016-09-01
gave the ssh terminal option a shot and that did the trick.  my terminal kung-fu is WEAK at best but it got done.  Thanx for your input!

---

### Post by sudodus on 2016-09-01
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

You can still ask questions about remote access and ssh in this thread, and then you might even change the title of the thread to something like 'Remote access to Raspberry Pi'.

If/when you have other problems, it is best to create a new thread with a good descriptive title to attract people who know about that problem.

---


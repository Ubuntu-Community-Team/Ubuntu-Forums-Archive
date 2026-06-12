---
title: "Data copying from USB flash drive without knowing?"
date: 2017-03-23
forum: Security
---

### Post by joben on 2017-03-23
hi everyone I have an urgent question and I would like to know what I should do


  due to accident, a very important USB flash drive with personal files was inserted into  an Ubuntu computer,is it possible in any kind of way  that the computer copied and saved files from the USB drive, even  though the files were not opened?can the computer scan the files and  keep them somehow? i installed default ubuntu and a few third party softwares... if yes,should I delete the computer? and if the computer was online can someone take the files from the USB  without me knowing?

  

is there any way for me to know if the computer copied the files??


thank you very much guys (-:

---

### Post by TheFu on 2017-03-24
> is it possible in any kind of way that the computer copied and saved files from the USB drive, even though the files were not opened?

Yes.  With a default install, this doesn't happen. However it isn't hard to setup this behavior if that was desired.  The copy would take whatever time the copy requires, so if you inserted it and immediately pulled it out, then it is very unlikely the system had time to notice the drive and start copying.

Usually people setup specific flash media to copy files over automatically - photographers will do this to copy new pictures into their photo library automatically.

Can someone do this remotely?  Sure.  Almost anything that can be done when sitting on the computer can be done remotely over ssh.

File systems have tuning parameters which can be enabled and disabled.  One of them is called 'atime' - this tracks whenever a file is accessed.  It is common to disable this on external or slow media. It is also common to disable it on media that has a limited write lifetime - flash drives.  How your system is configured is unknown, but you can look.  That result may not say what the config was 3 minutes ago. Anyone with root/sudo access can easily change the default.

There is not magical about Unix or doing things like this.  If you'd like to know more, there are lots and lots of resources.  This sort of stuff has been around for 20+ years.

---

### Post by joben on 2017-03-24
Thank you very much, so you are basically saying my data might have been stolen and is going somewhere in the internet.
is there any way for me to find out whether some files were copied or viewed (files that were only on the external USB flash drive)?

how reliable is checking the modified or viewed date on each file? if it was modified/viewed some time BEFORE connecting the USB, am I 100% safe?

---

### Post by TheFu on 2017-03-24
Doubtful. It is highly unlikely any of that happened.  If the last "file access times" are from unexpected times, then you only know that something touched them. Nothing more.  Lots of processes run on Unix systems. A few of them scan for new files and could "touch" those files you are worried about.

All of this is very unlikely.

"Modified" isn't the same as "accessed."  Never heard of "viewed" date. That is probably an imprecise term in some GUI.

There isn't anything that is 100% safe when it comes to computers, unless you built the chip, support chips, motherboard, extra chips, capacitors, all extra components, and assembled them all.  Then you'd have to create and build the OS, all modules, all other hardware and everything around the computer.  You get the point.  Heck, even HDD firmware is known to be hacked from time to time.

But all of this is extremely unlikely unless you are a spy.

---


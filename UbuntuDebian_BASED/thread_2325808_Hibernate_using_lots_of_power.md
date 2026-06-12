---
title: "Hibernate using lots of power"
date: 2016-05-25
forum: Ubuntu/Debian BASED
---

### Post by chamerjr on 2016-05-25
In my settings, I set my laptop to hibernate for everything rather than shutting down, sleeping, etc.  I did a test last night, unplugging my laptop at 100%, then closed the lid (set to hibernate on lid close).  I let it sit for about 90 to 120 minutes, opened it up, and it was at 95%.  That's an awful lot of power drained for something that's supposed to be off.  To be fair, I'm not sure if the laptop actually went into hibernate.  I'm just assuming it did because that's how I set it.  If there is a way to force hibernate, I'm certainly willing to test it again.    As an FYI, I'm running Elementary OS (based off Ubuntu).  Thanks in advance.

---

### Post by ajgreeny on 2016-05-25
Thread moved to **Other operating systems - Ubuntu/Debian based**

I have an old netbook with Atom 270N CPU, 1GB RAM, which hibernates well with Xubuntu 14.04 once the necessary extra file has been added to the filesystem (see [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403) for all the info on that) and I had that machine set to hibernate when the lid was closed.

Trying to do the same with 16.04 causes all sorts of problems which have to be dealt with.  The most important of these is that the machine will not go into hibernation when the lid is closed; it simply goes to suspend which does, of course, still use power.  I wonder if that is what is happening in your situation; which version of Ubuntu are you using?

There are other hibernation problems such as loss of wifi connection on wake up, and loss of cursor as well occasionally, but these can be overcome.  I have not yet, however, managed to get the netbook to hibernate when closing the lid which is very annoying and very necessary on this old machine with a very short life battery, so I shall probably move back to 14.04 for a while, and keep looking here to see if hibernation is getting any more successful.

---

### Post by chamerjr on 2016-05-25
Thanks for the information.  I'm running Elementary OS - Freya (based on Ubuntu 14.04).  Unfortunately, I'm running into some different problems in implementing the fixes on the page you suggested.  I'll keep you updated.  Right now it's time to put the kiddos in their bath before bed.

---

### Post by ajgreeny on 2016-05-27
Just a quick update.
I have now managed to get the netbook to hibernate when the lid is closed.
Previous settings for lid closure were to hibernate when on battery but suspend when on mains power supply.  The machine then always suspended, even when still on battery.  Changing the setting for mains supply also to hibernate means the machine will now hibernate as I want when the lid is closed.

Phew; another problem overcome.

---


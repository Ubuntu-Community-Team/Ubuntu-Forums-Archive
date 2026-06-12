---
title: "Avoid virtualmachine detection from ProctorU"
date: 2013-10-03
forum: Virtualisation
---

### Post by Enkouyami on 2013-10-03
[ProctorU]("http://www.proctoru.com/")'s secure proctored exam software supposedly can detect if you're running in a virtual machine and will not run at all. I need to use it, but don't have Windows or a Mac computer to use it on, only my VM Windows.

---

### Post by TheFu on 2013-10-03
Have you tried their "test it" with native Linux? Did that not work?
It is likely their software will force you to either use Java (non-secure) or load some plugin that runs native code for OSX or Windows. Those things don't work well under Linux, as you can imagine.  You might try WINE, but I wouldn't hold my breath.

From their FAQ:
> Is your service compatible with Linux?
No

Looks like you will be failing all your testing otherwise or modifying and building your own VM hypervisor that hides the things they look for.

It is probably easier to setup a small WinXP dual boot partition 20G should be enough for that.

---

### Post by Enkouyami on 2013-10-03
> **TheFu said:**
> Have you tried their "test it" with native Linux? Did that not work?
It is likely their software will force you to either use Java (non-secure) or load some plugin that runs native code for OSX or Windows. Those things don't work well under Linux, as you can imagine.  You might try WINE, but I wouldn't hold my breath.

From their FAQ:


Looks like you will be failing all your testing otherwise or modifying and building your own VM hypervisor that hides the things they look for.

It is probably easier to setup a small WinXP dual boot partition 20G should be enough for that.

The software they use is [LogMeInRescue]("https://secure.logmeinrescue.com/"), which isn't yet available on linux. The Windows XP, Vista, and 7 installer will not go through with installing on my system because I have a GPT hard drive. I can't install any other version of windows other than Windows 8 core, because the EUFI firmware on my laptop automaticlly enters that product key during installation and it won't let me enter anything else.

---

### Post by CharlesA on 2013-10-03
I don't see how doing the test on a VM would cause problems. LogMeInrescue is just a remote access application.

Check here:
[http://www.proctoru.com/tech.php](http://www.proctoru.com/tech.php)

I think they mean they won't do the exam if they see your running any virtual machines. Unless they dig thru you device manager, I don't think they should be able to tell if you are running on a VM or not.

Contact them and ask would be the best thing to do imho.

---

### Post by TheFu on 2013-10-03
> **Enkouyami said:**
> The software they use is [LogMeInRescue]("https://secure.logmeinrescue.com/"), which isn't yet available on linux. The Windows XP, Vista, and 7 installer will not go through with installing on my system because I have a GPT hard drive. I can't install any other version of windows other than Windows 8 core, because the EUFI firmware on my laptop automaticlly enters that product key during installation and it won't let me enter anything else.

[http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu](http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu)
There were other search results that might work too.

---

### Post by Enkouyami on 2013-10-04
> **TheFu said:**
> [http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu](http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu)
There were other search results that might work too.

Wine does not let me use my webcam and microphone, which are required.

---


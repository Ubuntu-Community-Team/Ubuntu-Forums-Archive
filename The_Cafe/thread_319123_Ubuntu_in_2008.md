---
title: "Ubuntu in 2008"
date: 2006-12-15
forum: The Cafe
---

### Post by wyo on 2006-12-15
A very voiceful fraction of Linux kernel developers decided to not accept proprietary driver in the kernel anymore and it seems Linus accepts it in the 2008 timeframe. But since Ubuntu strong ness depends partially on proprietary drivers I'd like to know how Ubuntu reacts.

I don't want to start a flame ware nor a serious discussion about the decision of the kernel developers since this belongs into the kernel mailing list. Yet first there's a single year to get prepared and work out solutions and yet second this probably has a strong impact on the motivation of other OSS developers. IMO it's very important Ubuntu clears its position to prevent dropping out of OSS work too soon. So my questions are:

Does Ubuntu use just standard kernels and give up one of its main advantages, the integration of proprietary drivers? So far Ubuntu is famest for its easy installation, perfect hardware detection and good quality in all areas.

Or does Ubuntu start patching (forking) the kernel so proprietary drivers still work? It might be possible to build APIs around the kernel so proprietary drivers still work, yet I'm not sure if this works well enough. And patching the kernel might not be the easiest solution after all.

Or am I just over suspicious and Ubuntu can still deliver the same good performance without proprietary drivers? I'm too pessimistic to believe that vendors will change their policy within this year since vendor will only start seriously considering Linux when it has reached 10% market share.

Or is there another alternate way for Ubuntu to cooperate with the situation? 

O. Wyss

---

### Post by v8YKxgHe on 2006-12-15
AFAIK, the module kernel patch to stop binary modules has not been accepted.

---

### Post by wyo on 2006-12-15
Yes, albeit Linus has hinted he will in 2008.

O. Wyss

---

### Post by givré on 2006-12-15
> **wyo said:**
> 
Or does Ubuntu start patching (forking) the kernel so proprietary drivers still work? 

patching is not forking, the majorty of the program you run in ubuntu and in any linux distro are patched, and the kernel itself is patched, and you are not running hundreds of forks...

And yes, this was not accepted by linus, read :
[http://ubuntuforums.org/showthread.php?t=318417](http://ubuntuforums.org/showthread.php?t=318417)
[http://ubuntuforums.org/showthread.php?t=318948](http://ubuntuforums.org/showthread.php?t=318948)
[http://beranger.org/?article=2132](http://beranger.org/?article=2132)

---


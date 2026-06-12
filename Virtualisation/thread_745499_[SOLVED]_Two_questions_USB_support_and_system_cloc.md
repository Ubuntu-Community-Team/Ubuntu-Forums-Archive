---
title: "[SOLVED] Two questions: USB support and system clock under vmware"
date: 2008-04-04
forum: Virtualisation
---

### Post by dwasifar on 2008-04-04
Two things.

1) I installed VMWare server under Gutsy and looked to the advice in [http://ubuntuforums.org/showthread.php?t=731001]("http://ubuntuforums.org/showthread.php?t=731001") to make USB work in vmware.  That fixes it in vmware but also seems to disable auto-mounting in Ubuntu.  Perhaps the USB drive is mounted SOMEWHERE but I can't find it.

2) Is there a way to deliberately make the vmware server present a time and date to the virtual machine that is unconnected to the actual hardware time and date?  I'd like a virtual machine that thinks time has stopped when it's "off," and picks up timekeeping at the same moment it left off when it's turned back "on."  Is there a way to achieve that?

---

### Post by dwasifar on 2008-04-12
Solved the first issue.  Apparently VMware steals the USB when it starts.  That's why I couldn't see it, because VMware was running.

The second issue, I found another way to do what I want without screwing with dates.

---

### Post by Junkieman on 2008-05-21
> **dwasifar said:**
> The second issue, I found another way to do what I want without screwing with dates.

Hi, please can you explain a few details how you solved this? I have the same issue. 

Thanks :)

---


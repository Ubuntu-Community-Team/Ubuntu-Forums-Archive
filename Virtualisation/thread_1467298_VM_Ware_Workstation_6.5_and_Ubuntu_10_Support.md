---
title: "VM Ware Workstation 6.5 and Ubuntu 10 Support?"
date: 2010-04-30
forum: Virtualisation
---

### Post by Intrawebs on 2010-04-30
Has anyone got this working?  I upgraded Ubuntu from 9.1 to 10 and noticed that the VM Ware Tools were still working (integrated mouse without pressing CTRL+ALT to get back to host OS).  So I then stupidly tried the following instructions [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

After that VM Ware Tools failed to upgrade, and of course removed the previous working version.  I get alot of the following errors during the VM Ware tools install.  Any advice would be appreciated.

__FreeBSD__ is not defined
_MSC_VER is not defined
HGFS mount = failed
VM communication interface socket family = failed

Also on boot there are HGFS errors

---

### Post by fjgaude on 2010-04-30
Well, it seems that VMware is out of sorts with anything higher than 9.04. Server is very difficult to get going, so I switched to Player 3.0 which is fine. I think you might have to upgrade to WS 7.0 to have things working correctly with 10.04, or even 9.10.

---

### Post by Intrawebs on 2010-04-30
> **fjgaude said:**
> Well, it seems that VMware is out of sorts with anything higher than 9.04. Server is very difficult to get going, so I switched to Player 3.0 which is fine. I think you might have to upgrade to WS 7.0 to have things working correctly with 10.04, or even 9.10.

That would make sense, this upgrade was actually a double one, I first had to get it to 9.1, cant remember what I was running before that, 8.* maybe.

---

### Post by dcstar on 2010-05-02
> **fjgaude said:**
> Well, it seems that VMware is out of sorts with anything higher than 9.04. Server is very difficult to get going, so I switched to Player 3.0 which is fine. I think you might have to upgrade to WS 7.0 to have things working correctly with 10.04, or even 9.10.

Player 3.1 beta is supposed to be fully 10.04 compatible, but the 10.04 client easy install scripts are broken.

Installing the "normal" way works ok.

---


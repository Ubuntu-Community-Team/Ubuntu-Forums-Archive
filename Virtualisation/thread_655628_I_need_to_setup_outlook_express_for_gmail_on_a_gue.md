---
title: "I need to setup outlook express for gmail on a guest XP os in VMware server..."
date: 2008-01-01
forum: Virtualisation
---

### Post by diablo75 on 2008-01-01
The title probably says it all.  I am wanting to set up Outlook Express running on an XP VM running in VMware Server on top of Ubuntu 7.10.  I've tried to set this up, but the inbound connection, I think..., is having some sort of port forwarding issue.  Outbound communication works fine after some port tweaking in Outlook.

Any ideas?

---

### Post by fjgaude on 2008-01-01
Have you setup vmware as NAT or Bridged?

---

### Post by diablo75 on 2008-01-01
I've tried both.  I think I need to fiddle around with the settings in outlook more than I do vmware.  Bridged should do the trick, I would think, if the right settings are configured in the guest OS.

---

### Post by fjgaude on 2008-01-01
Gosh, with NAT you shouldn't have to do anything within OE except setup the ISP logon ID and password.

---


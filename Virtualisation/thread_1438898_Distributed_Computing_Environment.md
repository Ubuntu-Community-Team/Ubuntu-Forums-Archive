---
title: "Distributed Computing Environment"
date: 2010-03-25
forum: Virtualisation
---

### Post by fiftyfour123 on 2010-03-25
I wasnt exactly sure where to put this, but, my school has a thing that they call a distributed computer environment. I download a citrix client onto my computer and i can access it anywhere. When i open it i see a windows desktop and it basically acts like a virtual machine. What exactly is this called and how can I set it up on Ubuntu?

---

### Post by PilotJLR on 2010-03-25
They are probably presenting you a desktop using Citrix XenApp (aka Presentation Server).

So you would need to install a Citrix client on your ubuntu computer:
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

### Post by fiftyfour123 on 2010-03-25
yeah, that sounds right. But i was actually saying that I wanted to host my own server on my ubuntu machine. Is there any alternative to citrix though. I'm not too fond of their client software.

---

### Post by PilotJLR on 2010-03-25
If you want to present linux desktop(s), then VNC is one easy choice. TightVNC, for example, can do this:
[https://help.ubuntu.com/community/VNC/Servers#tightvncserver](https://help.ubuntu.com/community/VNC/Servers#tightvncserver)

FreeNX is another good option:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

But if you want to host *Windows* desktops for users, then the options are all non-free... you'd need at least a Windows Server license, CALs, and RDS (Remote Desktop Services) CALs.

---

### Post by fiftyfour123 on 2010-03-25
So, even if I did use Citrix I can't do it for free?

---

### Post by PilotJLR on 2010-03-25
:-)

Citrix is quite far from being free.

The least expensive you could get with Windows TS desktops (and be compliant and legal) is the base Windows Server, CALs per user, and RDS per user. Your MSFT licensing program (Open, Select, etc) will determine this cost.

---

### Post by fiftyfour123 on 2010-03-25
Yeah, I don't want it that badly. Haha, thanks for the help.

---


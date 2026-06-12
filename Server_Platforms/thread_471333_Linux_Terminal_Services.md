---
title: "Linux Terminal Services"
date: 2007-06-11
forum: Server Platforms
---

### Post by zemeron on 2007-06-11
I was wondering if someone here could direct me in the right direction (if there is one) on what solutions exist for a Linux equivalent of terminal services. Ideally I'd like something that works like Citrix, with the ability to publish single apps as opposed to desktops. The reason for this is that I'd prefer to refresh my server hardware as opposed to all my desktops, but the cost of Windows + the cost of CALs + the cost of terminal services CALs + the cost of Citrix CALs can really add up to quite a large cost per user.

---

### Post by PetePete on 2007-06-12
I'm not too knowledable on these things , but would X11 fowarding over ssh be similar to what you require?

---

### Post by gaten on 2007-06-12
You could check out one of the following:
[LIST]
[*] X-Forwarding
[*]VNC
[*]FreeNX[/LIST]I've only used VNC myself, so I can't vouch for the others, but I have heard really good things about FreeNX (apparently it's faster than hell).

---

### Post by zemeron on 2007-06-12
> **gaten said:**
> You could check out one of the following:
[LIST]
[*] X-Forwarding
[*]VNC
[*]FreeNX[/LIST]I've only used VNC myself, so I can't vouch for the others, but I have heard really good things about FreeNX (apparently it's faster than hell).

Thanks. Looks like FreeNX might work out for me.

---


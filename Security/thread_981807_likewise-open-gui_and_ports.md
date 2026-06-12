---
title: "likewise-open-gui and ports"
date: 2008-11-14
forum: Security
---

### Post by oyankee on 2008-11-14
Hi,
I installed likewise-open and likewise-open-gui. bcs I need to autentificate with win2003 Active directory.
When I set login and pasw I get this:

The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

```

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to 'vsvsmv.mup.cz':
	88  UDP
	389 UDP
	464 UDP
	123 UDP
	88 TCP
	389 TCP
	445 TCP
	464 TCP
```

I have no firewall client installed. Ports should be open automaticaly then. Or am I wrong? What should I do and how? Thanks for replies.

---

### Post by pcconcepts on 2008-11-14
I ran into the same issue - to fix, I gave the Ubuntu box a static IP. Joining the domain worked perfectly after this. Don't forget to add your doamin user acct to the sudoers file on the ubuntu box. Good luck!

---


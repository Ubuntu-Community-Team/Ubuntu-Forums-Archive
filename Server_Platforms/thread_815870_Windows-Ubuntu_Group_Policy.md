---
title: "Windows-Ubuntu Group Policy"
date: 2008-06-02
forum: Server Platforms
---

### Post by Benismyhorse on 2008-06-02
Hi, this is my first post so don't be harsh, only started using Ubuntu   a couple of weeks back and I think it is great, 
So thought I would try it out at work (I am System Admin) but I just wanted to know if Ubuntu will use the Group Policy set in the Windows Server
NB: I already know how to get Ubuntu to connect to AD.

Thanks in Advance
Shane:)

---

### Post by Digressive on 2008-06-02
Hi, I'm new here too. Welcome!

To answer your question; as far as I know, no Ubuntu will not respect Windows GPO's because a GPO is just a bunch of registry settings, which as you know Ubuntu doesn't have.

It's the same with adding Mac OS X to AD as well, all AD provides is a single sign-on capability, no locking down of the desktop.

D

---

### Post by Benismyhorse on 2008-06-02
Hi, thanks for the response,
Do you know of anyway that I could on Ubuntu use a sort of group policy to create certain restrictions on certain user's thanks

---

### Post by Digressive on 2008-06-03
I don't know of a way, but I guess there must be a way to do that. Anyone?

---

### Post by rickyjones on 2008-06-03
I believe that Gnome as some sort of Admin Policy tool to lock down the desktop (stop users from changing resolution, etc...)

As for actual machine management I know that there are several large tools on the market that are meant for managing several Linux servers at a time, specifically. They mainly ensure, through the use of agents, that certain defined files (/etc/hosts, /etc/resolv.conf, ??) that you define are identical throughout the network using a push-pull method.

CFEngine is one such tool that I have heard of. I have not used any of these tools so I'm not sure how well they work or if they even will accomplish exactly what you are looking to do.

Unfortunately, in my opinion, yet another piece that holds Linux back from the enterprise is the lack of a group policy competitor. Microsoft did a really great thing with group policy. When used correctly it can be extremely powerful!

I hope this post helps!

Sincerely,
Richard

---


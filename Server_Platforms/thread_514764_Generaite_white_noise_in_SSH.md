---
title: "Generaite white noise in SSH"
date: 2007-08-01
forum: Server Platforms
---

### Post by B-Con on 2007-08-01
I was just watching a packet sniffer on my computer and set it to only show packets from my SSH session. Sure enough, every time I pressed a key there was a packet sent both ways, sometimes, two. When I did nothing, no packets where sent.

Obviously, this would make monitoring traffic a breeze. Even if an attacker couldn't monitor the content of an SSH session, they could tell how much data I was sending and/or when I was utilizing it and when it was sitting idle.

Is there a way to generate white noise over an SSH session? I see no option to do so in the standard SSH client, which seems odd to me since in security and cryptography we're taught passionately avoid data-leaking mistakes such as that. Is there any fix?

---

### Post by MJN on 2007-08-01
Whilst not white noise in the true sense you could perhaps use the ssh_config directive ServerAliveInterval to send an in-band burst of traffic during idle periods. Admittedly somewhat crude though.
 
Perhaps a more effective solution, which would fully mask live user activity would be to utilise X11 Forwarding of a lively/dynamic application (e.g. a process monitor) running from the remote end.
 
Whilst in some circumstances traffic profiling is of considerable concern (e.g. military networks as a notable example) are you sure your risk is not paranoia?
 
Mathew

---

### Post by B-Con on 2007-08-01
My personal risk isn't great, but I study a lot of computer security and, having (relatively) recently migrated to Linux I was checking out the OpenBSD SSH implementation and was just surprised to find not even an option for such a critical feature. Granted most users don't actively *need* such a feature, but by excluding that you ensure that no one who would need such a feature can use your program.

It just seems like such a potentially useful, yet easily created, feature that I was surprised to not see it.

Unless, of course, they used something like you suggested. That's not a bad suggestion.

---


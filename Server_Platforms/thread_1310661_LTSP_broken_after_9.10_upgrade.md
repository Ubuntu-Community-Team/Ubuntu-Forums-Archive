---
title: "LTSP broken after 9.10 upgrade"
date: 2009-11-02
forum: Server Platforms
---

### Post by gasman007007 on 2009-11-02
I had LTSP working wonderfully on Ubuntu Server 9.04. After upgrading to 9.10, the farthest I can ever get after booting a thin client is to the Busy Box shell as the user "initramfs". I have read elsewhere that Sunray thin clients are broken in 9.10 using SRSS (Sun Ray Server Software) because of a change in Gnome. Did this change also break LTSP?

I have already tried updating the ssh key and executed the "ltsp-update-image" command. Still at a dead end.

---

### Post by AlexanderDGreat on 2009-11-02
I'm an LTSP user, but not familiar in SRSS, have you tried talking to the guys at irc.freenode.net? #ltsp? Those guys there are great, really helpful and generous, they could give you a hand I'm sure.

I stay there myself sometimes to help others as a way of giving back to the community.

---

### Post by maximalz on 2009-11-03
I had the same problem. For me, rebuilding the client by "ltsp-build-client" worked.

---

### Post by gasman007007 on 2009-11-03
I would like to extend many thanks to both AlexanderDGreat and maximalz for your help. Executing the "ltsp-build-client" command did end up fixing whatever was messed up. Thanks!

---


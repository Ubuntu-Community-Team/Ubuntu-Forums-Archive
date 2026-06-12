---
title: "Upgrading to 10.04"
date: 2010-04-30
forum: Server Platforms
---

### Post by Vegan on 2010-04-30
So what is the CLI for this upgrade?

---

### Post by limey_rick on 2010-04-30
sudo do-release-upgrade -d

---

### Post by sostenible on 2010-04-30
I have 9.10 AMD64 without GUI runing as a file & printer server at a client's offices remotely controled with Webmin.

My question: upgrading 9.10 to 10.04 equals installing 10.04 from scratch? (the reason for upgrading is because I feel 9.10's ext4 is not as stable as it should.....and I guess in 10.04 it should be much more stable, is this right?).

---

### Post by Bachstelze on 2010-04-30
> **sostenible said:**
> 
My question: upgrading 9.10 to 10.04 equals installing 10.04 from scratch? (the reason for upgrading is because I feel 9.10's ext4 is not as stable as it should.....and I guess in 10.04 it should be much more stable, is this right?).

Yes and no. If you uprade, you will have the same packages as someone who did a fresh install (and, among other things, the same kernel with the same filesystem drivers), but your system won't be identical because all your configuration will be kept.

---


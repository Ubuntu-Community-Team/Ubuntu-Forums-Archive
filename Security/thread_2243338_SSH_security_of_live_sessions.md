---
title: "SSH security of live sessions"
date: 2014-09-08
forum: Security
---

### Post by nomenkultur on 2014-09-08
I was just wondering, since I tend to use live sessions a lot (especially from development builds).... is it a major safety risk since the default 'ubuntu' account has root privileges and a blank password, like would it be easy for another computer to SSH just knowing my IP and that I'm running live ubuntu???????

---

### Post by thnewguy on 2014-09-08
I don't think Ubuntu runs OpenSSH in the live session, does it? I'm pretty sure Ubuntu leaves remote access off by default. However, if you are running OpenSSH in the live environment you can disable it by running "sudo service ssh stop" when you first boot up from the disc.

---

### Post by papibe on 2014-09-08
Hi nomenkultur.

I can confirm (as thnewguy mentioned) that neither openssh-server or the meta package ssh are installed on the live Ubuntu USB/CD.

Only openssh-client is pre installed, but that is to connect to the outside, not receive connections.

Regards.

---


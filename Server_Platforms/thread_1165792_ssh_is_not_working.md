---
title: "ssh is not working"
date: 2009-05-21
forum: Server Platforms
---

### Post by manivel on 2009-05-21
i am using ubuntu box hardy LTS  i try connect lan (different machin fedora box) it is working fine as a same time i try to connect. from fedora machine to ubuntu box unable to connect. try to check in ubuntu sshd is not running and /etc/ssh/sshd_config is missing only is ssh_config some file also missing then i tryed to start services in ssh /etc/init.d/ ssh is not there.  can u help me i am able to access both direction.

Thanks

---

### Post by amingv on 2009-05-21
Have you already installed a ssh server? Only the client comes installed by default in Ubuntu.

```
sudo aptitude install ssh
```

---


---
title: "SSH Stopped working"
date: 2010-02-10
forum: Server Platforms
---

### Post by jdowns on 2010-02-10
I was running Ubuntu Server 9.04 and upgraded the kernel. Now I can't log in via ssh anymore. sftp also does not work.

I upgraded to 9.10 hoping that might fix the issue, but still no luck.

When I try to log in with Putty, I get a connection refused error. When working on the server directly, "ssh localhost" will ask for my password, and respond with "Permission denied, please try again"

Because both ssh and sftp don't work, is the problem with openssl perhaps? I don't know how to begin troubleshooting this. Any ideas on how I can get ssh working again?

Thanks for your help!

---

### Post by stlsaint on 2010-02-10
Not to insult your intelligence but did you do try re-installing openssh, or restarting ssh and updating?

---

### Post by jdowns on 2010-02-10
Haha! I had tried reinstalling ssh, not openssh-server. Thanks for pointing out the obvious :D

---


---
title: "Wireshark Security Root Privileges"
date: 2010-03-25
forum: Security
---

### Post by Rubi1200 on 2010-03-25
Having read on the forums about some of the dangers of running Wireshark as root, I would like to know if anyone can suggest some alternative packet sniffers/network analyzers which will offer similar results but without the security issues.
I am using Karmic Koala on a Fujitsu Siemens laptop with wireless router (firewall enabled)
Thanks in advance.

---

### Post by cdenley on 2010-03-25
No need to seek a wireshark replacement. You just need to configure it.
```

sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

```

Now, wireshark no longer requires root privileges to capture traffic. You just need to be a member of the admin group.

---

### Post by e24ohm on 2010-03-25
why is it not recommended to run wireshark as root with?

**Sudo** command?

---

### Post by cdenley on 2010-03-25
> **e24ohm said:**
> why is it not recommended to run wireshark as root with?

**Sudo** command?

The same reason it is not a good idea to run your desktop as root. The idea is user privilege seperation. You don't want anything running with more permission than it needs. If wireshark were somehow exploited to perform something malicious, the process should not have unlimited root permission. This would limit the damage that can be done. No process should have more privileges than is necessary.

---

### Post by Rubi1200 on 2010-03-25
Hi, Cdenley, and thanks for the quick response. Just one little problem; I already installed Wireshark. Do I now run the commands you posted in a terminal? And, can I paste and cut all of them to run all at once or do I run each one individually (noob question)?
Thanks for the help :)

---

### Post by cdenley on 2010-03-25
> **Rubi1200 said:**
> Hi, Cdenley, and thanks for the quick response. Just one little problem; I already installed Wireshark. Do I now run the commands you posted in a terminal? And, can I paste and cut all of them to run all at once or do I run each one individually (noob question)?
Thanks for the help :)

I assumed wireshark was installed. If it weren't, /usr/bin/dumpcap wouldn't even exist. Pasting them all at once should work, but I would go one at a time to make sure none of the commands result in an error.

---

### Post by Rubi1200 on 2010-03-25
Perfect!!!!! 
Thanks =D>

---

### Post by Noxxio on 2010-03-25
Just wanted to say thank you.

This resolved my odd issues with Wireshark and not being able to get it to run with proper permissions

Thanks again

---


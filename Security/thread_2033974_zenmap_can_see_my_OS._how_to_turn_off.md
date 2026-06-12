---
title: "zenmap can see my OS. how to turn off?"
date: 2012-07-27
forum: Security
---

### Post by jonny.milano on 2012-07-27
When auditing my server's security with the zenmap tool, I notice that it is able to detect the OS on my SSH port (Debian Ubuntu). Is there a way to turn this off?

---

### Post by Cheesemill on 2012-07-27
Edit /etc/ssh/sshd_config and add the line:
```
DebianBanner no
```

Even if you do remove it though, nmap can still run OS detection by other means (TCP/IP stack fingerprinting).

---

### Post by jonny.milano on 2012-07-27
ahh.. Very good to know. Thanks for the information! :)

---


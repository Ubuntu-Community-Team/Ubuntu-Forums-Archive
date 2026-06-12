---
title: "ubuntu server refusing connections"
date: 2011-08-03
forum: Server Platforms
---

### Post by Zeta-K on 2011-08-03
I'm trying to connect to my computer running ubuntu server 10.04 via both minecraft and filezilla and the server's been refusing all ssh connections (and by the looks of it, any other connection???). I don't even know exactly what I need to ask as I have very little networking experience but I'd like it to stop refusing connections. Help?

---

### Post by Wim Sturkenboom on 2011-08-04
This might be obvious, but does your server have an ip address? If so, can you ping it?

Do you have sshd installed, configured and working locally (ssh into the machine from the machine itself)?
Do you use a ftp server or sftp (inside sshd)?

Do you have iptables configured?
```

sudo iptables -L

```

This is probably the first line of the above command and indicates that it is not blocking incoming requests.
```

Chain INPUT (policy ACCEPT)

```
If *policy ACCEPT* is *policy DROP*, it blocks the incoming requests.

---


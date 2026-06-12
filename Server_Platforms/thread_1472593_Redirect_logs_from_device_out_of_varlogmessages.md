---
title: "Redirect logs from device out of /var/log/messages"
date: 2010-05-04
forum: Server Platforms
---

### Post by malarie on 2010-05-04
Good day, I have configured my Cisco firewall to redirect all its logs to  my Ubuntu 9.1 server (no UI.)

Now, my /var/log/messages is getting all the firewall logs + all other logs.

I'm wondering if there is a way to redirect the logs from my Cisco Firewall (coming  from UDP port 514) to another file.

Thanks.

---

### Post by ghost_ryder35 on 2010-05-04
> **malarie said:**
> Good day, I have configured my Cisco firewall to redirect all its logs to  my Ubuntu 9.1 server (no UI.)

Now, my /var/log/messages is getting all the firewall logs + all other logs.

I'm wondering if there is a way to redirect the logs from my Cisco Firewall (coming  from UDP port 514) to another file.

Thanks.
This how to is awesome for this.
[http://www.ubuntu.com/system/files/CentralLogging-v4-20090901-03.pdf](http://www.ubuntu.com/system/files/CentralLogging-v4-20090901-03.pdf)

---

### Post by tgalati4 on 2010-05-04
Nice!

---


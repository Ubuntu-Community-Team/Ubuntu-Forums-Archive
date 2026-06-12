---
title: "Firehol - how to unblock Transmission"
date: 2011-06-15
forum: Security
---

### Post by Don_Piotr on 2011-06-15
Hi,

So, in my firehol.conf
there is:

client "http https ftp pop3 pop3s smtp cups dhcp dns lpd mysql ntp rdp smtps samba ssh submission telnet p2p" accept

When I put:
client all accept
Transmission is working as it should.

I still want to block unknown clients.
How can I unblock it?

Thanks for the replies.

Piotr

---

### Post by handy on 2011-06-15
Can you give Transmission a specific port that you have opened for it in your firewall.

---

### Post by Don_Piotr on 2011-06-15
I think it won't work.
Between Firehol and internet, there is some
router, that is not my. So I have only some
local IP 10.0.0.x.
If I open a port, it won't by accessible
from outside.

Am I right?

---


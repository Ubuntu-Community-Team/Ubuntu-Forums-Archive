---
title: "Long wait times for SSH Authuntication - 6.10-server"
date: 2007-03-19
forum: Server Platforms
---

### Post by NewWithoutClue on 2007-03-19
Hey all.

Trying to track down why ssh is taking so long to authenticate.

Has anyone else noticed this delay?

Please share.
Paul

---

### Post by SishGupta on 2007-03-19
How long is long?

For some reason when I use my lan ip address it is taking me up to 6-7 seconds after i enter my username.

When i use my WAN ip it takes me milliseconds.

---

### Post by MJN on 2007-03-19
Probably the reverse lookup of your IP address. You could prove this by putting an entry for your client's LAN address in your server's /etc/hosts file hence no timeout waiting the DNS lookup (failure).

Mathew

---

### Post by conjur3r on 2007-03-19
You could tell the daemon not to lookup the DNS entry by putting
<code>
UseDNS no
</code>
into your /etc/ssh/sshd_config.  Don't forget to restart the sshd server.

---

### Post by apjone on 2007-03-19
great i have a similar problem on 6.06. WIll give that a try

update IT WORKS!

---

### Post by MJN on 2007-03-19
Nice one Conjur3r - I've been telling countless people the /etc/hosts workaround as I didn't realise there was a directive to turn it off! D'oh! ](*,)

Mathew

---

### Post by NewWithoutClue on 2007-03-19
Awesome. Both suggestions work.


Thanks for sharing,
Paul

---


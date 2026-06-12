---
title: "Configure firewall (Shorewall) to allow traffic for services on a Ubuntu Server"
date: 2011-11-02
forum: Server Platforms
---

### Post by gunnarflax on 2011-11-02
Hello everyone!

I have an Ubuntu Server 11.04 x64 which I want to secure.

The server will be open to Internet and I want to be able to SSH/SFTP into the machine and the SSH-server runs on a custom set port. I also want a web server accessible from the Internet. These tasks seems not to hard to perform but I also want SAMBA-shares to be accessible from within the local network and this seems to be a bit trickier.

If possible I also want to be able to "stealth" the ports necessary to protect the server further but also allow the SAMBA-shares to be automatically found within the local network.

I've never configured firewalls before except for a router and I always bump into a bunch of problem when doing it all by myself so I was hoping for some tips or preferably a guide on how to this.

Thank you!

(I've also posted this question on askubuntu since I need an answer rather quick. If this is against any rules which I'm not aware of, please forgive me and notify me so will I close one of the posts)

**Update:**
On second thought I'd could just as likely go with UFW if the same settings are achievable ("stealth" ports).

---


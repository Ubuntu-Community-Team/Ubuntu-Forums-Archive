---
title: "Server not allowing Samba, SSH access Need help"
date: 2009-08-01
forum: Server Platforms
---

### Post by oliv2915 on 2009-08-01
I can get online and ping all day long. I setup a samba server and ssh server but I am not getting access. I think it has to do with a setting in ufw not letting my eth1 (DHCP for LAN) thru ports.

---

### Post by swerdna on 2009-08-02
> **oliv2915 said:**
> I can get online and ping all day long. I setup a samba server and ssh server but I am not getting access. I think it has to do with a setting in ufw not letting my eth1 (DHCP for LAN) thru ports.
Read this excerpt on [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

And you can also infer from it how to open UFW for ssh too.

---


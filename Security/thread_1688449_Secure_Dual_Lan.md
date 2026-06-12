---
title: "Secure Dual Lan"
date: 2011-02-15
forum: Security
---

### Post by rdrifter on 2011-02-15
I got a dual LAN home server setup where eth0 is connected to the internal router and eth1 is connected to the external router, but I would like to harden the security of the internal interface. The system got apache2, ssh and vino server opened to the external nic. The internal nic used only for sharing files (samba) and dlna (minidlna).

It will be really great if some one could guide me on this.

---

### Post by rdrifter on 2011-02-22
bump

---

### Post by Jive Turkey on 2011-02-22
read the documentation on ufw and samba.  UFW is a firewall management tool that you can set and forget.  The docs for smb.conf will probably tell you how to set it to listen on only the interface you want and only respond to the host(s) you want.

IMHO you should disable/remove vino if you don't absolutely need it.  the packages denyhosts or fail2ban might be of interest to you as well.

Some services have a file in /etc/default/<nameofservice> which may or may not contain a directive to specify what interface(s) to use also.

If you don't have untrusted guests in your LAN you might not need to worry too much about hardening your internal subnet.

---

### Post by rdrifter on 2011-02-23
I have enabled these 2 options in the samba server so that it will be bind to eth0 and local host.

interfaces = 127.0.0.0/8 eth0
bind interfaces only = yes

but its still accessible when you are connected to the system via eth1, which got a different subnet.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
Try changing to:
interfaces = eth0

Then add:

hosts allow = your internal subnet e.g. 192.168.1/24 your ip address
hosts deny = 0.0.0.0/0

Then restart the samba services.
sudo service smbd restart
sudo service nmbd restart

---


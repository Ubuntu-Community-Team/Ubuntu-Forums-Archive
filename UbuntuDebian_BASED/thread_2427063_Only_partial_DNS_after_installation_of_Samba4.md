---
title: "Only partial DNS after installation of Samba4"
date: 2019-09-17
forum: Ubuntu/Debian BASED
---

### Post by symbolicfrank on 2019-09-17
I have a Linux Mint Cinnamon 19.2 server (Ubuntu 18.4), on which I installed Samba and created a domain. Since then the DNS only works partial, if at all. At the moment, servers outside the LAN can be resolved. The domain and local computers are not found.

There is a router at 192.168.1.254, that is the address of the nameserver in /etc/resolv.conf, which is symlinked to /run/systemd/resolve/resolv.conf. Changing this isn't permanent, even if I do that through systemd-resolver.

Then there is /etc/network/interfaces, which doesn't seem to be used anymore. And /etc/netplan/1-network-manager-all.yaml, which says: "renderer=NetManager". /etc/NetworkManager/NetworkManager.conf says "managed=false". 

There are two network interfaces, which I gave a fixed ip-address in the GUI, which worked, but the specified DNS servers are ignored.

Also, there was dnsmasq, but only on the virtual bridge (192.168.122.1), which isn't even in the local zone. After I reinstalled it, it is on all the interfaces.

But I have no idea how it should work. I have been trying for days to find out, without success. Can you guys tell me how I can diagnose and fix it?

---

### Post by slickymaster on 2019-09-17
Thread moved to **Ubuntu/Debian BASED** for a better fit

---

### Post by SeijiSensei on 2019-09-17
If this system is using systemd-resolved, then you can specify the DNS servers to use in /etc/systemd/resolved.conf.  See "[man resolved.conf]("https://manpages.debian.org/testing/systemd/resolved.conf.5.en.html")" for details. Basically uncomment the DNS= line and list the server IPs there with spaces between them. You'll probably have to restart systemd-resolved with "sudo systemctl restart systemd-resolved".

---

### Post by symbolicfrank on 2019-09-18
Thanks, I did. Then again, what am I supposed to supply? The router? The server itself? 127.0.0.53? But it doesn't matter, it is ignored.

systemd-resolve can find the server itself and google.com (uses router)
nslookup can only find google.com (uses router)
None of them can find server.domain

/etc/samba/smb.conf contains: "dns forwarder = 192.168.1.254", which is the only thing that seems to be used at all, and I think it requires dnsmasq.

Help!

---

### Post by SeijiSensei on 2019-09-18
Do you need a "dns forwarder" at all?  If so, try 127.0.0.53.

Is the "domain" a Samba domain?  That won't work; it needs to be a normal DNS domain like ubuntuforums.com.  You can get around this problem by adding an entry to /etc/hosts:

```

10.10.10.10     server.domain

```

---


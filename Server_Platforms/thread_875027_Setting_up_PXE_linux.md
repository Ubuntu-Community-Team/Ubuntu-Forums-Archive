---
title: "Setting up PXE linux"
date: 2008-07-30
forum: Server Platforms
---

### Post by deepsman on 2008-07-30
Hi all,
I am new to linux. 

Previously I was able to set up a simple pxe linux boot. I just set up the /etc/dhcp3/dhcpd.conf and /etc/default/tftpd-hpa. The server box with only one NIC and which is the on board NIC. 

I am having a problem right now. This is because I want to set up a same server with 2 NIC. 1 NIC for the pxe linux server with the 2nd NIC is to connect to internet network. How can I make this work?

I got an error message on the client and showing that "PXE-E11 ARP time out". Anybody know what wrong? 


Thanks

---

### Post by songshu on 2008-07-30
probably your server is listening on the wrong network card?

just a guess, but you want to set up all the internal servers to listen on the internal IP only, otherwise the whole world can PXE boot from your server ;)

---

### Post by BobMUK on 2008-07-31
Check your syslog to see what's going on:

grep -i tftp /var/log/syslog 

I'm running atftpd but the logging should be the same for you.
You should see lines like:
```

syslog.0:Jul 30 17:08:01 backendpvr in.tftpd[15940]: connect from 192.168.1.2 (192.168.1.2)
syslog.0:Jul 30 17:08:01 backendpvr atftpd[15940]: Advanced Trivial FTP server started (0.7)
syslog.0:Jul 30 17:08:01 backendpvr atftpd[15940]: Serving PXEClient/pxelinux.0 to 192.168.1.2:2070
syslog.0:Jul 30 17:08:01 backendpvr atftpd[15940]: Serving PXEClient/pxelinux.0 to 192.168.1.2:2071

```

Bob

---


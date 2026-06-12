---
title: "remote reboot and login"
date: 2013-01-26
forum: Server Platforms
---

### Post by maclenin on 2013-01-26
I am doing some work on a remote server and understand how to reboot the remote server (via ssh), when reqired: **sudo shutdown -r +0**

However, I am not as clear on how to log back in (via ssh) to the remote server once the remote server has rebooted (as its connection to the network will have been severed during reboot). 

There must be an "auto login" config that can be tailored to auto login the remote server, once the remote server has rebooted?

Thanks for any guidance.

---

### Post by sudodus on 2013-01-26
I have not used any autologin, but simply tested manually or waited to log in: when the system is up and running, it will accept log in as usual.

So it should be possible to make a script at the client computer, that tries, sleeps, tries again ... until it succeeds.

```
ssh -p port user@server-ip
```

If the server uses a non-standard port, it must be specified. See ```
man ssh
```

---

### Post by SeijiSensei on 2013-01-26
Unless the server gets a new IP address from DHCP when it is rebooted, you can just wait until it comes back up and log in again with SSH.  Using "ping ip.addr.of.server" will tell you when it's available again.

If the server does not have a static address, you need to fix that problem first.  Make sure the IP configuration is specified in /etc/network/interfaces as described in the "Static IP Address Assignment" section of [this document](https://help.ubuntu.com/12.04/serverguide/network-configuration.html).

A server is pretty useless if its address changes on every reboot.

---


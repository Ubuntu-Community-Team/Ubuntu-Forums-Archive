---
title: "Connecting wirelessly in Ubuntu Server 15.10 (systemd)"
date: 2015-11-08
forum: Server Platforms
---

### Post by Brinstar on 2015-11-08
I have searched for documentation on this topic but it seems this use-case isn't popular

I'm trying to connect an old laptop (which I want to repurpose as a little home server) to a wireless network, the wireless card is Intel Wireless 3945ABG (so it's supported by the kernel).

For some reason, there is no simple process to connect to a wireless network if I'm using Ubuntu Server 15.10 (or if there is, it's obscure enough that I couldn't find it by searching).

Is there some kind of command line utility that would make this easier or do I have to edit config files (which I don't mind doing, as long as I know where to start)??

The wireless card shows up as wlp12s0 when I run iwconfig, if that helps.

---

### Post by darkod on 2015-11-08
I don't know if it works for 15.10 too, but you can try something along the standard ubuntu server wifi config: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal)

Yes, you do need to edit the /etc/network/interfaces. That's where network settings are.

---

### Post by Brinstar on 2015-11-08
14.04 is not using systemd

---

### Post by darkod on 2015-11-08
I know, that's why I said I'm not sure if the regular config works for 15.10 or not. Did you try it? Are you sure systemd makes different networking setup?

---

### Post by Brinstar on 2015-11-08
Yes I did try it, and 15.10 does work with the /etc/network/interfaces setup but I am worried that when it comes to switching over to 16.04LTS things will be fully systemd.

I think between 14.10 and 16.04, systemd is being used in some hybrid way with the /etc/network/interfaces method.

---

### Post by darkod on 2015-11-08
Well, we'll have to wait and see for that I guess. Plus, once 16.04 is out there will be a new server guide on help.ubuntu.com, which there isn't right now for 15.10. I assume that is because it's non-LTS and people rarely use it for production servers. And there should be plenty wiki pages and instructions how to configure networking... :)

---

### Post by Brinstar on 2015-11-08
Looking forward to that new guide, I think many people would welcome having a good explanation of the systemd way, especially as it seems 16.04 is going to be systemd only.

---


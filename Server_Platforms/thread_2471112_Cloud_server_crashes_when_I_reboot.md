---
title: "Cloud server crashes when I reboot"
date: 2022-01-21
forum: Server Platforms
---

### Post by shadowsaunter on 2022-01-21
My cloud server crashes when I reboot, or I think it does.  I'm running Ubuntu Server 20.04 on a DigitalOcean droplet and it is configured for unattended-upgrades.  When I log in I am frequently greeted with a "system restart required" message, but when I do so my server never comes back up.  DigitalOcean offers a recovery console:

1. I'm not sure how the console works, but it when I open it I get a BIOS prompt which I can log into with my sudo enabled user and it goes through the startup routine with timestamps flying by.  After booting I get a normal shell login screen.
2. My other cloud servers do not open a BIOS prompt, they go straight to the normal shell login when I open recovery console.

Because I get the BIOS prompt, I think this server is crashing on reboot.  The DigitalOcean prompt says "Use the Recovery Console if you need to use the recovery ISO", so I guess it is loading an environment that fixes whatever is broken on this server until the next reboot, but I'm not sure where to start looking for a fix.  This is my VPN server, and I would really prefer to fix this install rather than rebuild it and redeploy keys to all of the connected devices.

Could anyone provide some pointers for where to start troubleshooting?

Thank you,

-Paul

---

### Post by slickymaster on 2022-01-21
*Thread moved to **Server Platforms**.*

---

### Post by shadowsaunter on 2022-01-21
Thanks for moving this post to a location that no one looks.  That was extremely helpful.

---

### Post by MAFoElffen on 2022-01-22
I know nothing about Digital Ocean's Recovery Console... But I did find these two links on it:
[https://docs.digitalocean.com/products/droplets/resources/recovery-console/](https://docs.digitalocean.com/products/droplets/resources/recovery-console/)
[https://docs.digitalocean.com/products/droplets/resources/recovery-iso/](https://docs.digitalocean.com/products/droplets/resources/recovery-iso/)

---


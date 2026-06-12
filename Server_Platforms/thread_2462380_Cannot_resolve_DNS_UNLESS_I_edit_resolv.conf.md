---
title: "Cannot resolve DNS UNLESS I edit resolv.conf"
date: 2021-05-19
forum: Server Platforms
---

### Post by LinuxNoob6 on 2021-05-19
Currently running Ubuntu 18.04.5 that is now patched and up to date. When I boot the server, I cannot ping google.com, however, I CAN ping 8.8.8.8. If I manually edit the resolv.conf file and change the setting to 127.0.0.1 I CAN then ping google.com. I know that this is reset after each reboot and is not a long term fix.

Running on this server is a Unifi controller, PiHole, and Wireguard (via PiVPN). 

I've set a static IP address via the netplan file and that seems to be working properly. I did NOT get any errors when applying the config file.

I **was** having an issue where the machine was showing two different static IP addresses (incorrectly), however, it appears I've resolved that issue.

Where have I gone wrong?

Thanks!

---

### Post by LinuxNoob6 on 2021-05-19
I think running this fixed the issue:

```
sudo rm -f /etc/resolv.conf
ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

However when I log in it shows that it failed to connect o the ubuntu changelogs and tells me to check my internet connection.

---


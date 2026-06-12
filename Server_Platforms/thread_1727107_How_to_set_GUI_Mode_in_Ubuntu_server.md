---
title: "How to set GUI Mode in Ubuntu server"
date: 2011-04-12
forum: Server Platforms
---

### Post by shariefbe on 2011-04-12
Dear friends,
Can anyone tell me how to use ubuntu server GUI mode. I installed ubuntu server in Desktop and i found that no GUI mode in that. Only text mode is showing. So waiting for help.

Than you in advance

---

### Post by arrrghhh on 2011-04-12
> **shariefbe said:**
> Dear friends,
Can anyone tell me how to use ubuntu server GUI mode. I installed ubuntu server in Desktop and i found that no GUI mode in that. Only text mode is showing. So waiting for help.

Than you in advance

There is no GUI-mode.

If you want a GUI, install Ubuntu Desktop - not the meta-package, download full Ubuntu Desktop and install it fresh.  No point in trying to fit a round peg into a square hole... Ubuntu Server is designed without a GUI.  There's some web-ui tools that might be helpful, but if you want a full desktop environment, install Ubuntu Desktop!!!

---

### Post by imac_89 on 2011-04-12
I second that motion. Why did you choose to use Ubuntu Server anyway?

---

### Post by Iker Etxebarria on 2011-04-14
Ubuntu server is better to reduce the CPU consume associated to the GUI. So if you need GUI it has no sense to have ubuntu server, install ubuntu desktop.

---

### Post by fenderr357 on 2011-04-14
Like they said if you need a desktop, just install the desktop version. But if you need a light-weight GUI for your server try just running:

```
sudo apt-get install gnome-core gdm xinit
```

---


---
title: "Configure VirtualBox application to run in seamless mode"
date: 2013-08-07
forum: Virtualisation
---

### Post by vmalep on 2013-08-07
Dear all,

I am running Ubuntu 13.04, but I need some Windows applications for my work, in particular Explorer to launch a F5 VPN tunnels, Outlook to connect to M$ Exchange and Excel/Word for compatibility issues (in particular with .xlsx files).

I currently have a XP guest, but to switch between the virtual machine and Ubuntu is not very friendly. I have seen the seamless mode, but it is not well integrated to Ubuntu Unity: the start bar is mostly hidden and occupies part of the bottom screen and I still have to launch applications via the Start/menu windows button, etc.

I wonder if Unity could not integrate VB guest applications as it does for WebApp. I know this is not an easy stuff, but it would be great because it would make the virtualization transparent.

What do you think? Should I open an idea on Brainstorm?

BR
Pierre

---

### Post by ian-weisser on 2013-08-07
No, for several reasons. Including that Brainstorm has been closed.

If find that seamless works well with several desktop environments, including Xubuntu.

---

### Post by ibjsb4 on 2013-08-07
Seamless plays nice with the classic desktop.

```
sudo apt-get install gnome-session-fallback
```

---


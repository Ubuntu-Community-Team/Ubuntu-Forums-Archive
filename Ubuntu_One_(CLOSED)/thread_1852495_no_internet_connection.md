---
title: "no internet connection"
date: 2011-09-30
forum: Ubuntu One (CLOSED)
---

### Post by anwmalos on 2011-09-30
I have an installation of ubuntu 11.04 desktop which serves as http/smb server, media center, router etc, so the configuration is somewhat customized and gnome network manager is disabled. All the network configuration is done through /etc/network and custom scripts

I tried to sign in with ubuntu one on this installation and the sign in button is grayed out as it says that there is no internet network connection which is wrong, as there is an active network connection with no outbound firewall or proxy.

Any ideas?

PS: It's really frustrating that ubuntu one cannot be managed through CLI only.

---

### Post by thefasterblueone on 2011-09-30
> **anwmalos said:**
> PS: It's really frustrating that ubuntu one cannot be managed through CLI only.

Ubuntu One can be managed through CLI, try this:

```
man u1sdtool
```

---

### Post by anwmalos on 2011-09-30
> **thefasterblueone said:**
> Ubuntu One can be managed through CLI, try this:

```
man u1sdtool
```

I've already tried that and it's pretty funny because although it is a CLI tool, it actually needs a GUI to work. If you try it through ssh you will understand what I mean...

---

### Post by anwmalos on 2011-09-30
Well, I confirmed it on stock ubuntu desktop 11.04 and 11.10 so I'll just file a bug report

---


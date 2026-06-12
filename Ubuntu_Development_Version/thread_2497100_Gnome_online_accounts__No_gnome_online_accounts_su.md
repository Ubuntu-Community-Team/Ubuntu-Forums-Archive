---
title: "Gnome online accounts : No gnome online accounts support found"
date: 2024-04-23
forum: Ubuntu Development Version
---

### Post by hectorsales on 2024-04-23
I have added two gmail email accounts from gnome-control-center, but something seems to be wrong. I use a service, loaded on desktop login, collects the mails and provides the dbus service: bubblemail.

[http://bubblemail.free.fr/documentation](http://bubblemail.free.fr/documentation)

if i launch from console i got the next error:

```
~$ bubblemaild


WARNING:root:No gnome online accounts support found



```

```
Logs:
23/04 11:56:18 DEBUG:service(139): Bubblemail service ready
23/04 11:56:28 WARNING:service(187): No gnome online accounts support found
23/04 11:56:28 DEBUG:account(463): Cleanup GOA accounts
23/04 11:56:28 DEBUG:plugin(288): Running on_collect hook for libnotifyplugin
23/04 11:56:28 INFO:service(193): No enabled account found, bypass collect
23/04 12:00:38 DEBUG:settingswindow(125): No accounts

```

Best Regards

---

### Post by jbicha on 2024-04-23
Did it work in Ubuntu 23.10?

gnome-online-accounts had a major API bump for GNOME 46 so some things that used the old gnome-online-accounts may not work any more.

There is a project, gnome-online-accounts-gtk, that was useful for the gnome-control-center forks for Budgie, Cinnamon, and Unity. But that may be completely unrelated to what your app needs. (Apps that only use gnome-online-accounts integration like Evolution weren't affected by the API bump.)

---

### Post by hectorsales on 2024-04-24
> **jbicha said:**
> Did it work in Ubuntu 23.10?

gnome-online-accounts had a major API bump for GNOME 46 so some things that used the old gnome-online-accounts may not work any more.

There is a project, gnome-online-accounts-gtk, that was useful for the gnome-control-center forks for Budgie, Cinnamon, and Unity. But that may be completely unrelated to what your app needs. (Apps that only use gnome-online-accounts integration like Evolution weren't affected by the API bump.)

Thanks for your response, I solved it by setting up the Gmail accounts through nautilus. This worked for me

---

### Post by jbicha on 2024-04-24
I think that it's required to reauthenticate with GNOME Online Accounts after upgrading to 24.04 LTS.

---


---
title: "No D-Bus daemon running -- virt-manager from remote host."
date: 2013-06-17
forum: Virtualisation
---

### Post by 1clue on 2013-06-17
Hi.

I had an xubuntu setup, installed KVM on it and now that I actually understand something about KVM I decided to reinstall the entire box.

Three days ago, I had the ability to ssh -X <my-xubuntu-box>, and then run virt-manager.

No more.

I can run virt-manager from the newly installed xubuntu box, but not from the same Mac that was running it before.

Nothing has changed on the Mac, it hasn't even been run since then.

The entire error text:
```
Error starting Virtual Machine Manager: No D-BUS daemon running


Traceback (most recent call last):
  File "/usr/share/virt-manager/virt-manager.py", line 383, in <module>
    main()
  File "/usr/share/virt-manager/virt-manager.py", line 326, in main
    config = virtManager.config.vmmConfig(appname, appversion, ui_dir)
  File "/usr/share/virt-manager/virtManager/config.py", line 98, in __init__
    self.conf.add_dir(self.conf_dir, gconf.CLIENT_PRELOAD_NONE)
GError: No D-BUS daemon running


```

But when I look on the Linux box, it's running:
```
ps axf | grep dbus
 1172 ?        Ss     0:00 dbus-daemon --system --fork
 5023 pts/1    S+     0:00              \_ grep --color=auto dbus
 2754 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch startxfce4
 2757 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch startxfce4
 2758 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 2822 ?        S      0:00  \_ /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3

```

So here are the possibilities that I see:
[LIST=1]
[*]Something changed about dbus (I see a security fix from a few days ago)
[*]I took a shortcut on installing and missed something.
[*]All of the above?
[*]None of the above?
[/LIST]

Could somebody who knows more about KVM give me a clue?  
Thanks.

---


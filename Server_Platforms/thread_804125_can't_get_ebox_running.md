---
title: "can't get ebox running"
date: 2008-05-22
forum: Server Platforms
---

### Post by tmilam on 2008-05-22
I installed ebox a week or two ago, then uninstalled it. Now I'm reinstalling and having trouble with it. Here is what happens:

```
The ebox group has not been set in the config file.Creating the eboxlogs database
Skipping apache port setting as current port and new port are equal
The ebox group has not been set in the config file.invoke-rc.d: initscript ebox, action "apache" failed.
The ebox group has not been set in the config file.invoke-rc.d: initscript ebox, action "apache" failed.
```

I even tried apt-get remove --purge (with no luck, same results).

If I try to start ebox with /etc/init.d/ebox/start I get this 

```
The ebox group has not been set in the config file.
```

---

### Post by foolano on 2008-05-25
Hi,

That's a known [bug]("https://bugs.launchpad.net/ubuntu/+source/ebox/+bug/213939").

You can workaround it by doing the following:

```
sudo apt-get remove --purge libebox
```

```
sudo ln -s /usr/bin/gconftool-2 /usr/bin/gconftool
```

Reinstall eBox again

---


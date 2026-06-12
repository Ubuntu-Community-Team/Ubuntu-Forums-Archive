---
title: "Ubuntu - dial up internet services running by default"
date: 2010-08-15
forum: The Cafe
---

### Post by stmiller on 2010-08-15
Ubuntu has a couple of dial-up internet services running by default in the background. Even the latest 10.10 alphas still have these.

It's 2010 - how can we remove these from running 24/7 in the default Ubuntu install?

[B]pppd-dns – for dial up internet

dns-clean – for dial up internet[/B]


Other things running by default 24/7 that people may also not need:

[B]saned – for scanners

bluetooth – for bluetooth[/B]

others... :)

I find it odd that Ubuntu makes strides to get a quickly booting desktop, yet leaves so many random services running default at boot. 

What do you think?

---

### Post by fatality_uk on 2010-08-15
Try connecting to a SonicWall SSL-VPN without pppd, very hard. So don't be taking my pppd away dude :) I am sure a quick trawl through Synaptic would get rid.

---

### Post by cariboo on 2010-08-15
pppd is also used with usb wireless dongles. As with everything Linux, if you don't need the service disable it. With upstart it is pretty simple to disable a service eg:

```
sudo chmod -x /etc/init.d/bluetooth
```

all the startup scripts are in /etc/init.d. just remove the executable bit from the services you don't want to run.

**Note**: be careful when doing the above, if you disable to much, your system may be unusable.

---

### Post by stmiller on 2010-08-15
Thanks - I'm a sysadmin I know how to enable/disable services. :)

I was more asking a broad 'Ubuntu' question for things Ubuntu chooses to run at default.

Thanks for your input! That all makes sense. Cheers,

---


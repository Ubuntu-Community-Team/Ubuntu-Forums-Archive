---
title: "Landscape Dedicated Server Installation"
date: 2009-11-25
forum: Server Platforms
---

### Post by stefanadelbert on 2009-11-25
I'm really interested in Landscape as a way of monitoring and updating my network of Ubuntu servers and desktops. I would like to run the Landscape server/service locally (and avoid paying for a hosted service), but am struggling to find info on how to do this or if it is actually even possible.

Is anyone running their own Landscape server successfully? Any guides or tutorials out there that anyone recommends?

---

### Post by volkswagner on 2009-11-26
It doesn't look like you can roll your own, nor will you be able to.

[http://brainstorm.ubuntu.com/idea/6338/](http://brainstorm.ubuntu.com/idea/6338/)

---

### Post by Thirtysixway on 2009-11-26
> **volkswagner said:**
> It doesn't look like you can roll your own, nor will you be able to.

[http://brainstorm.ubuntu.com/idea/6338/](http://brainstorm.ubuntu.com/idea/6338/)

Actually you can run a dedicated server

[http://www.canonical.com/projects/landscape/dedicated-server](http://www.canonical.com/projects/landscape/dedicated-server)

It's not GPL'd but you can still buy a dedicated server version from Canonical.  Just so OP knows, landscape is not free and is a paid service from Canonical.  That's one of the ways they keep in business is funds made through that.

---

### Post by stefanadelbert on 2009-12-01
This is a shame. It seems like an awesome way to manage a network of Ubuntu machines, but unfortunately our company isn't big enough to warrant paying for this service and the network is getting to the point where it is a bit of a pain to have to ssh around and "apt-get update && apt-get upgrade".

I can understand that they need to be able to make money somehow and I wouldn't want Ubuntu and Canonical to crash because I think they are doing great things bringing Ubuntu, Linux and GPL to the fore.

A scaled down free version or an alternative would be good.

---

### Post by agrteknolan on 2009-12-03
> **stefanadelbert said:**
> This is a shame. It seems like an awesome way to manage a network of Ubuntu machines, but unfortunately our company isn't big enough to warrant paying for this service and the network is getting to the point where it is a bit of a pain to have to ssh around and "apt-get update && apt-get upgrade".

Cron job?

---

### Post by stefanadelbert on 2009-12-03
I suppose that I could put a cron-type solution together. All machines on the network would need to get hold of the latest cron schedule - another cron job. I would need a HDD monitoring and reporting setup for each machine.

Just would be nice to use Landscape - it is pretty feature packed, looks good(!) and is specifically designed to manage a network of Ubuntu machines.

---


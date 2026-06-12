---
title: "How To Create Ubuntu Server With Synaptic Server"
date: 2010-09-08
forum: Server Platforms
---

### Post by MES5464 on 2010-09-08
I live in a rural area and the only internet worth having is satellite. However, with satellite internet comes daily download limits. I have over seven computers in my household (all running Ubuntu) and keeping them ALL up to date is proving difficult. What I would like to do is setup a Ubuntu server with a copy of Synaptic server running on it. I then want to point all of the client machines to my local Synaptic server for updates. This way I can have a single machine update in the middle of the night, and then the client machines can update locally, instead of going out to the internet for updates.

Would someone point me to a tutorial that explains how to setup my own Synaptic server?

---

### Post by FuturePilot on 2010-09-08
Apt-cacher-ng is what you want. 

On the machine that will be your server install apt-cacher-ng

```
sudo apt-get install apt-cacher-ng
```

On the client machines create /etc/apt/apt.conf.d/02proxy with this inside

```
Acquire::http { Proxy "http://ip-of-server-goes-here:3142"; };
```

Don't forget to add that file on the server itself so anything it downloads gets added to the cache.

The way this works is that when a client downloads an update from the internet it's added to the cache. Then any other client that also needs that update will download it from the local server cache instead of from the internet.

You can get some stats and some maintenance options if you point a browser to [http://ip-of-server:3142/acng-report.html](http://ip-of-server:3142/acng-report.html)

---

### Post by MES5464 on 2010-09-08
Thank you FuturePilot!

I just love Linux. What a great computer experiance! I knew that the community would take care of me and provide just the right solution. Life is good with Linux!

---


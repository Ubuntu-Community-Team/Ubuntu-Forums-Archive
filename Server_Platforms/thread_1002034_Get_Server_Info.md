---
title: "Get Server Info"
date: 2008-12-04
forum: Server Platforms
---

### Post by Lemons on 2008-12-04
Well, I have a single and simple question. Can I get the status of a server on my windows desktop, and if so how? I love connecting to it remotely, but viewing the stats is a plus for me also (Know if it will need a new HDD, load, all that stuff). I would prefer a way to interact with it and samurize, but anyway would work.

~Kris

---

### Post by lykwydchykyn on 2008-12-04
Webmin has various modules to look at logs, SMART data, memory load, etc.

There are, of course, countless other approaches to this.  You could simply share out /var/log over http, for instance (though you'd want to heavily secure it).

---

### Post by hictio on 2008-12-04
If you decide to go with the Webmin route, this module is amazing:
[WebminStats](http://webminstats.sourceforge.net/)

This PHP script will give you a snapshot of what's going on on your system, no historical; but really easy to use, just needs PHP
[PHP Sys Info](http://phpsysinfo.sourceforge.net/)

Another option, if your server has the necessary dependencies installed, might be to export an app like [gkrellm](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html) to your (Linux) desktop via SSH.

---

### Post by CrucifiedEgo on 2008-12-04
check out munin.  it's a breeze to setup in it's default form, and gives great historical data.
```
sudo aptitude install munin munin-node
``` and it writes by default to /var/www/munin.  You can check out my personal server at [http://67.207.149.18/munin](http://67.207.149.18/munin)

If you look at the monthly HDD use graph, you'll see that it suddenly spiked.  turns out clamav was goign crazy and writing out new 37MB definition files in /var every 15 minutes.  I probably wouldn't have caught it until it took something down if not for munin.

---

### Post by Thirtysixway on 2008-12-04
I  like to use uprecords to see my uptimes.

---


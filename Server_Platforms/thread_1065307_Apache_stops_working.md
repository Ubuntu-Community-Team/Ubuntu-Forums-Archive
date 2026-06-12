---
title: "Apache stops working"
date: 2009-02-09
forum: Server Platforms
---

### Post by self-defence on 2009-02-09
Hi,

I've got an Ubuntu 6.06 server setup as a web server for a few webs sites.
It had been working fine for over a year and had a quite nice uptime.
But about two weeks ago I started having problems with it. Once every few days (4-6 days) the web server just shoppes working. And when I try to start it I keep getting an error and unless I reboot the whole machine it just woun't start working again. After the reboot it works fine for a few days again and then same story again. I've already tried updating the server but it happened again just a 1/2 an hour ago.
Anyone know how I could get this thing working or at least how to get to the root of the problem?

The error I keep getting when I try to start the server is
```
module proxy_http_module is already loaded, server not started (or something similar)
```
I have no idea what module and how it can be loaded or what does this mean anyway.

Thanks for the help.
Bye

---

### Post by beno1990 on 2009-02-09
If you don't need the said module, then do the following

Open a terminal on the server (or SSH into it, whatever you use for terminal access), then enter the following:

```

cd /etc/apache2/mods-enabled

```

Then type dir. Search for an entry similar to the name of the problem module. It'll probably show something like *proxy_http_module.load* and *proxy_http_module.conf*.

Then, assuming the above filenames are correct, type

```

sudo rm proxy_http_module.conf proxy_http_module.load

```

Let me know if this works for you.

---

### Post by self-defence on 2009-02-10
I'm not sure but I might need this module. Because I seem to remember in the httpd.conf file a redirect from the main web server to one that is on the internal lan.
If I delete this wount that render the redirection or forwarding non functioning?
I mean is there any way I could check some logs to determine why the module is loaded and why it wount load again?

Thanks for the help beno1990.

---

### Post by self-defence on 2009-02-15
Hi again,

well it happened again. Right on schedule around 6 to 7 days.
Same thing apache will not start because of this module. But I'm not sure if I can remove the module, since I think I might need it.

Any insights to a solution?

Thanks and bye.

---


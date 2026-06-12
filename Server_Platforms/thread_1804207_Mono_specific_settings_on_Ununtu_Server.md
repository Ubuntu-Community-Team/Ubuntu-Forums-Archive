---
title: "Mono specific settings on Ununtu Server"
date: 2011-07-14
forum: Server Platforms
---

### Post by KommerszUnicum on 2011-07-14
Hi Guys!

(Ubuntu Server 11.04)

I have a general problem about the basic configuration of the Mono. The new "structure" Ubuntu has for Apache and mod_mono configuration is not fully clear for me. I'd like to specify IOMap for BlogEngine ASP.Net application. In the apache directory I have the Blogengine specified as a "default" enabled site. But I see that the application pools have to be specified in the /etc/mono-server2 directory.

The application pool data on that directory can be manipulated with mono-server2-admin script. But I can't find the IOmap parameter on the script to specify it for my application.

I haven't found clear information about the IOMap usage on Ubuntu. The one specifed in the mono-project website is so general. 

Could you please help me find out the location where should I set IOMap for my Blog?

Thank you!

---

### Post by directhex on 2011-07-14
File a bug in Debian against mod-mono and I'll take a look.

---

### Post by KommerszUnicum on 2011-07-18
> **directhex said:**
> File a bug in Debian against mod-mono and I'll take a look.
Thank you for the answer.

Can I report the exact error I've got with my BlogEngine.NET application on launchpad for you? I've narrowed down the problem to a mod_mono/apache specific issue.

---

### Post by directhex on 2011-07-20
anything *requiring* IOMAP is an upstream bug. an inability to set it via mono-server2-admin is a bug i'm interested in.

---

### Post by KommerszUnicum on 2011-07-25
Thank you for your help **directhex**!

I've filed a bug in the ubuntu launchpad (Bug #815939). We can continue there if you have further questions.

Thank you!

---


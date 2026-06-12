---
title: "Essbase install on Ubuntu 9.10 AMD 64-bit server"
date: 2009-12-27
forum: Server Platforms
---

### Post by glbeach on 2009-12-27
Although I have "played" with Ubuntu for a couple of years, I am now learning how little I know.  I am attempting to convince a company to support running Oracle's Essbase on Ubuntu 9.10.  They have asked me to set up a pilot to demonstrate how it might work for them.  My goal is to convince them they have no need to continue supporting a proprietary system, i.e., Microsoft and rather should use Ubuntu both in the back office and on the desktop.

I am looking for guidance on setting up Essbase 11.1.1.1.3 on the Ubuntu Server - what types of underlying permissions, directories, groups, etc. need to be set up for the application to work.  This is NOT in a virtual environment, rather on a physical hard drive on a "department-scale" server, i.e, 25 or fewer users - though the pilot will only be 4 or 5 users.

Any guidance will be appreciated.

Regards,
G. Beach

---

### Post by Cheesemill on 2009-12-27
If I were you I wouldn't use Ubuntu as Oracle haven't certified it for use with the software, you're bound to run into problems. The only Linux OS's that are certified are either Oracle Enterprise Linux or Red Hat, both of which will cost you.

You could try CentOS which is compiled from the Red Hat source with any copyright infringing graphics/logos etc removed so it can be had for free.

If you do decide to try with Ubuntu then either go for 8.04 or wait until 10.04, on mission critical systems like what you're talking about the last thing you want is to have to upgrade every 18 months, that's the whole point of LTS releases.

I don't think you'll have much luck trying to convince a company to support Essbase on Ubuntu when even Oracle won't support it.

---


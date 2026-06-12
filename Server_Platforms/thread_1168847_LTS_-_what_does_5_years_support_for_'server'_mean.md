---
title: "LTS - what does 5 years support for 'server' mean?"
date: 2009-05-24
forum: Server Platforms
---

### Post by Rich99 on 2009-05-24
I have a dapper server, but I've also added other packages over the years, such as gnome etc.  Dapper is EOL for desktop this june, but EOL for the server is another 2 years away.  What does that actually mean?  Does it mean that the security team will only update the select packages that ship on the server cd?  Or does it mean that any packages that are server related will be kept updated - for example if I used a different ftp server to that that came on the server cd?  What about packages like xinetd - this wasn't on the server install originally, but it's hardly a desktop item....

I am the only person with shell access to the server, other people only interact with the machine through the services it provides (apache, exim, samba etc), so does that mean even though I have a desktop environment installed that I am still secure for another 2 years?

---

### Post by Vegan on 2009-05-24
The LTS versions of Ubunto are looked after for 5 years which is what you are probably looking at.

I use the more recent builds as I run a basic LAMP system.

---

### Post by ugm6hr on 2009-05-25
From [https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

> What (packages/repositories) are maintained (supported)?

Not all packages in the main repository are maintained (supported) equally in an LTS release: Server packages are maintained for 5 years, and defined as all packages that are part of the the seeds "server-ship" or "supported-common" are supported for five years.

For regular releases, all the packages in main are maintained for 18 month.

Packages in all other repositories (universe, multiverse, etc) are not officially maintained but may be getting some support from the community or an ISV. Be aware that apt does not check if a package is maintained (supported) or not, you have to do that on your own.

For more info: 

Unfortunately, I can't find [Dapper seed lists]("http://people.ubuntu.com/~ubuntu-archive/germinate-output/ubuntu.dapper/") that match those names.  However, it does give further links re: the seeds, so may help you identify which seeds are going to receive ongoing support.

From: [https://wiki.ubuntu.com/SeedManagement](https://wiki.ubuntu.com/SeedManagement)
> Ubuntu Server LTS:

    * Hardware compatibility updates (until next LTS)
    * Security updates and select bug fixes (5 years)
    * This is defined as the union of the server-ship and supported-server seeds 
The supported-server exists, but server-ship does not.

However, the most useful link I have found is the [maintenance check script]("https://launchpad.net/ubuntu-maintenance-check"), which appears to check your system and tell you which packages are supported until when.  Looks like this is currently the latest version: [http://bazaar.launchpad.net/~nijaba/ubuntu-maintenance-check/trunk/annotate/head%3A/maintenance-check](http://bazaar.launchpad.net/~nijaba/ubuntu-maintenance-check/trunk/annotate/head%3A/maintenance-check)

Hope that helps!

---

### Post by Rich99 on 2009-05-25
> **ugm6hr said:**
> From [https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

However, the most useful link I have found is the [maintenance check script]("https://launchpad.net/ubuntu-maintenance-check"), which appears to check your system and tell you which packages are supported until when.  Looks like this is currently the latest version: [http://bazaar.launchpad.net/~nijaba/ubuntu-maintenance-check/trunk/annotate/head%3A/maintenance-check](http://bazaar.launchpad.net/~nijaba/ubuntu-maintenance-check/trunk/annotate/head%3A/maintenance-check)

Hope that helps!

That's all really helpful, thanks for that. I spent some time googling LTS & reading up the dapper & hardy release pages, but nothing ever linked to those pages.  I'll get reading them now, they sound just what I was after :)

---

### Post by Rich99 on 2009-05-25
I couldn't find those metapackages the faq mentions, but that script did everything I needed.  Thanks!

---


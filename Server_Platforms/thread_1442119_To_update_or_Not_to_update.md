---
title: "To update or Not to update?"
date: 2010-03-29
forum: Server Platforms
---

### Post by dudemanbubba on 2010-03-29
I have several file servers in our offices and I am relatively new to Ubuntu / Linux.  I get notices that there are updates for the server software from time to time.  Is it typical to update everything when available or should I follow "If it ain't broke, don't fix it..." mentality?

I would hate for everything to be working fine and then have an update throw me a curve.

Thanks!

---

### Post by r_s on 2010-03-29
you should go for updates as they include latest kernels, latest security measures and also the latest software, your files would not be affected by updates.

---

### Post by n0dix on 2010-03-29
If you don't have the experience to solved the problems that may be present in the update i recommend you not doing.

---

### Post by dudemanbubba on 2010-03-29
Are there generally problems associated with updates?  If so, are they usually documented so I can review prior to me making the update?

---

### Post by n0dix on 2010-03-29
Generally there are few problems with update but depends on you to solved them: look in the forum, in internet, bug reports, etc. You have to be more careful because you maintain a server not a personal computer.

---

### Post by conradin on 2010-03-29
Every OS runs risks when updating.

---

### Post by snowpine on 2010-03-29
Hi Dudeman, first question: Which Ubuntu release are you currently running? Hopefully 8.04 or newer; if you are running 7.10 or older, you DEFINITELY want to upgrade to a newer release, because older releases are no longer supported by Canonical.

Assuming you are running 8.04 (or newer), your release is supported. This means you may install updates if you wish. These updates include only security patches and bug fixes; Ubuntu will never give you a major "jump" to a new kernel or package version within a release (that's accomplished by upgrading to a new release).

This command is the safest in my opinion:

```
sudo apt-get update && sudo apt-get upgrade
```

apt-get upgrade will NOT update your kernel or remove any packages.

This  command is a "deeper" update:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

apt-get dist-upgrade will upgrade your kernel and may also swap a few of your libraries out for newer versions. dist-upgrade may be more dangerous if you're not sure what you're doing.

The answer to your question likely depends upon your security needs and the purpose of these servers. If the servers are open to the outside world or contain sensitive data, you absolutely should upgrade periodically to fix any bugs or security vulnerabilities.

---

### Post by dudemanbubba on 2010-03-29
I used 8.04 to setup the servers since it was the current LTS.  Also, I use webmin for a lot of things.  At the Webmin start screen it usually tells me which packages have updates available and I have the option of updating them through Webmin.

---

### Post by snowpine on 2010-03-29
> **dudemanbubba said:**
> I used 8.04 to setup the servers since it was the current LTS.  Also, I use webmin for a lot of things.  At the Webmin start screen it usually tells me which packages have updates available and I have the option of updating them through Webmin.

Good choice... 8.04 server will be fully supported through 2013. :)

---

### Post by HermanAB on 2010-03-30
As servers go, I recommend a policy of 'don't fix it if it ain't broke'.  I almost never update my servers - I install them from scratch every 3 years, secure them and lock them down. After that I leave them alone till something breaks.  The result is pretty much 100% uptime - barring lightning strikes taking out the UPS.

---

### Post by jrusso2 on 2010-03-30
Yea if they are production server don't update unless you have identical test server to test on first.

---

### Post by slakkie on 2010-03-30
> **jrusso2 said:**
> Yea if they are production server don't update unless you have identical test server to test on first.

+1

And in a production enviroment you always, always, always, have a backup policy. So going back is a possibility.

---


---
title: "Limit Monthly Bandwidth on Apache2 vHost"
date: 2011-09-30
forum: Server Platforms
---

### Post by tehxnite on 2011-09-30
Hi I'v been searching the internet for quite a while, looking for a module that would limit bandwidth on websites hosted with Apache on a per-vhost basis.
Example:
LinuxFire.net > Unlimited Bandwidth Per Month
SiteA.com > 5GB/mo
SiteB.com > 20GB/mo

And then display a webpage telling visitors the site has used up it's monthly bandwidth when its all used up.

I'v seen this done with cpanel hosted sites, but I cannot afford nor do I want to use cpanel.
Is there a module or at least some sort of work around for this result?

---

### Post by Dangertux on 2011-09-30
Have you checked out mod_bw?

---

### Post by tehxnite on 2011-09-30
Isn't that the one that is part of cpanel?
I couldn't find that module by itself, however if you know where I can grab a copy of it I would LOVE to compile it and try it out.

---

### Post by Dangertux on 2011-09-30
You should be able to install from repos via

```

sudo apt-get install libapache2-mod-bw

```

If not you can get the source here : [http://packages.debian.org/source/lenny/libapache2-mod-bw](http://packages.debian.org/source/lenny/libapache2-mod-bw)

Hope that helps

---

### Post by tehxnite on 2011-09-30
Looks like that module is just for limiting the connection bandwidth. What I want is to give each vhost an individual monthly transfer quota.
For example SiteA.com would have a total transfer of 10GB/mo and after that anyone visiting would get an error page saying that the site has been shut down until next month or until the owner pays for more bandwidth... That sort of thing.

---

### Post by Dangertux on 2011-09-30
You can still do it that way with mod_bw you just have to configure it in each vhost ie: each vhost has a different  configuration for mod_bw, if that makes sense. 

for example

```

<Virtualhost *>
      BandwidthModule On
      ForceBandWidthModule On
      Bandwidth all 1024000
      MinBandwidth all 50000
      LargeFileLimit * 500 50000
      Servername www.example.com
    </Virtualhost>

```

---


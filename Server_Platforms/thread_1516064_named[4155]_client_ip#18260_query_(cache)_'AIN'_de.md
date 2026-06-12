---
title: "named[4155]: client ip#18260: query (cache) '/A/IN' denied"
date: 2010-06-23
forum: Server Platforms
---

### Post by Gorlist on 2010-06-23
Hi! right noticed in my logs last few days allot of query cache errors. Confused on the cause and slightly concerned. Ubuntu 8.04 and plesk 9.5. 

```

Jun 22 11:52:34 sv1 named[4155]: client 81.37.117.175#18168: query (cache) 'movieslinger.com/MX/IN' denied
Jun 22 11:52:34 sv1 named[4155]: client 81.37.117.175#18168: query (cache) 'design-gateway.com/MX/IN' denied
Jun 22 11:52:34 sv1 named[4155]: client 81.37.117.175#18168: query (cache) 'onlinelabs.com/MX/IN' denied
Jun 22 11:52:35 sv1 named[4155]: client 81.37.117.175#18169: query (cache) 'ns1.telecomottawa.com/A/IN' denied
Jun 22 11:52:35 sv1 named[4155]: client 81.37.117.175#18169: query (cache) 'ns2.evanzo.com/A/IN' denied
Jun 22 11:52:35 sv1 named[4155]: client 81.37.117.175#18169: query (cache) 'sdnccg.com/MX/IN' denied
Jun 22 11:52:36 sv1 named[4155]: client 81.37.117.175#18186: query (cache) 'idrink.com/MX/IN' denied
Jun 22 11:52:36 sv1 named[4155]: client 81.37.117.175#18186: query (cache) 'ns2.techiemedia.net/A/IN' denied
Jun 22 11:52:39 sv1 named[4155]: client 81.37.117.175#18222: query (cache) 'mescosteel.com/MX/IN' denied
Jun 22 11:52:40 sv1 named[4155]: client 81.37.117.175#18235: query (cache) 'animalsynergy.com/MX/IN' denied

```

Could this be a compromised bind? I killed the named service (4155) for a short while but it takes a number of sites (not all) offline - just wondering if anyone has some advice or suggested whats happening?

Best Regards,

---


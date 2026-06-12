---
title: "USC locks right up"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-17
tried to download/install and got lockup.

```

ventrical@ventrical-OptiPlex-755:~$ uname -a
Linux ventrical-OptiPlex-755 4.3.0-2-generic #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-OptiPlex-755:~$ 



```

---

### Post by flocculant on 2015-12-17
usc is pretry much borken afaik - pretty sure it'll be why 64 built and 32bit didn't

---

### Post by MikeMecanic on 2015-12-17
I see that you only have one choice to download (19).  My search returns 3 choices (Restricted Codecs) and I choose the one that have 395 installations. The installation went fine.  Synaptic shows Version 64.  Maybe you should try Kernel 4.4 ?

---

### Post by ventrical on 2015-12-18
> **MikeMecanic said:**
> I see that you only have one choice to download (19).  My search returns 3 choices (Restricted Codecs) and I choose the one that have 395 installations. The installation went fine.  Synaptic shows Version 64.  Maybe you should try Kernel 4.4 ?

The topic is Ubuntu Software Center. Not kernel 4.4 or synaptic package manager. Thanks for your suggests.
Regards..

---

### Post by kansasnoob on 2015-12-18
Isn't USC being dumped in favor of GNOME Software Center? I never use either - color me old skool, I learned Synaptic clear back in the Freespire days to avoid their CLR app.

---

### Post by grahammechanical on 2015-12-18
Yes. At some point during this development cycle USC should be replaced by Gnome Software. And I think that it is all to do with something called AppStream.

[http://blog.tenstral.net/2015/12/appstreamdep-11-fully-supported-in-debian-now.html](http://blog.tenstral.net/2015/12/appstreamdep-11-fully-supported-in-debian-now.html)

Gnome Software is compatible with AppStream. I do not think that USC is compatible. I also think that if Ubuntu Personal (Mir+Snappy core + Unity8) becomes a usable alternative to traditional Ubuntu then USC would be replaced by a snap app store. So, no point is making USC compatible with AppStream. Which would have to happen if Ubuntu is to keep place with Debian.

> And another item from the good news department: It&#8217;s highly likely that  Ubuntu will follow Debian in AppStream/DEP-11 support with the upcoming  Xenial release!

Yes, by using Gnome Software instead of USC. An easy fix.

Regards

---

### Post by ventrical on 2015-12-18
> **kansasnoob said:**
> Isn't USC being dumped in favor of GNOME Software Center? I never use either - color me old skool, I learned Synaptic clear back in the Freespire days to avoid their CLR app.

Of course I use synaptic also  but I was just testing USC (which we are supposed to do in testing? )

@grahammechanical...

Ahh yes . Thanks 4 new news.

Regards..

---

### Post by kansasnoob on 2015-12-21
> **ventrical said:**
> Of course I use synaptic also  but I was just testing USC (which we are supposed to do in testing? )

@grahammechanical...

Ahh yes . Thanks 4 new news.

Regards..

Yep, I understand testing. I never use the release upgrade process in the real world but i still test release-upgrader* just to check for obvious big, bad bugs. I've just been too lazy to test USC.

---

### Post by ventrical on 2015-12-21
> **kansasnoob said:**
> . I've just been too lazy to test USC.

+1 :)

What was I thinking ? :)

Regards..

---


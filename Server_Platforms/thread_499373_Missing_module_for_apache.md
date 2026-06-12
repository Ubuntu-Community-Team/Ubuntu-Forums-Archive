---
title: "Missing module for apache"
date: 2007-07-12
forum: Server Platforms
---

### Post by camellito on 2007-07-12
Hi, some knows where is the mod_security (modesurity.org) in Feisty? it is not in the repos... sorry for my bad english, ty.

---

### Post by Footballkid4 on 2007-07-12
Weird that it doesn't show up in the repos.  I did an apt-cache search for libapache2-mod and it wasn't anywhere in the list.

Anyways, found it here:
[http://packages.ubuntu.com/warty/web/libapache2-mod-security](http://packages.ubuntu.com/warty/web/libapache2-mod-security)

---

### Post by camellito on 2007-07-12
Thanks Footballkid4!, one more thing ¿how I can load it to the synaptic?

---

### Post by Footballkid4 on 2007-07-12
Download the package from that site that supports your architecture.  Once installed, it should load itself into synaptic package manager.  It may not, however, because like apt-get, it is repo based, and as discovered, that package isn't in the repos.  That doesn't mean you can't remove it though.  You can always use the dpkg command for installed packages.

---

### Post by camellito on 2007-07-12
But that package is for warty, not for feisty. ¿Will work anyway? sorry but i am very newbie :(

---

### Post by Footballkid4 on 2007-07-12
Didn't even pay attention to that actually.  Honestly, I don't see why it wouldn't work, unles it's going to complain about your kernel version.  I checked the Feisty list and libapache2-mod-security isn't on there.  Apparently it was removed.

---

### Post by camellito on 2007-07-12
There are no doubts that I am lost :(

---

### Post by Footballkid4 on 2007-07-12
> **camellito said:**
> There are no doubts that I am lost :(

Looks like support for libapache2-mod-security was removed in Feisty.  You might have to consider downgrading to Dapper or something on the lower end.  Other than that, you have to deal without the security module or just make sure you know what you're doing before playing with scripts.  The chances that you'll run into problems with apache security if you're always paying attention is slim.

---

### Post by riotact on 2007-07-19
I'm not real keen to downgrade (especially since I just upgraded to Feisty) or download custom apps - I'd rather just apt-get them... Isn't that why we all love Ubuntu?

I have noticed the package libapache2-mod-ifier in the list of Feisty packages. Is this perhaps a replacement for mod-security?

---


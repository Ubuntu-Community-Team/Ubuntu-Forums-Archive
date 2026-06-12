---
title: "Ubuntu One folder syncing with other Ubuntu based distros?"
date: 2010-07-29
forum: Ubuntu One (CLOSED)
---

### Post by casbahdk on 2010-07-29
I use Ubuntu Lucid on my desktop box, and would like to seed the contents of some folders to my Zepto Znote V11a netbook and to my IBM laptop, both of which are running Peppermint Ice. Is this possible and how do I go about getting this to function?

---

### Post by duanedesign on 2010-07-29
Peppermint Ice uses OpenBox?

You will need to install Ubuntu One and all its dependencies. Even then there arre no gurantees as Ubuntu One has never been tested on that distro.

I would look at what others have done to install Ubuntu One on Kubuntu and Xubuntu. You would start with:

```
 sudo apt-get install ubuntuone-client python-ubuntuone-storage* ubuntuone-client-gnome
```

---

### Post by casbahdk on 2010-07-29
> **duanedesign said:**
> Peppermint Ice uses OpenBox?

It is based on Lubuntu and uses LXDE and OpenBox.

---

### Post by casbahdk on 2010-07-30
Cheers duanedesign. Your solution works without problems for seeding files and folders. I haven't tried installing Tomboy or Rhythmbox, as I want to keep my Peppermint Ice system lean and mean.

Thanks again

---


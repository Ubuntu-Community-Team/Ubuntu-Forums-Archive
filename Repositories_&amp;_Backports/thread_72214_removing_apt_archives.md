---
title: "removing apt archives?"
date: 2005-10-05
forum: Repositories &amp; Backports
---

### Post by dskloet on 2005-10-05
Hi,

My directory /var/cache/apt/archives is taking a lot of space and I wondered whether those files are still needed. Am I correct in thinking those files have allready done their work when I apt-get-installed them? Can I remove those files safely? Is there any reason not to?

thanks,
David

---

### Post by DJ_Max on 2005-10-05
It's there for when you uninstall something and want to install it again without downloading everything again. 

```
sudo apt-get clean
```
You can also do
```
sudo apt-get autoclean
```

---

### Post by dskloet on 2005-10-06
Thanks!

I guess I should have read the man page for apt...

---

### Post by bugi on 2005-10-06
You can also do it manually in Synaptic (settings-preferences-files-clear cache)
:-)

---

### Post by DJ_Max on 2005-10-06
Yeah, but using the command line makes you feel smart. ;)

---


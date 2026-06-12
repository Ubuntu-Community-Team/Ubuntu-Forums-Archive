---
title: "How do i change wine's drive directories?"
date: 2009-02-15
forum: Wine
---

### Post by MasterNetra on 2009-02-15
I was wondering how do i unlock winecfg's setting for changing where its looking for its fake drive C. I want to setup multiple accounts to share the same wine directory (in a effort to safe on a lot of space) but wine won't let you change by default. How do i get it to let me or is there some way to do it manuelly?

---

### Post by u497 on 2009-02-15
by default its c drive is at /root/.wine/z_xx or something like that. im deleting this folder when i get felt bad about it.
so it makes wine completely~ safe i guess.
when you run wine it will create those folders again.
the folders starting with '.' are hidden on linux.
so you hawe to set showhidden folders option on on kde. or whatewer browser you are using.
so you can see wine virtual drives and folders.:lolflag:

---

### Post by overlord.gaurav on 2009-02-15
From what I understand, [this]("http://ubuntuforums.org/showthread.php?p=6720520") is what you're looking for.

---

### Post by 0bso on 2009-02-15
> **overlord.gaurav said:**
> From what I understand, [this]("http://ubuntuforums.org/showthread.php?p=6720520") is what you're looking for.

This (using sym links) is how I set mine up that way. After you get the first one set up (as outlined in the third post) repeat the last 2 commands for the additional users so the sym links on all the acounts point to the same target folder.

Should look something like this:
```

mkdir /mnt/shared/wineStuff
rm -rf /home/user/.wine
ln -s /mnt/shared/wineStuff /home/user/.wine
rm -rf /home/user2/.wine
ln -s /mnt/shared/wineStuff /home/user2/.wine
rm -rf /home/user3/.wine
ln -s /mnt/shared/wineStuff /home/user3/.wine

```

---


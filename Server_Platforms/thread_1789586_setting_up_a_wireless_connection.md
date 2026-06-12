---
title: "setting up a wireless connection"
date: 2011-06-24
forum: Server Platforms
---

### Post by Otiosedodge on 2011-06-24
Hi All,

I'm trying to set up a wireless connection on 11.04.

I enter the following command:

```
iwconfig wlan0 essid "myESSID"
```

and receive the following message:

```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; operation not permitted.

```

Any ideas?

Thanks

---

### Post by volkswagner on 2011-06-24
Operation not permitted... This is because you need to have root priv, or run sudo.

Check out [this post]("http://ubuntuforums.org/showpost.php?p=10700392&postcount=2") for some more help on wireless via command line.

```
sudo iwconfig wlan0 essid "myESSID"
```

---

### Post by Otiosedodge on 2011-06-24
Thanks, that did it. I went to the post you suggested, and ran into some problems. I'll detail them there.

---


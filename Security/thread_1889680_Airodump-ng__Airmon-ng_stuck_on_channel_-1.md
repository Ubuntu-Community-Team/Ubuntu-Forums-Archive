---
title: "Airodump-ng / Airmon-ng stuck on channel -1"
date: 2011-12-01
forum: Security
---

### Post by CorySCline on 2011-12-01
I have seen the patches for this problem located at [http://ubuntuforums.org/archive/index.php/t-1628520.html](http://ubuntuforums.org/archive/index.php/t-1628520.html)

I have followed them, but I end up with:
```
cory@cory-FQ565AA-ABA-a6700f:~/compat-wireless-2010-10-16$ make
[: 1: -gt: argument expected
test: 1: -ge: unexpected operator
make -C /lib/modules/3.0.0-13-generic/build M=/home/cory/compat-wireless-2010-10-16 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  CC [M]  /home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.o
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c: In function ‘ath_wakeup_ar3k’:
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:55:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:66:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: warning: passing argument 2 of ‘tty->driver->ops->tiocmset’ makes integer from pointer without a cast [enabled by default]
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: note: expected ‘unsigned int’ but argument is of type ‘void *’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: error: too many arguments to function ‘tty->driver->ops->tiocmset’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:71:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: warning: passing argument 2 of ‘tty->driver->ops->tiocmset’ makes integer from pointer without a cast [enabled by default]
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: note: expected ‘unsigned int’ but argument is of type ‘void *’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: error: too many arguments to function ‘tty->driver->ops->tiocmset’
/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:75:2: error: too many arguments to function ‘tty->driver->ops->tiocmget’
make[3]: *** [/home/cory/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.o] Error 1
make[2]: *** [/home/cory/compat-wireless-2010-10-16/drivers/bluetooth] Error 2
make[1]: *** [_module_/home/cory/compat-wireless-2010-10-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make: *** [modules] Error 2

```

Any ideas?

---

### Post by emiller12345 on 2011-12-01
you need to open up the chan.c file in your linux-wireless
```
$ gedit /home/cory/compat-wireless-2010-10-16/net/wireless/chan.c
```
make the + changes.. 
```
&#65279;--- a/net/wireless/chan.c 
+++ b/net/wireless/chan.c 
@@ -49,9 +49,12 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev, 
 { 
     struct ieee80211_channel *chan; 
     int result; 
+    struct wireless_dev *mon_dev = NULL; 
  
-    if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) 
+    if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) { 
+        mon_dev = wdev; 
         wdev = NULL; 
+    } 
  
     if (wdev) { 
         ASSERT_WDEV_LOCK(wdev); 
@@ -76,5 +79,8 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev, 
     if (wdev) 
         wdev->channel = chan; 
  
+    if (mon_dev) 
+        mon_dev->channel = chan; 
+ 
     return 0; 
 }
```
and then
```
$ make clean && make && sudo make install
```

---


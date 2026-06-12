---
title: "Kino issue (dv1394)"
date: 2009-07-30
forum: Ubuntu Studio
---

### Post by niiize on 2009-07-30
When running Kino it states a warning saying: "dv1394 module is not loaded or permission denied for /dev/1394/0"

Now.. I can see that dv1394 module is probed with the lsmod command, but there is no dv1394 file in the /dev/ directory. When I do a seach for it, it apphears to be at /sys/module/. Why is that?


Thnx

---

### Post by cotcot on 2009-07-30
I hope [[COLOR="Red"]this[/COLOR]]("http://ubuntufriends.wordpress.com/2008/06/25/kino-and-dv-1394-in-ubuntu-hardy/") can help you.

---

### Post by Dragonbite on 2009-07-30
Plug in your firewire camcorder and run
```
chmod 777 /dev/raw1394
```

That's what has worked for me multiple time.

---

### Post by niiize on 2009-07-30
To give raw1394 777 permission did not seem to work. The warning is not there anymore, more than when I first start up Kino, then it shows but not after I have klicked the recording tab once more...? It is a logitech webcam I am trying to capture with. Also if I look in IEEE 1394 tab there is no component showing. Also, thank you cotcot for the link, it was excellent. Though I've read somewhere some versions in Kino rather use dv1394 than raw1394.. What is the differens

---


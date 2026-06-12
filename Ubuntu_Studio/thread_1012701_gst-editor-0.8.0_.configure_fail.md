---
title: "gst-editor-0.8.0 ./configure fail"
date: 2008-12-16
forum: Ubuntu Studio
---

### Post by mapellil on 2008-12-16
Hello all,
i'm a Ubuntu beginner tying to install gst-editor-0.8.0 while running ./configure i got back the below error:

checking for gstreamer-0.10 >= 0.10.0... yes
checking GST_CFLAGS... -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2  
checking GST_LIBS... -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0  
checking for libgnomeui-2.0 libglade-2.0... configure: error: GNOME 2.0 required but not found

i've tryied to install libgnomeui-2.0 libglade-2.0 GNOME 2.0 through Synaptic but installation fails. C
Could someone help me? thanks in adv:confused:

---

### Post by ibutho on 2008-12-16
Hi and welcome to the forum.

You need to install libgnome2-dev in order to resolve that problem.

---

### Post by mapellil on 2008-12-16
Hi, thanks for the help but i've
tryied to install libgnome2-dev using synaptic but download fails giving msg:

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

if i say Y, it gives:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.4.1-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.4.1-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls-dev_2.4.1-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls-dev_2.4.1-1ubuntu0.1_i386.deb)
  404 Not Found


any helps? thanks! :confused:

---

### Post by ibutho on 2008-12-16
Try the following. Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install libgnome2-dev
```

---

### Post by mapellil on 2008-12-16
Hi Thanks,
unfortunately giving "sudo apt-get update" give me back a lot of err msgs like:

Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'it.archive.ubuntu.com'
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'it.archive.ubuntu.com'

there could be some prblm on my company proxy/firewall?:frown:
thanks

---

### Post by ibutho on 2008-12-16
Is your internet connection working properly? Have you tried changing the mirrors to point to a different country near you?

---

### Post by mapellil on 2008-12-17
Thanks you are right! was the mirror  :p

---


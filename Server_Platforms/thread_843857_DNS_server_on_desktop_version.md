---
title: "DNS server on desktop version?"
date: 2008-06-28
forum: Server Platforms
---

### Post by boberic on 2008-06-28
im using ubuntu desktop. ive tried the server edition and it only proved to frustrate, and confuse me. im wondering if it is possible to setup a FTP and a DNS server in ubuntu desktop edition, and if so how? can some one point me to a tutorial or just tell me how.

thanks.:confused:

---

### Post by HalPomeranz on 2008-06-28
Well there's nothing that prevents you from installing the packages for BIND (DNS) and vsftpd from the repositories:

```

sudo apt-get install bind9 vsftpd

```

From there you'll need to rustle up some tutorials on configuring this software.  Perhaps somebody else can chime in on the thread with their favorite HOW-TOs.

---

### Post by ibutho on 2008-06-28
For setting app server apps, look at [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/) .

---

### Post by windependence on 2008-06-28
You can certainly set up one on the desktop version.

May I ask why you want to do this? Unless you have a very large amount of computers on your network, you don't really need one and if that's the case you should be using the server version anyway.

-Tim

---

### Post by ikki_72 on 2008-08-19
> **windependence said:**
> You can certainly set up one on the desktop version.

May I ask why you want to do this? Unless you have a very large amount of computers on your network, you don't really need one and if that's the case you should be using the server version anyway.

-Tim
maybe he simply don't have enough machine to do that or don't want to bother another installation. Like me. Ubuntu server is nice and easy, but you won't learn much from it than setting it up from scratch (installing the needed apps)

---


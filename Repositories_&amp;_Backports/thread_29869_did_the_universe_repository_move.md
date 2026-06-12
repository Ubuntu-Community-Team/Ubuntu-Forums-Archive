---
title: "did the universe repository move?"
date: 2005-04-26
forum: Repositories &amp; Backports
---

### Post by deuce868 on 2005-04-26
I am not able to connect to the universe repositories for Hoary I've been using for quite some time now. 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

Anyone know if they moved or just are down this morning?

Thanks

---

### Post by Hinko on 2005-04-26
I haven't tried, but I'm quite convinced they didn't move them.

---

### Post by rhipwell on 2005-04-30
I´ve been experiancing the same issue. 

I tried to connect to us.archive.ubuntu.com via firefox and got a message stating that the document contains no data. 
I have been having this issue off and on for some time now and have to figure it out. 

I´ve also gone as far as trying init bounces ( init 1; init 5 ), reboots and modifying my sources.list file to show us.archive.ubunutlinux.org instead of us.archive.ubuntu.com ( which didn´t work by the way )

If anyone has any suggestions at all, I would be more then happy to try them out. Thanks alot

---

### Post by Laterix on 2005-04-30
I have some problem. Yesterday it worked just fine. Hopefully it's just temporarily down. I just installed new Hoary Hedgehog and I really need these resporities.

---

### Post by momo66 on 2005-04-30
Im getting the same message

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe libsmjs1 1.5rc6a-1
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out

---

### Post by AgenT on 2005-04-30
[QUOTE=rhipwell]I´ve been experiancing the same issue. 

I tried to connect to us.archive.ubuntu.com via firefox and got a message stating that the document contains no data. 
I have been having this issue off and on for some time now and have to figure it out. 

I´ve also gone as far as trying init bounces ( init 1; init 5 ), reboots and modifying my sources.list file to show us.archive.ubunutlinux.org instead of us.archive.ubuntu.com ( which didn´t work by the way )

If anyone has any suggestions at all, I would be more then happy to try them out. Thanks alot[/QUOTE]

Works fine in Firefox here. And here is the ping result:```

ping -c 1 us.archive.ubuntu.com
PING us.archive.ubuntu.com (216.165.129.13:cool: 56(84) bytes of data.
64 bytes from us.archive.ubuntu.com 
(216.165.129.13:cool: icmp_seq=1 ttl=57 time=37.0 ms

--- us.archive.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 37.054/37.054/37.054/0.000 ms 

```

---

### Post by jodef on 2005-04-30
There may have been a problem earlier on today, when I tried earlier this morning I had some problems but about half an hour later I was able to access it.

---


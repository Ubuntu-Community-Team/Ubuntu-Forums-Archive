---
title: "&quot;synchronize to ubuntu one&quot; crashes nautilus"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by afonteijn on 2010-05-01
I'm running Ubuntu 10.04 64 bit and every time I try to add a folder to syncronize with ubuntu one in nautilus, it crashes nautilus. I can then start nautilus up again and do the same thing, and again it will crash.

Any thoughts how to solve this?

---

### Post by afonteijn on 2010-05-02
Somehow the problem solved itself. After several hours that directory was synchronized with ubuntu one (even though in nautilus it initially stated that it wasn't a synchronized directory). 

I wonder if there is a way to clearly see what the ubuntu one service is doing on my pc. Right now it just seems that nothing is happening most of the time, and then suddenly synchronization has happened.

Anyway, problem solved.

---

### Post by joshuahoover on 2010-05-03
> **afonteijn said:**
> Somehow the problem solved itself. After several hours that directory was synchronized with ubuntu one (even though in nautilus it initially stated that it wasn't a synchronized directory). 

I wonder if there is a way to clearly see what the ubuntu one service is doing on my pc. Right now it just seems that nothing is happening most of the time, and then suddenly synchronization has happened.

Anyway, problem solved.

Thanks for following up on this! It's always much appreciated by those of us on the forums. :)

Not to be a broken record here on the forums today, but it's important to note that we've been experiencing large spikes in new users and overall use with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. We'll keep everyone updated on our progress in the following spots:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Thanks!

Joshua

---

### Post by dojo23 on 2012-01-06
Same problem here on 10.04 32 bits. Except didn't solve alone, like you.

Also when I get to the ubuntu one page, I don't get the "add this computer" message. Could be related?

I will keep trying and let u know if I get anything solved.

---

### Post by Erik1984 on 2012-01-07
This sometimes happens to me as well. Also 10.04 32-bit. It happened today. However there doesn't seem to be a clear pattern and when I restarted nautilus the problem was gone.

In case it helps: two lines appear in kern.log that seems to correspond with the Nautilius crash:

```

[ 6271.855491] __ratelimit: 15 callbacks suppressed
[ 6271.855501] nautilus[1774]: segfault at 402c001f ip b7005b41 sp bfaae180 error 4 in libglib-2.0.so.0.2400.1[b6fd9000+c8000]

```

---


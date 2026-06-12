---
title: "Safe to write to NTFS drive?"
date: 2009-05-10
forum: Security
---

### Post by Kareeser on 2009-05-10
I read somewhere on the web (yes... this starts off good), that it's indivisible to write to an NTFS file system on Linux, because the specification hasn't been released.

However, the post was in 2005, so I'm not sure whether that information is still relevant.

Is installing "ntfsprogs" enough?

From a security standpoint, if I were troubleshooting a Windows drive, would it be okay if I did the bulk of my work in Linux? I don't exactly trust Windows in safe mode... heh.

---

### Post by cariboo on 2009-05-10
This really isn't a security question, but it is safe to read/write to an NTFS partition. the ntfs-3g driver is built in to the kernel. I don't have any ntfs partitions any more, but has been safe to write to it for about 3 years.

---

### Post by HermanAB on 2009-05-11
It is perfectly safe.

It is so good, that one can share encrypted NTFS USB disk drives between Linux and Windows.  [http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by Hamid2547 on 2011-01-31
i still wonder is it completely safe to write on ntfs drive?,or i can do this but it not recommended,and is there any additional software i need to install that make it safe in ubuntu 10.10?

---

### Post by CharlesA on 2011-01-31
It's still safe. There isn't a way to check NTFS drives for errors yet, but that would be something Windows does better.

Since the thread is from 2009, it's now closed.

---


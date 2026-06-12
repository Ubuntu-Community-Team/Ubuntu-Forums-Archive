---
title: "rkhunter: how to interpret the result?"
date: 2017-02-06
forum: Security
---

### Post by martemarziano on 2017-02-06
Hi, running the following command:

```
sudo rkhunter --check --rwo 
```

produces the following result:

```
Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable


Warning: User 'postfix' has been added to the passwd file.
Warning: Group 'postfix' has been added to the group file.
Warning: Group 'postdrop' has been added to the group file.
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-140501425: data
         /dev/shm/pulse-shm-2332197186: data
         /dev/shm/pulse-shm-1265051268: data
         /dev/shm/pulse-shm-2560223208: data
         /dev/shm/pulse-shm-2693838744: data
         /dev/shm/pulse-shm-4100390045: data
Warning: Hidden directory found: /etc/.java
```

I feel being completely at loss as to how to interpret the result above. I really appreciate if anyone can give me a hint. Thanks in advance!

---

### Post by deadflowr on 2017-02-06
*Thread moved to **Security**.*

---

### Post by Habitual on 2017-02-06
[To avoid these warnings]("https://help.ubuntu.com/community/RKhunter") section.

be advised
```
rkhunter --proupd 
```
is the LAST THING you want to "do" with rkhunter.
This command tells rkhunter everything it scans for is A-OK, ***as is***.
You must vet "Warning: " messages in /var/log/rkhunter.log before issuing it.

Carry on!

---

### Post by HermanAB on 2017-02-06
Well, the thing to bear in mind is that unless you have a deliberately unsecured web server sitting on the wild wild web as a honey pot, a positive returned by rkhunter has about 110% probability of being a false positive.

---

### Post by martemarziano on 2017-02-08
> **HermanAB said:**
> a positive returned by rkhunter has about 110% probability of being a false positive.

I am beginning to understand that. I had similar concerns about the results from scanning with ClamAv. Now I have run rkhunter once more and I get the following:

> /usr/bin/awk
         Current hash: 2531d65f43f6ed32b8d1f8c9d61075301aee23a43dd635ec55feff72a44ccc0a
         Stored hash : 91c3e9551264fc2b8a46a104715d51c13d717460f460e5d0d97295c69196ed1c
         Current symbolic link target: '/usr/bin/awk' -> '/usr/bin/gawk'
         Stored symbolic link target : '/usr/bin/awk' -> '/usr/bin/mawk'
Warning: The file '/usr/bin/gawk' exists on the system, but it is not present in the 'rkhunter.dat' file.

I would really appreciate to get any help to understand what this is all about. Thanks in advance!

---

### Post by HermanAB on 2017-02-09
Well, the Windows maintenance philosophy is to add 3rd party scanners, programs and patches to try and repair problems after they occurred.

The Linux philosophy is to strengthen the system so that problems do not occur in the first place and when a problem does occur, get a new version and re-install the whole ball of wax from scratch so that the problem won't occur again.

So, rkhunter and clamav are kinda useless on Linux machines.

---

### Post by martemarziano on 2017-02-09
> **HermanAB said:**
>  The Linux philosophy is to strengthen the system so that problems do not occur in the first place
Thanks for taking your time to comment on my post.
My problem is that I don't quite understand the nature of this problem and why it has occurred in the first place in order to do something about it. Any explanation for what causes this would be highly appreciated.

cheers,
martemarziano

---


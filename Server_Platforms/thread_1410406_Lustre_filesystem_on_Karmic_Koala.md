---
title: "Lustre filesystem on Karmic Koala"
date: 2010-02-18
forum: Server Platforms
---

### Post by jermen on 2010-02-18
One or two months ago I started to play with Lustre filesystem. It works on Hardy (after kernel downgrade) without any problems. I mean all parts - MDS/MDT, OSS/OST and client. I have prepared kernel packages + modified initrd and everything works great, I can even boot clients directly from Lustre.

But now I'm trying to make lustre _client_ work also on Karmic Koala, but it seems impossible. 

I followed instructions in "/usr/src/modules/lustre/debian/README.Debian" and [Lustre support matrix]("http://wiki.lustre.org/index.php/Lustre_Release_Information#Lustre_Support_Matrix") at lustre.org.

Both told me that I should use kernel 2.6.22. But with this version Karmic Koala boot fails on missing "/proc/self/mountinfo" used by "mountall":

```
mountall: /proc: unable to mount: Device or resource busy
mountall: /proc/self/mountinfo: Not such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (XXXX) terminated with status 1
```

Imho this means that ubuntu packages linux-patch-lustre and lustre-source are broken, because they wants me to install kernel version not compatible with Karmic.

In the Lustre Support Matrix I saw there should be a support for client 1.8.2 for vanilla 2.6.30 kernels.

So the questions are following:

[B]1) Is there any chance I will be able to boot Karmic Koala with 2.6.22 kernel?

2) Is 2.6.30 + Lustre patch working with Karmic? (/proc/self/mountinfo has been added in 2.6.26, but there can be other problems, so I'm rather asking)

3) If 2.6.30 is OK, can I use 1.8.2 Lustre client with Lustre 1.6.4.2 on servers?[/B]

Any suggestions/hints/tips are welcome.

Thank you.

P.S. Of course, I can try it myself, but I rather wanted to ask more experienced users about their opinion instead of spending many hours trying to do something impossible :)

---

### Post by jermen on 2010-02-28
Problem is "solved": [download patch for Lustre 1.8.2]("http://jermen.posterous.com/lustre-182-patch-to-compile-on-ubuntu-910-amd")

---

### Post by r_c_sekar on 2010-03-27
Can you post the steps that you took ? I seem to have some issues in patching..

---

### Post by jermen on 2010-03-28
Hi, I have prepared short how-to:

[http://jermen.posterous.com/lustre-client-182-on-ubuntu-910-karmic-koala](http://jermen.posterous.com/lustre-client-182-on-ubuntu-910-karmic-koala)

---


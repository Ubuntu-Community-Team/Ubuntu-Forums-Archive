---
title: "Xen on Feisty segfaulting"
date: 2007-09-20
forum: Server Platforms
---

### Post by bregant2 on 2007-09-20
Hi all,

I have just recently started using Ubuntu and am really enjoying it, but I am looking to use it as a Xen Dom0.  I have followed the howto here: [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen), and have used LVM instead of loopback.  So far everything is good.  I can run "xm list" and it shows that I have one domain running (Dom0).  Great.

The problem starts when I try to run the command "xm create -c /etc/xen/rpjoom". (rpjoom is the name of the vm that I want to start)  It winds up crashing with this output:

*** glibc detected *** /usr/bin/python: free(): invalid pointer: 0xb7d770f0 ***

<Backtrace not included>
<Memory dump not included>

No handlers could be found for logger "xend"
Error: Boot loader didn't return any data!

<Then here it prints the usage instructions for the command>

I have tried reinstalling, only to be faced with this same error.  Any ideas?

Thanks,
Bob

---


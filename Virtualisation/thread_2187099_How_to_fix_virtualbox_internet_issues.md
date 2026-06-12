---
title: "How to fix virtualbox internet issues?"
date: 2013-11-10
forum: Virtualisation
---

### Post by hamishmb on 2013-11-10
I have a few virtual machines used for testing new/unstable versions of my apps, but after upgrading to virtualbox 4.3.2, I have no internet access inside guests. I'm using NAT, all guests are 32-bit, running on 64-bit Mint 13 LTS (Based on Ubuntu 12.04). The guests report that the web connection is active and connected, and the host connection is active and working. However, any attempts to use the internet inside a VM result in errors exactly as if it weren't connected! Could someone please help me fix this quickly?

Thanks in advance,
Hamish

---

### Post by hamishmb on 2013-11-11
Temporary fix: using Bridged Adapter instead, which ironically didn't used to work before! Anyway it's sort-of fixed now, but if anyone has advice on using NAT, please let me know anyway :)

---

### Post by inearlygaveup on 2013-11-12
Your quick fix worked for me - thanks):P

---

### Post by hamishmb on 2013-11-24
*UPDATE: The reason NAT doesn't work in vbox-4.3.2 is that it is incorrectly configured, so I'm using 4.2, for which NAT does work (though bridged adapter doesn't!?!?). It will work in the future version 4.3.3 :) You're welcome.

Hamish

---


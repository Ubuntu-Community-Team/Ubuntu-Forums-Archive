---
title: "Dual Welcome Screen since Upgrade from 10.04 to 10.10 server."
date: 2010-10-11
forum: Server Platforms
---

### Post by fsavoir on 2010-10-11
Hi,

I'm wondering how to be able to fix the double / dual Welcome message when I login with SSH ?

I have two Welcome message with 10.04 and 10.10 :)

Any tips?

Thanks.

fred

---

### Post by asm74 on 2010-10-11
Got this issue too after upgrade 10.04 to 10.10.
My workaround - I've emptied the following file: /etc/motd.tail

sudo cp /etc/motd.tail /etc/motd.tail.backup
sudo sh -c 'echo "" > /etc/motd.tail'

---

### Post by Danimoth on 2010-10-14
Had the same problem. Workaround works for me. 

Filed a bug report on launchpad: 
[https://bugs.launchpad.net/ubuntu/+bug/660470](https://bugs.launchpad.net/ubuntu/+bug/660470)

---

### Post by charlesherdt on 2010-10-14
Same problem here. Removing /etc/motd.tail solved the issue.

---

### Post by fsavoir on 2010-10-16
Thanks a lot.

Solved !

---

### Post by Thaskalas on 2010-11-10
Ooh, my first bean  LOL!

This fixed the problem for me as well, Thanks!

---

### Post by AlphaWu on 2010-11-13
Thanks!

---

### Post by jamov on 2011-04-20
Just as FYI. I had the same issues when I updated 10.04 lts server with the latest updates as of this posting's date.  This was not an upgrade to 10.10

asm74's workaround corrected the issue in my case as well. Thanks!

---

### Post by greennewb on 2011-04-22
I can also confirm this.  10.04 LTS here as well, same issue after applying updates.  Also not an upgrade to 10.10.  Same solution resolved the problem.

---


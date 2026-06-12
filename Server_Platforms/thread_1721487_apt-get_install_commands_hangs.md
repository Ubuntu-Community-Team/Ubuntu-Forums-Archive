---
title: "apt-get install commands hangs"
date: 2011-04-04
forum: Server Platforms
---

### Post by kagrahar on 2011-04-04
I have installed Ubuntu 64bit 10.04 LTS version. I am trying to install open-iscsi and my apt-get install commands hangs
[COLOR=black][FONT=Arial]================================================== ===[/FONT][/COLOR]
[COLOR=black][FONT=Arial]root@gnat:~# uname -a[/FONT][/COLOR]
[FONT=Arial][COLOR=black]Linux gnat 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux[/COLOR][/FONT]
[FONT=Arial][COLOR=black]root@gnat:~# apt-get install open-iscsi[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Reading package lists... Done[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Building dependency tree [/COLOR][/FONT]
[FONT=Arial][COLOR=black]Reading state information... Done[/COLOR][/FONT]
[FONT=Arial][COLOR=black]The following extra packages will be installed:[/COLOR][/FONT]
[FONT=Arial][COLOR=black]open-iscsi-utils[/COLOR][/FONT]
[FONT=Arial][COLOR=black]The following NEW packages will be installed:[/COLOR][/FONT]
[FONT=Arial][COLOR=black]open-iscsi open-iscsi-utils[/COLOR][/FONT]
[FONT=Arial][COLOR=black]0 upgraded, 2 newly installed, 0 to remove and 20 not upgraded.[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Need to get 684kB of archives.[/COLOR][/FONT]
[FONT=Arial][COLOR=black]After this operation, 1,696kB of additional disk space will be used.[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Do you want to continue [Y/n]? y[/COLOR][/FONT]
[FONT=Arial][COLOR=black]0% [Connecting to us.archive.ubuntu.com (91.189.88.31)][/COLOR][/FONT]
[FONT=Arial][COLOR=black]0% [Connecting to us.archive.ubuntu.com (91.189.88.31)[/COLOR][/FONT]
[COLOR=black][FONT=Arial]=================================================[/FONT][/COLOR]
[COLOR=black][FONT=Arial]my sources.list seems to be fine. What might be the issue?? never had this issue on a 32 bit version of Ubuntu 9[/FONT][/COLOR]
[COLOR=black][FONT=Arial]Any help to resolve this is very much appreciated.[/FONT][/COLOR]

---

### Post by arrrghhh on 2011-04-04
I assume it's a network issue?  Can you ping us.archive.ubuntu.com?

Does apt-get update work?

Also, why are you running everything as root?  It's a bad idea, assuming you know why it's not a huge deal ;).

---

### Post by kagrahar on 2011-04-04
arrrghhh -you da the man!! Yes. It was a networking issue. I have two network interfaces eth0 and eth1..I disabled eth1
apt-get install is working now.
What I dont understand is why it wouldnt work when I have two interfaces up and running

---

### Post by arrrghhh on 2011-04-05
> **kagrahar said:**
> arrrghhh -you da the man!! Yes. It was a networking issue. I have two network interfaces eth0 and eth1..I disabled eth1
apt-get install is working now.
What I dont understand is why it wouldnt work when I have two interfaces up and running

Assuming both interfaces were "connected", you'd need to tell the routing table which one to use... Can't just use both at the same time, the default route for the second was probably taking priority - using 2 cxns at once is tricky, but doable ;).

---


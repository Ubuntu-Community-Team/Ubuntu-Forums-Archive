---
title: "Ubuntu Server &amp; Ubuntu Desktop : the real difference ?"
date: 2007-12-03
forum: Server Platforms
---

### Post by Spear on 2007-12-03
Hi,

I just joined a new company (as sysadmin) and what do i find in the server room (except the usual bunch of W2003 servers) ?

A workstation working as a proxy (Squid), running a Fedora 4 on a single hard disk with no backup.
What's lying near, unused, ready for the recycle bin ? A bi-pIII with four working disks.

This morning, i configured the bi-PIII to have RAID V (hardware), and, of course, i''ve taken the option to run it as the main proxy server (Raid will bring a better hardware security) with the old one as a backup.

Sure, they'll both run Ubuntu instead of Fedoredhat ;)

But here i am : every linux distribution is made of a kernel and a bunch of applications & configuration tools working around, tuned, making their differences.

I could install an ubuntu Desktop and tune it, but there is a server version : what does it bring ? (Except the fact it has lamp and seems to be totally nude). Is it safer ? Does it bring some dedicated server tools natively ?

Can you guys please bring me some light ?

Thanks in advance !

---

### Post by Vadi on 2007-12-03
I have no idea myself. But I did install apache and all of cms stuff on my laptop and it works just fine (just on localhost for now -cough-)

---

### Post by p_quarles on 2007-12-03
I believe the server edition uses a kernel optimized for for server purposes. It's been a while since I've used it (personally prefer Debian as a server), so I can't remember exactly what's different. 

That said, you can also use the Ubuntu alternate installation disk to setup a command line installation. Using either this method or the server edition will give you a cleaner installation -- i.e., no restricted modules manager (which you won't need), no bluetooth modules, etc. It'll be a lot easier to build a server "up" from  a minimal install than it would be to tune a desktop install.

---

### Post by andhar on 2007-12-03
I ended up using Xubuntu for my server install once I got it working the way I needed it to, I stop xfce from auto loading at startup.

---

### Post by mellowd on 2007-12-03
I've read a few notes here and there and there definately is a difference in the kernel between the two. 

Here is an article and you can continue to research from there:

[http://www.enterprisenetworkingplanet.com/netos/article.php/3710641](http://www.enterprisenetworkingplanet.com/netos/article.php/3710641)

---

### Post by mellowd on 2007-12-03
One big difference is that the 32bit server can support 64GB of ram via hacks in the kernel.

---


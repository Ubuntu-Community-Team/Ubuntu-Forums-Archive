---
title: "Ubuntu 12.10 Server + RAID5"
date: 2013-02-13
forum: Server Platforms
---

### Post by frobear on 2013-02-13
Hi All,

I have installed Ubuntu 12.10 Server on my HP Microserver. I installed it onto an SSD and now have 4 1TB HDD which I want to configure as RAID5.

How do I go about doing this, can I do this from the console or remotely using telnet or is there a GUI tool available?

Any help would be great, most guides I have found are to do it at OS install time (ie OS installed on RAID) or for older versions.

Thanks !

---

### Post by mosalem on 2013-02-13
yes. you are able to make it done completely by the console
this is good tutorial using mdadm to setup the raid.
check out page 32
[http://download.intel.com/support/chipsets/rste/sb/intelr_rste_linux.pdf](http://download.intel.com/support/chipsets/rste/sb/intelr_rste_linux.pdf)

check out your motherboard whether it has the controller. if yes you can have a better performance by using intel driver imsm.

---

### Post by mosalem on 2013-02-13
> **frobear said:**
> Hi All,

I have installed Ubuntu 12.10 Server on my HP Microserver. I installed it onto an SSD and now have 4 1TB HDD which I want to configure as RAID5.

How do I go about doing this, can I do this from the console or remotely using telnet or is there a GUI tool available?

Any help would be great, most guides I have found are to do it at OS install time (ie OS installed on RAID) or for older versions.

Thanks !
yes. you are able to make it done completely by the console
this is good tutorial using mdadm to setup the raid.
check out page 32
[http://download.intel.com/support/ch...rste_linux.pdf](http://download.intel.com/support/ch...rste_linux.pdf)

check out your motherboard whether it has the controller. if yes you can have a better performance by using intel driver imsm.

---

### Post by Cheesemill on 2013-02-13
Check out rubylaser's blog, it has some great info on RAID using mdadm.

[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

---

### Post by SaturnusDJ on 2013-02-13
> **frobear said:**
> telnet

Telnet is not secure. Use SSH.

---

### Post by codemaniac on 2013-02-13
Thread Moved to "Server Platforms".

Cheers!!

---

### Post by rubylaser on 2013-02-13
I would definitely use mdadm in this case as opposed to the Fakeraid in the HP Microserver.  mdadm  is not dependent on hardware, is very portable, and easy to setup.  Another option, if it's just for home media storage and you don't need the faster performance associated with realtime RAID, SnapRAID is another viable solution.

---

### Post by frobear on 2013-02-13
Thanks everyone for there responses.

I used the mdadm tutorial posted by Cheesemill, cheers for that, worked a treat, slowly coming together :)

---


---
title: "Server help...."
date: 2007-02-17
forum: Server Platforms
---

### Post by sk8aelf on 2007-02-17
ok  i have asked a few questions in the irc channel  and have gotten responses over the past few weeks  so not a total noob when it comes to the linux world as well as ubuntu.... but here goes..

simply put  running 6.10 verision of ubuntu server  lamp is installed
hostname is working all static ip settings are set    doing everything thru the ssh portal and webmin

webmin installed and working   everything is workign the way i want it..... my issue...

i have 2 40 gig drives mirrored for the ubuntu load
i have 2 160 sata drives ( that the system does pick up) i want to mirror  for web hosting....

dmraid and mdadm is installed  i get an error when i try and mirror the drives
"Failed to create RAID : mdadm in --create mode failed :

mdadm: error opening /dev/md0: No such file or directory
"

what i am wantin in the end  and im not sure if/what the config needs to be  to have those drives as the /var/www  file

so what im wantin is .... software raid on 2 160gig drives     and those drives set at the /var/www file .....  anyway to make this happen?

-thank you for your time/help

---

### Post by samiux on 2007-02-17
Hi,

Hope this may help you.
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

Samiux

---


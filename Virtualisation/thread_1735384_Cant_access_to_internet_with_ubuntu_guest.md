---
title: "Cant access to internet with ubuntu guest"
date: 2011-04-21
forum: Virtualisation
---

### Post by hossain2004a on 2011-04-21
I installed new version of Ubuntu 10.10 guest with my virtualbox 
I install my VM on XP and that's newest version.
 
after installing.....
then i try some software. and install squid3 and bind9 through terminal
still have internet access.......
 
then it goes out... i dont have internet on my ubuntu guest
I remove virtualbox and install it again... nothing happened....
But i have internet in Red hat and Windows server 2003
i think i have some problem with my setting that i cant find it...
Plz help me out!!!!

---

### Post by hossain2004a on 2011-04-22
bump

---

### Post by lmarmisa on 2011-04-22
Try to switch to Bridged Adapter on the VB Network settings menu of your virtual machine.

---

### Post by hossain2004a on 2011-04-22
My ubuntu became mad . i dont know... i put this Ip and getway to get it work:
 
10.0.0.16
10.0.0.2
 
I dont know ....
I used 9.04 LTS before but nothing like that happened!!

---

### Post by CharlesA on 2011-04-22
What networking mode are you using? Bridge, NAT, host-only?

---


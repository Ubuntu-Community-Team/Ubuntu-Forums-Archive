---
title: "Seeking advice about firewall"
date: 2008-03-29
forum: Security Discussions
---

### Post by kd5tmu on 2008-03-29
I recently started living with my friends' parents because my situation is tough and doesn't allow me to find my own place yet.  I dualboot XP and Gutsy and they want me to only use my computer on their network in XP so that they can give me McAfee to run because they are afraid that someone will hack into their network through my computer.  Is there a way I can get the same security benefits that the McAfee Firewall etc.  gives Windows users?  I hate going into windows

I regularly get the BSoD
It's decreases my battery life by HALF on this laptop
I don't do anything that REQUIRES windows!

Please help

---

### Post by NightwishFan on 2008-03-29
Ubuntu has all ports closed by default it should be better then a good firewall, although it has one.

---

### Post by Dr Small on 2008-03-29
> **NightwishFan said:**
> Ubuntu has all ports closed by default it should be better then a good firewall, although it has one.
Although, as you turn on different services, such as Apache, SSH, etc, it opens the port. If you are going through a router and it has a firewall on it, simply use that.

Dr Small

---

### Post by euler_fan on 2008-03-29
Offer to pay them $200 (or your local equivalent) every time they prove someone  hacks them through your computer. They can't and you won't.

So long as you're not willy-nilly installing things off the 'Net if you want to be slightly paranoid you can use something like Firestarter to manage your IPTables firewall, and use rkhunter and chkrootkit to check for rootkits. Another one to look into would be either OSSEC-HIDS, AIDE, OSIRIS, or Samhain for host intrusion detection. Then, of course, there's SNORT for network intrusion detection. 

I've personally had bad luck with OSSEC in terms of having all of its functionality work on any of my machines. The only thing I know for sure that works is monitoring your auth log. AIDE is a static file checker and Samhain is a more comprehensive HIDS.

---

### Post by hyper_ch on 2008-03-31
> **NightwishFan said:**
> Ubuntu has all ports closed by default it should be better then a good firewall, although it has one.

No, Ubuntu has no ports closed by default.

---

### Post by NightwishFan on 2008-03-31
Mine does O_o

---

### Post by hyper_ch on 2008-03-31
did you install firestarter?

---

### Post by NightwishFan on 2008-03-31
Fresh install of Xubuntu Hardy. I tested on shields up right now.

---

### Post by hyper_ch on 2008-03-31
no services listening to any ports and ports closed are different matters ;)

---

### Post by NightwishFan on 2008-03-31
It reports some as stealthed as well. (Not arguing just saying)

---


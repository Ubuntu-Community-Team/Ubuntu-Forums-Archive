---
title: "Networking layout"
date: 2011-11-12
forum: Server Platforms
---

### Post by nyu2007 on 2011-11-12
Hi All,

I will replace my recent windows network with open-sourse system ( Ubuntu Server/Desktop was the best choose for me).
I don't known how to setup my system for the best.

I have over 400PC's with 5 departments. and I don't have hardware router or switch layer3. I prefer router software.

Could you suggest me an network layout for my case?

Many thanks for any suggest!!
Regards,
NyU

---

### Post by spynappels on 2011-11-14
If you are looking for help, you need to give more details. For example, as you say you are replacing an existing Windows system, what is wrong with reusing the same networking setup for your open source infrastructure?

If you give more details, we may be able to help.

---

### Post by SeijiSensei on 2011-11-14
Why not start small?  Install an Ubuntu server on your current Windows network and configure it to handle some or all of the tasks you think you'll need.  (DNS, mail and intranet services are a good starting point.) Once you've gotten your feet wet, you can start to think about the big picture.

Are you really going to retrain 400 people to use Ubuntu instead of Windows?  How much have you budgeted for that?  Have any bespoke applications that only run on Windows/IIS/.NET/ASPx?  

How are you handling authentication, etc.?  Do you use Active Directory currently?  What are you planning to use in its stead? 

Believe me, the networking layout is going to be the least of your problems!

---


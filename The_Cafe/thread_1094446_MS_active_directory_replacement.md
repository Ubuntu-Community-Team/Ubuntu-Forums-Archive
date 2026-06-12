---
title: "MS active directory replacement?"
date: 2009-03-12
forum: The Cafe
---

### Post by Wesley on 2009-03-12
hi guys

a friend of mine own a business that has 11 XP machines and will have 3 more coming sometime next week.

At the moment, they all connected as workgroup, she asked me to setup a file server so all employees places their documents on the file server.

i had a good play with MDS (Mandriva Directory Server), works pretty well but no group policy. i'd like to see if there is anything better out there and free.

the cost of MS server 2003 with 15 CALs simply cost too much just for small business.

cheers

---

### Post by SunnyRabbiera on 2009-03-12
Samba might be able to help you.

---

### Post by LowSky on 2009-03-12
Yea Ubuntu with SAMBA is the thing you will need to support A Windows Workgrup. infact that is how all linux server connect to Windows computers in this fashion

It can be annoying to set up but very possible. here are some links

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

---

### Post by Wesley on 2009-03-12
blimey, samba server config looks murder! lol 

there must be GUI setup for samba server?

---

### Post by SunnyRabbiera on 2009-03-12
Not as far as I know, as servers usually dont use GUI so there never been any real incentive.

---

### Post by Coreigh on 2009-03-12
There is a GUI of sorts its called SWAT.

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Its not as easy as you want it to be and you should still know how the conf files work but it can help sift through all those settings.

---

### Post by Bölvaður on 2009-03-12
People I talk to seem to know samba better than linux, as it is so widely used.

---

### Post by thisllub on 2009-03-12
Samba will do your head in but once you get it set up properly it works.
Reliably.

---


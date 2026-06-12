---
title: "SAMBA and Windows 7"
date: 2015-10-21
forum: Server Platforms
---

### Post by Billy_Martinez on 2015-10-21
Hello, I have an Ubuntu server at my job that's running OS version 14, and I'm having a weird problem with SAMBA that I need help with. I want to be able to do two things with this server. The first thing that I want to be able to do is setup a share that I can connect to from a Windows 7 machine using a user account on the Linux server. I installed SAMBA and setup the config file and I was able to connect to it from my desktop running Ubuntu, but I wasn't able to connect to it from any of my Windows machines. Whenever I try to connect to the share using a windows machine I get a message about the user not being authorized. At my job all of the employees use their employee numbers to log into the domain. The only thing that I could think that could be wrong is that it's trying to use my employee number to authenticate vs the user account that I setup in samba which is my first name. It would be nice to be able to specify the username that I want to use to connect to the server with, but Windows 7 doesn't give me that option even though my Linux machine did. The second thing that I want to be able to do is to setup another share and connect to that share using a domain user account. I want that share to use a group on my domain that my employee number belongs to for authentication. This is all for the sake of research, my goal is to start using Ubuntu servers at my job.

---

### Post by Billy_Martinez on 2015-10-21
UPDATE!!

I logged into my Ubuntu server and I added my employee number as a user account and I also added it as an account in Samba, and now I can see the shared folder, but it still won't let me connect to it. The login box popped up, but when I put in my employee number and password it didn't work. I noticed in my Linux box that there was a default work group so I tried specifying WORKGROUP in the username like so "WORKGROUP/123456" and it still didn't work.

---

### Post by Billy_Martinez on 2015-10-21
I also configured the network card to map to my networks DNS so that can't be the problem. 

Please Help

---

### Post by Billy_Martinez on 2015-10-21
LOL Ok I feel kind of stupid. I've been using Linux so much that I confused the foward slash with the back slash. It should be like this WORKGROUP\123456 instead of WORKGROUP/123456.

Now when I try to connect I keep getting an error message stating that multiple connections are not allowed by this user account.

---

### Post by SeijiSensei on 2015-10-22
That's an annoying Windows limitation.  See [http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users](http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users).  If that doesn't help search Google for "multiple connections are not allowed by this user account samba".

I've wondered whether it also appears if you use the Professional editions.  It's the sort of thing Microsoft does to force businesses to buy Pro versions rather than the Home versions.  I don't have a Pro version around at the moment to test this out.  Maybe your business has one?

---

### Post by Billy_Martinez on 2015-10-22
> **SeijiSensei said:**
> That's an annoying Windows limitation.  See [http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users](http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users).  If that doesn't help search Google for "multiple connections are not allowed by this user account samba".

I've wondered whether it also appears if you use the Professional editions.  It's the sort of thing Microsoft does to force businesses to buy Pro versions rather than the Home versions.  I don't have a Pro version around at the moment to test this out.  Maybe your business has one?


I ended up restarting the Win 7machine and that killed all of the connections which solved the problem.

---


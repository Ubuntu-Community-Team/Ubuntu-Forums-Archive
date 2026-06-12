---
title: "Ubuntu web server! 8 Months without a restart and still going strong!"
date: 2007-02-08
forum: Server Platforms
---

### Post by TitanKing on 2007-02-08
I believe that Ubuntu is one of the best Web servers available. I have installed Ubuntu on our first web server over 8 months ago. The server works hard as it handles all branches over the country e-commerce. It handles millions of hits per month and transfers gigs of data!

Ubuntu is brilliant and have not failed me ever! Thanks for all the hard work guys! I have three running production Ubuntu servers now and it never gave me 1 days trouble!

I recommend Ubuntu as a web Server, you install and relax :popcorn:

---

### Post by phossal on 2007-02-08
8 months without a *restart?*

---

### Post by TitanKing on 2007-02-08
> **phossal said:**
> 8 months without a *restart?*

Well yes!? This ain't Windows you know... Not that big of a deal, but this is with updates and a really heavy load each day...

---

### Post by JimTDI on 2007-02-08
Awesome!!!  I love to hear stuff like that!!  Glad Ubuntu has not let you down!!

We're getting ready to switch from SuSE 8 with KDE to Ubuntu Server 6.06 this weekend on our production server, so your story makes me even more confident we're making the right move.

---

### Post by TitanKing on 2007-02-09
> **JimTDI said:**
> Awesome!!!  I love to hear stuff like that!!  Glad Ubuntu has not let you down!!

We're getting ready to switch from SuSE 8 with KDE to Ubuntu Server 6.06 this weekend on our production server, so your story makes me even more confident we're making the right move.

Nah, just jump for Ubuntu Server 6.10, it is extremely stable...

---

### Post by MJN on 2007-02-09
There'd be little to benefit from going to 6.10 as much of the server-side software remains pretty much the same. I'd stick with 6.06 for the server, particularly if the next upgrade is likely to be a while.
 
Mathew

---

### Post by jtc on 2007-02-09
I'd say 6.06 seems wiser then 6.10 for a serious production server.

Besides the packages being more tested the Long Term Support is rather valuable.

---

### Post by christhemonkey on 2007-02-09
My uptime on my home file server was about 3 months.
Not too shabby.


Had to restart it as i dist-upgraded to edgy.... (new kernel with support for my modem so its now a web server too :D)
Ah well.


Im very very happy with my healess ubuntu server.

---

### Post by Brazen on 2007-02-09
> **TitanKing said:**
> Nah, just jump for Ubuntu Server 6.10, it is extremely stable...
This is very very bad advice.

JimTDI, it's good to see you are being smart and using Dapper.  There are many good reasons to use Ubuntu Dapper with LTS over Edgy for a production server.

Regarding the OP, I had a CentOS machine running LAMP + Samba at home that I think had a continuous uptime of like a year and a half.  I only took it down because I wanted to switch to Ubuntu (had already switched a few servers at work, Dapper of course) and also used VMWare Server to split services into 3 virtual machines (1 for Apache, 1 for MySQL, and 1 for Samba).

---

### Post by Aberrix on 2007-02-09
glad to hear, haven't had a hiccup on my server yet either!

---

### Post by Brazen on 2007-02-09
This isn't an Ubuntu machine, but for the heck of it I went around and checked all our linux boxen for uptime.  I found a router built with CentOS with an uptime of 845 days!

And really, the only reason any of the others don't have such outrageous uptimes is because we still have to reboot to get a kernel update, and this box I've just forgotten about so I've never rebooted it to boot the latest kernel (it is automatically updated though, so everything else is patched).

---

### Post by fearevilleet on 2007-02-12
Please post the IP address of these servers so we can test test via digg

lol,,

---

### Post by JimTDI on 2007-02-12
[QUOTE=Brazen;2128886]This is very very bad advice.

JimTDI, it's good to see you are being smart and using Dapper.  There are many good reasons to use Ubuntu Dapper with LTS over Edgy for a production server.

Thanks for comments!  They're both good versions, I had a little trouble with 6.10 (fresh install) on my bench box - so chose 6.06 for it, as well as my production server.  The LTS was a major deciding factor as well.  So far, 6.06 has proved very stable for me, and for my environment.  Not knocking 6.10 - just my choice.

Now I'll try for some major uptime as well!  :-)  :-)

---

### Post by Brazen on 2007-02-13
> **fearevilleet said:**
> Please post the IP address of these servers so we can test test via digg

lol,,

Ha, well, actually it's an internal router, not accessible via the internet.

---

### Post by lenwood on 2007-02-13
> I'd say 6.06 seems wiser then 6.10 for a serious production server.

Can you explain? What does 6.06 have (or not have) that would make it a better choice? I don't disagree with you, I'm just curious . Actually, I'm not smart enough to have an opinion.

Thanks,
Chris

---

### Post by jtc on 2007-02-13
> **lenwood said:**
> Can you explain? What does 6.06 have (or not have) that would make it a better choice? I don't disagree with you, I'm just curious . Actually, I'm not smart enough to have an opinion.
The main benefit, as previously mentioned in this thread, is that 6.06 is an LTS (Long Time Support) release. That means that its server packages will be mainted (security updates, etc)  for five years time. Desktop package get three years.

6.10 is a normal release, which is merely mainted for 18 months. This is generally not an issue when it comes to a computers at home, but when you run a production server you might not want to have to touch it more then necessary once you've got it running as you want it to.

---

### Post by Brazen on 2007-02-13
> **jtc said:**
> The main benefit, as previously mentioned in this thread, is that 6.06 is an LTS (Long Time Support) release. That means that its server packages will be mainted (security updates, etc)  for five years time. Desktop package get three years.

6.10 is a normal release, which is merely mainted for 18 months. This is generally not an issue when it comes to a computers at home, but when you run a production server you might not want to have to touch it more then necessary once you've got it running as you want it to.

6.10 isn't even so much a "normal" release.  Ubuntu's goals for 6.10 were more inline with being a cutting edge system, trying out new things, etc.  This is good for desktops and testing out the latest technologies, but very bad for production servers.  There is even official Ubuntu documentation (too lazy to find it myself, but I have read it) that says 6.06 is their recommendation for production servers.

Also, I've answered this question a 100 times on this forum.

---


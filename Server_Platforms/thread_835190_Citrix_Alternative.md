---
title: "Citrix Alternative"
date: 2008-06-20
forum: Server Platforms
---

### Post by shingalated on 2008-06-20
Does anyone know of a free or low cost alternative to Citrix Application Server?  Citrix is very expensive, and slow, and we would rather not use it if we could avoid it.

Anyone know of anything equivalent that could host an application to multiple users (about 20) over a network?

I would love a free way to do this, or at least cheaper than Citrix.

---

### Post by gtdaqua on 2008-06-20
[http://www.brianmadden.com/content/article/Is-there-any-viable-alternative-to-Citrix-MetaFrame]("http://www.brianmadden.com/content/article/Is-there-any-viable-alternative-to-Citrix-MetaFrame")

---

### Post by johnbradbury on 2008-06-23
Is there no way of setting up Linux to do this?

I'd be very interested in setting up an open source TS server..

---

### Post by shingalated on 2008-06-25
I tried Sun's Secure Global Desktop, which looked like it could have been a good solution, but much of the interface seemed broken, and pretty much everything I clicked produced an error 500 "Internal Server Error"

---

### Post by Bosk22 on 2008-06-25
Try

[http://www.ltsp.org/](http://www.ltsp.org/)        - The Linux Terminal Server Project

or

[http://www.NoMachine.com/](http://www.NoMachine.com/)  - Its like windows remote desktop but for linux

One of these may meet some of your needs

Bosk

---

### Post by koenn on 2008-06-25
> **Bosk22 said:**
> Try

[http://www.ltsp.org/](http://www.ltsp.org/)        - The Linux Terminal Server Project
or
[http://www.NoMachine.com/](http://www.NoMachine.com/)  - Its like windows remote desktop but for linux

One of these may meet some of your needs

... if the application in question runs on Linux ...

---

### Post by promodus on 2008-06-25
> **shingalated said:**
> Does anyone know of a free or low cost alternative to Citrix Application Server?  Citrix is very expensive, and slow, and we would rather not use it if we could avoid it.

Anyone know of anything equivalent that could host an application to multiple users (about 20) over a network?

I would love a free way to do this, or at least cheaper than Citrix.

Is this a windows application?
May I ask which application this is?

---

### Post by bloodniece on 2008-06-25
Lot of questions to yours.

The program in question is a Win32/64 app or Linux app?
Are the clients Linux or Windows clients or a mix?
The Linux Terminal Server Project is worth looking into.
We use MS Terminal Services and have been very happy with it.  We have 2 servers setup as exact mirrors, clients connect to the least busy server.

---

### Post by shingalated on 2008-06-26
The application is Microsoft NAVision, which runs on windows.  The clients will need to be mostly Windows PCs, and a couple Macs.  The application runs on windows only, so LTSP isn't really an option.

---

### Post by koenn on 2008-06-26
out of curiosity :
why do you expect that people on a Linux forum would know about running a Windows application on a Windows Server, accessed by Windows and Mac clients ?

---

### Post by shingalated on 2008-06-30
> **koenn said:**
> out of curiosity :
why do you expect that people on a Linux forum would know about running a Windows application on a Windows Server, accessed by Windows and Mac clients ?

Because there are a lot of smart people here, some of which also use Windows and Mac.

---

### Post by Kileli on 2008-07-18
Has any one found a good solution for this i am setting up to launch multiple Ubuntu clients however i have a few windows apps that i cannot get to work in emulators such as wine is there a Linux app server out there that can host windows apps?

---

### Post by songshu on 2008-07-19
Why would you want to have a Linux server serving Windows applications that?
If you need to run windows only programs, run windows.

if that is too expensive look for alternative programs, also it would help if you mentioned which apps you are talking about

---

### Post by Kileli on 2008-07-30
i have just one application that is windows based thats it. i cannot get it to emulate it is to dependent on .dll and .mdb

---

### Post by songshu on 2008-07-30
can i ask which app that is?

---

### Post by Kileli on 2008-07-30
> **songshu said:**
> can i ask which app that is?

its a program called broker that a partner of my company created

---

### Post by songshu on 2008-07-30
> **Kileli said:**
> its a program called broker that a partner of my company created

its called "vendor lockin" and I've been there as well, it took me two years to replace a custom made MS access database with something OS independent.

The options are very simple, replace the app. or run windows.

---

### Post by Kileli on 2008-07-30
Thats really disappointing. i was really hoping that i would be able to tweak the wine registries to run this app. do you have any experience with wine-tricks?

---

### Post by songshu on 2008-07-30
i never use wine, i've been playing with the wine/crossover server once but had little luck with crashing applications, you can run wine/crossover as a server but they need to support it first, and 95% is not good enough to me when its about important data that can be lost.

in the end i figured it would be better to rewrite that damned ms access thing, i made that cursed thing 6 years ago myself by the way so can not blame anybody else.

but maybe you have more luck with wine then i did, you might try your luck.

p.s.

some retorical questions:
how old is "broker" and if you add the windows server (licensing + the added maintenance etc..) + dekstops running purely for that what is the TCO?
you might want to consider the long term options, i guess its a business app. so you might be able to show its cheaper to replace it then to keep it.

doesn't the "partner company" have an option to host their own app. in citrix?

---

### Post by Kileli on 2008-07-30
> **songshu said:**
> i never use wine, i've been playing with the wine/crossover server once but had little luck with crashing applications, you can run wine/crossover as a server but they need to support it first, and 95% is not good enough to me when its about important data that can be lost.

in the end i figured it would be better to rewrite that damned ms access thing, i made that cursed thing 6 years ago myself by the way so can not blame anybody else.

but maybe you have more luck with wine then i did, you might try your luck.

p.s.

some retorical questions:
how old is "broker" and if you add the windows server (licensing + the added maintenance etc..) + dekstops running purely for that what is the TCO?
you might want to consider the long term options, i guess its a business app. so you might be able to show its cheaper to replace it then to keep it.

doesn't the "partner company" have an option to host their own app. in citrix?

I'm not sure how old the app is exactly just a few years i believe.
We have other functions that require windows but the department that i want put on Linux doesn't need to be on windows except for this one program. i have only a few ubuntu machines running in the environment currently and i am using a citrix server to host this app but it would be better in my opinion to run it locally. mostly because we can only serve 25 simultaneous users on citrix 
i have been pushing to have it rewritten in Mysql but alas only money talks

---

### Post by koenn on 2008-07-30
> **Kileli said:**
> 
i have been pushing to have it rewritten in Mysql but alas only money talks

MS access databases, especially if they're disguised as applications, are death traps. At the most, ms access can be used to produce prototypes - you don't want them in a production environent.
A programmer or a software vendor selling you an application based on msaccess is a crook. He and his program are not worth a single penny of the company's money.

---

### Post by Kileli on 2008-07-30
> **koenn said:**
> He and his program are not worth a single penny of the company's money.

Thats awesome i've been screaming this for weeks. when i started digging into the programming i discovered how much code has been borrowed from other sources. looks like i get to turn a 12 MSaccess project towards mysql fun for me. yeah i asked and this app is 12 years old

---

### Post by songshu on 2008-07-30
> **Kileli said:**
> Thats awesome i've been screaming this for weeks. when i started digging into the programming i discovered how much code has been borrowed from other sources. looks like i get to turn a 12 MSaccess project towards mysql fun for me. yeah i asked and this app is 12 years old

looks like a daunting project, don't take it lightly cause you might have users that are married to that app. as long as they have been with the company....
in my experience, money does not count and neither does programming sense or making decisions that will benefit you in the future....its politics.

---

### Post by ats6902 on 2011-08-23
Hi all, if looking for a real alternative to Citrix XenApp, try Open Virtual Desktop (OVD) actually in a early v3 release candidate. It provides among many other features, seamless published application access to both Windows and Linux worlds!!!
 
[http://www.ulteo.com](http://www.ulteo.com)
 
ATS

---


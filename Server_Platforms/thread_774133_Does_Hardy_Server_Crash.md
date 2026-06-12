---
title: "Does Hardy Server Crash?"
date: 2008-04-29
forum: Server Platforms
---

### Post by martyssweb07 on 2008-04-29
I know all over the other forums people are complaining about hardy crashing, and yup it's happened to me a few times too.   But, for the desktop, I can live with that until they resolve the issue.

Does this issue affect the server release?  I have several gutsy servers installed, and don't want to risk upgrading until, I've heard about reliability.  A server hanging is not the same as a desktop. It's not an annoyance it's the seventh sign.

---

### Post by Mr.Carramba on 2008-04-29
would like to know this as well!
will set up new deployment server but after all complains on the forum I'm not sure I dear to do so. Would be really bad if application server would start crashing.
is it safer to stick to gutsy for now?

---

### Post by Brazen on 2008-04-29
Gutsy?!  Dear god, stick with Dapper if anything, on a server.

---

### Post by Mr.Carramba on 2008-04-29
> **Brazen said:**
> Gutsy?!  Dear god, stick with Dapper if anything, on a server.

hehe :) 
why is so? I had not yet encountered any problems with gutsy, is there something I don't know :)
*sorry for stealing thread*

---

### Post by frankos44 on 2008-04-29
I upgraded 2 of out busiest web servers remotely and they have been 100% OK so far.

One of them I had to re-install PHP5-GD again for some reason.

As for using a very old out of date release as someone mentioned earlier is asking for trouble. Fortunately Linux is a secure stable server platform so guess it doesn't matter too much but I personally think its bad practice to be more than one release out of date with any software.

LAMP is still uses Apache2 and PHP5 so no changes to the websites was necessary in my case.

---

### Post by Mr.Carramba on 2008-04-29
> **frankos44 said:**
> I upgraded 2 of out busiest web servers remotely and they have been 100% OK so far.

One of them I had to re-install PHP5-GD again for some reason.

As for using a very old out of date release as someone mentioned earlier is asking for trouble. Fortunately Linux is a secure stable server platform so guess it doesn't matter too much **but I personally think its bad practice to be more than one release out of date with any software**.

LAMP is still uses Apache2 and PHP5 so no changes to the websites was necessary in my case.

argy on that! this is the reason why I'm considering to install newest ubuntu server release, if it's working good and only desktop version is making trouble due all a lot more hardware compability need in comparison with server edition.

---

### Post by Brazen on 2008-04-29
> **Mr.Carramba said:**
> hehe :) 
why is so? I had not yet encountered any problems with gutsy, is there something I don't know :)
*sorry for stealing thread*

To put it short, Conanical themselves recommends sticking with the LTS releases on production servers (so it says on the website).  The non-LTS releases are somewhat of a testing-ground for features that will be in the next LTS release.  Of course this is an over-simplification, and then non-LTS releases are still quite stable, but if you are serious about 100% uptime and reliability (which I am, when it comes to my servers), then stick with the LTS releases.

6.06 Server will still be getting security and bugfix updates for another 3 years, so you have plenty of time before you need to get anxious about upgrading to 8.04.  Although I would certainly encourage you to try out 8.04 on development and testing servers, and even try out the next non-LTS releases on development and testing servers, as that is the best situation to find out if there are bugs or not.

---

### Post by tubezninja on 2008-04-29
> **martyssweb07 said:**
> 
Does this issue affect the server release?  I have several gutsy servers installed, and don't want to risk upgrading until, I've heard about reliability.  A server hanging is not the same as a desktop. It's not an annoyance it's the seventh sign.

My servers have been running since their upgrades completed (current uptime: 5 days,  5:34).  Not a crash yet.

But then, the server platform is pretty much stripped down to ONLY the services you need for your particular application.  There's a lot more running on the desktop installation, what with the GUI, the print and file sharing services, all the included apps and whatnot.  There could very easily be an issue related to the desktop suite that we're not seeing on the server side.

---

### Post by Mr.Carramba on 2008-04-30
> **Brazen said:**
> To put it short, Conanical themselves recommends sticking with the LTS releases on production servers (so it says on the website).  The non-LTS releases are somewhat of a testing-ground for features that will be in the next LTS release.  Of course this is an over-simplification, and then non-LTS releases are still quite stable, but if you are serious about 100% uptime and reliability (which I am, when it comes to my servers), then stick with the LTS releases.

6.06 Server will still be getting security and bugfix updates for another 3 years, so you have plenty of time before you need to get anxious about upgrading to 8.04.  Although I would certainly encourage you to try out 8.04 on development and testing servers, and even try out the next non-LTS releases on development and testing servers, as that is the best situation to find out if there are bugs or not.

this is really good point!
will be weird when installing 6.06 when there is 8 out ^^
but when it's ok to move to 8, when 9 non LTS is released?

---

### Post by gtdaqua on 2008-04-30
> 
**Does Hardy Server Crash?**

I know all over the other forums people are complaining about hardy crashing, and yup it's happened to me a few times too. But, for the desktop, I can live with that until they resolve the issue.

Does this issue affect the server release? I have several gutsy servers installed, and don't want to risk upgrading until, I've heard about reliability. A server hanging is not the same as a desktop. It's not an annoyance it's the seventh sign.



whatever edition is released, it is not good to roll out immediately in production environment, even if it is a LTS release. you should wait for sometime to see if there is a major issue reported, then test in your environment and then be approved for production. Remember, the admin (you) have to do the final approval so its not a walk in the park to simply upgrade to the next release when it comes out.

In my case, Hardy is not very friendly with VMware or vice versa. I had to tweak a few bits here and there to get VMware server working. So think twice before you upgrade.

---

### Post by ibutho on 2008-04-30
I have a server that was running 7.10 and last week I successfully upgraded it to 8.04 using aptitude. So far I have not had any problems after the upgrade. The machine is used for printing, dns, dhcp and as a test web server.

---

### Post by Brazen on 2008-04-30
> **Mr.Carramba said:**
> 
but when [is it] ok to move to 8, when 9 non LTS is released?

For me, it will be when I've finished thoroughly testing 8.04 for the services in our environment.  I'm not incredibily anxious though, as for the most part a file server will still just serve up files, an Apache server will still just serve up webpages, and a MySQL server will stil just serve up databases, whether it's from 6.06 or 8.04.

The thing I am most interested in is JeOS (JeOS is part of the Ubuntu suite, if you haven't heard of it), as almost all of my servers are virtualized.

---


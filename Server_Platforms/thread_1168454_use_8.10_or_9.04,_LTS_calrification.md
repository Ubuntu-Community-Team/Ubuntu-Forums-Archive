---
title: "use 8.10 or 9.04, LTS calrification"
date: 2009-05-24
forum: Server Platforms
---

### Post by salim.madni on 2009-05-24
dear gurus

q.1
advise shell we use 9.04 or 8.10, as some says 9.04 is new to market so wait sometime till it become stable.but what i know it has release since when it become stable.

q.2
can also someone let us know the policy every 6months release has version x.04 or x.10 always. any meaning to this? specially

q.3
also some say ubuntu LTS is very stable what is this exactly where and how we can download and use, is it special release as compare to ubuntu

regards
salim

---

### Post by Cheesemill on 2009-05-24
> 
q.2
can also someone let us know the policy every 6months release has version x.04 or x.10 always. any meaning to this? specially

The Ubuntu release cycle is every 6 months, the version number of each release relates to the year and month of the release (9.04 = 2009, 4th month).

> 
q.3
also some say ubuntu LTS is very stable what is this exactly where and how we can download and use, is it special release as compare to ubuntu


Normal releases of Ubuntu are only supported for 18 months after their release, but every couple of years LTS (Long Term Support) versions are released (the last was 8.04). These are supported for 3 years for the Desktop and 5 years for the server.

This gives businesses the opportunity to run Ubuntu without having to update all of their systems every 18 months.

LTS versions can be downloaded from any of the usual locations, Ubuntu site, torrents, etc.

Cheesemill

---

### Post by koenn on 2009-05-24
[http://www.ubuntu.com/products/whatIsubuntu/releases](http://www.ubuntu.com/products/whatIsubuntu/releases)

for production servers, you'll want the LTS releases. 
No sysadmin in his right mind wants to deal with a new release every 6 monts, on production servers

---

### Post by Kareeser on 2009-05-24
As for question one: It's up to you, as a system admin, to decide how "on the edge" you want your server to be.

Servers don't often rely on services that go wrong easily (such as compositing, a window manager, graphical interfaces, etc), so in essence, the risk in upgrading is lower.

I tend to stick one release behind the current release.

---

### Post by balloooza on 2009-05-24
I use 8.04, 8.10, 9.04, just because they work, they all work, as long as long as there is no hardware problems, even a normal non-lts release is supported for 18 months.

for an end user, I recomend the latest, your first question
> q.1
advise shell we use 9.04 or 8.10, as some says 9.04 is new to market so wait sometime till it become stable.but what i know it has release since when it become stable.
(I hate to misinterpret this, but I think I know what you are saying)
The 9.04 release is perfectly stable, in my opinion, other distros, such as mandriva (I use it) and arch (it is just bare linux, the only possibe issues are ones created by the user), are usualy *allways stable* (strong statement, this is just my opinion) WHere as fedora (one other I use now) and linux mint (dropped, after some non technical issues, and slowing development) usualy need some time to stableize.

HTH
mark

---

### Post by mellowd on 2009-05-24
For a production server I'd use 8.04 LTS.

As with what everyone has already said above, you don't upgrade production servers every 6 months. We have RHEL 3 servers still in use even though RHEL 5 has been out for ages

---

### Post by Vegan on 2009-05-24
Considering my own needs are well filled with an LAMP stack, I feel no pressing concerns about upgrading to each semiannual release. Each one is tested reasonably well and I have never had a problem.

I was using 8.04 but had to upgrade to 8.10 to be able to have php5 and mono work together. I no longer need mono, as my sites are now all PHP based. I made the decision to use PHP as its widely used and even Microsoft's web development tools now tow the line.

My IBM is the live "production" box, it works nominally save for the occasional disk failure. Disks are the only weak point. The old SDRAM seems impervious as does the processor.

9.04 has a status screen (I added uptime to it) and my server has 768 MB of RAM and the status says I am using 22% of it with PHP running. On the face of it, I have enough RAM for now.

The stupid disk failed last week but this time the backup was nuked too. So I have to rebuild my sites from scratch. So this time I am moving to a pure PHP site. PHP seems adequate, its well documented and its a defacto standard now.

So at the end of the day, for a fresh install, I download and fry the latest version of Ubuntu. With the IBM up, i use the upgrade tools for a live upgrade.

Ubuntu needs minimal disk space, the disk size desired is more a matter of how many web pages etc. you want to post.

A file server is another animal, so here storage is more important. My IBM has a 137 GB limit, so its useless as a file server. Eventually a new machine will replace the IBM but limitations are a dime a dozen. The next limit is 2 TB MBR limit. Moving to a 64-bit server needs more RAM, but supports GPT volumes that can exceed 2 TB. The boot problem remains.

So given this backdrop, you can now see more clearly why I use the new versions of Ubuntu. :p

---

### Post by salim.madni on 2009-05-25
dear gurus,

i am very new nebiew to ubuntu world that is why thousands of questions comes and you all help great. my skills all in redhat basically

greate views review and read by all

i need more clarification, let me know my target

- i will use simple ubuntu server, with axigen email server,clamav,antispam and webmin max...this is all support to work run as full flegdes email server

now, concerns
1) when we say support valid till 2010 support, this means all patches and reported issue will be enterrain and patches provided and then no more patches right
2) but how about if issues raised in year 2012 say after 2+ 3+ years...then this means we need to upgrade our os
3) LTS is 1 year old almost and lot of changes comes like php,kernel,samba version etc
4) if we have not purchase or buy support, this means even support valid they will not help us right away? is it?

bottom line i know, u use any linux or ubuntu mostly 99.99% if things working fine ok perfectly tested...it work for 10+ years no changes needed even on os, application level until very nesccary like oracle database servers, email server only update signatures of av/as comes etc

now  a question for me what version should i use?

regards
salim

---

### Post by Sef on 2009-05-25
> 1) when we say support valid till 2010 support, this means all patches and reported issue will be enterrain and patches provided and then no more patches right
2) but how about if issues raised in year 2012 say after 2+ 3+ years...then this means we need to upgrade our os
3) LTS is 1 year old almost and lot of changes comes like php,kernel,samba version etc
4) if we have not purchase or buy support, this means even support valid they will not help us right away? is it?


1) That is correct.

2) If there are security holes, or other issues, then they will not be fixed, if they are not supported.

3) Once a distro is released, only security patches are added.   It is very rare for Ubuntu to update applications once a distro is released.

4) If you have not purchased support, you cannot call or email them for support.   You can always come here, go to other forums for help, or ask people you know for help.

---

### Post by koenn on 2009-05-25
> **Sef said:**
> 
4) If you have not purchased support, you cannot call or email them for support.   You can always come here, go to other forums for help, or ask people you know for help.

maybe it's worth clarifying the 2 meanings of support,  i.e.

1. A release is supported until (date) -> until that date, security fixes will be released, (and some other interseting things, such as the repositories are available, ... )

2. "I have (bought) a support contract" -> I'm entitled to the support described in the contract (which could be e.g. the availability of a helpdesk, a service level agreement, .... )

---

### Post by salim.madni on 2009-05-28
dear gurus

once again thanks all

too much surprise and confusion for me as beginner user of ubuntu server level plateform. 

- the older release like ubuntu 6 lts and ubuntu 8.04 LTS hary heron. they support 2013 april
- where the new releases just like ubuntu 9.04 Jaunty Jackalope has 1 year support

is there anything very special programs,packages,applications in ubuntu 8.04 LTS hary heron which has not come upto now.

the bottom line what things has make ditinguised and unique LTS USING ubuntu 8.04 LTS hary heron as compare to others?


regards
salim

---


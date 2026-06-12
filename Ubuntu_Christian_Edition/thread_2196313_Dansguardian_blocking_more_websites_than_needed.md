---
title: "Dansguardian blocking more websites than needed"
date: 2013-12-28
forum: Ubuntu Christian Edition
---

### Post by Steve_and_Becky on 2013-12-28
Here is my problem.  I just installed Ubuntu 12.04 Christian Edition.  It works great for me, but dansguardian is blocking more websites than I need blocked.  How do I change the settings so that it is not blocking so much?  I have tried uninstalling it altogether, but then my computer does not want to connect at all after I uninstall dansguardian.  Something aobut dansguardian helps my computer connect to the internet. Help! I can't figure out how to change the dansguardian settings or how to uninstall it without losing my internet connection.   

Thanks!

Becky

---

### Post by Steve_and_Becky on 2013-12-30
Ok, I have gone through old threads that could have given me information for how to fix this one on my own.  But, the information is from so long ago that I am afraid to use that information.  I hope that someone can walk me through this because I am not at all experienced in command lines and what command lines to use to configure dansguardian the way it needs to be configured for us.  Can someone please give me some direction?  If I don't get some soon, I fear I will have to just pay the money to take my computer in to a computer shop that knows ubuntu and have them help me.

---

### Post by jonathonblake on 2014-01-01
> **Steve_and_Becky said:**
>  Can someone please give me some direction?  

What, specifically are you wanting to add/remove/change.

> I fear I will have to just pay the money to take my computer in to a computer shop that knows ubuntu and have them help me.

There are a couple of changes in Dansguardian as used in UCE, and the stock version.  Changes that are not immediately obvious, but do affect how the filters operate.

jonathon

---

### Post by Steve_and_Becky on 2014-01-05
I need to at least change the age level.  Right now it is set to preschool.  My husband and I are 50 years old and 48 years old respectively.  We obviously do not need the strict filtering that a preschooler needs.  I would also like to change a couple of exception lists.  But I can't figure out how to get in to them to change them and I have not been able to figure out how to get into the settings to change the age limit.

---

### Post by ronbu on 2014-01-18
The age level is set at /etc/dansguardian/dansguardian1.conf .  You can do  a search for "naughtynesslimit" and change the value to 100 for old children or 160 for young adults.  The lists in /etc/dansguardian/lists can be changed to allow access to parts or all of websites.  More information is at:  [http://contentfilter.futuragts.com/wiki/doku.php?id=grey...list_or_exception...list&DokuWiki=gvhxljbpcoxc](http://contentfilter.futuragts.com/wiki/doku.php?id=grey...list_or_exception...list&DokuWiki=gvhxljbpcoxc) .

---

### Post by jeff60 on 2014-05-14
Hi. I understand the whole idea of Christian Ubuntu I really do. It is to provide a safe place and atmosphere to work and play in Linux while providing some good Christian tools. and I understand that the last Christian Ubuntu version was all about the family and I support and appreciate the efforts behind this work wholeheartedly but can we have the option of having a good working and safe desktop for us adults to?. I believe that dansguardian should be set on it's lowest are even it's second lowest setting by default without the option of setting it lower or turning it off while being given the option to set it higher if we want. I'm all for that however I still need to be able to use the Internet without being told that perfectly normal and innocent searches and sights have been blocked. so I guess what I'm asking is not for the option of being able to turn dansguardian off but for the option of being able to have it turned down by default. and if the dansguardian install in the next release of Christian Ubuntu could come with a content list of things we want to block on top of what ever setting it is set on by default (like K9 comes with for instance) that could be useful as will. That aside great job on the last Christian Ubuntu distro. I can't wait to try out the next one. and I hope to be able to replace Linux mint with it as my primary OS for my laptop and Openmandriva as my emergency backup OS for my desktop (in case I manage to fry my Windows 7 install) I appreciate all the hard work. By the way is there a prospective date for the next release?

---


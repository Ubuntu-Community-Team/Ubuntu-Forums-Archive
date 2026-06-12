---
title: "Linux Mail Server"
date: 2008-02-14
forum: Server Platforms
---

### Post by Black Mage on 2008-02-14
What is a good mail server for Linux? I've tried using this one here but it seems to have some issues...and I'm prob not an advanced enough user yet. 

[http://flurdy.com/docs/postfix/#conf_mta](http://flurdy.com/docs/postfix/#conf_mta)

---

### Post by Gen2ly on 2008-02-14
nice.  putting in your own mail server can be really useful.  I am still taking a look into them but although postfix is the defacto standard, Exim is (from what i've read) easier to setup.  In fact, this review 

[http://shearer.org/MTA_Comparison#Quick_Answer](http://shearer.org/MTA_Comparison#Quick_Answer)

recommends it.

---

### Post by p_quarles on 2008-02-14
Moved to Server Platforms. Please post support questions in the appropriate forum.

---

### Post by faulkes on 2008-02-14
> **Black Mage said:**
> What is a good mail server for Linux? I've tried using this one here but it seems to have some issues...and I'm prob not an advanced enough user yet. 

[http://flurdy.com/docs/postfix/#conf_mta](http://flurdy.com/docs/postfix/#conf_mta)

The default for ubuntu server is Postfix - almost all mail servers are complex if you are new to setting them up, some moreso than others.

I would suggest you read the community documentation and the official server guide documentation, available at:

Official Server Guide for Postfix:

[https://help.ubuntu.com/7.10/server/C/postfix.html](https://help.ubuntu.com/7.10/server/C/postfix.html)

and the Community Documentation for Postfix:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Faulkes

---

### Post by motio on 2008-02-15
try sitadell working very good and you have a deb  to install
good lak

---

### Post by ronald.higgins on 2008-02-15
There are many punters for Citadel on the forum, postfix seems the standard and there is Exim as well which is the default MTA for Debian if I am not mistaken.

I hear that Citadel is pretty easy too set up though so try that out.

---

### Post by hyper_ch on 2008-02-15
Postfix is simple to setup and has very powerful spam checks built into itself.

---

### Post by DDuong on 2008-02-17
I have a Postfix mail server setup and it's pretty easy.  I am also in the middle of learning :)

---

### Post by KCPokes on 2008-02-17
There are numerous "out of the box" solutions that are available for free.  All are pretty easy to set up and use.  You can check out Citadel, Zimbra, OpenExchange, etc...

If you want to experiment on your own, I'd still recommend Postfix.  Just keep in mind that all are going to be a challenge if you are not familiar with how email is set up (ports, MX records, etc...).

---

### Post by faulkes on 2008-02-17
> **KCPokes said:**
> There are numerous "out of the box" solutions that are available for free.  All are pretty easy to set up and use.  You can check out Citadel, Zimbra, OpenExchange, etc...

If you want to experiment on your own, I'd still recommend Postfix.  Just keep in mind that all are going to be a challenge if you are not familiar with how email is set up (ports, MX records, etc...).

Correct.

Just keep in mind that as a community, we are here to help no matter what solution
you choose to go with.

Faulkes

---

### Post by MJN on 2008-02-17
Unless it's MS Exchange then you're on your own...! ;)

---

### Post by HermanAB on 2008-02-18
BTW, I just got Citadel to run on my Eee PC.  See the bottom of this:
[http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)

I'd love to see someone make MS Exchange run on the Eeep!

(Of course my guide is for Mandriva - since there are already lots of people running Xubuntu on the Eeep that doesn't present a challenge anymore, but my guide will help *buntu Eeep users too.)

Cheers,

Herman

---

### Post by ronald.higgins on 2008-02-18
> **MJN said:**
> Unless it's MS Exchange then you're on your own...! ;)

lol ....

Indeed ... ;)

---

### Post by Black Mage on 2008-02-20
Ok, so I got postfix, the mysql databases, and the squirrellmail installed using this tutorial: [http://flurdy.com/docs/postfix/#conf_mta](http://flurdy.com/docs/postfix/#conf_mta)

But the tutorial seems to end without explaining everything. So how do I send/recieve messages and get it working with squirrelmail? 

I've done the telnet localhost p25 test and everything works, but not when I try to use evolution with it.

---

### Post by Mr. C. on 2008-02-21
Most of the "tutorials" you find are not tutorial at all - they are recipes; you just follow the directions and mix the ingredients and hope it comes up soup.

Mail servers are complex.  Before you build the monolithic system, you should understand the components.  Since you have the basic server running, you're on your way.  But when things aren't working (eg. Evolution), you need to know how to diagnose and where to look for problems.

Start with your mail logs.  What log messages do you see that correspond to your attempts to connect with Evolution.

About squirrelmail, that's a different problem altogether.  That's an IMAP web client.  tackle one thing at a time.

If you're really interested in how the system works, get The Book of Postfix: [http://www.postfix-book.com/](http://www.postfix-book.com/) .  Also, start with the postfix.org basic debugging strategies:

[http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html)

MrC

---

### Post by hyper_ch on 2008-02-21
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p5](http://www.howtoforge.com/perfect_server_ubuntu7.10_p5)

---

### Post by MJN on 2008-02-21
I think that tutorial is one of the best (or should that be worst?) examples of how bad these guides are... it doesn't teach anything and so whilst it *may* give you something resembling a 'working' mail server setup it teaches you nothing so when it fails, or when you need to customise it to your own requirements, you're stuck.
 
As MrC says break the task down into managable chunks and build it one step at a time. You will soon understand how it works and be in a much better position to reach your ultimate goal.
 
Mathew

---

### Post by hyper_ch on 2008-02-21
MJN:

It depends what you want. Some people just want a step-to-step guide on howto setup something... others want to explore how it works.

You can't combine both in a easy-to-follow guide. The perfect howtos will just setup a server that can be used to host multiple websites with all necessary services. If one wants to find out more about it, he can of course consult further... but at one point you just want to get it up and running.

---

### Post by MJN on 2008-02-21
Sure, I understand. But surely noone wants to have to keep coming back asking for help when things break. Besides which, given the amount of threads along the lines of 'I've followed this guide, but is doesn't work' or 'I've followed this guide, but I want to do x' it seems people really do want to learn (but decided to take what appeared to be the 'easy' way out!) :)
 
Mathew

---

### Post by Black Mage on 2008-02-21
> **hyper_ch said:**
> [http://www.howtoforge.com/perfect_server_ubuntu7.10_p5](http://www.howtoforge.com/perfect_server_ubuntu7.10_p5)

Should I purge everything I've done so far with postfix , reinstall and use that one?

---

### Post by hyper_ch on 2008-02-21
I don't think you have to purge. You are given there the complete config files... you just need to adjust them to your server.

MJN: What appears to you that people want to learn "how to do x" I say, that they have a specific need and just want to resolve that issue. Not necessarily learn on how to do it.

---


---
title: "Firefox 53 and older hardware"
date: 2017-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-04-19
According to [https://www.ghacks.net/2017/04/19/firefox-53-0-release-find-out-what-is-new/](https://www.ghacks.net/2017/04/19/firefox-53-0-release-find-out-what-is-new/)> Windows XP, Windows Vista, 32-bit Mac OS X, and Linux support for processors older than Pentium 4 or AMD Opteron, are no longer supported.

---

### Post by exhile on 2017-04-19
Windows Vista just recently expired and the latest version of Google Chrome for Linux only supports 64-bit. Not surprised FireFox 53 is making the same move.

---

### Post by LastDino on 2017-04-22
So, are there any lightweight alternatives? 

I do have one machine with P4 3.0 Ghz, and it is one proud linux machine, works as a Email and Net browsing station for my parents. 

They are very used to Firefox tbh

---

### Post by vasa1 on 2017-04-22
Take a look at netsurf-gtk. It's in the repos:```
sudo apt-get install netsurf-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libmozjs185-1.0 netsurf-common
The following NEW packages will be installed:
  libmozjs185-1.0 netsurf-common netsurf-gtk
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,169 kB of archives.
After this operation, 7,946 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```Javascript seems to be off by default but it can be turned on via the GUI (Edit > Preferences > Content).

---

### Post by LastDino on 2017-04-22
That was quick.

I installed it to try it out. After some checking, gmail and general sites load pretty fast but sites like Amezon and Flipkart had a trouble loading

[ATTACH=CONFIG]274701[/ATTACH]

I'm guessing but some others addons are needed? But this should work for time being to at least for their needs. Thank you :KS

---

### Post by vasa1 on 2017-04-22
I'm guessing quite a few heavy sites won't work with this browser. Even the "Quick Links" at the top of each forum page don't work (with javascript enabled).

---

### Post by mörgæs on 2017-04-22
> **LastDino said:**
> 
I do have one machine with P4 3.0 Ghz

That should work fine with Firefox. Processors *older than* Pentium 4 (that is, without SSE2) are losing support, and I would consider them too slow to be of practical value anyway.

---

### Post by LastDino on 2017-04-22
> **mörgæs said:**
> That should work fine with Firefox. Processors *older than* Pentium 4 (that is, without SSE2) are losing support, and I would consider them too slow to be of practical value anyway.

Oh, for some reason I interpreted otherwise I see. Sorry for that :-#

---


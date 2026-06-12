---
title: "Need someone running amd64 to package something, please!"
date: 2006-11-11
forum: The Cafe
---

### Post by user1397 on 2006-11-11
if anybody here has an amd64 PC, please tell me if you have the time to package something for me.

The actual package is tovid, for more details see here: [http://tovid.org](http://tovid.org)

---

### Post by user1397 on 2006-11-11
Nobody? :(

---

### Post by taurus on 2006-11-11
You can't build it yourself on your AMD64!!!

---

### Post by user1397 on 2006-11-11
> **taurus said:**
> You can't build it yourself on your AMD64!!!dont u love sarcasm:rolleyes:

---

### Post by Turtle.net on 2006-11-12
What do you want to package in ? And why do you need a packagefor AMD64 if you only have a x86 ?

---

### Post by jdong on 2006-11-12
IIRC tovid is a Python app, so if it's packaged properly it's architecture-neutral, right?

And you might want to exercise some more patience and politeness on this request -- tovid has no Debian packaging whatsoever in the link you posted, so you're asking someone to debianize the source package, not just rebuild an existing source package on an AMD64.

---

### Post by jdong on 2006-11-12
Well, I decided to go ahead and be nice anyway: 
[http://buntudot.org/people/~jdong/tovid/](http://buntudot.org/people/~jdong/tovid/)

There's an all-architecture .deb there along with my sources.

**DISCLAIMER**: These are not Ubuntu-quality packages! To be all correct, libtovid should've been separated into a python-tovid package and the package should've been built with python_central. It'd be great if someone with packaging experience could make these changes and get this package into Universe.

---

### Post by Biker on 2006-11-12
I have download your package and compiled it for you in a couple of minutes.

Download the tovid_0.29-1_amd64.deb package from my (anonymous) FTP server eovermeer.nl

---

### Post by jdong on 2006-11-12
Tovid is a pure Python and Bash scripted suite, so it doesn't make any sense to make separate i386 and amd64 debs... you should just be making an "all" deb (like what I made and linked" that works on any architecture.

---

### Post by user1397 on 2006-11-12
Wow, thanks jdong! and thanks biker!

i did not intend to be rude or impolite in any way when i asked for this favor.

my original intention for packaging tovid for amd64, was because i was responsible for packaging the 0.29 version for i386 (i used checkinstall, as so did everybody else that made ubuntu deb's), as seen here: [http://tovid.sourceforge.net/download/kubuntu/](http://tovid.sourceforge.net/download/kubuntu/)

but there was no 0.29 version for amd64, as seen here: [http://www.netsoc.ucd.ie/~rory/linux/ubuntu/]("http://www.netsoc.ucd.ie/%7Erory/linux/ubuntu/")

since i wanted to help tovid, and since my main guide that a lot of people use on these forums is heavily concentrated on using tovid, and since the script which i made for installing tovid is important too, i wanted to have easy-to-access-for-ubuntu-users-debs.

i did not know that tovid was architecture independent, i'll ask the main tovid guy why there are 2 different ubuntu arch's.

jdong, one question, i did not really understand if the all-arch deb u made is usable or not.  is it good enough to upload to the tovid website?

---

### Post by jdong on 2006-11-13
> **erik1397 said:**
> 
jdong, one question, i did not really understand if the all-arch deb u made is usable or not.  is it good enough to upload to the tovid website?

It beats checkinstalled packages for sure. I've also added all the dependencies and recommends from the tovid wiki as dependencies, so gdebi properly pulls in all the tools that tovid needs. IMO a lot of the "recommends" are such key features of tovid that not having them would cripple tovid...

---

### Post by user1397 on 2006-11-13
> **jdong said:**
> It beats checkinstalled packages for sure. I've also added all the dependencies and recommends from the tovid wiki as dependencies, so gdebi properly pulls in all the tools that tovid needs. IMO a lot of the "recommends" are such key features of tovid that not having them would cripple tovid...man, thanks so much.  i'll ask the tovid guy to upload ur package to the official repo.  

how can tovid become part of ubuntu repos?
that would be great.

---

### Post by user1397 on 2006-11-13
jdong: wapcaplet, the head tovid guy, said okay about uploading ur deb to the official tovid website.  how would u like to giv it to him?

the easiest way to reach him is on IRC, irc.freenode.net, #tovid.
he's on all the time, actually, he's on rite now.

or you can email him ur deb (like i did), but i wont giv you his email ithout his permisson.

---

### Post by jdong on 2006-11-13
Just hand him the link to my web server.

As far as tovid entering the official repositories, it's gotta be packaged correctly. While my package works just fine, it's not up to Ubuntu caliber. Perhaps I'll do that as a part of my MOTU schooling this next week or two.

---

### Post by user1397 on 2006-11-13
> **jdong said:**
> Just hand him the link to my web server.

As far as tovid entering the official repositories, it's gotta be packaged correctly. While my package works just fine, it's not up to Ubuntu caliber. Perhaps I'll do that as a part of my MOTU schooling this next week or two.arite man, i'll give him the link.  thank you so much for your help, and i hope u learn enough to makje an ubuntu-caliber tovid package! :D

---


---
title: "clamav"
date: 2006-11-10
forum: The Cafe
---

### Post by TheRingmaster on 2006-11-10
will it ever be updated in the repositories?

---

### Post by Polygon on 2006-11-10
you could download it / package it and send it into the multi/universe people and then they will update the repos

although im not sure myself on how to pack a .deb

---

### Post by TheRingmaster on 2006-11-10
I would if i could.

---

### Post by pianoboy3333 on 2006-11-10
I could if I felt like it ;)

---

### Post by pianoboy3333 on 2006-11-10
> **TheRingmaster said:**
> I would if i could.

What version would you like me to package for you?

---

### Post by TheRingmaster on 2006-11-10
0.88.6 is the latest stable version, but you could also do .90rc3

[ClamAV&#8482;: Stable releases and RCs]("http://www.clamav.net/stable.php#pagestart")

---

### Post by pianoboy3333 on 2006-11-10
for edgy?

EDIT

and I don't see an rc3 of 0.90

I'll have these up tommorow probably

---

### Post by TheRingmaster on 2006-11-10
yes for edgy

I am sorry .90rc2 not 3

---

### Post by maniacmusician on 2006-11-10
Actually if you send it to be included in the repos, I'm pretty sure they'd like to be pointed to the source. It's not good policy to accept packages from just anyone, they package it themselves, I think.

But putting up a package would probably be useful for users who just want it. Asking the owners of [www.getdeb.net](www.getdeb.net) to put it up would be good too...they have some really great software picks on there. Especially stuff that's hard to find otherwise.

---

### Post by user1397 on 2006-11-10
how do you package a deb from source?  (apart from checkinstall)

---

### Post by TheRingmaster on 2006-11-10
the link I gave are the sources. i think

---

### Post by maniacmusician on 2006-11-10
Yeah. Someone suggested that you make the packages and send them in, and I was saying that they probably don't accept packages.

---

### Post by TheRingmaster on 2006-11-10
how can i send the sources then?

---

### Post by pianoboy3333 on 2006-11-11
Well, when you package something properly (not checkinstall) then you end up with certain files that you can use. There's the *.orig.tar.gz which has the original source, and then there are dsc files and such that include the changes that you can apply to recreate how the source folder was before you used "debuild" or whatever command to build the package.

For info on building packages, read the ubuntu yelp pages on your system on it, and checkout [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) which is the Debian New Maintainer's Guide.

---

### Post by user1397 on 2006-11-11
> **pianoboy3333 said:**
> Well, when you package something properly (not checkinstall) then you end up with certain files that you can use. There's the *.orig.tar.gz which has the original source, and then there are dsc files and such that include the changes that you can apply to recreate how the source folder was before you used "debuild" or whatever command to build the package.

For info on building packages, read the ubuntu yelp pages on your system on it, and checkout [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) which is the Debian New Maintainer's Guide.arite man, thanks for the info.

---

### Post by TheRingmaster on 2006-11-11
did any one send in the new source yet.

---

### Post by pianoboy3333 on 2006-11-12
Yea... I'm not able to package it... I don't know why, if you would like for the MOTU to package it, add it to [https://wiki.ubuntu.com/MOTU/Packages/Candidates](https://wiki.ubuntu.com/MOTU/Packages/Candidates)

---

### Post by pichalsi on 2006-11-12
sorry for offtopic but is antivirus really needed for linux?

---

### Post by TheRingmaster on 2006-11-12
> **pianoboy3333 said:**
> Yea... I'm not able to package it... I don't know why, if you would like for the MOTU to package it, add it to [https://wiki.ubuntu.com/MOTU/Packages/Candidates](https://wiki.ubuntu.com/MOTU/Packages/Candidates)
that will be fine for now

---

### Post by TheRingmaster on 2006-11-12
> **pichalsi said:**
> sorry for offtopic but is antivirus really needed for linux?
you never know

---

### Post by maniacmusician on 2006-11-13
It's more for those times when you have to send files to windows people. good practice to scan them.

---

### Post by TheRingmaster on 2006-11-13
well I am constantly sending emails, sometimes with attachments, to someone with windows.

---

### Post by pianoboy3333 on 2006-11-14
> **pichalsi said:**
> sorry for offtopic but is antivirus really needed for linux?

Yes, although quite rare, viruses for linux are possible, but there haven't been that many.

---


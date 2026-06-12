---
title: "RIP Pinta"
date: 2011-09-07
forum: The Cafe
---

### Post by szymon_g on 2011-09-07
well...
seems that the only user-friendly app for graphics on linux is dead. now linux users have to convince themself that Gimp is great ;)

/// edit
i forgot a link:

[https://groups.google.com/group/pinta/browse_thread/thread/6955dc6de7b80f07?hl=en&pli=1](https://groups.google.com/group/pinta/browse_thread/thread/6955dc6de7b80f07?hl=en&pli=1)

---

### Post by Alwimo on 2011-09-07
I'm sure another person will pick up the source code and continue it, and/or another app will be made.

---

### Post by szymon_g on 2011-09-07
> **Alwimo said:**
> I'm sure another person will pick up the source code and continue it, and/or another app will be made.

sure. nobody could be arsed to help this guy for over a year- so why anyone would do this now?

---

### Post by fatality_uk on 2011-09-07
> **szymon_g said:**
> sure. nobody could be arsed to help this guy for over a year- so why anyone would do this now?

Exactly, I have been involved in 3 Open Source projects that have faded out to nothing! Shame.

---

### Post by Dragonbite on 2011-09-07
While it sounds dumb.. or obvious, this brings up the question of how DOES one get involved?

Of course "download the code", but I must be an idiot because the only way I can see downloading the code is downloading the components individually?  The big "Download" button gives me the application, but not source.

I need "Git for Dummies" or something.

---

### Post by Shpongle on 2011-09-07
try apt-get source pinta

I'm sure you know this will not be the most up to date.

---

### Post by el_koraco on 2011-09-07
> **szymon_g said:**
> now linux users have to convince themself that Gimp is great 

Dude, with an attitude like this, who cares what you think?

---

### Post by Dragonbite on 2011-09-07
> **Shpongle said:**
> try apt-get source pinta

I'm sure you know this will not be the most up to date.

Do you need to have the Sources repositories enabled?

---

### Post by Shpongle on 2011-09-07
Yes you do , its usually the same as the deb http line except its deb-src http . 

eg

deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main
deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main


I also needed to install dpkg-dev 

then you should be able to pull it with apt-get source pinta

you can also use git to pull the latest version from the git repository

Im sure man git will provide the details. I think its something like git clone or git pull or something

---

### Post by Dragonbite on 2011-09-07
Johnathan just pointed me to the latest commit because the links on Git are not working (comes back "Not Found").

So I have one set of source and am hoping to poke around it some soon.  Just for fun, I don't think I am a good enough programmer to take it over or anything like that.

---

### Post by Shpongle on 2011-09-07
> **Dragonbite said:**
> Johnathan just pointed me to the latest commit because the links on Git are not working (comes back "Not Found").

So I have one set of source and am hoping to poke around it some soon.  Just for fun, I don't think I am a good enough programmer to take it over or anything like that.

Let us know how you get on with it :-).

---

### Post by mips on 2011-09-07
I only discovered pinta about a year ago and love it. This is indeed sad news.

---

### Post by Alwimo on 2011-09-12
Pinta has been revived and a new release is planned.

[http://www.omgubuntu.co.uk/2011/09/pinta-revived-release-planned/](http://www.omgubuntu.co.uk/2011/09/pinta-revived-release-planned/)
[http://groups.google.com/group/pinta?hl=en](http://groups.google.com/group/pinta?hl=en)

Who would have seen this coming? :p

Yay for open source.

---

### Post by mips on 2011-09-12
Cool stuff.

Pinta really is one of those must have OSS apps!

---

### Post by BrokenKingpin on 2011-09-12
> **szymon_g said:**
> well...
seems that the only user-friendly app for graphics on linux is dead. now linux users have to convince themself that Gimp is great ;)

GIMP does not aim to be a simple graphics editor. It is a professional level graphics editor, and for the features it offers the interface is fine (and even better once they have the version out where everything is in one window).

Pinta is a completely different type of graphics editor than GIMP, so it isn't fair to compare the two. I am glad to see the Pinta project revived though.

---

### Post by LMP900 on 2011-09-12
> **BrokenKingpin said:**
> GIMP does not aim to be a simple graphics editor. It is a professional level graphics editor, and for the features it offers the interface is fine (and even better once they have the version out where everything is in one window).

Pinta is a completely different type of graphics editor than GIMP, so it isn't fair to compare the two. I am glad to see the Pinta project revived though.

Well said. There was a smile on my face when I came across the news that it has been revived. I hope it's a success.

---


---
title: "Launchpad"
date: 2010-08-20
forum: Security
---

### Post by Klump on 2010-08-20
Greetings,

I always hear 'do **NOT** install anything from anywhere except the official repositories'. But I find a lot of great apps that are not included in repositories and would like to ask... how actually secure launchpad is? Are the codes reviewed by anyone? How do I make sure that a piece of software is not going to harm my Ubuntu? If I add a PPA for some program I won't going to check it's code every time it updates or am I being too cautious?

Klump

---

### Post by ajgreeny on 2010-08-20
Although I don't think there is any real worry about the contents of ppa repositories as far as security is concerned, neither is it possible to say that some weakness in these generally newer, updated versions of packages might not make them more vulnerable.

Having said that, I have had several packages of updated versions of a few things in past Ubuntu versions, eg vlc, banshee, gimp, and have never had any worries about them, nor problems with them.

Ask about specific packages here and I'm sure someone will tell you about any likely problems from using it.

---

### Post by Soul-Sing on 2010-08-20
I agree with ajgreeny, but it is almost impossible to say how "safe" launchpad PPA's are a priori. I am not aware of any issue's with them over 4,5 years of Ubuntu.
If you are in doubt of something (a part. PPA) ask on this forum, there are a lot of exper. Ubuntu-users to give you advice.

---

### Post by bodhi.zazen on 2010-08-20
It depends on the ppa, as with everything else, I trust ppa that are associated with a project such as

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

or

[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)

more then personal ppa (unless I know the individual of course).

Ubuntu has some of the largest repos on all distros, and the sheer size of the repos is one of the major advantages. What is it you want ? Depending on what you want, you may be better off with Fedora, Gentoo, or Arch. 

Fedora has smaller repos, but some of the Fedora apps are bleeding edge. Gentoo is cutting/bleeding edge. Arch is faster to introduce new versions of apps, but primarily the re-package code (last time I looked) so may be less bleeding.

---

### Post by wacky_sung on 2010-08-20
Do you think sites like [Truecrypt]("http://www.truecrypt.org/") can be trusted even you cannot find any repository for it?

---

### Post by bodhi.zazen on 2010-08-20
> **wacky_sung said:**
> Do you think sites like [Truecrypt]("http://www.truecrypt.org/") can be trusted even you cannot find any repository for it?

Are you asking me ?

I use LUKS over truecrypt as it is in the repositories and works for my needs.

Truecrypt is, IMHO, established enough that if it had a feature I needed, not provided by alternates, I would trust it enough use it.

---

### Post by wacky_sung on 2010-08-20
> **bodhi.zazen said:**
> Are you asking me ?

I use LUKS over truecrypt as it is in the repositories and works for my needs.

Truecrypt is, IMHO, established enough that if it had a feature I needed, not provided by alternates, I would trust it enough use it.

Thank for replying.The only thing which i like about Truecrypt is the range & type of encryption level and the choice to choose.

---

### Post by Klump on 2010-08-20
Thanks for the replies, people. I wasn't talking about any particular program and you answered my question. I too haven't had any problems (none that I know) and I tend to trust such popular PPAs like VLC, KeePassX, etc. but I was just curious about the whole mechanism. Actually I've tried quite a few distros (OSS, Arch, Fedora) but I love Ubuntu's (and Mint's) amount and variety of software, launchpad and community the most :) Thanks again.

P.S. I've been using Truecrypt ever since someone promoted it here in these forums. I started using it in Windows as well and I believe it's developers can be trusted.

Klump

---

### Post by rookcifer on 2010-08-20
> **Klump said:**
> Greetings,

I always hear 'do **NOT** install anything from anywhere except the official repositories'. But I find a lot of great apps that are not included in repositories and would like to ask... 

If you don't find an app in the repos, there are PPA's, which is a better option than just downloading some random .deb.

> how actually secure launchpad is? Are the codes reviewed by anyone? 

Good question.  No, it is doubtful that the launchpad packagers and maintainers scour through the source code of each package they add.  However, they do *test* the packages which means if something fishy was going on, chances are they'd find it.  And if they didn't find it, it wouldn't take long before the community at large did.

> How do I make sure that a piece of software is not going to harm my Ubuntu? If I add a PPA for some program I won't going to check it's code every time it updates or am I being too cautious?

You can pretty much rely on the official repos.  Since they are digitally signed, it is extremely unlikely that if someone cracked the repos that they could get users to download their malicious apps (they wouldn't have the signing key).

As for PPA's, those are not vetted like the official repos are, but are vetted by the community in a sense.  If the PPA is popular enough, chances are some geek would eventually identify any suspicious packages.

> **wacky_sung said:**
> Thank for replying.The only thing which i like about Truecrypt is the range & type of encryption level and the choice to choose.

You can choose what sort of encryption you want in LUKS, too.  In fact, it offers more choices of ciphers (it will use any cipher that's in the kernel and there's a fair number of them).  The only thing it doesn't do is offer cascading, which most experts say is of dubious value anyway.  (Actually, you can cascade, but you'll have to do it manually).

---

### Post by cariboo on 2010-08-21
For more info on what it takes to create a ppa, have a look [here]("https://help.launchpad.net/Packaging/PPA"). That should give you some insight to how secure ppas are.

---


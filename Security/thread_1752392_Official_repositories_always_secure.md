---
title: "Official repositories always secure?"
date: 2011-05-07
forum: Security
---

### Post by wi0 on 2011-05-07
I understand that it's up to the user to decide whether to trust a PPA they add. What about the official repositories. Is all software in those is checked "officially" ? Is software there compiled from sources after a check, and is there is a check before an update included?

---

### Post by bodhi.zazen on 2011-05-08
Nothing is always and there are security vulnerabilities in the official repositories. This is why we have regular security updates and why an installed and updated version of Ubuntu is more secure then a live CD, which lacks the most recent security patches.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

But ...

The official repositories are watched by many.

The ppa are watched by some, but less people then the repos.

3rd party projects vary. large projects (gnome , KDE, kernel) are watched by many, small projects are watched by few or none. Some third party repos are closed source (nvidia as one example, parts of Virtualbox as another).

If you are not going to trust the repositories of major distros such as Debian, Fedora, Ubuntu, SUSE, Centos, Slackware, Gentoo, etc then you will have to go with LFS and review the source code for yourself, which means the code is reviewed by one, you.

---

### Post by wi0 on 2011-05-08
I can appreciate the scientific carefulness in making absolute statements.

I was aiming for a more colloquial  "always". Security vulnerabilities (unintentional) aside, what about malware? If I randomly go around the internet, installing everything I can find on a windows system, malware infection is very likely. If I do the same with ubuntu, manually adding .debs and PPAs, infection is perhaps less likely because there's not much malware for linux around, but it's not a very smart move anyway.

Correct me if I'm wrong, but the purpose of the official repos on the other hand is to be a safe source for software for any purpose. Having said that, I'm not sufficiently familiar with the process of getting an application (and future updates) into the repositories, hence my questions in the first post.

---

### Post by bodhi.zazen on 2011-05-08
What is it you want to know that I did not answer ?

There is no known malware of any kind in the repositories. In theory there could be, but the repos are maintained by Canonical or the MOTU (depends on the repo).

---

### Post by rookcifer on 2011-05-08
> **wi0 said:**
> Correct me if I'm wrong, but the purpose of the official repos on the other hand is to be a safe source for software for any purpose. Having said that, I'm not sufficiently familiar with the process of getting an application (and future updates) into the repositories, hence my questions in the first post.

To get an application in the official repos means you have to submit it to the Debian developers for review first.  Then after a while, if you've done everything to their specs, they will add it.  Since Ubuntu uses the Debian repos, this means it is also available to Ubuntu users.  At least this is the way it worked when I last checked into it (because I had some code I wrote that I wanted to get into the repos).  It's not as quick or easy as one would think.

The repos themselves stay secure from tampering because all the packages are digitally signed with an unforgeable cryptographic signature.  As long as the packagers protect their signing key, you can be assured the packages have not been tampered with by some hacker.

---

### Post by tgm4883 on 2011-05-09
> **rookcifer said:**
> To get an application in the official repos means you have to submit it to the Debian developers for review first.  Then after a while, if you've done everything to their specs, they will add it.  Since Ubuntu uses the Debian repos, this means it is also available to Ubuntu users.  At least this is the way it worked when I last checked into it (because I had some code I wrote that I wanted to get into the repos).  It's not as quick or easy as one would think.

The repos themselves stay secure from tampering because all the packages are digitally signed with an unforgeable cryptographic signature.  As long as the packagers protect their signing key, you can be assured the packages have not been tampered with by some hacker.

Actually you just need to 

A) Submit it to the REVU process
B) Get it through the REVU process (fixing any packaging bugs you have)
C) it is not in the universe repo

---


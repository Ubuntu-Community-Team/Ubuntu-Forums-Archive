---
title: "debian minimal"
date: 2010-08-25
forum: The Cafe
---

### Post by sandyd on 2010-08-25
what do you think of debian minimal? Even with pure-ftpd, apache, mysql, postfix, and samba installed, it only takes up 40mb of RAM. And apt is much much faster on it than in ubuntu. Im currently considering converting my servers to debian right now.

---

### Post by dtoronto on 2010-08-25
Good to know, I've been looking for ways to scale down my resource consumption on my servers, and looking at other distros.  The one thing I really like about Ubuntu is the repositories are the most comprehensive for the apps that I use on my servers.

---

### Post by Bachstelze on 2010-08-25
My Ubuntu takes 45 with all that plus BIND and NTPD.  Not much of a difference...

---

### Post by XubuRoxMySox on 2010-08-25
It's pro'lly great on servers, and great on desktops for people who know what they're doing, who know exactly what they want installed and how to do that.

My own experimental exploration of Debian was very positive, but I battled for the better part of a week to get all my hardware and stuff recognized and working. It's not for newbies or technically-challenged dixiedancers, but it definitely is lighter on resources than Ubuntu! The simplicity and ease of Xubuntu is more than worth the 10 or 20 extra megs of RAM difference to me though.

-Robin

---

### Post by juancarlospaco on 2010-08-25
*Ram not used, ram wasted.*

---

### Post by Bachstelze on 2010-08-25
> **juancarlospaco said:**
> *Ram not used, ram wasted.*

If you only have 64, though, you want to give yourself some room just in case.

---

### Post by koenn on 2010-08-25
> **dtoronto said:**
>   The one thing I really like about Ubuntu is the repositories are the most comprehensive for the apps that I use on my servers.
weird, given that ubuntu's repos are derived from debian's ...

---

### Post by Bachstelze on 2010-08-25
> **koenn said:**
> weird, given that ubuntu's repos are derived from debian's ...

With some very nice additions.

---

### Post by koenn on 2010-08-25
> **Bachstelze said:**
> With some very nice additions.
such as ?

---

### Post by mips on 2010-08-25
> **carlee said:**
> what do you think of debian minimal? Even with pure-ftpd, apache, mysql, postfix, and samba installed, it only takes up 40mb of RAM. And apt is much much faster on it than in ubuntu. Im currently considering converting my servers to debian right now.

Go for it. Why do you need the affirmation?

---

### Post by Bachstelze on 2010-08-25
> **koenn said:**
> such as ?

More kernel modules available for easy instllation with dkms, for example for Broadcom wifi cards, or apparmor, or branded Mozilla stuff (silly, but still something the lambda user likes)...

And overall better maintained, security updates are generally uploaded to Ubuntu several days before they are uploaded to Debian.

---

### Post by koenn on 2010-08-25
> **Bachstelze said:**
> More kernel modules available for easy instllation with dkms, for example for Broadcom wifi cards, or apparmor, or branded Mozilla stuff (silly, but still something the lambda user likes)...

And overall better maintained, security updates are generally uploaded to Ubuntu several days before they are uploaded to Debian.

oh, ok - I was thinking about ('end user') applications and the likes. 
I run very generic hardware with the traditional server software (network infrastructure, web,filesharing, ...) so there's little ubuntu would have over debian in that respect.

---

### Post by Spice Weasel on 2010-08-25
Ubuntu's repositories are absolutely a waste of time if you just want a basic system.

---

### Post by Paqman on 2010-08-25
> **Spice Weasel said:**
> Ubuntu's repositories are absolutely a waste of time if you just want a basic system.

Eh? There's plenty of packages in them that are useful for building a lightweight system. You don't *have* to install ubuntu-desktop.

---

### Post by Spice Weasel on 2010-08-25
> **Paqman said:**
> Eh? There's plenty of packages in them that are useful for building a lightweight system. You don't *have* to install ubuntu-desktop.

There's lots for building a lightweight system, but there is about ten times more bloat. I'm not talking lightweight, when I say basic I mean that how much of the repository does the average user need and use? I'd personally like to disable the parts that I won't ever use.

---

### Post by Paqman on 2010-08-25
> **Spice Weasel said:**
> I'd personally like to disable the parts that I won't ever use.

Why's that then? A big repo is a good repo, surely?

---

### Post by Spice Weasel on 2010-08-25
Less updating time, quicker installs/removals etc.

---


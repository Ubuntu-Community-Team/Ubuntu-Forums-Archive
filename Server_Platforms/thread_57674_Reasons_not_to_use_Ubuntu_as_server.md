---
title: "Reasons not to use Ubuntu as server?"
date: 2005-08-17
forum: Server Platforms
---

### Post by OneSeventeen on 2005-08-17
At work we have some Suse Linux Enterprise Server 9 licenses, and all the novell folks around here are going crazy about how wonderful SLES9 is.

I personally don't care for SLES, primarily because they still use RPMs and I have yet to get the network configured properly.  The Ubuntu LiveCD started up just fine and I was browsing the web in no time.

The only downside I've seen is lack of PHP5 support, which I hear is because of instabilities?

Anyway, I'm wondering if you would reccomend Ubuntu for a production server over something like SLES 9.  Why or why not?

(support for ubuntu is *much* cheaper, but it looks like PHP5 wouldn't be supported :( )

---

### Post by JonahRowley on 2005-08-18
Ubuntu is really wasted on a server.  All the work goes into desktop-oriented things.  Debian would be a better choice, Debian Sarge (the latest release) is now stable and is very good.

---

### Post by nad on 2005-08-20
Not to knock the ubuntu developers, but, running a production server based on debians testing tree is an oxymoron.

---

### Post by Velox Letum on 2005-08-20
I run a webserver + PHP and such for development on Ubuntu, but I certainly wouldn't run it on a production environment...at least not yet. I use Fedora Core 1 for my production servers...used to use FreeBSD until CPanel stopped working.

---

### Post by LordHunter317 on 2005-08-21
[QUOTE=nad]Not to knock the ubuntu developers, but, running a production server based on debians testing tree is an oxymoron.[/QUOTE]Seeing as the QA in testing is much, much higher than RH's QA all the time generally, no.

The bigger issues are paid support (offered, but not enough coverage, currently) and security updates.

The manner in which both are currently done are personal no-gos for production Ubuntu for me.

I'll stick with RHEL or Debian with HP's paid support.

---

### Post by OneSeventeen on 2005-08-22
Okay, so just to clarify, heres why I was leaning towards Ubuntu:

[list=1]
[*]It is Open Source (unlike most "enterprise" servers)
[*]Support is $400/yr for up to 10 issues
[*]It runs the software I need
[*]It runs right out of the box on my server, whereas SuseLinux Enterprise Server 9 does not.
[*]It is easy to set up and maintain.
[/list]

Am I hearing that the support is sub-par?  SLES9 doesn't even run the software I want, nor do they support most of the software that actually runs on the server.

I'm really leaning towards Ubuntu based on what I've used in the past, and how much I like Ubuntu on my desktop, so I do want to know if Ubuntu as a server is dumb, but I also don't have the $$ to throw on new enterprise server software, nor do I want to use closed source software.

By production server, I mean this would be for a department at a major US University, and would run nothing but PHP5 apache 2, MySQL and PostgreSQL.

I definitely want to keep it simple, and all of the paid features of SLES 9 just entitle me to "updates"  which Ubuntu does as well...

So I guess now the question is, in light of what I'm running, will I be better off running debian?  If so, who offers paid support and for how much?

---

### Post by koggo on 2005-08-23
I have a server running Ubuntu fine, not sure what all the chaos is about.

---

### Post by nad on 2005-08-23
There is nothing wrong with running ubuntu as a server, especially in a smaller non-critical environment, as long as the administrator is knowledgeable and aware that certain available upgrades could break his system.

In which case, the conservative administrator may wish to go the safer route with a proven system whose upgrades have been thoroughly tested.

---

### Post by nocturn on 2005-08-23
I'm running Ubuntu on a home server and it works great.
If you find all your packages in main (or 99%), then you should be fine.

Debian may be more stable, but I did not go that way because of their slipping release cycles.

Also note that 6.04 will introduce a longer support term for server installs.

---

### Post by LordHunter317 on 2005-08-23
[QUOTE=koggo]I have a server running Ubuntu fine, not sure what all the chaos is about.[/QUOTE]Because those of us who run production boxes that make our companies thousands or millions of dollars a day need certain requirements Ubuntu is currently unable of meeting.

[quote=nocturn]Also note that 6.04 will introduce a longer support term for server installs.[/quote]Wonderful, but this isn't real problem.  Unless a substantial amount of server software in universe transitions to main between now and then, Ubuntu as a supported server is useless, because I have to use universe anyway, which kills my support.

---

### Post by OneSeventeen on 2005-08-26
Well, I've decided to go with debian, but I'm not super impressed with them either.  How long does it take for a product to be pushed into main/stable?

PHP5 has been out for over a year, and has made more changes between it and 4 than 4 and 3 (IMO).

But oh well, that's what dotdeb is for, and if our server crashes, then it crashes... that's why I'm setting up a couple of other workstations with debian so it can mirror the site, just in case.

Thanks for the tips though, this has helped a lot in deciding a server.

---

### Post by Brian Puccio on 2005-08-27
[QUOTE=OneSeventeen]Well, I've decided to go with debian, but I'm not super impressed with them either.  How long does it take for a product to be pushed into main/stable?[/QUOTE]

Double check the debian website for an answer. This page:

[http://packages.qa.debian.org/p/php5.html](http://packages.qa.debian.org/p/php5.html)

Points to this page:

[http://bjorn.haxx.se/debian/testing.pl?package=php5](http://bjorn.haxx.se/debian/testing.pl?package=php5)

See also:

[http://www.debian.org/devel/testing](http://www.debian.org/devel/testing)

You can find even more information about Debian's stable/testing/unstable breakdown by googling or reading the Debian website.

---

### Post by snpz on 2005-08-29
Do Ubuntu developers are not interested in developing something SLES-like?
Really good desktops+Ubuntu Enterprise server. That would be really nice!

---


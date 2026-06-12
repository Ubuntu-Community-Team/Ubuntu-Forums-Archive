---
title: "Is this a joke? Canonical, please stop supporting Dapper NOW!"
date: 2009-06-02
forum: The Cafe
---

### Post by zugu on 2009-06-02
I know people around here like to think Windows is insecure, but here's what I found while browsing Launchpad:

[**96 open CVE bugs**]("https://bugs.launchpad.net/ubuntu/dapper/+bugs?field.has_cve=on") in Ubuntu Dapper

Some of the vulnerabilities have been reported in **2007**. I mean, is this a joke? For an 'enterprise-ready', LTS release this is **unacceptable**. You'd have to be out of your mind to install this in a production environment, but what about people who already installed it years ago, hoping Canonical would provide support and security patches?

Look at [this]("https://bugs.launchpad.net/ubuntu/dapper/+source/vlc/+bug/122207") VLC media player CVE report. It's been reported  in the middle of 2007. Not only it's not fixed in the middle of 2009, it's been closed as "Won't Fix" for other, EOL'd Ubuntu releases. Now it's as if they want Dapper to die so that they can close the bug with the same "Won't Fix".

Dapper's Squirrelmail is also in a [very, very bad situation]("https://bugs.launchpad.net/ubuntu/dapper/+source/squirrelmail/+bug/375513"). [Ruby]("https://bugs.launchpad.net/ubuntu/dapper/+source/ruby1.9/+bug/241657"). [PHPMyAdmin]("https://bugs.launchpad.net/ubuntu/dapper/+source/phpmyadmin/+bug/82003"). [Wordpress]("https://bugs.launchpad.net/ubuntu/dapper/+source/wordpress/+bug/89654"). [Python]("https://bugs.launchpad.net/ubuntu/dapper/+source/python2.3/+bug/163845"). [Lighttpd]("https://bugs.launchpad.net/ubuntu/dapper/+source/lighttpd/+bug/279490"). [Java]("https://bugs.launchpad.net/ubuntu/dapper/+source/sun-java6/+bug/319367"). [OpenSSL]("https://bugs.launchpad.net/ubuntu/dapper/+source/openssl/+bug/146269"). **Jesus Christ, this is insane!**

I honestly hope they just remove Dapper from all Ubuntu mirrors, the thing is riddled with gaping security holes it's obvious they won't lift a finger to fix. So better remove it and tell everyone who installed it to replace it with some newer Ubuntu version, or even another OS.

Canonical, please stop official support for Dapper now! It's not as if you're offering any, anyway, but at least you make people aware of the huge risks they're taking everyday they continue to use Dapper on their servers and workstations.

---

### Post by Giant Speck on 2009-06-02
Canonical is ending support for Dapper Drake this month.

---

### Post by zugu on 2009-06-02
> **Giant Speck said:**
> Canonical is ending support for Dapper Drake this month.So for most of its miserable life, Dapper was a failure. I'm sure Canonical will be relieved to see it die, just like with other EOL'd releases.

---

### Post by Giant Speck on 2009-06-02
> **zugu said:**
> So for most of its miserable life, Dapper was a failure. I'm sure Canonical will be relieved to see it die, just like with other EOL'd releases.

 I'm sure not enough people use Dapper for it to really be of any concern now anyway.

---

### Post by zugu on 2009-06-02
> **Giant Speck said:**
> I'm sure not enough people use Dapper for it to really be of any concern now anyway.Such a professional attitude. </sarcasm> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014. Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".

And it's not about cutting support, it's about critical security bugs that were open for 2 years! 2 years of exposing your users to shocking vulnerabilities (just read the CVE documentation for the VLC bugs, it makes you shiver).

How is this professional again?

I vow not to use any Canonical product again.

---

### Post by handy on 2009-06-02
I had Dapper running on a machine for the best part of 2 years & never had any security problems, it did things for me that later releases would not do on the same hardware.

I don't know what you are complaining about, I consider you to be creating a storm in a tea cup.

If there had of been serious security issues with Dapper, we would all have been familiar with them a looong time ago, as the forum would have been hearing all of the tales of woe.

Your attempt at making such a big splash OP, seems to be a year or so too late as it is happening at such a crucial time in the life of Dapper (the end of it) that I think in reality you are a troll.  Whether you know it or not is another question.

---

### Post by Giant Speck on 2009-06-02
> **zugu said:**
> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014. Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".

The difference between XP and Dapper is that XP, while being extremely outdated, is still the most-used Windows version (around 68% of computer users still use XP).  Dapper is likely used by a very small minority of Ubuntu users.

---

### Post by handy on 2009-06-02
Don't feed them, they only grow.

---

### Post by gn2 on 2009-06-02
> **zugu said:**
> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014.

Hmmm maybe by 2014 they'll have fixed the (up to) "Extremely Critical" unpatched vulnerabilities that remain outstanding.

[http://secunia.com/advisories/product/16/](http://secunia.com/advisories/product/16/)
[http://secunia.com/advisories/product/22/](http://secunia.com/advisories/product/22/)

And that's just the ones that are known about in the OS itsself, it doesn't address vulnerabilities that remain undisclosed or those in the many thousands of applications that can be run on the XP operating system.

> **zugu said:**
> I vow not to use any Canonical product again.

Ubuntu is not a Canonical "product".

---

### Post by Giant Speck on 2009-06-02
> **gn2 said:**
> Ubuntu is not a Canonical "product".

Wait... then what is it?  :confused:

---

### Post by billgoldberg on 2009-06-02
> **handy said:**
> don't feed them, they only grow.

:) :)

---

### Post by gn2 on 2009-06-02
> **Giant Speck said:**
> Wait... then what is it?  :confused:

Good question.

The linux distribution known as Ubuntu isn't owned by Canonical, therefore it's not one of their products.

Canonical own trademark rights to the name Ubuntu and they promote and support the distribution.

Everyone and at the same time no-one owns the distribution.

---

### Post by Wolki on 2009-06-02
> **zugu said:**
> Such a professional attitude. </sarcasm> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014. Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".

I only checked the first few, but they all are in universe or multiverse. The Ubuntu web page is clear about that:

[QUOTE=http://www.ubuntu.com/community/ubuntustory/components]Canonical does not provide a guarantee of regular security updates for software found in universe but will provide these where they are made available by the community. Users should understand the risk inherent in using packages from the universe component.[/QUOTE]

So I do not really understand your point. Is it that Canonical is not doing something they clearly state they would not do? Is it that they should provide updates they did not promise regardless of whether they have the capacity to do it? Is it that Ubuntu should not contain community-supported at all (which means getting rid of universe/multiverse)?

[edit] a small clarification: while your list contain some software that is in main (such as python and openssl), the specific versions affected by the bugs are not the versions in main, but older versions for compatibility included in universe. #146269 is tricky as it is still marked "New" for dapper, but the USN linked in the bug claims that it is fixed.

---

### Post by Solicitous on 2009-06-02
> **zugu said:**
> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014. Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".


Currently do you know how many unresolved security issues exist in Win XP?  Nope, no-one but Microsoft do.  I think you'll find if the number was ever revealed XP would have more security issues than Dapper.  However don't forget MS release patches for the OS they built (essentially no applications), Ubuntu releases patches for the OS and applications etc.

---

### Post by koshatnik on 2009-06-02
> **zugu said:**
> Such a professional attitude. </sarcasm> MS provides security patches to Windows XP since 2001 and it will continue to do so until 2014. Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".

And it's not about cutting support, it's about critical security bugs that were open for 2 years! 2 years of exposing your users to shocking vulnerabilities (just read the CVE documentation for the VLC bugs, it makes you shiver).

How is this professional again?

I vow not to use any Canonical product again.

And crying about it on a public forum will achieve what?

An adult would have responded by emailing Canonical directly with your thoughts and concerns, and then removed Dapper in light of the information you found out, which is of huge concern to you clearly, and installing something else.

You just look a bit daft airing this in the manner you have.

---

### Post by HavocXphere on 2009-06-02
> **zugu said:**
> Canonical announces 5 years of support on the server, only to tell people "you're not meaningful enough for us to do what we said we'd do".
Support means they will help you troubleshoot any problems that you have...if you are a paying support customer.

It does not mean that Canonical endeavors to fix any and all bugs that may be reported by the general public.

And if you read the standard SLA very carefully you'll find that even the commercial customers receive a "best effort" style service, not guarantees.

> **zugu said:**
> they just remove Dapper from all Ubuntu mirrors
Not a very realistic suggestion. They'd get sued by corp customers...and they'd lose since they are contractually bound. The general public will also be very very unhappy about the lack of mirrors.

---

### Post by Kareeser on 2009-06-02
> **zugu said:**
> Such a professional attitude. </sarcasm> ... I vow not to use any Canonical product again.

I'd suggest you ask Canonical for your money back.

That's right, isn't it, it's a free operating system... so in the future, I'd advise commenting nicely instead of adopting a self-righteous attitude.

---

### Post by Viva on 2009-06-02
> **handy said:**
> don't feed them, they only grow.

+1

---

### Post by forrestcupp on 2009-06-02
In my opinion, Dapper was the most stable version ever released.  If those things really mattered that much, they would have been fixed a long time ago.

We have a much more recent LTS.  Why don't you stop wasting your time and criticize the new LTS?

> **zugu said:**
> 
I vow not to use any Canonical product again.
I doubt if anyone cares.

---

### Post by finer recliner on 2009-06-02
look at the OP's post history. he mostly just complains about anything open source. he's a troll. as stated before: don't bother posting, you're only feeding him.

---

### Post by Simian Man on 2009-06-02
I think this is just the problem of the Debian packaging methods being wholly unmaintainable.  Rather than expect somebody to port security fixes back into ancient versions of software, you should just upgrade the components that you rely on or live with the risks.

---

### Post by frodon on 2009-06-02
Ok i'm closing this thread as nothing good and productive is going to happen.

I's been said that dapper support will soon end and that a more up to date LTS release exists (ubuntu Hardy Heron) so i suggest you to swich to hardy heron so that your box won't be left unsupported.

Feel free to PM me if you have valid arguments to re-open the thread.

---


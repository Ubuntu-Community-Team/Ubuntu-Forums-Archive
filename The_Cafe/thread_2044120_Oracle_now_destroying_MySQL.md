---
title: "Oracle now destroying MySQL"
date: 2012-08-18
forum: The Cafe
---

### Post by Primefalcon on 2012-08-18
[http://developers.slashdot.org/story/12/08/18/0152237/is-mysql-slowly-turning-closed-source?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Slashdot%2Fslashdot+%28Slashdot%29](http://developers.slashdot.org/story/12/08/18/0152237/is-mysql-slowly-turning-closed-source?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Slashdot%2Fslashdot+%28Slashdot%29)

I was wondering how long it would take Oracle to start pulling this nonsense with MySQL since MySQL is their main competitor... and IMO probably the main reason they bought Sun...

Time to fork?

---

### Post by KiwiNZ on 2012-08-18
The reasons to purchase were far greater than this. Things move on.

---

### Post by Primefalcon on 2012-08-18
> **KiwiNZ said:**
> The reasons to purchase were far greater than this. Things move on.
Sure I don't doubt there were other reasons such as buying a lawsuit in a can against Google with the patents acquired.

But lets face it, Oracle's big money maker is their database, and that competes directly with MySQL which is/was the largest market-share database in web servers used.... Which leaves me in no doubt at all that MySQL  was a major consideration to this purchase.

Also.... This from PC World: [http://www.pcworld.com/businesscenter/article/239132/wikileaks_cable_offers_new_insights_into_oraclesun_deal.html](http://www.pcworld.com/businesscenter/article/239132/wikileaks_cable_offers_new_insights_into_oraclesun_deal.html)
> Oracle told U.S. authorities that the EU was "pressuring it to divest MySQL as a condition for approval of the merger," a move that would "destroy" the deal

So without MySQL Oracle would not have purchased Sun.......

---

### Post by lykwydchykyn on 2012-08-18
Oracle and MySQL are relational databases; the similarities pretty much end there.  I've used both, and I don't see them as competition; they are about as far removed in my opinion as Solaris and Android.

In any case, there are already forks -- MariaDB is probably the best known and mentioned in the article.

Plus, postgresql is better anyway :P :D

Oracle can do what they like, nobody expected them to charge forward with open development anyway.  Who knows, in six months they may dump the whole thing on Apache like they did with openoffice.

---

### Post by Primefalcon on 2012-08-18
> **lykwydchykyn said:**
> Who knows, in six months they may dump the whole thing on Apache like they did with openoffice.
Not likely.... not when Oracle said MySQL was a dealbreaker if it wasn't included....

---

### Post by JDShu on 2012-08-18
> **lykwydchykyn said:**
> Oracle and MySQL are relational databases; the similarities pretty much end there.  I've used both, and I don't see them as competition; they are about as far removed in my opinion as Solaris and Android.


The way they work is very different, but they target the same market, so yes, they are competitors.

Anecdote: I happen to know somebody who interviewed at Oracle. As part of the inteview, he had to give a satisfactory presentation that showed that Oracle is a better database than MySQL.

---

### Post by vexorian on 2012-08-18
If their objective is to ruin mySQL then dropping it on Apache is also a good method.

> **Primefalcon said:**
> Sure I don't doubt there were other reasons such as buying a lawsuit in a can against Google with the patents acquired.

But lets face it, Oracle's big money maker is their database, and that competes directly with MySQL which is/was the largest market-share database in web servers used.... Which leaves me in no doubt at all that MySQL  was a major consideration to this purchase.

Also.... This from PC World: [http://www.pcworld.com/businesscenter/article/239132/wikileaks_cable_offers_new_insights_into_oraclesun_deal.html](http://www.pcworld.com/businesscenter/article/239132/wikileaks_cable_offers_new_insights_into_oraclesun_deal.html)


So without MySQL Oracle would not have purchased Sun.......
If the Java lawsuit on Android was one of their main objectives then I almost feel sorry for oracle.

Almost.

To me, it is looking like they just wanted to look for the best ways possible to ruin the whole world. Eagerly Waiting for how are they gonna ruin VirtualBox next.

---

### Post by synaptix on 2012-08-18
Wouldn't this violate Sherman Antitrust Act?

---

### Post by cariboo on 2012-08-18
> **Primefalcon said:**
> [http://developers.slashdot.org/story/12/08/18/0152237/is-mysql-slowly-turning-closed-source?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Slashdot%2Fslashdot+%28Slashdot%29](http://developers.slashdot.org/story/12/08/18/0152237/is-mysql-slowly-turning-closed-source?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Slashdot%2Fslashdot+%28Slashdot%29)

I was wondering how long it would take Oracle to start pulling this nonsense with MySQL since MySQL is their main competitor... and IMO probably the main reason they bought Sun...

Time to fork?

[MariaDB]("http://mariadb.org/") is being written by the same group that originally wrote MySQL, so no need for a fork.

---

### Post by JDShu on 2012-08-18
> **synaptix said:**
> Wouldn't this violate Sherman Antitrust Act?

Not in any clear sense. For one, Oracle's aquisition of Sun was evidently approved by the US Government.

---

### Post by lykwydchykyn on 2012-08-18
> **JDShu said:**
> The way they work is very different, but they target the same market, so yes, they are competitors.

If there's overlap in some situations, it's not one I've experienced.  Not that I've experience everything, so I'll freely admit I'm probably wrong.

I guess my own experiences where I work (and other db's as well), I can't remember a situation where there was a debate between using one or the other.  When Oracle was used, it was the only thing that would have worked, and when MySQL was used it would have been laughable to use Oracle.

> 
Anecdote: I happen to know somebody who interviewed at Oracle. As part of the inteview, he had to give a satisfactory presentation that showed that Oracle is a better database than MySQL.

Fair enough.

---

### Post by MadmanRB on 2012-08-18
The problem lays in that a lot of things use mySQL including some linux apps so this is pretty nasty.

---

### Post by vexorian on 2012-08-18
There's little oracle can do that would hurt the free software projects that already use mysql. If this keeps happening, the developers can just take the latest release to be licensed GPL and fork away. The projects will just need to switch to the fork (or distribution's packagers can do the change themselves).

It is the risk of companies like Oracle buying out projects what makes me happy we got the GPL.

---

### Post by Primefalcon on 2012-08-19
> **vexorian said:**
> It is the risk of companies like Oracle buying out projects what makes me happy we got the GPL.
Agreed 100%... since MySQL was a dealbreaker..... I really have to wonder..... Did Oracle really not understand what the GPL is when they bought Sun....

They got left with nothing after they did the same to OpenOffice, now they pull the same kinda thing with MySQL... Do they not understand this stuff can easily be forked.... that the only thing they really own is the name?

---

### Post by KiwiNZ on 2012-08-19
> **Primefalcon said:**
> Agreed 100%... since MySQL was a dealbreaker..... I really have to wonder..... Did Oracle really not understand what the GPL is when they bought Sun....

They got left with nothing after they did the same to OpenOffice, now they pull the same kinda thing with MySQL... Do they not understand this stuff can easily be forked.... that the only thing they really own is the name?

one does not rise to management in a company the size of Oracle without being aware of the industry one is in and have a good level of intelligence.

---

### Post by jwbrase on 2012-08-19
> **synaptix said:**
> Wouldn't this violate Sherman Antitrust Act?

Probably, but the US government's record of actually enforcing the Act is very spotty, so it's rather moot.

---

### Post by Primefalcon on 2012-08-19
> **KiwiNZ said:**
> one does not rise to management in a company the size of Oracle without being aware of the industry one is in and have a good level of intelligence.
I disagree, the guy who owns oracle either does not understand the GPL.... or he does understand the GPL and thinks people wouldn't just fork it anyhow....

One way or the other..... he's made a gross miscalulation.

---

### Post by forrestcupp on 2012-08-19
> **KiwiNZ said:**
> one does not rise to management in a company the size of Oracle without being aware of the industry one is in and have a good level of intelligence.

Sometimes some that have risen to big company management don't act like they have the level intelligence required. ;)
I've seen big, upper management and CEOs do some very stupid things.

Besides, GPL is relatively so small a part of the market that it's very possible to have a high level of understanding of the tech market and all of the competitors without understanding the inner workings of the GPL license.

---

### Post by stmiller on 2012-08-19
Oracle pretty much owns MySQL. So they could close the source and change the license if they wanted and start charging for it.

MariaDB is 100% compatible with MySQL. A true drop in replacement. All mysql commands, APIs, etc work. 

MariaDB is GPLv2 and is looking more and more like the future...

---

### Post by vexorian on 2012-08-19
> Oracle pretty much owns MySQL. So they could close the source and change the license if they wanted and start charging for it. It is not possible to retroactively change the license of stuff that was already released. So if Oracle do that, there's nothing stopping you from taking the last GPL-ed release and keep on working on it with the GPL.

---

### Post by forrestcupp on 2012-08-19
> **vexorian said:**
> It is not possible to retroactively change the license of stuff that was already released. So if Oracle do that, there's nothing stopping you from taking the last GPL-ed release and keep on working on it with the GPL.

That's true that you could take the last GPLed release and work with it. But if Oracle changed their license to a proprietary license (which the owner is allowed to do), anything developed from that point on would be closed, and anything forked from an earlier release wouldn't be compatible with future releases.

---

### Post by vexorian on 2012-08-21
> **forrestcupp said:**
> That's true that you could take the last GPLed release and work with it. But if Oracle changed their license to a proprietary license (which the owner is allowed to do), anything developed from that point on would be closed, and anything forked from an earlier release wouldn't be compatible with future releases.
Yeah, but I don't think we would have to care about the new features.

The FOSS projects that currently use mysql, would just move to the GPL version.

---

### Post by rg4w on 2012-08-21
Is this all that different from the reasons Libre Office was created?

Next up:  VirtualBox.

---


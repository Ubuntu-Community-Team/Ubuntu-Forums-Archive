---
title: "What is the future for MySQL and OpenOffice?"
date: 2010-02-15
forum: The Cafe
---

### Post by bwallum on 2010-02-15
Hi

Now that [Oracle has fully digested Sun]("http://www.oracle.com/us/corporate/press/044428") what is the future for OpenOffice and MySQL?

---

### Post by j.bell730 on 2010-02-15
Well, both are released under the GPL, and the source is available for both, so Oracle has little influence on them.

Both will likely continue to be developed regardless of Oracle's thoughts on them.

---

### Post by lykwydchykyn on 2010-02-15
I'm intrigued at how Oracle keeps talking about being able to offer "whole stack" solutions to its customers.  They seem to have every intent of getting behind solutions that are 100% Oracle from hardware to OS to middleware to apps.

An office suite would seem to factor significantly in the equation, and I believe they've already rebranded Star Office as "Oracle Office".  This gives me hope for the resources they'll pour into OpenOffice.

As for MySQL, I couldn't say.  We'll just have to see what comes.

I do think Oracle's role is significant; a project is more than just a chunk of code and a free license.

---

### Post by t0p on 2010-02-15
> **j.bell730 said:**
> Well, both are released under the GPL, and the source is available for both, so Oracle has little influence on them.

Both will likely continue to be developed regardless of Oracle's thoughts on them.

Not necessarily.  If Oracle decide they don't want to continue with the projects, their continuation will depend on how many devs are willing to work unpaid on them.

Sun have put a lot of resources into MySQL and OO, in terms of personnel, equipment and more.  I don't know how many devs from outside of Sun are on the projects; but I'm sure it would have a serious impact if Oracle pulled the plug.

**EDIT:** in [this press release]("http://www.oracle.com/us/corporate/press/042364") Oracle make a number of promises about MySQL, including:

> 
4. Commitment to enhance MySQL in the future under the GPL. Oracle shall continue to enhance MySQL and make subsequent versions of MySQL, including Version 6, available under the GPL. Oracle will not release any new, enhanced version of MySQL Enterprise Edition without contemporaneously releasing a new, also enhanced version of MySQL Community Edition licensed under the GPL. Oracle shall continue to make the source code of all versions of MySQL Community Edition publicly available at no charge.

[...]

6. Increase spending on MySQL research and development. Oracle commits to make available appropriate funding for the MySQL continued development (GPL version and commercial version). During each of the next three years, Oracle will spend more on research and development (R&D) for the MySQL Global Business Unit than Sun spent in its most recent fiscal year (USD 24 million) preceding the closing of the transaction.


[And as for OO]("http://searchenterpriselinux.techtarget.com/news/article/0,289142,sid39_gci1379904,00.html"):

> 
Oracle also said it would continue to develop, promote and support OpenOffice, and the OpenOffice.org community edition. It will manage it as an independent Global Business Unit, using Sun's development and support teams.


So it would seem MySQL will be alright for the next few years.  And OO will continue for a while at least.

---

### Post by bodhi.zazen on 2010-02-15
> **bwallum said:**
> Hi

Now that [Oracle has fully digested Sun]("http://www.oracle.com/us/corporate/press/044428") what is the future for OpenOffice and MySQL?

Moved to the Cafe.

---

### Post by mickie.kext on 2010-02-15
> **j.bell730 said:**
> Well, both are released under the GPL, and the source is available for both, so **Oracle has little influence on them**.

Both will likely continue to be developed regardless of Oracle's thoughts on them.

That **bold** is as far from truth as it can get. 

MySQL and OpenOffice are GPLv2 and LGPLv3 respectively, but are in fact corporate effort, entirely funded by Sun and now Oracle. Outside contributions are minor and get mainlined only if outside contributor assign copyright to Sun (and now Oracle). All core developers of those two projects are on Oracle payroll now, and if Oracle decides to relocate them on another project, MySQL and OpenOffice are toast. Possible fork would need to have new name,  new developers, and new funding which greatly limits its chance of success, especially in case of MySQL.

That were hard facts and worst possible scenario. Now speculation about future:

Oracle needs OpenOffice to fight Microsoft Office, and needs MySQL to fight other open source RDBMSes as well as Microsoft SQL Server. I expect Oracle to fund OpenOffice heavily, because they do not have competing product and they need OpenOffice. 

As for MySQL, they will probably take easy on that as they do not want to cannibalize their own Oracle 11g. But at same time, there is chance that cannibalization is inevitable, so they would rather do it themselves then let EnterpriseDB (PostgresPLUS)or Ingres do it. So I think they will keep improving MySQL steadily, while improving their own DB at faster pace. If open source databases close in for a kill, they will probably pour more money in to MySQL to fight them off.

---

### Post by falconindy on 2010-02-15
Some possible futures scenarios for MySQL:

1) Stop all development and mothball the project.
2) A slow phaseout of paid support, leaving only the community edition of MySQL with limited development.
3) Community edition disappears, leaving only a paid version with support included.
4) More money is poured into the project, mutating it into some sort of Oracle, Jr.

Out of all of these, I think that 2 is the most likely, if anything happens at all. Oracle clearly supports open source, so it would seem counterintuitive, to me, for them to completely ditch MySQL. However, are they a business and in the end they're out to make money. So, the prospect of MySQL being somewhat hampered from a support POV seems plausible in an effort to get enterprise customers to migrate from MySQL to Oracle.

---

### Post by zekopeko on 2010-02-15
I don't think the majority on these forums understands that MySQL and Oracle 11g are on completely different levels. That is why the EU gave a green light on the acquisition deal. They just don't compete even in the enterprise sectors.

I think that Oracle will continue to fund MySQL because it is a potential cash cow for lower tier business solutions.

OO.org will hopefully final blossom into a true community project. Sun was notorious at how badly they managed the project community-wise. If Oracle is willing to invest heavily they could create an awesome office suite that could directly compete with MS Office. Give it some cloud functionality that is powered by Oracle tech and you have a nice product.

---

### Post by lykwydchykyn on 2010-02-15
> **zekopeko said:**
> I don't think the majority on these forums understands that MySQL and Oracle 11g are on completely different levels. That is why the EU gave a green light on the acquisition deal. They just don't compete even in the enterprise sectors.

I think that Oracle will continue to fund MySQL because it is a potential cash cow for lower tier business solutions.


As someone who works with Oracle and MySQL every day, I completely agree with you.  They're both SQL databases, but the similarity stops there or shortly afterwards.  Different feature sets, different SQL syntax, different architectures.  The idea that MySQL would ever become "Oracle lite" is just too far fetched; both codebases are very old and complex, trying to reconcile them would not only be pointless it'd be nigh on impossible.

Last time I sat down with our Oracle reps I got the feeling they are something in the vein of IBM in being a "solutions" company.  In other words, they're more interested in selling you a package that you'll be paying annual support on for 10 years than making sure their flagship SKUs are running on every computer.  In other words, I don't think it matters to Oracle if you're paying them for MySQL support or Oracle support, as long as you're paying them.

---

### Post by Twitch6000 on 2010-02-15
Well Novell has the open office problem fixed with go oo.

As for mysql I think redhat will probably fork it if orcale doesn't work on it.

---

### Post by RiceMonster on 2010-02-15
> **Twitch6000 said:**
> Well Novell has the open office problem fixed with go oo.

As for mysql I think redhat will probably fork it if orcale doesn't work on it.

Why Red Hat?

---

### Post by mickie.kext on 2010-02-16
> **Twitch6000 said:**
> As for mysql I think redhat will probably fork it if orcale doesn't work on it.

No way, Red Hat invested in EnterpriseDB and they are pushing Postgres. 

There is already few MySQL forks, most notable are MariaDB and Drizzle.


MariadDB is from original MySQL founder Monty Widenius, who founded new company called AskMonty. They plan to stay compatible with MySQL. Drizzle is slimed down version on MySQL intended primarily for web serving.  They are planing to break away from MySQL code-base and change licence to more permissive LGPL in future. 

> I don't think the majority on these forums understands that MySQL and Oracle 11g are on completely different levels. That is why the EU gave a green light on the acquisition deal. They just don't compete even in the enterprise sectors.
That is very true right now, but you do not see bigger picture. Oracle is old traditional RDBMS, while MySQL tried to be different and inovative, and one day maybe displace Oracle. Saying "they are different and they are not competing" is same as saying that for Itanium 9300 and POPWER7 CPUs. Yes, one is EPIC other is RISC and one is ultra expensive (POWER) while other is cheper (Itanium) and yes they are completely different beasts. But they are in same market, UNIX and Linux server market, so both are after similar customers and therefore they are competing. Same goes for MySQL and Oracle DB. They are both ofter different solutions to some of same problems and while Oracle is superior now, MySQL AB and Sun had chance to change that in years down the road. Now that chance seems lost. 

So it was not about competition *now*, it was about competition *in the future*. It takes years to gain market position and chance to be serious competitor.

---


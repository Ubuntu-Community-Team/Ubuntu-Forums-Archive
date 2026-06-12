---
title: "Needed: New coldfusion Server"
date: 2009-10-27
forum: Server Platforms
---

### Post by conradin on 2009-10-27
Hi all,
I have a windows server 2003 computer running my website. I host a variety of client and server applications most of which I know can be run on an Ubuntu Server. However, I am running cold-fusion mx, and I'm a bit gun shy at this point regarding macro-media products on Linux. Is there a free / open-source solution to run (all things) cold-fusion mx on Ubuntu?

(yes I'm aware of cold-fusion support in the newer versions of Cold Fusion. I have no funds allocated to purchase newer software at this time)

---

### Post by Vegan on 2009-10-27
You could run both a Windows and a Linux sever side by side. Linux knows how to live on such a network. It can take some tasks away from Windows but you reliance on ColdFusion is a nuisance.

For this reason, the two machine idea allows you to investigate alternatives or roll your own. Today ColdFusion competes with PHP and ASP. If you are up to it, its not that hard to change to another web tool. 

I use PHP as its fine for my needs, I do not need the baggage of ColdFusion that tries to drag every known application under the sun to the web. They call it middleware. Oracle has a competing product called OracleFusion based Java. Oracle gives it away to developers to evaluate.

PHP has one primary feature, its free! I use the phpBB for my forum, its fast and uses a SQL database to store articles, not unlike the way this forum does.

So depending on you needs Linux may not be really suitable. It's all dependent on what all you are doing.

Hardware is cheap, a PC is a commodity.

---

### Post by conradin on 2009-10-28
The server I am currently managing is nearly a decade old with possibly hundreds of thousands of pages scripts and application dependencies. Any sort of migration is going to stink. This said, I actually like your idea Vegan, of breaking up the services. 

 If i revamp it will probably be with an open-source CMS which are mostly PHP to my knowledge. 

I looked around in the forums and saw Ratlio although that looks like a pay version cold fusion alternative. Online I have seen a java based product called "smith". Ive never used it or even heard of it until now.

---

### Post by Lars Noodén on 2009-10-28
Adobe advertises a more recent version, Coldfusion 9, as running on Ubuntu 9.04.  Which is a good surprise and not what I would expect from Adobe's reputation.  I presume that the page may show 9.10 soon:
[http://www.adobe.com/products/coldfusion/systemreqs/](http://www.adobe.com/products/coldfusion/systemreqs/)

As for FOSS systems that can run coldfusion code, I'm not sure.  
Here's one guess:
 [http://www.smithproject.org/](http://www.smithproject.org/)

You might find it easier to develop in java server pages (jsp) than php.  Apache's Tomcat helps there.  php gets a lot of press, and there are good things to say about it, but is overrated.  It has come a long way, but has really only caught up to where perl and others were years and years ago.  (See for example HTML::Mason or the rest of CPAN)   I've also seen fast, custom work done using Ruby-on-Rails.  

With as big a change as you are proposing, it would be very, very well worth surveying the landscape to see what is there already.  Just to pick one, I would take a look at Apache's Lenya.
[http://lenya.apache.org/](http://lenya.apache.org/)

---

### Post by conradin on 2009-10-29
Thank you all for the input, I'm going to consider it.

---

### Post by Nixforce on 2009-10-30
Open Bluedragon is free. Here is from there site.

> Open BlueDragon, is the worlds favourite open source GPL J2EE CFML runtime engine, supporting all the popular CFML frameworks. Open BlueDragon is the open source version of the popular BlueDragon CFML engine. BlueDragon was the first ever CFML alternative engine and with over 10 years of production banked you can be assured it is ready for deployment.

There is an installation guide at [wiki.openbluedragon.org]("http://wiki.openbluedragon.org/wiki/index.php/Launching_the_Installation_Script_%28OBD_Installer%29") and it does mention Ubuntu as a support OS.

---


---
title: "Apache vs. Windows Server 2003"
date: 2005-01-11
forum: The Cafe
---

### Post by BWF89 on 2005-01-11
I was talking to a friend on AIM a few hours ago. My friend has some sort of an online hosting buisness and he said that after talking with alot of the companies before he would use their service they said that Windows Server was a better quality than Linux (what I presume to be Apache). But I argued that even if WS03 was better than Apache, Apache was free so you could use the money you saved from buying a free server on buying more server boxes to make up for it so their essentually even?

Without putting all the "Free & Open Software is better than propriatory no matter what" spin on it, is Windows Server better than Apache?

Oh and my friend is useing Linux (Apache) for his hosting needs because he can't afford a Windows Server. But if he has some money he said he would go with Windows...

---

### Post by Rogee on 2005-01-12
As a web developer, I would take BSD/Apache over Windows IIS any day.  Linux works fine as well.

I am a little biased though, as I program mostly in PHP and use either MySQL or PostgreSQL.  But with all the sites I have pushed live, I have had the most problems with IIS servers.

I'm sure Windows Server is fine, but I just find Apache to be much easier.  You CAN run Apache on a Windows machine, but I've never seen that on any professional web hosting packages.  I guess it depends on what language you write your scripts in and what you're familiar with.

---

### Post by nocturn on 2005-01-12
Well,   I you check Netcraft ([www.netcraft.com](www.netcraft.com)), it shows that Apache has a 68% market share and rising in webservers where MS IIS has 21% and falling.

On, top of that, the longest uptimes are all held by Unix-like machines running Apache (Linux does not often make these, but if you read the FAQ, there is a problem getting the uptimes from Linux boxes that resets it after +-490 days, windows uptimes are measured correctly).

Most serious hosting providers run on Linux and BSD, this includes the really big ones like AKAMAI. 
So, in this market, MS fails to gain a substatantial market share (21% is very low for the world's biggest software company).

BTW, most of hotmail and Microsoft.com runs of Solaris, FreeBSD and *gasp* Linux.  They use these especially as cluster controllers to protect the weaker Windows servers behind them.  If you google for the attempts MS has made to migrate Hotmail to windows, you can have a good laugh.

---

### Post by nocturn on 2005-01-12
BTW, did you friend mention what he finds better in Windows server/IIS over Apache/Linux?

Many people (including a lot of admins) dislike Linux/Apache/MySQL  because it does not have a point-and-click install and administration.  It requires a little more knowledge to set up properly then Windows/IIS/MSSQL, but the latter installs with insecure defaults, so it works out-of-the-box.

I have found it very typical of MS oriented people to say 'I don't like Linux' or 'Windows is superior', but most of them fail to express exactly what is better about Windows.

---

### Post by mctavish on 2005-01-12
I've never used windows server 2003 in anger, but I do have a few certifications in it - necessary for my uni. 

Anyway, what I want to say is that server 2003 can fill many roles, for example as a DNS server, DHCP server, 'soft' router, clustering, or web server. 

Definitely I'd see linux/bsd as a very strong competitor to server 2003 in the web server area.

Where server 2003 is strong though is large network infrastructure and adminitration through active directory. I don't know of linux having an alterative to that. Not to say that one doesn't exist though.

---

### Post by nocturn on 2005-01-12
[QUOTE=mctavish]I've never used windows server 2003 in anger, but I do have a few certifications in it - necessary for my uni. 

Anyway, what I want to say is that server 2003 can fill many roles, for example as a DNS server, DHCP server, 'soft' router, clustering, or web server. 

Definitely I'd see linux/bsd as a very strong competitor to server 2003 in the web server area.

Where server 2003 is strong though is large network infrastructure and adminitration through active directory. I don't know of linux having an alterative to that. Not to say that one doesn't exist though.[/QUOTE]

Not to flame anyone but Linux/BSD and Unix dominate the Webserver/DNS market.
See my post above, MS has only 21% market share in webservers while none of the root DNS servers are running windows.    Server 2003 hopes to gain some share of the markets you described.

Active Directory is basicly just a non standard implementation of LDAP and Kerberos, which are not MS techologies, they are available under OSS licenses.    

You can replicate most of it's functionality with OpenLDAP and MIT-kerberos or Heimdal on Linux.  Although integrated solutions are available from Novell.

---

### Post by tiiim on 2005-01-12
[QUOTE=mctavish]I've never used windows server 2003 in anger, but I do have a few certifications in it - necessary for my uni. 

Anyway, what I want to say is that server 2003 can fill many roles, for example as a DNS server, DHCP server, 'soft' router, clustering, or web server. 

Definitely I'd see linux/bsd as a very strong competitor to server 2003 in the web server area.

Where server 2003 is strong though is large network infrastructure and adminitration through active directory. I don't know of linux having an alterative to that. Not to say that one doesn't exist though.[/QUOTE]
 deff bsd/Linux (UNIX-like enviorements) dont fall for the Windows point and click drag you in features. Point and click does not nessary mean better... who wants graphics on a server anyway... slow down.

If he wants security openBSD will keep him tight and stable for years. But basically any UNIX-variant including Linux is the best way not cos' its free it is also reliable, well supported and stronger in security.

---

### Post by machiner on 2005-01-12
This is a silly topic.  If you really think your site needs to be hosted on a windows box, you should go back to tetris.

BAAAAAAAAAAAAAAaa hahahahahhahahah..

Silly.

---

### Post by az on 2005-01-12
"This is a silly topic. If you really think your site needs to be hosted on a windows box, you should go back to tetris."

Actually, it is a good question.


Other things to consider are TCO and FUD.

TCO is Total Cost of Ownership.  While Linux (and other platforms like BSD) are free, there still is a cost involved.  If you are an enterprise that already has an IT department that is trained to use Microsoft products (many many schoold just teach MS) it would be neccessary to either hire or train people in using linux.  It costs nothing for you to learn, because you do it in your spare time.  If, however, you do it on company time, it involved meeting set goals (exams, certifications) and doing so while being payed.
Another option is to purchase support.

It can be argued back and forth which platform offers the lowest TCO.  You will have to make your own opinion on that.

FUD refers to Fear, Uncertainty and Doubt.  People are conservative when it comes to money.  If something works, why risk having to spend money to fix it after you bugger it up by trying to make it better.  If many people around you are using Microsoft products and you have no good examples of successful buisnesses that use linux, you will end up using MS.

The fact that there are lawsuits and software patents threatening linux and open source software increase FUD.  The lawsuits do not have to be valid, and the threats do not have to be great - they just have to be there.

Microsoft boasts that it has a better support system for their platform.  They say that there is a clear line of responsability.  To someone who does not know how open source buisinesses make money, this is a convincing argument.
Open Souce business is based on providing support.

Anyway, again, good question.

---

### Post by nocturn on 2005-01-12
[QUOTE=azz]"This is a silly topic. If you really think your site needs to be hosted on a windows box, you should go back to tetris."

Actually, it is a good question.
[/QUOTE]

This is indeed a good question, but the friend of the original poster did not give his reasons for preferring W2003 over Linux, which is a shame.

And some of the reasoning is off as someone running a public webserver (or hosting company) off Windows will be the odd one (refering to market share).

---

### Post by shimon on 2005-01-12
this will answer the questions

Apache:
[img]http://secunia.com/graph/?type=sol&period=all&prod=72[/img] [img]http://secunia.com/graph/?type=cri&period=all&prod=72[/img]

------------------------------------

IIS 6:

[img]http://secunia.com/graph/?type=sol&period=all&prod=1438[/img] [img]http://secunia.com/graph/?type=cri&period=all&prod=1438[/img] [img]http://secunia.com/graph/?type=imp&period=all&prod=1438[/img]

Source: secunia.com

edit: i officall proclame vb as the werst implamation of bbcode the img tag does work on those ^^

---

### Post by machiner on 2005-01-12
C'mon, Azz...do you sell for Microsoft?

This argument has no merit.

<----------------edited because I don't want to play here - it's a propoganda filled useless argument------------------>

Do what you want.

a ps for systems integration -- off topic, not serving webs but definately part of the COST and FUD nonesense:
[http://www.linuxjournal.com/article/8026](http://www.linuxjournal.com/article/8026)

---

### Post by jdodson on 2005-01-12
[QUOTE=nocturn]Well,   I you check Netcraft ([www.netcraft.com](www.netcraft.com)), it shows that Apache has a 68% market share and rising in webservers where MS IIS has 21% and falling.[/QUOTE]

i am not sure you are saying this, but to be fair just because some "product" holds the market does not mean it is the best.

mcdonalds is the "king of fast food" in the united states.  what i mean by that is they are the market leader, does that mean that thier food is the best?  no.  because windows is the market leader for desktop computers does that mean it is the best, well honestly that is debatable, however personally i dont think they are.

now to answer the question on if apache is better than iis.  

ok well lets start breaking it down a bit.  when you buy any product you must look at a few things: price, value, lifespan, quality and need.  you also have to see if the product will do what it claims, not sure what word you would use for that.   

so when you look at price, it is fairly simple.  what price is the lowest?  however you must also contrast that with the others such as value, lifespan, etc.  so if you buy something for 3 cents that has a lifespan of 2 minutes and another product costs 4 cents and has a lifespan of 4 minutes, obviously the 4 cent item is a better deal because it has a double lifespan.  not this would not work if you only NEEDED something that had a 2 minute lifespan, then obviously you would be wasting that extra cent.

value, this is somewhat subjective so i will simply leave this to subjectivity.  suffice it to say i understand what i consider value to be, and i hope in your mind you know that as well.

quality.  if two items both cost 3 cents and one item breaks down 35% of the time whereas the other item only breaks down 2% of the time and all other factors are the same(which they never are, but lets ASSume they are) then obviously go with the product that breaks down less.

so when you look at a product it is good to consider a few things.  

"what do i NEED to get the job done" - making a list is nice.  realize that purchasing a product that goes above these requirements is not necesarally a good thing.  for instance if you need something that only cuts oranges, why would you get something that cuts oranges and banannas if you are never going to cut bannanas?  if the orange/bannana slicer takes up twice as much space and costs more, what have you gained?  it is worth mentioning that planning to the future is a good thing, however buy things that are in idle are useless to a corporation even if you got a "good deal."  purchasing something for the sole reason of "it was a good deal" is stupid.

"what product is more reliable" - in the case of a server you must look at uptime, virus threats/spyware threats and securability(i.e. how hard is it to secure this machine and can it be done).

"how much is this going to cost me in the short and long run" - you need to look at the sticker price and beyond the sticker price.  support costs should be considered here as MANY businesses require support of somekind.

"does this product contribute to the bottom line?" - not all aspects of a buisness directly contribute to the bottom line.  i.e. IT might not bring in the money for a corporation, however it does keep it moving twoard that goal.  if a product is purchased for show or for some function that does not aid in making a profit for the corporation, it is useless.  if you are not running a business this does not apply.

"does this product help or hinder my choice or freedom" - this is pretty sticky as freedom is not always needed for a buisness to thrive.  you do not NEED to be free(as in freedom) to make a profit.   if you are a pure windows shop, switching to a non-windows solution is hell simply because windows is so proprietary.  if you choose products with vendor lock-in hooks, do not be surprised that it might be difficult to switch to another "solution."  many companies do not consider this and it perpetuates the continuation of proprietary solutions.

so to answer the question if apache is better than iis?  well, what do you think?  this is not a loaded question, i am not saying gnu/linux is better(though, personally i do think gnu/linux is better).  i am saying that the answer to the question is for every person to make.

---

### Post by BWF89 on 2005-01-12
Thanks jdodson. Now, where would I be able to pick up one of these orange/bananna slicers :) ?

---

### Post by jdodson on 2005-01-12
[QUOTE=BWF89]Thanks jdodson. Now, where would I be able to pick up one of these orange/bananna slicers :) ?[/QUOTE]


the home shopping network at 3am :)

---

### Post by az on 2005-01-12
"C'mon, Azz...do you sell for Microsoft?"


No.  Read my post again.  I am just explaining the way other people see it.


The fact is, it just takes one higher placed IT guy to have had a bad experience with Linux or Unix in general some time in the past to XNay this option today.

---

### Post by nocturn on 2005-01-13
[QUOTE=jdodson]i am not sure you are saying this, but to be fair just because some "product" holds the market does not mean it is the best.
[/QUOTE]

I'm sorry for the duality.  No, I do not think market share in itself is any reflection of the quality of a product.    I referred to it because some people seem to think Win/IIS is the standard on servers as it is on the desktop and Apache/*nix is the new guy on the block,this is simply not true.

What I do see as a support for the quality of Apache compared to IIS is Microsoft's failure to 'eat it's own dogfood'.  Not being able to run Hotmail and microsoft.com of their own products is very bad marketing-wise.  It would be like Ford standardising on Mazda as company cars because of troubles with their own product.

Again, it is a shame that the friend of the poster did not specify what his issues with Linux/Apache are.

---

### Post by nocturn on 2005-01-13
[QUOTE=shimon]this will answer the questions

Apache:
[img]http://secunia.com/graph/?type=sol&period=all&prod=72[/img] [img]http://secunia.com/graph/?type=cri&period=all&prod=72[/img]

------------------------------------

IIS 6:

[img]http://secunia.com/graph/?type=sol&period=all&prod=1438[/img] [img]http://secunia.com/graph/?type=cri&period=all&prod=1438[/img] [img]http://secunia.com/graph/?type=imp&period=all&prod=1438[/img]

Source: secunia.com

edit: i officall proclame vb as the werst implamation of bbcode the img tag does work on those ^^[/QUOTE]


Shimon, I looked at these graphics, but they mean little by themself.
To interpret these,  you will need more information about the data itself.  
A total number of vulnerabilities is not good for comparison, specially between a single platform product (IIS) and a multiplatform one (Apache).

---

### Post by Magneto on 2005-01-13
[QUOTE=nocturn]Shimon, I looked at these graphics, but they mean little by themself.
To interpret these,  you will need more information about the data itself.  
A total number of vulnerabilities is not good for comparison, specially between a single platform product (IIS) and a multiplatform one (Apache).[/QUOTE]
 I do winblows and unix administration and there's no way IIS is better unless you're supporting a pure winblows environment and are utilizing other server products in the Microsoft line, other than that I see no benefit to it. The security issues are way too scary, not that apache isnt prone to security flaws too but I just get alot more updates with apache and when I get patches for IIS its usually right before or after some crucial scary critical flaw is announced.

---

### Post by nocturn on 2005-01-13
[QUOTE=Magneto]I do winblows and unix administration and there's no way IIS is better unless you're supporting a pure winblows environment and are utilizing other server products in the Microsoft line, other than that I see no benefit to it. The security issues are way too scary, not that apache isnt prone to security flaws too but I just get alot more updates with apache and when I get patches for IIS its usually right before or after some crucial scary critical flaw is announced.[/QUOTE]

I agree with you.  What I also forgot to mention is the window-of-oportunity for a vuln. and if exploits are in the wild.

MS has a very slow response to security issues in general, there are issues that have been outstanding for over 2 years (search for bugs found by gobbles if you are interested, these are mostly IE).

I have found Apache very responsive to bugs found in it's software and most are fixed before exploits hit the web, which minimizes the impact)

To compare security, this is a vital metric.

I have been running (public) Apache webservers for years, and it is a fine piece of software.  It is not perfect, but compared to the mess IIS makes (I've had to run this too), it is a pleasure.

---

### Post by az on 2005-01-13
"Not being able to run Hotmail and microsoft.com of their own products is very bad marketing-wise"

To be fair, I strongly beleive that this is not true.

A year and a half ago, Microsoft was fighting a DOS attack and had a few of their servers switched to another server (Akamai, I beleive) for a few hours.  When it was revealed that the company sometimes used linux it caused the biggest stink.  It did not take long for MS to switch again.

I do not think that they would run Hotmail and the like on anything but their own stuff.

Can someone substantiate this claim?

I am not trying to be partisan here, just objective.

---

### Post by nocturn on 2005-01-13
[QUOTE=azz]"Not being able to run Hotmail and microsoft.com of their own products is very bad marketing-wise"

To be fair, I strongly beleive that this is not true.

A year and a half ago, Microsoft was fighting a DOS attack and had a few of their servers switched to another server (Akamai, I beleive) for a few hours.  When it was revealed that the company sometimes used linux it caused the biggest stink.  It did not take long for MS to switch again.

I do not think that they would run Hotmail and the like on anything but their own stuff.

Can someone substantiate this claim?

I am not trying to be partisan here, just objective.[/QUOTE]

I hadn't checked lately (I just did).  But what I'm talking about predated the Akamai migration.  Netcraft used to show most sites owned by MS to run FreeBSD and some on Solaris.

Here are 2 articles on the migration problems of hotmail:
[http://www.theregister.co.uk/2001/12/12/microsoft_hotmail_still_runs/](http://www.theregister.co.uk/2001/12/12/microsoft_hotmail_still_runs/)
[http://www.theregister.co.uk/2002/11/21/ms_paper_touts_unix/](http://www.theregister.co.uk/2002/11/21/ms_paper_touts_unix/)

A netcraft check of MSN today shows most of the domains running of Windows, yet there are still FreeBSD entries remaining:
FreeBSD  	 unknown  	 14-Aug-2004  	 207.68.172.246  	 Microsoft
FreeBSD 	Microsoft-IIS/5.0 	19-Oct-2003 	207.68.172.246 	 Microsoft FreeBSD 	Microsoft-IIS/5.0 	30-Sep-2003 	207.68.172.246 	 Microsoft 
(note that the fact theat the webserver shows IIS mostly indicates that FreeBSD is running as a cluster controller for Windows backend servers).
The query: [http://uptime.netcraft.com/up/graph/?host=msn.com](http://uptime.netcraft.com/up/graph/?host=msn.com)

Microsoft.com today seems mainly Windows (following the decision outlined in the second article I quoted).

---

### Post by nocturn on 2005-01-13
This is one of my farvourites:
Microsoft uses FreeBSD to host anti-Unix site 
[http://www.theinquirer.net/?article=3077](http://www.theinquirer.net/?article=3077)

---

### Post by az on 2005-01-13
Those articles are quite old.  2001 and 2002.

---

### Post by nocturn on 2005-01-14
[QUOTE=azz]Those articles are quite old.  2001 and 2002.[/QUOTE]

Yes they are.  They are mainly about the trouble they had running Windows 2000.
In the last years, I have not really followed MS any more, I'm focussing on Linux/Unix.

But, although they are old,  the fact that MS was only able to switch to Windows webservers in the last 2 years does mean that their Internet products are the newbies on the market.  The same goes for PDA's (although they now also dominate that market).

This is different from what many people belief, that MS holds a majority of the server market and that *nix/Apache is only now competing (like FireFox).

---

### Post by az on 2005-01-14
"this is different from what many people belief, that MS holds a majority of the server market"

Well, there is webserver and there is corporate server....  Have you seen statistics on where MS is in that market?

Which one generates more revenue?

---

### Post by nocturn on 2005-01-14
[QUOTE=azz]"this is different from what many people belief, that MS holds a majority of the server market"

Well, there is webserver and there is corporate server....  Have you seen statistics on where MS is in that market?

Which one generates more revenue?[/QUOTE]

Maybe, but revenue is not an issue for Apache, Linux or FreeBSD.

BTW, MS holds a large share for corporate servers, but nowhere near the 99% dominance they have on the desktop.    Exchange is quite big nowdays, but many 'big' apps (SAP, ClearCase, ...) still run of Unix most of the time.  This is also a big-money market where they would like to get a piece of, but it is hard for them to gain some ground there.

---

### Post by az on 2005-01-14
"Maybe, but revenue is not an issue for Apache, Linux or FreeBSD"

What do you mean by that?


My point is that it generates more income for Microsoft to cater to this clientele.  That makes it a tougher market to crack.  

Equaly, it also generates more income for an open-source company to offer this kind of service to a company.  Revenue makes the world go 'round.

---

### Post by nocturn on 2005-01-14
[QUOTE=azz]"Maybe, but revenue is not an issue for Apache, Linux or FreeBSD"

What do you mean by that?
[/QUOTE]

I mean for Apache/Linux/FreeBSD themselves only number of installs and connection loads are important.  Because the software is Free (both meanings), there is no revenue.

> 
My point is that it generates more income for Microsoft to cater to this clientele.  That makes it a tougher market to crack.  

Equaly, it also generates more income for an open-source company to offer this kind of service to a company.  Revenue makes the world go 'round.

Possibly, but a service company can make good money out of (remote) support for complex servers such as SAP or ClearCase.

MS is stong in the corporate server (Exchange I mean) through leveraging their Dekstop dominance (Outlook).

The integration of PIM functions in one server is actually a very good one (not an MS invention either).  That is were I see a lag on the OSS side (although you can replicate much of that functionality and projects like OpenXchange are rising). 
Commecially, Lotus Notes is an alternative to this, although it is not as widely used as in the past.

---

### Post by Magneto on 2005-01-14
[QUOTE=nocturn]  Exchange is quite big nowdays, but many 'big' apps (SAP, ClearCase, ...) still run of Unix most of the time.  This is also a big-money market where they would like to get a piece of, but it is hard for them to gain some ground there.[/QUOTE]

Would you rather run a database on x86 MS 2003 Server or HPUX, AIX or Solaris? Even SCO Openserver?   That's why many companies pay 3-10 times the amount on hardware and OS licensing fees for server reliability and stability.

Microsoft has huge Server market share, but this isnt a Server OS thread so all this stuff is offtopic :)

Apache Web Server is the premier webserver in the marketplace and it is free.  When compared to IIS embedded in the Operating System of Windows 2003 Server, there is no comparison. One requires purchase and doesn't offer the same level of support.  

If you want to compare based on a specific case then that would be a better discussion.

---

### Post by nocturn on 2005-01-14
[QUOTE=Magneto]Would you rather run a database on x86 MS 2003 Server or HPUX, AIX or Solaris? Even SCO Openserver?   That's why many companies pay 3-10 times the amount on hardware and OS licensing fees for server reliability and stability.[/QUOTE]

For me personally it is a no-brainer.
First choice: Linux/Apache/MySQL 
Second choice: Solaris/Apache/MySQL

MS does not make my lists.

---

### Post by Magneto on 2005-01-14
[QUOTE=nocturn]
MS is stong in the corporate server (Exchange I mean) through leveraging their Dekstop dominance (Outlook).

[/QUOTE]

Yes but that isn't necessarily the case anymore. Many people select  Windows Server OS because of the company's support infrastructure, ease of use(supposed), availability of knowledgeable technicians, relative low cost when compared to other enterprise commercial operating systems and their respective hardware platforms.  The latter argument also being the reason for the surge in Linux server expansion in the marketplace. The disinformation about  Microsoft is thick in the industry too.  The TCO lies regarding Linux and Windows have not been put to rest yet either.

---

### Post by lozzd on 2005-01-15
I compromise.

/me is one of the only people that use Apache 2 on Windows... 
peace of piss to set up, and my web server has now been running the 80 days straight its been a web server. not a problem. Slowly getting into linux now, but a simple thing like finding the php config file is a challenge for me wheras i know exactly where it is on windows.

Only thing i can think of for a good reason to have IIS is a program that requires it... such as exchange's webmail program, etc.. in which case i'd have the IIS proxying through apache.

---


---
title: "Crawler stuck on my front door"
date: 2009-10-10
forum: Security
---

### Post by Silvernail on 2009-10-10
My ban log show a crawler has made 849 pages of 50 attempts to log on since Sept 15. The  IP is 77.88.29.248. 

Is the any way to stop this site short of catching a plane  to Kiev UK and shooting the computer?

Before the 15th I sent the site an email asking to stop and they answered that I should  do something on my end.

Well I already  had. I put them on permanent ban.

TIA
Dave

---

### Post by Chayak on 2009-10-11
Reconfigure your SSH to work on a higher port like 2200.  Brute force bots typically only try port 22.

---

### Post by lensman3 on 2009-10-11
Add a block rule in IPTABLES for the IP address.  You might also block the whole IP range.  Have iptables quietly drop all packets from that address.  

Here is one I used to use in my script for block the IP address ranges for the US military.

DOD_NET="214.0.0.0/8 \
         215.0.0.0/8" 
   for NET in $DOD_NET; do  
       $IPT -A blocked -p tcp  -j REJECT --reject-with tcp-reset
   done


You may not want to reject with tcp-reset, because I think this send a packet back, but then the other end has to deal with it.

I block entire class 1, 2, and 3 IP ranges especially from eastern Europe and Asia.  I consider it OK for me to contact them, but not the other way around with my current config.

---

### Post by Lars Noodén on 2009-10-12
lensman3 has the right idea with IP Tables.  

Also try looking up the IP number using 'whois'.

If the contact information is different than the address you have already contacted, then let them know what is going on.  The ISPs have an obligation to deal with crackers.

---

### Post by scorp123 on 2009-10-12
> **Lars Noodén said:**
>  The ISPs have an obligation to deal with crackers. Yeah right. Good luck with that, especially outside of the EU or USA. :D

---

### Post by Silvernail on 2009-10-12
> **Lars Noodén said:**
> 
Also try looking up the IP number using 'whois'.

If the contact information is different than the address you have already contacted, then let them know what is going on.  The ISPs have an obligation to deal with crackers.

I did and did.
I  got a reply that it was their crawler and I should do something on my end to prevent it  if I didn't like it.

```
whois 77.88.29.248
```
returns
> 
role:           Yandex LLC Network Operations
address:        Yandex LLC
address:	1 bld. 21 Samokatnaya St.
address:	111033
address:	Moscow
address:	Russian Federation
phone:		+7 495 739 7000
fax-no:		+7 495 739 7070
remarks:        trouble:      ------------------------------------------------------
remarks:        trouble:      Points of contact for Yandex LLC Network Operations
remarks:        trouble:      ------------------------------------------------------
remarks:        trouble:      Routing and peering issues:  [email]noc@yandex.net[/email]
remarks:        trouble:      SPAM issues:                 [email]abuse@yandex.ru[/email]
remarks:        trouble:      Network security issues:     [email]abuse@yandex.ru[/email]
remarks:        trouble:      Mail issues:                 [email]postmaster@yandex.ru[/email]
remarks:        trouble:      General information:         [email]info@yandex.ru[/email]
remarks:        trouble:      ------------------------------------------------------
admin-c:        VLI1-RIPE
admin-c:	TVB11-RIPE
tech-c:         VLI1-RIPE
nic-hdl:        YNDX1-RIPE
mnt-by:         YANDEX-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@yandex.ru[/email]


---

### Post by pricetech on 2009-10-12
Moving SSH to another port should work.  I've done it on 2 Hardy machines, though it failed in Jaunty.

If you want instructions I'll see can I find my notes and either send them to you or post them.

---

### Post by scorp123 on 2009-10-12
> **pricetech said:**
> Moving SSH to another port should work. ... If you want instructions  Instructions? Like edit **/etc/ssh/sshd_config** and modify the "Listen" port or add another one? 

That's not really efficient IMHO. First of all I wouldn't do it on the Linux system's SSH configuration but rather I'd change the port-forwarding on the exterior router (this is assuming there is one ... ) so that at least internally inside the LAN the SSH daemon can continue to run port 22. 

Second, and that's IMHO far more efficient ... Why not ban the entire IP range and be done with it? If you have no business with those parts of the world then their IP ranges have no business being able to reach your system. At all. Ever. So ... lock them out.

You may want to read the manual on this:
```
man 5 hosts_access
```

As per manual, you'd edit this file:
```
gksudo gedit /etc/hosts.deny
```

Go to the bottom of the file and add their DNS name and their IP ranges -- according to the "whois" entry this would be:
```
ALL: 77.88.0.0/18
ALL: .yandex.ru 
```

This should prevent any connection attempts that originates from their networks.


EDIT: Syntax error corrected.

---

### Post by Lars Noodén on 2009-10-13
As scorp123, /etc/hosts.deny is another option.  I tried both IP Tables and /etc/hosts.deny earlier today and could not get a proper test of which is less of a burden on system resources.  

However, instead of this;

```
ALL: 77.88.0.0/18
[s]ALL: .yandex.ru[/s]
```I would propose skipping the DNS lookups, since you are checking your logs periodically any way.

```

ALL: 77.88.0.0/18
ALL: 77.88.29.0/24
ALL: 77.88.28.0/22
ALL: 77.88.24.0/21

```These were collected from whois:
|code]
whois 77.88.29.248|grep route|sed -e "s/route:/ALL:/;s/  */ /"[/code]

---

### Post by pricetech on 2009-10-13
> **scorp123 said:**
> 
That's not really efficient IMHO.

Efficient ??

> **scorp123 said:**
> 
 First of all I wouldn't do it on the Linux system's SSH configuration but rather I'd change the port-forwarding on the exterior router


That doesn't always work.  Some routers will only forward to the same port number.  I don't have an explanation for why, it's just an issue I've run into.

I will say this about changing the port;  IANA says 49152 to 65535 are the Dynamic / Private ports so I'd pick something in that port range.

Granted, some people consider changing the port to be "security through obscurity" but if you can make your front door invisible as well as locking it, why not ??

---

### Post by scorp123 on 2009-10-13
> **Lars Noodén said:**
>  ALL: 77.88.0.0/18
[s]ALL: .yandex.ru[/s][/code]I would propose skipping the DNS lookups  Hmmm ... Yes, why not. One less name lookup to bother your DNS with.

But I'd at least put it into a comment so when you check the file again in six months or so you still remember what that strange IP range is about, e.g.

```
# stupid spammers from
# *.yandex.ru:
ALL: 77.88.0.0/18
```

BTW ... Someone correct me, but **"denyhosts"** wasn't mentioned yet? In case someone is interested: That package will scan for failed login attempts and then automatically adapt the **"/etc/hosts.deny"** list based on the repeated failed logins you'd be getting. A similar mechanism would be **"fail2ban"** which works in a similar way, but instead of adapting **"/etc/hosts.deny"** it will auto-create firewall rules and block hosts via the built-in "iptables" firewall.

"Denyhosts" tutorial:
[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

"Fail2Ban" tutorial:
[http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

(that last tutorial is written with Debian "Etch" in mind ... but all the things shown there should work 1:1 in Ubuntu as well, given that Ubuntu is based on Debian)

---

### Post by scorp123 on 2009-10-13
> **pricetech said:**
> Efficient ?? Yes. Because: if someone _REALLY_ wants to seriously attack you they could just as well give you a really thorough port-scan from 0 all the way up to port 65535. A SSH daemon that is listening on one of those ports (instead of port 22) would sooner or later be found too. There are plenty of tools out there that will identify protocols by sending a few probe packets and evaluating the answers they get back. So moving SSH from port 22 to another port would not solve the problem ... you'd just be moving ports around until they find your SSH port again. That's what I meant.

So instead of that I'd rather consider banning the IP range of those guys once and for all. 

> **pricetech said:**
>  Some routers will only forward to the same port number. I know what you mean. Yes, some routers are very limited, unfortunately.

> **pricetech said:**
>  but if you can make your front door invisible as well as locking it, why not ?? As I said above: That would only be a temporary fix. Maybe it will work. Or maybe it will cause your attackers to start port-scanning you like mad until they find the open SSH port again. So the best thing here would really be if your router/firewall silently dropped all packets that originate from their IP range ... and that's it. You're a "black hole" to them. That's as close as "make your front door invisible" as it could get.

---

### Post by pricetech on 2009-10-13
> **scorp123 said:**
>   snip   
So instead of that I'd rather consider banning the IP range of those guys once and for all. 

/snip



I got it now.  You were talking apples and I was reading oranges.

> **scorp123 said:**
>  As I said above: That would only be a temporary fix. Maybe it will work. Or maybe it will cause your attackers to start port-scanning you like mad until they find the open SSH port again. So the best thing here would really be if your router/firewall silently dropped all packets that originate from their IP range ... and that's it. You're a "black hole" to them. That's as close as "make your front door invisible" as it could get.

I like to think that most attackers are inherently lazy, but since he has contacted the offending ISP who knows what they might try just to be vindictive.

---

### Post by Silvernail on 2009-10-13
I need to apologize  to all of you. I omitted some important information in my original post.

This attack is on my website.

Orbit.theplanet owns the hosting service.

I got in contact with them and they sent me an email saying they had found the server in Russia and was blocking it. The email was timed 9:32 am and I got it about 10. I looked and there was no entry in my ban log after 9:15. Went back this evening and it was at it again. The hits are coming about every 30 to 50 seconds apart.

Your dialog has not been in vail. I have learned a lot reading it.

Thanks.
Dave

---

### Post by scorp123 on 2009-10-14
> **Silvernail said:**
>  This attack is on my website.  And what exactly is it trying on your web site? To login or to copy the data?

I think "fail2ban" would still work here and modifying "/etc/hosts.deny" can't harm either.

---

### Post by phillw on 2009-10-14
Just for info. Yandex is Russias largest search engine - it's bots go a wandering like the google, yahoo, msn ones etc.

We have it pop by about once a week to have a look at a forum I help out with. The spider always behaves and identifies itself correctly as a search engine spider.
As with all the other allowed spiders, it never by-passes the 'no spiders allowed' notices for private sections.

ProjectHoneyPot have an apache module that links to their database thus providing an up to date Black-List. 

There is some more information on http:BL and how it works here.

[http://www.projecthoneypot.org/httpbl_api.php](http://www.projecthoneypot.org/httpbl_api.php)

But, as mentioned above - If you just want to stop Yandex, then IP blocking should do it for you - although I'm not sure what their entire list of IP addresses for their bots are.


Regards,

Phill.

---

### Post by scorp123 on 2009-10-14
> **phillw said:**
>  Yandex is Russias largest search engine I thought Google is the largest search engine -- anywhere :D

But thanks for the tip. :)

---

### Post by phillw on 2009-10-14
I am sure google IS the largest, by far, search engine !!  Yandex is a 'bit' player in comparrison !!

To tell all spiders not to index your site, simply put

```
[FONT=verdana][SIZE=2][COLOR=#000000]<meta name="robots" content="**no**ne"> [/COLOR][/SIZE][/FONT]

```

In your header - All well behaved spiders (including yandex) will take heed & not index the page.

A full article on the subject of spiders can be found here...

[http://www.thesitewizard.com/archive/robotstxt.shtml](http://www.thesitewizard.com/archive/robotstxt.shtml)

Regards,

Phill.

---

### Post by Silvernail on 2009-10-15
> **phillw said:**
> Just for info. Yandex is Russias largest search engine - it's bots go a wandering like the google, yahoo, msn ones etc.



From what you say, would the Google bot act the same way if I blocked it.

Would I be safe in allowing Yandex to access my web site. Although I can not see what anyone in Russia would want to know about fly fishing on the Texas gulf coast.

---

### Post by phillw on 2009-10-15
> **Silvernail said:**
> From what you say, would the Google bot act the same way if I blocked it.

Would I be safe in allowing Yandex to access my web site. Although I can not see what anyone in Russia would want to know about fly fishing on the Texas gulf coast.

The article I linked to earlier, has spider rules, you can choose to allow / block different spiders, no spiders or all spiders. 

I can only say how the site owner of the forum that I help out at has it configured.

All search spiders who correctly identify them-selves are allowed in the general 'public' area of the forums. This is where the threads and blogs are stored. 
No spiders are allowed access to profiles (human visitors only) nor are they allowed onto areas that are marked 'private' - such as 18+, community team board etc.

All spiders (and everyone else) are logged as to where they go. If a spider was found to be in breach of the rules - it would be banned, reported to project honey pot & a stiff letter sent to it's owner.

The link to Project Honey Pot also includes how a spider should identify itself in the octect returned when you query the http:BL listing.  All incoming IP's are tested against that BL (Which has caused some problems - with people having had current IP address used for bad things in the past) - Everyone on the forums I help out at, are in agreement that 'if in doubt - keep them out' - Some ISP's have issued members with new IP numbers, when it is shown that they are innocent.

The battle against 'baddies' and 'saddos' is a never-ending fight.

Sites such as Project Honey Pot and Stop Forum Spam maintain lists of 'bad' IP addresses - Both are free to join. We're currently just using project honey pot - but will probably be including stopforumspam in the forseeable future. We also, like most boards, require a valid email address to allow 'posting' rights.

To sum up - I don't know how popular fly fishing is in Russia - but by allowing what has always been a well behaved spider on VPOLink  onto your site, to index yours - you can find out :)

If you want a link to a site that provides free stats for your web-site, telling you where people come from & what they do - I'll happily send you the link that I'm using for my own site.

Regards,

Phill.
P.S. There is an ongoing discussion about Yandex's bots, here ..   [http://www.forumpostersunion.com/showthread.php?t=3973](http://www.forumpostersunion.com/showthread.php?t=3973)
With one exception of causing an 406 exception (that would be the fault of the bot & it seems to have been an isolated case) they are of the general opinion that it's an okay bot.

---

### Post by phillw on 2009-10-16
He he .... when I looked at this forum the stats say ....

			[[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/index.php#top") 			[Currently Active Users]("http://ubuntuforums.org/online.php"): 9306 (525 members and 8603 guests and 178 Spiders) 		

That's a lot of spiders wandering around - do say hello if you meet one - lol

Going back to project honeypot ...

[http://www.vpolink.com/blog.php?u=3](http://www.vpolink.com/blog.php?u=3)

Goes some way to sum up my thoughts on hackers / errant spiders.
That particular spider now shows as a 'bad-un' on all sites who are members of project honey pot and use the http:BL

Phill.

---

### Post by Silvernail on 2009-10-16
Anybody know anything about this crawler?
> dave@gadabout:~$ whois 208.115.111.247
dotnetdotcom.org 208-115-111-240-SLASH28 (NET-208-115-111-240-1) 
                                  208.115.111.240 - 208.115.111.255
Wowrack.com WOW-ARIN-NET2 (NET-208-115-96-0-1) 
                                  208.115.96.0 - 208.115.127.255

# ARIN WHOIS database, last updated 2009-10-16 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
> 
dave@gadabout:~$ traceroute 208.115.111.247
traceroute to 208.115.111.247 (208.115.111.247), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.273 ms  0.361 ms  0.467 ms
 2  tx-76-6-64-1.dhcp.embarqhsd.net (76.6.64.1)  29.668 ms  30.601 ms  32.302 ms
 3  tx-71-0-224-9.sta.embarqhsd.net (71.0.224.9)  33.730 ms  35.494 ms  36.897 ms
 4  ge-6-12.car1.Houston1.Level3.net (4.78.8.13)  40.029 ms  41.498 ms  42.704 ms
 5  ae-2-5.bar1.Houston1.Level3.net (4.69.132.230)  59.681 ms  59.900 ms  60.094 ms
 6  ae-13-13.ebr1.Dallas1.Level3.net (4.69.137.138)  53.926 ms  34.382 ms  36.513 ms
 7  ae-92-98.ebr2.Dallas1.Level3.net (4.69.146.91)  38.427 ms ae-72-78.ebr2.Dallas1.Level3.net (4.69.146.75)  39.649 ms ae-82-88.ebr2.Dallas1.Level3.net (4.69.146.83)  39.865 ms
 8  ae-2.ebr1.Denver1.Level3.net (4.69.132.105)  70.834 ms  71.062 ms  71.286 ms
 9  ae-1-100.ebr2.Denver1.Level3.net (4.69.132.38)  70.013 ms  70.241 ms  70.468 ms
10  ae-2.ebr2.Seattle1.Level3.net (4.69.132.53)  99.485 ms  99.713 ms  99.954 ms
11  ae-2-52.edge1.Seattle3.Level3.net (4.68.105.44)  95.995 ms  97.690 ms  98.844 ms
12  WBS-CONNECT.edge1.Seattle3.Level3.net (4.71.156.82)  100.419 ms  76.388 ms  76.373 ms
13  216.18.227.70 (216.18.227.70)  78.297 ms  79.393 ms  81.442 ms
14  216.18.239.2 (216.18.239.2)  82.632 ms  83.604 ms  85.290 ms
15  route.g3-4.sea.wowrack.com (216.176.189.2)  87.003 ms  89.187 ms  91.141 ms
16  crawl6.dotnetdotcom.org (208.115.111.247)  92.945 ms  95.059 ms  96.525 ms
dave@gadabout:~$ 


---

### Post by scorp123 on 2009-10-17
> **Silvernail said:**
> I can not see what anyone in Russia would want to know about fly fishing on the Texas gulf coast. Hmmm ... why not? Here in Switzerland we also get lots of Russian tourists. In some typical tourist destinations such as Gstaad and Davos they have now started to hire Russian-speaking people to accommodate the many Russian tourists. Apparently the Russians tend to spend money like mad, even more so when they feel right at home and the people in the shop speak fluent Russian too ... 

During the European soccer championship "Euro 2008" the many Russian millionaires that invaded cities such as Zurich and Berne (or Vienna in Austria) they literally "emptied" entire jewelery shops: they went inside and "armed" with credit cards and cash they emptied every shelf, every vitrine, every window ... Some of  those jewelery shops looked like they had been thoroughly robbed empty, except that the shop owners had big smiles on their faces.

So if Russian crawlers have started to take an interest in your web site ... who knows? Maybe fly-fishing in Texas will be the next big trend for Russian tourists ... ?

---

### Post by Lars Noodén on 2009-10-18
> **Silvernail said:**
> Anybody know anything about this crawler?

@ Silvernail : There is a list of many crawlers at [The Web Robots Pages](http://www.robotstxt.org/)
[http://www.robotstxt.org/db.html](http://www.robotstxt.org/db.html)

Sorry about missing the port 80, port 443 references implied but not named in the original post.  Based on the second reply to your original post, I incorrectly jumped to the conclusion that your machine was being hit on port 22.  

Any self-respecting crawler will be programmed to honor your settings in /robost.txt  Check your web server logs for that robot's activities and if it begins a crawl with a visit to your robots.txt file, then you should be able to ban it there.  ( I would have posted the link days ago but that particular site, or jumps in between, were unavailable to me.)

If you just want it to slow down the frequency of its visits, then you might add metadata to your web pages (or the engine generating your web pages) to tell the robot to cache the results for days, weeks or months, depending on how static the web pages are.  I'm not referring to  [ROBOTS=NOINDEX, NOFOLLOW](http://www.robotstxt.org/meta.html), but instead to using http-equiv to set a [date](http://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.3) in Universal Time and formatted.  e.g. **date ––utc +'%FT%T'**

```

<META HTTP-EQUIV="EXPIRES"
CONTENT="Mon, 02 Jul 2010 11:12:01 GMT">

```

For unrespectable web-crawlers, an IP Tables ban will work.

---

### Post by phillw on 2009-10-18
An additional look up area can be found here

[http://www.botsvsbrowsers.com/](http://www.botsvsbrowsers.com/)

I've checked a few lookups of spiders and it seems to have a good, upto date list.

Like the original OP I, too, popped an email over to yandex - asking that they provide a spider page for web-masters - I have not have an answer - if the OP could email me with the address that they used to elicit the reply 'do something your-self', I will explain to them that they are running real close to the line of being on a robot BL.

I still recommend the use of project honey pot for incoming spiders and any new members, along with caphta & verified emails.
As a spider cannot identify itself as a legit spider & be a harvester it will return a 'false' in the returned octect for being a spider.
They also give a 'score' of any incoming IP address. Not perfect - nothing is.. And, if u want to keep it upto date, use a quicklink or donate an MX record. It's a sorta nice, warming, feeling when the following drops into your inbox ...

[http://www.vpolink.com/blog.php?b=33](http://www.vpolink.com/blog.php?b=33)

That IP address is not only now on our blacklist, but also now will show up on everyone else who uses their database ..

[http://www.projecthoneypot.org/index.php](http://www.projecthoneypot.org/index.php)

I'm looking to fully integrate 

[http://www.stopforumspam.com/](http://www.stopforumspam.com/)

into our lookup list, both for receiving information from & sending 1st day attacks to.

The more web-masters who take part in these schemes, the better and more upto date these databases are.

Phill.

---

### Post by Silvernail on 2009-10-18
Sent you a private PM could not find an email address for you.

---

### Post by phillw on 2009-10-19
i used the addurl email address, don't know if i will get a response.

Phill.

---

### Post by Silvernail on 2009-10-19
Got your emails copies of your responce to Yandex. Thank  you for your help and involvement in this.

I guess I  will go ahead and install a 'robot.txt' file. *( interestingly, a search of this website  returns only 2 references to 'robot.txt'*.

Your wiki link is a great help.

Dave

---

### Post by Silvernail on 2009-10-19
How does this  happen? I notice that once or twice a day this crawler seems to slip in.

From my ban log
 > 	N/A  	Today at 09:37:56 PM  	
77.88.29.248 		N/A 	Today at 09:37:07 PM 	
77.88.29.248 		N/A 	Today at 09:36:18 PM 	
**77.88.29.248 		N/A 	Today at 09:35:28 PM **	
77.88.29.248 		N/A 	Today at 09:34:40 PM 	
77.88.29.248 		N/A 	Today at 09:33:51 PM 	
77.88.29.248 	


From my Guest/Users on  line
> 
Guest  (220.181.53.229)  	09:46:01 PM  	Logging into the forum.
Guest (65.55.207.69) 	09:42:27 PM 	Viewing the topic TRADE 20 gallon Aquarium for fly rod & reel.
**Guest (77.88.29.248) 	09:35:28 PM 	Viewing the board index of Texas Flyfishers Piscatorial Patter.**
Guest (65.55.207.101) 	09:19:57 PM 	Viewing the board Spring Creek.
Guest (65.55.207.131) 	09:18:57 PM 	Viewing the topic August Outing: Port Mansfield - Getaway Adventures Lodge.
Guest (72.30.79.96) 

---

### Post by Lars Noodén on 2009-10-20
> **Silvernail said:**
> *( interestingly, a search of this website  returns only 2 references to 'robot.txt'*.


Yep.  That pretty much sums up the state of web skills.  It feels like I'm starting to find more broken sites than functional ones, especially in navigation and internationalization. 

> **Silvernail said:**
> 
How does this happen? I notice that once or twice a day this crawler seems to slip in.

Get some more information about the crawler by setting up, at least temporarily, a way to track the user agent strings the visitors choose for themselves.  If it's part of your regular log, it will cause it to take up a lot of space, so a separate log might be recommended:  

```

 CustomLog logs/agent.log "%t\t%a\t%{User-agent}i\t%U\t%q" 

```

You can use other 
[apache log format codes](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats) if you want.  But run the log until the crawler shows up again. 

If it's an honest crawler, then something was missing from robots.txt.  If it's dishonest, then Limit or RedirectMatch can be used by Apache to stop it, or even IP Tables.

---

### Post by Silvernail on 2009-10-20
'www.texasflyfishers.org' has a home page and a bunch of educational pages written in HTML.  This home pages navagation menu has a link to 'Forums'. Using SMF *Small Machine Forums* software.

My question would be, where do I put the 'robot.txt' file. In the same directory as the index.html file?   I'll go to the  SMF help site for information on their software code.

Thanks
Dave

---

### Post by Lars Noodén on 2009-10-21
robots.txt always goes at the top, once for each site, and manages the whole site.  So if there are owners for different sections, they will have to contact you for changes to /robots.txt

It should be retrievable at the URL [http://www.texasflyfishers.org/robots.txt](http://www.texasflyfishers.org/robots.txt)

---

### Post by phillw on 2009-10-21
> If it's an honest crawler, then something was missing from robots.txt. If it's dishonest, then Limit or RedirectMatch can be used by Apache to stop it, or even IP Tables.

Assuming we're still on about the yandex robot - it is a well behaved robot.

If you just want robot control for your forum area then

```
<META NAME="ROBOTS" CONTENT="NONE"> 
``` in html

```
<META NAME="ROBOTS" CONTENT="NONE" /> 
```in xhtml

will stop all 'behaved' robots.

The googlebot has it's own command - so you can allow the google bot only on ....

```
<META NAME="GOOGLEBOT" CONTENT="INDEX, FOLLOW"> 
```

Again, changing >  to /> in xhtml.

In your headers for the forum area. As most forum areas use dynamic pages, you should have a module that generates your headers for you in your code somewhere.

As an example, my meta-tags look like below & are called by each page as the FIRST thing it does (It also looks after handling the mime-type, char-set etc. for me... ask if you need the full details)

```
 ***php header***
<!DOCTYPE html 
     PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title><?php echo $title ?></title>
<meta http-equiv="Content-Type" content="<?php echo $mime ?>;charset=<?php echo $charset ?>" />
<meta http-equiv="Content-Style-Type" content="text/css" />
<link rel="stylesheet" media="screen" type="text/css" href="./css/mgj.css" />
<link rel="stylesheet" media="print" type="text/css" href="./css/mgj_print.css" />
<meta name="description" content="hire plant parts spares engineering services"/>
<meta name="keywords" content="keys, locks, engine, parts, hire, plant, services, engineering,
consumables,"/>
<meta name="copyright" content="M.G. Judd Ltd., 2009. All rights Reserved."/>
<meta name="no-email-collection" content="http://www.unspam.com/noemailcollection" />
<meta name="ROBOTS" content="ALL" /> 
***php footer***

```

Phill.

---

### Post by Silvernail on 2009-10-23
> **phillw said:**
> Assuming we're still on about the yandex robot - it is a well behaved robot.


Late yesterday I filed another trouble ticket with my host 'The  Planet'. They responded and said they would sent it to the unix guys for investigation. I notice that at 10:26 AM the entries in the ban log stopped. About 8 this evening I get an email saying they had put in on the deny list.  I checked the ban log and it had started back at 7:06 pm.

I sent off another email and got a response that they did not know why it was still a problem. They would upgrade the trouble ticket.

Thought just occured. Could it come in through my DSL line and not through my IP server?

Let me study what information you have given me. It may be Monday before I get back to you. Tis faire season here in Southeast Texas.

Thanks for your help
Dave

---

### Post by phillw on 2009-10-23
See next posting

---

### Post by phillw on 2009-10-23
>  Thought just occured. Could it come in through my DSL line and not through my IP server?Depends if you are hosting on your own machine, or using planet.

I'm bemused at your problems with yandex's spider - I have read a few forums that specialise in spiders and none report it as a bad one.

The big boss of the forum I'm involved with is unavailable for a while (family illness). Instead of just the IP addresses can you report back the spider name. It'll be something like ..

spider22.yandex.ru

**UPDATE**
I have found a site that reports that certain yandex spiders do NOT obey robots.txt - This is somewhat puzzling, but I'll give you the link.

[http://crawlerinfo.com/check/cid,280/Yandex-1-01-001-%28compatible--Win16--I%29.html#Hosts](http://crawlerinfo.com/check/cid,280/Yandex-1-01-001-%28compatible--Win16--I%29.html#Hosts)

I'll go see if it is reported by others.

**UPDATE (Again)**

The ones complaining about it are dated circa 2008, which was when yandex spiders left russia and wandered into the world. The early spiders were
bandwidth heavy and various comments on stopping them were discussed... Below is one such thread (You'll note that yandex isn't the only bandwidth
hungry spider).

[http://forums.jumba.com.au/showthread.php?t=7385](http://forums.jumba.com.au/showthread.php?t=7385)


Phill.

---

### Post by Silvernail on 2009-10-25
Since I posted last, The Planet has notified me that they have blocked it by using the .htacess directory. I haven't gone to look at it but my ban log shows no activity from that Ip for over 24 hours.

I'm going to finish reading all the links all of you provided so that I will be better informed.

I'm going to  go out on a limb and ask this thread be marked solved.

Again, let me give a great big thank you for everyones help in this matter.

Dave

---


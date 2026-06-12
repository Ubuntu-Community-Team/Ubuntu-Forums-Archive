---
title: "webalizer hasn't created logs in almost a year!"
date: 2014-03-11
forum: Server Platforms
---

### Post by rebeltaz on 2014-03-11
I am running Ubuntu 10.04 LTS Server hosting three web sites. I rarely look at the webalizer stats, but I went to look at them the other day and I noticed that the logs were almost a year old. It seems webalizer hasn't updated it's logs since last May! 

Is there any obvious reason that this might be?

---

### Post by TheFu on 2014-03-11
Out of storage?  I don't know - what do the system logs say?  
What did the alarms say when they went off?  
How does the server monitoring normally work?
Do the backups show any clear changes?  How has the webalizer code and/or config changed in the last few years?  
Is any configuration management used?

---

### Post by rebeltaz on 2014-03-11
I may have to start over with a fresh server. I have did have ispconfig installed, as well as awstats, but I have noticed that for some reason these are no longer installed. I am also noticing a LOT of activity on this server where there should be very little. Not sure what has happened, but I think I need to reinstall from scratch.

---

### Post by TheFu on 2014-03-11
Servers get pwoned every day and unmonitored servers are pwoned for months and years. Just sayin.
Going 12.04 or will you wait for 14.04?

---

### Post by rebeltaz on 2014-03-12
Yeah.. I know... :( 

I'll install 12.04 probably. What are good steps to take for security? Any good web pages I should read?

---

### Post by lisati on 2014-03-12
A good place to start might be here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by CharlesA on 2014-03-12
> **TheFu said:**
> Servers get pwoned every day and unmonitored servers are pwoned for months and years. Just sayin.
Going 12.04 or will you wait for 14.04?

+1. I'd go with 12.04 to start and bump it up to 14.04 a month or two after release if I was doing it.

But yeah, definitely look into securing the box. I usually have logwatch running on all my *nix boxes and have it mailed to me so I can keep an eye on what is going on. I have [CSF]("http://configserver.com/cp/csf.html") installed on my production servers as a sorta monitoring service as it checks binaries for changes via hashes and a ton of other stuff.

This is a good read too:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by TheFu on 2014-03-12
> **rebeltaz said:**
> Yeah.. I know... :( 

I'll install 12.04 probably. What are good steps to take for security? Any good web pages I should read?

Just published an article about my "First 5 Minutes on a New Server" ... [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server). It has the minimal steps taken on every machine + links to other security pages if your needs are greater or you are running any internet-facing services.

Good, versioned, backups are rule #1 for securing a system.

Ubuntu has some good security pages, but the NSA, SANS, OWASP, Debian and Redhat all have good stuff. There are books on the subject too - "Real World Linux Security" by Bob Toxen (a LUG member) has the old-school stuff that still applies too, but any security book from O'Reilly is useful.

---

### Post by thufirhawat2 on 2014-03-12
> **CharlesA said:**
> +1. I'd go with 12.04 to start and bump it up to 14.04 a month or two after release if I was doing it.

But yeah, definitely look into securing the box. [COLOR=#FF0000]**I usually have logwatch running on all my *nix boxes and have it mailed to me so I can keep an eye on what is going on.**[/COLOR] I have [CSF]("http://configserver.com/cp/csf.html") installed on my production servers as a sorta monitoring service as it checks binaries for changes via hashes and a ton of other stuff.

This is a good read too:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I am pretty sure that the part I highlighted makes you my hero, sir. 

I have been trying to figure out how to get Ubuntu server logs in a more digestible format, and the automatic e-mail is icing on the cake. Took me 30 minutes (with pre-testing in my virtual environment) to set up, and works great, very informative! Thank you!

---

### Post by CharlesA on 2014-03-12
> **TheFu said:**
> Just published an article about my "First 5 Minutes on a New Server" ... [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server). It has the minimal steps taken on every machine + links to other security pages if your needs are greater or you are running any internet-facing services.

Good read, thanks. I've not used that type of software before, but I tend to fall back to the same "basic" base install scripts that I've been using for my servers that deal with getting postfix set up, ssh secured, logwatch installed, etc. I think I will have to look into ansible even if it's just to see what is possible with it.

> Good, versioned, backups are rule #1 for securing a system.

Yep, the best thing about versioned backups is you can roll back to before the box was owned so you don't have to worry about your code or applications being owned after wiping the box and reinstalling.

> **thufirhawat2 said:**
> I am pretty sure that the part I highlighted makes you my hero, sir. 

I have been trying to figure out how to get Ubuntu server logs in a more digestible format, and the automatic e-mail is icing on the cake. Took me 30 minutes (with pre-testing in my virtual environment) to set up, and works great, very informative! Thank you!

Welcome. It isn't really a "replacement" for keeping an eye on the regular logs and getting to know your system, but it helps identify potential problems in an easily digestible format.

---

### Post by TheFu on 2014-03-12
Thanks. Glad to hear I wasn't too far off with that article.  Wrote it after reading a few similar articles that appeared to be written by non-administrator people. Seemed they completely forgot monitoring, alarming, and performance statistics gathering. I'm still using an old SysUsage version and didn't want to push folks that way until I'd migrated to the centralized version here.

We can all do a little better with our setup consistency.  Doesn't matter if you are running 1 server or 20,000 - consistency matters. It doesn't matter to me HOW that is accomplished either.  Following a list of commands in a paper notebook is just as good as 100% automatic setups - consistency matters more on the road to "doing it better every time."

I love the term "DevOps" ... been doing that since the early 1990s professionally. Since 2000, my slant has switched from developer-centric to admin-centric and about halfway back. From what I can tell, being good at both is hard. I'll keep trying.

Oh and using **LogWatch** is a good thing, if something larger doesn't fit.  I use it at home.

---

### Post by rebeltaz on 2014-03-12
I will definitely be reading that. Thanks for all the help guys.

---

### Post by TheFu on 2014-03-12
> **rebeltaz said:**
> I will definitely be reading that. Thanks for all the help guys.

If you see anything wrong or unclear, please let me know.

---

### Post by CharlesA on 2014-03-12
> **TheFu said:**
> We can all do a little better with our setup consistency.  Doesn't matter if you are running 1 server or 20,000 - consistency matters. It doesn't matter to me HOW that is accomplished either.  Following a list of commands in a paper notebook is just as good as 100% automatic setups - consistency matters more on the road to "doing it better every time."

I would rather be running the same (or very similiar) setup on any servers I manage and if that means not messing with it outside of updates and scanning logs, so be it.

Of course, with that being said, I'm managing 4 Debian 7 boxes right now, so having everything running the same version of the OS is quite handy, even if each machine is slightly different.

I forgot to mention the unattended-upgrades package, which I have set to install security updates and apticron, which notifies me of available updates in the event I have an update pending that isn't security related.

---

### Post by rebeltaz on 2014-03-13
I pretty much knowhow to install a server - I've done it several times, but since my system was apparently hacked and I do not claim to know anything - started reinstalling through this guide: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

I did skip the DNS setup, because I didn't need that. I installed the mail components but I don't have a mail server either, nor do I really understand any of the mail setup.

Then I went through your (theFu) guide and moved on to one of the links at the bottom of your page for Bryan Kennedy's guide. I noticed that both "5 Minute" guides installs LogWatch. Is the email address used in that pushed through postfix (or dovecot) or a standard email server?

Linux, servers... I understand. mail and dns, not so much.

Once again, I appreciate y'alls help!

---

### Post by TheFu on 2014-03-13
Generally, system emails on Linux use some MTA like postfix, qmail or sendmail. There are exceptions - extremely rare. Postfix was designed as a 95% replacement for sendmail with security at the center. Sendmail can do a few things that postfix cannot, so there is a place for it when an extremely complex situation arises. I've never needed it since my first corporate email server in 1996.

**Were you able to figure out how they hacked you so it won't happen again?**

Avoid complexity and complex tools if they are not absolutely required.

---

### Post by CharlesA on 2014-03-13
> **rebeltaz said:**
> I pretty much knowhow to install a server - I've done it several times, but since my system was apparently hacked and I do not claim to know anything - started reinstalling through this guide: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

Depending on what you are hosting, leaving ispconfig or cPanel or some other web based panel out of your configuration might be a good idea. I run Nginx/php-fpm and a few other things, but I don't deal with a web frontend.

> Then I went through your (theFu) guide and moved on to one of the links at the bottom of your page for Bryan Kennedy's guide. I noticed that both "5 Minute" guides installs LogWatch. Is the email address used in that pushed through postfix (or dovecot) or a standard email server?

I use postfix and if you don't have a true mail server setup, you could set it up to relay to Gmail or something like that. I need to have my home box set up as a relay because my ISP blocks port 25, but if this box is "in the wild" you should be able to just configure postfix to send mail out.

> **TheFu said:**
> Generally, system emails on Linux use some MTA like postfix, qmail or sendmail. There are exceptions - extremely rare. Postfix was designed as a 95% replacement for sendmail with security at the center. Sendmail can do a few things that postfix cannot, so there is a place for it when an extremely complex situation arises. I've never needed it since my first corporate email server in 1996.

I've seen sendmail installed on Debian before, but it gets purged and postfix installed because I know how to configure postfix. In my mind, using what your know how to use instead of relying on the defaults helps tremendously, but I also do not know what sendmail can do that postfix cannot.

> **Were you able to figure out how they hacked you so it won't happen again?**

Avoid complexity and complex tools if they are not absolutely required.

+1. I'm a bit curious to see how the box was owned and as a general rule, only install the minimum amount of software/packages to get to job done. Anything extra can be a security risk due to unpatched vulnerabilities or lack of updates if there are not from a supported repo.

---

### Post by rebeltaz on 2014-03-13
I honestly have no idea. Aside from ispconfig, I had phpBB3 installed, a search engine module, a chat module and the php pages that I myself wrote. I did install WordPress, but that was a week before I posted this topic, so I know that the damage had already been done. Before I wiped it last night, I removed the search engine directory, the phpBB3 directory and the chat module directory, but I guess the damage had already been done. I don't know anything about how to hack networks, so I don't know where to look. 

I am hosting three sites - the one in my signature as a hobby and two others, one for each of my company divisions - [www.ShelbyCycle.com](www.ShelbyCycle.com) and [www.ShelbyTVService.com](www.ShelbyTVService.com) - so ispconfig made things easier than manually editing the config files.

Before I wiped everything, I made sure that I had copies of all three site directories. When I reinstall the sites, I plan on reinstalling the search module from source code and leaving off phpBB3 as well as the chat module. I will be reinstalling WordPress, but I will reinstall it from scratch and import my posts.

I did run iftop last night after reinstalling the server and I still see that a LOT of traffic is attempting to contact the server, but instead of 30 megs being transferred in 10 minutes (my 6mb business DSL is limited to 300-400kbs upload) there was only 30 megs over an eight hour period. Just out of curiosity, will the traffic ever stop trying? I know that I had the server completely shut down for a week trying to diagnose a DSL issue and that didn't deter them.. :(

---

### Post by TheFu on 2014-03-13
Ah ... php.   Ah ... installing from source.

They will keep trying as long as your IP exists and connects. It isn't like there is a human doing it. Heck, your box was probably the command-n-control for 20% of a worldwide botnet.

I would suggest completely review of everything (machines, code, services, configurations) you put on the internet since what you did last time (and will likely do again) was not sufficient. We've all been there. This was just your turn. ;)

Just FYI, my company doesn't allow anything with php or java to be placed on the internet. If those things are needed, then VPN is required.  The core php guys have released fresh versions that had multiple, high-severity, security issues - and they knew it at release time!  Shipping was more important than security.  That was a key reason when we migrated off php here.  Java took a little longer - it was after Oracle took over though.  

I'm not certain if either of these languages is to blame. It could just be that lots of noob programmers pick up java and php and start coding for features, not security. Either way, the quality of the average java and php code out there is lessened.

Have you scanned your connection - in AND out - to see what is easily available?  Might want to check all the other systems inside the same subnet.  If they got shell access, they probably tried to compromise other machines too.  I'd use **pfSense** as the firewall so that a state-full packet firewall is used. It has nice reports, will connect with many NMS and pretty graphs. ;)

So ... installing from source makes it highly unlikely that you will patch any running services.  Use the ubuntu repos and if that isn't up to date enough, use a trusted PPA.  If there isn't a trusted PPA, I wouldn't use the software at all. Just sayin'.  Installed settings are rarely "secure settings."

The core Wordpress code isn't that bad, but some of the addons are highly non-secure. Plus it is hard to secure any program running on a language platform with 2x more security issues than any others. Be careful.  

Oh - and it isn't just me who is concerned about PHP. Here's what the OWASP guys said: 
> There are, unfortunately, serious issues in all areas that make it difficult to write secure PHP applications. These are difficult to work around if you are forced to use PHP, but you need to be aware of them. 
[https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)  - PHP Security Cheat Sheet

I'm coming at this from a non-php programming standpoint, but I definitely am a developer AND system admin. These days I'm working on a back-end server for a few different Android apps that need to work on the internet and inside a LAN seamlessly. Security has me paranoid with these.  We are NOT using any PHP. ;)

---

### Post by rebeltaz on 2014-03-13
Wow... now I'm wondering if I even want to keep running these sites!

As for the php, is it really THAT dangerous? The code I wrote doesn't rely on forms or anything fancy (to me) like that. On page, I just did it so that, as I added images to a directory, they were automatically added to the page. On the other page, I did it so that I could just keep a list of the other pages which generates the links needed since I was adding so many pages at the time. 

If I were to post the code for one (it's short) could you tell me if it is a security issue?

And you are right... I am not a professional coder. I just learned what I needed to know to write the page and that was all. 

Maybe I''ll leave the search function off then if that could be an issue. That is the only other code I would install outside of WordPress and I didn't/wouldn't install any addons to that.

I ran iftop on my desktop system, also connected to the subnet and I do see traffic that I don't think should be there - just not with any significant volume. Other than that, how can I tell what's going on?

I just ran nmap on my DSL modem and came back with this:
```

23/tcp    open  telnet
25/tcp    open  smtp
110/tcp   open  pop3
1863/tcp  open  msnp
5050/tcp  open  mmcc
5190/tcp  open  aol
8080/tcp  open  http-proxy
50000/tcp open  iiimsf

```

Ports 1863, 5050, 5190 and 50000 shouldn't be open, I wouldn't think. And interestingly, ports that I DID open (for a security camera system) 7777, 8181, 9000 and 8888 don't show up on that list. If these are not opened in the Pinholes section of the modem, how do I close them? I removed the camera ports for right now, btw.

---

### Post by TheFu on 2014-03-13
Only you can determine how "risky" what you are doing is.   I am NOT a php programmer and reviewing code is not something I'd do for free even if  it were in a language I know.

Running an nmap from inside the network might not be returning the truth. There are external services that will perform the scan for you. GRC has a free one. A small restaurant with open wifi might work too. Larger chain stores will filter connections, so those can't be used.

If you didn't open the ports on the router, how do you suppose they were opened?  Things may be much worse than has been discovered so far.

Could an open relay for email and web traffic have been running? 

There is NO WAY that I'd have telnet, pop3 or an http-proxy (if that is really what it is) running on my network connection. These names don't necessarily mean anything, but could be true.  If I had hacked your box, I'd use a reverse ssh connection on a non-standard port to remain in contact. The binary would be renamed to something recognized as normal, something expected.

Uh... some of those security cameras are extremely hackable. Saw a presentation on that last fall. Using google, it is possible to find them on the internet and "watch."  Nanny-cams get lots of hits.

I'm dropping from this thread with one more thought.  To learn how to secure your systems, the best way that I know is by learning to hack them.  There are Defcon groups around the world. In the USA, they are usually found using the areacode after DC - DC202, DC303, DC404, DC402 ... you get the idea - google. The OWASP guys are good too.  IronGeek posts videos of presentations about hacking things from many cons. Watching how they hack is eye opening, normal people have absolutely no idea how wild the internet really is. These are primarily IT security professionals - people paid by large organizations to break into their networks, but anyone can view and attend these conferences.  The lock picking 101 classes are usually full.

Good luck with your systems.

---

### Post by Lars Noodén on 2014-03-13
PHP is almost *that* bad, I used to use it and was always having to work around problems.  Where you can start is to make sure that no variables *ever* take data or input from outside the program and then pass it on unmodified to the system.   Despite being in Wikipedia, here is a good example of what to avoid: [http://en.wikipedia.org/wiki/Taint_checking#Example](http://en.wikipedia.org/wiki/Taint_checking#Example)

Some terms to look up are data validation and taint checking.

---

### Post by TheFu on 2014-03-17
Current warning from Brian Krebs about Wordpress ping-backs.
[https://krebsonsecurity.com/2014/03/blogs-of-war-dont-be-cannon-fodder/](https://krebsonsecurity.com/2014/03/blogs-of-war-dont-be-cannon-fodder/)

Mainly using WP to perform DoS attacks against other WP blogs, but any blog that supports pingbacks might be used.  I run a RoR blog, but have never enabled pingbacks. I don't think it is any safer than WP, just less popular and less likely to be attacked.

I consider his Monday blog article to be a **MUST READ.**

---

### Post by CharlesA on 2014-03-17
Thanks for the link. :) Note to self, if and when I get to installing wordpress, I'll have to disable that "feature."

---

### Post by rebeltaz on 2014-03-17
I will be sure to do that as well. 

On a related note, after reinstalling and activating one of my sites for a few minutes, I found this line in the error.log:
```
[Mon Mar 17 01:50:16 2014] [error] [client 192.151.152.186] File does not exist: /var/www/robotsandcomputers.com/web/++++++++++++++++++++++result:+chosen+nickname+"apposespignee";+nofollow+is+found;+success;+bb-code+not+working;, referer: http://www.robotsandcomputers.com/++++++++++++++++++++++result:+chosen+nickname+%22apposespignee%22%3b+nofollow+is+found%3b+success%3b+bb-code+not+working%3b
```

---


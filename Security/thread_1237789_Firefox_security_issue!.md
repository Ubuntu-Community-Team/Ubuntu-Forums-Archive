---
title: "Firefox security issue!"
date: 2009-08-11
forum: Security
---

### Post by jesushero on 2009-08-11
Just had a bit of a scare with Firefox... In my 2 years of using Linux exclusively (no dual boot or anything else) I have never seen this happen before!

I was searching Google for something relating to Ohm's law and resistors for electronic circuits. While on Google's search results (with no other webpage open) a new tab popped up, firefox kind of disappeared and a little window popped up:

[ATTACH]124497[/ATTACH]

This reminded me of what always happens on Windows computers after a few weeks online. I got a terminal up and did the following:

```
user@Computer:~$ netstat -tuan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.68:51963      209.85.229.113:80       ESTABLISHED
tcp        0      0 192.168.1.68:46170      204.11.51.35:80         TIME_WAIT  
tcp        0      0 192.168.1.68:43480      209.85.227.104:80       ESTABLISHED
tcp        0      0 192.168.1.68:38221      217.41.217.215:80       ESTABLISHED
tcp        0      0 192.168.1.68:58010      93.170.159.203:80       TIME_WAIT  
tcp        0      0 192.168.1.68:41124      213.120.163.176:80      ESTABLISHED
tcp        0      0 192.168.1.68:58018      93.170.159.203:80       TIME_WAIT  
tcp        0      0 192.168.1.68:58420      88.221.170.77:80        ESTABLISHED
tcp        0      0 192.168.1.68:44194      209.85.227.154:80       ESTABLISHED
tcp6       0      0 :::21                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::631                  :::*                    LISTEN     
udp        0      0 0.0.0.0:40251           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*                          
udp        0      0 192.168.1.255:123       0.0.0.0:*                          
udp        0      0 192.168.1.68:123        0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          
udp6       0      0 fe80::20a:48ff:fe0a:123 :::*                               
udp6       0      0 ::1:123                 :::*                               
udp6       0      0 :::123                  :::*           


user@Computer:~$ lsof -i TCP
COMMAND  PID  USER   FD   TYPE DEVICE SIZE NODE NAME
firefox 6102 user   47u  IPv4  25340       TCP Computer.home:43480->wy-in-f104.google.com:www (ESTABLISHED)
firefox 6102 user   48u  IPv4  25591       TCP Computer.home:44194->wy-in-f154.google.com:www (ESTABLISHED)
firefox 6102 user   56u  IPv4  25676       TCP Computer.home:41124->213.120.163.176:www (ESTABLISHED)
firefox 6102 user   57u  IPv4  25684       TCP Computer.home:58420->a88-221-170-77.deploy.akamaitechnologies.com:www (ESTABLISHED)
firefox 6102 user   60u  IPv4  25639       TCP Computer.home:51963->ww-in-f113.google.com:www (ESTABLISHED)
firefox 6102 user   64u  IPv4  25695       TCP Computer.home:38221->217.41.217.215:www (ESTABLISHED)

```

Two of the IP's on Netstat are unrelated to anything I was viewing:

93.170.159.203
88.221.170.77

Both port 80's, both assigned to PID 6102, firefox... Probably ad-servers... 

I thought I'd "play along" and see what happens.. The security on my system is quite good, so firefox can't really cause much damage the way things are set up, so I didn't mind experimenting with this.

I clicked OK, and "watched" netstat..

This came up on my terminal business:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.68:49992      74.125.105.31:80        ESTABLISHED
tcp        0      0 192.168.1.68:44735      209.85.227.113:80       ESTABLISHED
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::631                  :::*                    LISTEN
udp        0      0 0.0.0.0:40251           0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*
udp        0      0 0.0.0.0:631             0.0.0.0:*
udp        0      0 192.168.1.255:123       0.0.0.0:*
udp        0      0 192.168.1.68:123        0.0.0.0:*
udp        0      0 127.0.0.1:123           0.0.0.0:*
udp        0      0 0.0.0.0:123             0.0.0.0:*
udp6       0      0 fe80::20a:48ff:fe0a:123 :::*
udp6       0      0 ::1:123                 :::*
udp6       0      0 :::123                  :::*

user@Computer:~$ lsof -i TCP
COMMAND  PID  USER   FD   TYPE DEVICE SIZE NODE NAME
firefox 6102 user   39u  IPv4  27636       TCP Computer.home:44735->wy-in-f113.google.com:www (ESTABLISHED)
firefox 6102 user   43u  IPv4  27695       TCP Computer.home:49993->74.125.105.31:www (ESTABLISHED)
firefox 6102 user   47u  IPv4  27701       TCP Computer.home:47317->64.86.16.10:www (ESTABLISHED)
user@Computer:~$ netstat -tuan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.68:49993      74.125.105.31:80        ESTABLISHED
tcp        0      0 192.168.1.68:44735      209.85.227.113:80       ESTABLISHED
tcp6       0      0 :::21                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::631                  :::*                    LISTEN     
udp        0      0 0.0.0.0:40251           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*                          
udp        0      0 192.168.1.255:123       0.0.0.0:*                          
udp        0      0 192.168.1.68:123        0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          
udp6       0      0 fe80::20a:48ff:fe0a:123 :::*                               
udp6       0      0 ::1:123                 :::*                               
udp6       0      0 :::123                  :::*                  
```

There was also another TCP connection on netstat initially, to 64.86.16.10, as can be seen on LSOF, but it disappeared before I could copy and paste.

Now, I can understand the ad-servers being there, but I seriously don't understand how 64.86.16.10 got there! Firefox did a little animation and displayed this, in the new tab it had initially opened:

[ATTACH]124498[/ATTACH]

As is evident, this looks like a typical Windows malware/spyware thing.. But it somehow affected Firefox running on a Windows-free network! How did the page pop-up? It happened with no user interaction! I DID NOT click on anything when it popped up! It was NOT a pop-up from a website that had just loaded! Not to mention that firefox has the pop-up blocker enabled! This happened straight after the latest update, earlier today.

Here's the version info: 

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.13) Gecko/2009080316 Ubuntu/8.04 (hardy) Firefox/3.0.13
```

So is it about time I got rid of firefox and went on to a different browser? I'd rather stick to lynx on Ubuntu Server if I have to put up with the same windows ******** that got me "converted" to linux in the first place!

Any thoughts/ideas?

---

### Post by cariboo on 2009-08-11
Try installing the nosscript add-on and see if the same thing happens.

---

### Post by bodhi.zazen on 2009-08-12
Well the problem is that these things are "cross platform" meaning it is a browser thing and not a windows / linux thing.

Specifically java script , java, and flash are all cross platform.

I suggest you look at :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

In addition I lock down firefox with apparmor. Here is my current profile :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.13.firefox.sh](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.13.firefox.sh)

So even if one of there cross platform cracks runs it can not (in theory) affect system files. In practice nothing is fool proof and security == constant vigilance not install it and forget it.

---

### Post by bobince on 2009-08-12
> a little window popped up

That's a perfectly normal JavaScript ‘alert()’ box. Any web site can do it, pop-up blocker or no; it cannot be stopped.

> firefox kind of disappeared

It's still clearly present in your window list. Presumably the script lowered the Firefox window to the bottom of the pile where you wouldn't see it. You can (and probably should) disable this annoying capability from Preferences->Content->JavaScript->Advanced->Raise or lower windows.

> I seriously don't understand how 64.86.16.10 got there!

That's an HTTP connection to searchplaceonline.com, the fraudware site showing you the fake scanner and alert() message. An ad server will have redirected you to it.

It is common for (a) compromised sites to redirect to fraudware adverts like these, and (b) ad networks to include bogus Flash ads that redirect you there. But it's very unlikely this found its way directly onto a Google search results page. I would guess it had been a part of a previous page you had open which hid itself and lurked for a bit.

Whilst many fraudware affiliates do operate browser and plugin exploits (so far always targeting Windows), there is no evidence of a security issue here, just the usual misleading JavaScript tricks malware operators have been using for years.

---

### Post by bodhi.zazen on 2009-08-12
Thank you for that very nice explanation [bobince]("http://ubuntuforums.org/member.php?u=819260")

---

### Post by jesushero on 2009-08-12
Thanks everyone for the replies!

cariboo907, I just did, got noscript, adblock plus and request policy... I think it was about time, I was always reluctant to try the ad-ons for some reason..

bodhi.zazen, thanks for the links!

bobince, thanks for the detailed explanation! It was the first time since I converted to Linux that I had this happen, and I got kind of alarmed. Not that it could do much, I log in as a user with access only to a home folder.. No sensitive data in there, so not much damage to be done.. But still, I guess it was a good reminder that I need to keep up to date with everything being as secure as possible. Thanks for the javascript tip as well, the raise/lower windows one!

I also got ClamAV, out of interest, which pointed out 3 files in the firefox cache, javascript... They're rm'd now. 

Thanks again!

---

### Post by witeshark17 on 2009-10-06
Is it generally agreed that the Noscript add on is recommended?

---

### Post by bodhi.zazen on 2009-10-06
> **witeshark17 said:**
> Is it generally agreed that the Noscript add on is recommended?

No, but I would not browse without it. It takes a few minutes to install and configure, but it is well worth it IMO.

Other people use yes script, which allow everything except a black list, but then you need a blacklist.

Some people feel it is a crime to block java script, visit the mibbit site with java script blocked for example.

It is like all of security, only you can decide how much hassle you want to put up with for how much security.

---

### Post by witeshark17 on 2009-10-06
Thanks for your quick reply! This will help me make up my mind! :KS

---

### Post by SoylentSteak on 2009-10-08
I got something like this just yesterday. It didn't worry me, because I know Ubuntu is too secure to be corrupted by these things. Just to be sure, I did a virus check, and sure enough, nothing was there. I used to have NoScript, but it was a major hassle unblocking everything on each new site I visited. YesScript may be less of a hassle, but you don't need it, either. There's a difference between those stupid little fraudware things popping up and them actually harming your computer. One almost has to be *trying* to get a virus when using a good Linux distro. Just keep Ubuntu up to date and you'll be fine.

It is possible to get a little junk in Firefox, but it's not going to affect the core of your system and is easily fixable.

---

### Post by __p1n__ on 2009-10-08
Personally I've stopped using firefox for all browsing with the exception of a secure on-line banking site.

The SQLite files that remain stored on your disk regardless of history/cache preferences is a bit alarming and even starting on a blank page results in connections to various IP addresses.  Some add-on's actually exacerbate this.  The four add-ons that I use are noscript, adblock, flashbock, and, showip but as I said, I've moved over to opera for general browsing.

Note: you can manually delete the SQLite files after a session if you're concerned about privacy.

---

### Post by bodhi.zazen on 2009-10-08
> **__p1n__ said:**
> Personally I've stopped using firefox for all browsing with the exception of a secure on-line banking site.

The SQLite files that remain stored on your disk regardless of history/cache preferences is a bit alarming and even starting on a blank page results in connections to various IP addresses.  Some add-on's actually exacerbate this.  The four add-ons that I use are noscript, adblock, flashbock, and, showip but as I said, I've moved over to opera for general browsing.

Note: you can manually delete the SQLite files after a session if you're concerned about privacy.

I will tell you the same thing I was told long ago ...

NoScript blocks Flash so no need for both flashblock and noscript =)

Wee hooo .... One less extension :twisted:

> The **NoScript Firefox extension** provides extra protection for Firefox, Flock, Seamonkey and other mozilla-based browsers:  this free, open source add-on allows **[JavaScript]("http://en.wikipedia.org/wiki/JavaScript"), [Java]("http://en.wikipedia.org/wiki/Java") and [Flash]("http://en.wikipedia.org/wiki/Adobe_Flash") and other [plugins]("http://hackademix.net/2009/02/07/browser-plugins-add-ons-and-security-advisers/")**  to be executed only by **trusted web sites of your choice** (e.g. your online bank),  and provides **the most powerful [Anti-XSS protection]("http://noscript.net/features#xss")** available in a browser.

---

### Post by __p1n__ on 2009-10-08
> **bodhi.zazen said:**
> I will tell you the same thing I was told long ago ...

NoScript blocks Flash so no need for both flashblock and noscript =)

Wee hooo .... One less extension :twisted:

Woo hoo!

---

### Post by update_manager on 2009-10-08
> **SoylentSteak said:**
> 

It is possible to get a little junk in Firefox, but it's not going to affect the core of your system and is easily fixable.

This is not true. Many of the issues in Firefox can be used to execute code.

For an example, look at this issue:
[http://www.mozilla.org/security/announce/2009/mfsa2009-51.html](http://www.mozilla.org/security/announce/2009/mfsa2009-51.html)

*"Mozilla security researcher moz_bug_r_a4 reported that the BrowserFeedWriter could be leveraged to run JavaScript code from web content with elevated privileges. Using this vulnerability, an attacker could construct an object containing malicious JavaScript and cause the FeedWriter to process the object, running the malicious code with chrome privileges."*

Chrome privileges are equal to the privileges of Firefox. For an Ubuntu user, this means that a website that can execute any local command with the privileges of the user running Firefox assuming the attacker 1.) knows how to exploit this issue and 2.) the user isn't running an updated version of Firefox.

---

### Post by __p1n__ on 2009-10-08
> **update_manager said:**
> This is not true. Many of the issues in Firefox can be used to execute code.

For an example, look at this issue:
[http://www.mozilla.org/security/announce/2009/mfsa2009-51.html](http://www.mozilla.org/security/announce/2009/mfsa2009-51.html)

*"Mozilla security researcher moz_bug_r_a4 reported that the BrowserFeedWriter could be leveraged to run JavaScript code from web content with elevated privileges. Using this vulnerability, an attacker could construct an object containing malicious JavaScript and cause the FeedWriter to process the object, running the malicious code with chrome privileges."*

Chrome privileges are equal to the privileges of Firefox. For an Ubuntu user, this means that a website that can execute any local command with the privileges of the user running Firefox assuming the attacker 1.) knows how to exploit this issue and 2.) the user isn't running an updated version of Firefox.

Exactly.  If you're *REALLY* serious about security then turn off images and disable javascript.  Just say No to Web 2.0!

---

### Post by rookcifer on 2009-10-08
> **update_manager said:**
> 
Chrome privileges are equal to the privileges of Firefox. For an Ubuntu user, this means that a website that can execute any local command with the privileges of the user running Firefox assuming the attacker 1.) knows how to exploit this issue and 2.) the user isn't running an updated version of Firefox. **3.) The user is not using a MAC system like AppArmor.**

There, fixed it for you.

---

### Post by witeshark17 on 2009-10-08
All very interesting. But it would seem that the vast majority of auto attacks loose on the internet would be Windows aimed, using .exe files and registry edits. I see no reason for serious, for profit hackers to make any real effort that would likely need to be modified for individual, non Windows computers. Does this make sense? Thanks all for the replies! :cool:

---

### Post by gali98 on 2009-10-08
I got this same popup and "virus-scanner" thing a couple of weeks ago. 
I actually downloaded the file and ran it with wine to see what it did. As far as I know it did nothing (didn't change any registry settings / files.) which didn't surprise me.
Thanks to all the others for the explanations! I was asking myself some of those questions.
Also, just so you know, karmic now comes with better apparmor profiles (with one for firefox.) 
[https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#New%20profiles](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#New%20profiles)
After reading this, I enabled it :)
Kory

---

### Post by witeshark17 on 2009-10-08
> **gali98 said:**
> I got this same popup and "virus-scanner" thing a couple of weeks ago. 
I actually downloaded the file and ran it with wine to see what it did. As far as I know it did nothing (didn't change any registry settings / files.) which didn't surprise me.
Thanks to all the others for the explanations! I was asking myself some of those questions.
Also, just so you know, karmic now comes with better apparmor profiles (with one for firefox.) 
[https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#New%20profiles](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#New%20profiles)
After reading this, I enabled it :)
Kory FYI, there is no registry in any Unix based OS. That is a Windows only system core.

---

### Post by emarkay on 2009-10-08
> **bodhi.zazen said:**
>  NoScript blocks Flash so no need for both flashblock and noscript  

True but many times I want to view the flash content and FlashBlock makes it much easier to just "click: to view.

I use these security addons:   	AskForSanitize, BetterPrivacy, FlashBlock, NoScript.

	 	 	 	  [FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

---

### Post by update_manager on 2009-10-08
> **rookcifer said:**
> There, fixed it for you.

AppArmor is unlikely to be effective at mitigating issues in Firefox. 

If the attacker owns up Firefox but can not gain any further access to the system they still could still get online information (usernames/passwords, cookies, probably email, etc) that Firefox can normally access.


I'm not saying that Firefox is any less secure than other browsers. However, claiming Ubuntu's security features prevent an attacker from doing really bad stuff with Firefox vulnerabilities is not true.

For an example, Metasploit ([http://trac.metasploit.com/browser/framework3/trunk/modules/exploits/multi/browser](http://trac.metasploit.com/browser/framework3/trunk/modules/exploits/multi/browser)) maintains some exploits that would likely affect Ubuntu through Firefox.

---

### Post by witeshark17 on 2009-10-08
> **update_manager said:**
> AppArmor is unlikely to be effective at mitigating issues in Firefox. 

If the attacker owns up Firefox but can not gain any further access to the system they still could still get online information (usernames/passwords, cookies, probably email, etc) that Firefox can normally access.


I'm not saying that Firefox is any less secure than other browsers. However, claiming Ubuntu's security features prevent an attacker from doing really bad stuff with Firefox vulnerabilities is not true.

For an example, Metasploit ([http://trac.metasploit.com/browser/framework3/trunk/modules/exploits/multi/browser](http://trac.metasploit.com/browser/framework3/trunk/modules/exploits/multi/browser)) maintains some exploits that would likely affect Ubuntu through Firefox. All good to keep in mind. But isn't it unlikely that anyone would put any effort into theoretical exploits that are nearly certain to result in little and rarely successful information harvesting?

---

### Post by update_manager on 2009-10-08
> **witeshark17 said:**
> All good to keep in mind. But isn't it unlikely that anyone would put any effort into theoretical exploits that are nearly certain to result in little and rarely successful information harvesting?

Some (not all) of the issues that affect Firefox will result in reliable exploits that could be used to steal data. 

"nearly certain to result in little and rarely successful information harvesting" is false - an attack targeting an XSS vulnerability in Firefox ("universal XSS") could be cross platform.

---

### Post by SoylentSteak on 2009-10-08
> **update_manager said:**
> This is not true. Many of the issues in Firefox can be used to execute code.

For an example, look at this issue:
[http://www.mozilla.org/security/announce/2009/mfsa2009-51.html](http://www.mozilla.org/security/announce/2009/mfsa2009-51.html)

*"Mozilla security researcher moz_bug_r_a4 reported that the BrowserFeedWriter could be leveraged to run JavaScript code from web content with elevated privileges. Using this vulnerability, an attacker could construct an object containing malicious JavaScript and cause the FeedWriter to process the object, running the malicious code with chrome privileges."*

Chrome privileges are equal to the privileges of Firefox. For an Ubuntu user, this means that a website that can execute any local command with the privileges of the user running Firefox assuming the attacker 1.) knows how to exploit this issue and 2.) the user isn't running an updated version of Firefox.


Well, if it's only able to run things the user has privileges for, that still shouldn't be a serious problem for the wellbeing of the system, provided he's not doing something stupid, like running as root, right?

Also, I take it that having Firefox up to date also would take care of this?

---

### Post by witeshark17 on 2009-10-08
> **SoylentSteak said:**
> Well, if it's only able to run things the user has privileges for, that still shouldn't be a serious problem for the wellbeing of the system, provided he's not doing something stupid, like running as root, right?

Also, I take it that having Firefox up to date also would take care of this? Not to mention that root user isn't enabled by default in most later distros.

---

### Post by update_manager on 2009-10-08
> **SoylentSteak said:**
> Well, if it's only able to run things the user has privileges for, that still shouldn't be a serious problem for the wellbeing of the system, provided he's not doing something stupid, like running as root, right?

Also, I take it that having Firefox up to date also would take care of this?

Executing code with normal user privileges is  bad since a user's data is owned by their user account. Another issue is that once an attacker has a regular user account, jumping privileges to root isn't extremely hard ([http://blog.cr0.org/2009/08/linux-null-pointer-dereference-due-to.html](http://blog.cr0.org/2009/08/linux-null-pointer-dereference-due-to.html)).

Keeping Firefox up to date helps a lot as now the attacker also needs to know about an issue that Mozilla hasn't fixed yet. NoScript can also prevent some sites from doing bad stuff.

---

### Post by gali98 on 2009-10-09
> **witeshark17 said:**
> FYI, there is no registry in any Unix based OS. That is a Windows only system core.
Quite right. But Wine uses a registry just like windows ;)
Kory

---

### Post by witeshark17 on 2009-10-09
AFAIK, banking and other secure websites have their own forms of security. But I would still not do any personal banking or shopping at a coffee shop Wifi loacation... :popcorn:

---


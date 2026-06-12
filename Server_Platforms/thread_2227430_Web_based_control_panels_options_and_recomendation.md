---
title: "Web based control panels options and recomendations"
date: 2014-06-02
forum: Server Platforms
---

### Post by Yves_Dawson on 2014-06-02
[FONT=Open Sans, sans-serif][COLOR=#333333]Hi all,

[/COLOR][/FONT][COLOR=#333333][FONT=Open Sans]I'm not an absolute beginner at linux but I'm far from being experienced.  So I'm looking for a web based control panel for my Ubuntu Server 14.04.

I saw that Zentyal was not upgraded for version 14, only for version 12.  So what would be the best control panel to manage all aspects of the server (web, dns, mail, security, etc.) ?

I've read about cPanel, Plesk, ISPConfig, Ajenti and some more but I can't really understand the pros and cons of them with my lacking experience.

So I'd like to hear the point of view of experimented Linux users.

Thanks

[/FONT][/COLOR]

---

### Post by CharlesA on 2014-06-02
I'd go for the no control panel route personally. I find that any sort of web based control panel adds more attack surface to your server and should be used with caution.

Also: Do **NOT** use Zpanel, that thing is a security nightmare.

---

### Post by Yves_Dawson on 2014-06-02
Indeed, security is one of my concerns.

But I'm not experienced enough on linux to manage it all on command line for now.

Do you have any suggestion of how else it could be done?

---

### Post by CharlesA on 2014-06-02
Depends on what you want to do with the server, to by honest. I don't think I would run mail or DNS normally unless I was using cPanel cuz it kinda needs DNS and mail.

If you just want basic web hosting, the wiki has good documentation to both Apache and Nginx, but I prefer using the Archwiki for somethings.

My suggestion to you is to play around on a test system - maybe set up a VirtualMachine and just mess around with it, break things, fix the broken stuff, see what happens.

That's how I learned... lots of trial and error.

---

### Post by TheFu on 2014-06-03
I have nothing to add that Charles didn't already say.  I don't use panels either. 

I think they are all added attack vectors for crackers. If running an internal-only server, that probably isn't a concern. External is a different ballgame completely. Be cautious out there.

The way I manage servers is through **ansible** - but to get that setup means understanding exactly what you want. It isn't really useful for your stage of administration.

---

### Post by tgalati4 on 2014-06-03
Install the desktop version and use ssh with X-forwarding.  Then you have the complete desktop at your disposal.  Don't leave ssh running and facing the web unless you really need it.  Otherwise learn the command line.  Running a server is not finger-painting.

---

### Post by kosmokramer314 on 2014-06-03
I'd like to add some more clarity as to why using a web panel for server administration is a bad idea.  
[LIST=1]
[*]Exposes control of your server to the internet.
[*]Has many default settings that often go over looked and are gaping holes for exploits.
[*]Many users that deploy control panels do so because they don't know how to be a server administrator and don't actively patch and monitor security updates.
[*]You don't know what you're doing, so don't make it easier for bad guys.
[/LIST]

Learning to control your server, and be a good administrator, is not that difficult if you take some time to work at it.  Set aside a few hours a day to find tutorials for what you want to accomplish.  Pick one application and read.  Before diving in to that application however, learn how to take a backup and deploy.  Learn how to use aptitude instead of apt-get for safely installing new applications and rolling back with better success. Whatever you do...don't use a control panel...coming from someone in the web hosting industry..just don't.

---

### Post by Yves_Dawson on 2014-06-04
Thanks to all for your opinions.

Looks like the point is made real clear: No panel ;)

And using Aptitute looks like a good way of doing things.

We talked a lot about security.  That may be a little off-topic but what do you guys think of the following tutorial on securing the server:

[http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)

And does it all applies to Ubuntu 14?

---

### Post by CharlesA on 2014-06-04
It makes some good points, but I think some of the things it has you do is overkill such as changing the port ssh runs on as that doesn't really do much for security except cut down on log noise from bots.

I've been running LogWatch, [CSF]("http://www.configserver.com/cp/csf.html"), and using keys for ssh and I've been fine. Some of the suggestions in the link you posted are security through obscurity, which I do not feel does much good overall other than tell an attacker you aren't running a specific version of apache or php.

---

### Post by kosmokramer314 on 2014-06-04
I find value in these for your everyday security:

1.Install and configure Firewall - ufw (this can be frustrating when testing, so I would advise shutting OFF ufw when testing new applications..when ready, turn it back on and adjust firewall rules if needed)
3.SSH - Key based login, disable root login and change port (key based login is great, but if you log in from many different locations this can be difficult)
4.Protect su by limiting access only to admin group 
10.Install and configure Apache application firewall - ModSecurity
12.Scan logs and ban suspicious hosts - DenyHosts and Fail2Ban
15.Scan open Ports - Nmap (followed by figuring out what needs to be open or not)

---


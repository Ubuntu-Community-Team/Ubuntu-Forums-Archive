---
title: "Firefox 1.x multiple vulnerabilities"
date: 2006-02-07
forum: Server Platforms
---

### Post by dejitarob on 2006-02-07
Mozilla has [released]("http://www.mozilla.com/firefox/releases/1.5.0.1.html") Firefox 1.5.0.1 in order to fix several bugs and multiple security vulnerabilities, "the most serious of which could lead to remote code execution". Here are the details of the vulnerabilities via [secunia.com]("http://secunia.com/advisories/18700/"):

> Multiple vulnerabilities have been reported in Firefox, which can be exploited by malicious people to bypass certain security restrictions, conduct cross-site scripting attacks, potentially disclose sensitive information, and potentially compromise a user's system.

1) Some errors in the JavaScript engine where certain temporary variables are not properly protected may be exploited to execute arbitrary code via a user-defined method triggering garbage collection.

One of the vulnerabilities affects only version 1.5. The other affects version 1.5 and prior.

2) An error in the dynamic style handling can be exploited to reference freed memory by changing the style of an element from "position:relative" to "position:static".

Successful exploitation may allow execution of arbitrary code.

The vulnerability has been reported in version 1.5.

3) An error in the "QueryInterface" method of the Location and Navigator objects can be exploited to cause a memory corruption.

Successful exploitation may allow execution of arbitrary code.

The vulnerability has been reported in version 1.5.

4) An input validation error in the processing of the attribute name when calling "XULDocument.persist()" can be exploited to inject arbitrary XML and JavaScript code in "localstore.rdf", which will be executed with the permissions of the browser the next time the browser starts up again.

5) Some integer overflows in the E4X, SVG, and Canvas functionalities may be exploited to execute arbitrary code.

The vulnerabilities have been reported in version 1.5.

6) A boundary error in the "nsExpatDriver::ParseBuffer()" function in the XML parser may be exploited to disclose data on the heap.

The vulnerability does not affect version 1.0.

7) The internal "AnyName" object of the E4X functionality is not properly protected. This can be exploited to create a communication channel between two windows or frames having different domains.

This does not pose any direct risks and does not allow bypass of same-origin restrictions or disclosure of web content from other domains.

---

### Post by spartas on 2006-02-07
I made a post about this exact issue [here](http://ubuntuforums.org/showthread.php?t=126622) just yesterday.  Hopefully it will be secured before too long.

---

### Post by ice60 on 2006-02-07
i don't think they effect Ubuntu. i was looking at it earlier today at securityfocus. i'll see if i can find the page i was looking at.

---

### Post by ice60 on 2006-02-07
[http://www.securityfocus.com/bid/16476](http://www.securityfocus.com/bid/16476)

[color=red]EDIT[/color] i just asked about it and it looks like Ubuntu is vulnerable.

---

### Post by Janzuka on 2006-02-08
So is it possible that there is going to be an update for breezy to fix that problem somehow, or do i have to install the latest version of firefox to be safe?

---

### Post by Oceola on 2006-02-08
Firefox 1.5.01 ha been available for several weeks and updated the 1.5 I've been running for a while. Seems all you had to do was allow the autoupdate to occur. Mine went smoothly with no issues and works fine. It's actually faster than 1.5 and i thought that was a big improvement over 1.07.
By the way before some troll wants to caustically remark on the failures, everything works and most of the issues I see are operator error or just a failure to explore the software, opting for the Microsoft mentality of having everything hidden, even the errors or flaws.;)

---

### Post by towsonu2003 on 2006-02-08
[QUOTE=Janzuka]So is it possible that there is going to be an update for breezy to fix that problem somehow, or do i have to install the latest version of firefox to be safe?[/QUOTE]
With this security hole, they will now **have to** update the firefox in the repositories to 1.5.0.1... Previously, they didn't want to do that, claiming that there was no security issues with 1.0.7 so it really didn't need to be updated. From my point of view, they just didn't want to deal with the major breakage firefox brings into ubuntu. I guess now (hopefully) they have to deal with it...

Hopefully, they will understand that this was a mistake and fix this dependency thing between a number of crucial packages and firefox (just a browser) when Dapper comes out. 

So I guess this should be brought up in the Dapper forum too?

I've been long disturbed by the integration of firefox into the distro anyway...

PS. From [http://www.securityfocus.com/bid/16476](http://www.securityfocus.com/bid/16476) :
> Multiple Mozilla Products Memory Corruption/Code Injection/Access Restriction Bypass Vulnerabilities:
Vulnerable:
*Mozilla Firefox 1.0.7*
Mozilla Firefox 1.0.6
Mozilla Firefox 1.0.5
Mozilla Firefox 1.0.5
Mozilla Firefox 1.0.4
Mozilla Firefox 1.0.3

PS. Offtopic remark: what happened to LordHunter? S/he would usually get involved into such discussions?

---

### Post by Oceola on 2006-02-08
I don't understand this dependency on the Gecko engine. At the Firefox site there's discussion of this issue being improved and simplified for Dapper and here there's seems to be a completely different perspective and an almost disregard for even the current changes.

When I went to install 1.5 there was the issue of the failure to suppiort yelp and its' loss. I couldn't install Breezy as i'm on Dial up and the disc I recieved would have left me off line and with hours maybe days of patches and fixes.  In an effort to maintain the use of Ubuntu and upgrade I've located sites and softwares which showed a dependence on the Gecko engine like Firefox but they also showed you could substitute Thunderbird's Gecko engine. If the Gecko engine is the issue for providing linkage, why not just use the engine on it's own and allow Firefox to stand alone or make connections where it will. I'd like to upgrade to Dapper and use the 1.5 or 1.5.01 which I already have installed in Hoary but can't see losing the upgrade capabilities of my current Firefox which worked splendidly in order to be in the same circumstance which Breezy created.

What bothers me most is this cloistered response to an open souce situation. This OS should allow the installation of all sorts of software without having to have some special manifestation which requires such a massive upgrade and the possible exclusion of software which folks are using.

---

### Post by towsonu2003 on 2006-02-08
I wonder if this is an issue for other distros as well... ?

---

### Post by dejitarob on 2006-02-08
Yes, these vulnerabilities are for all versions of Firefox 1.x regardless of which platform, distribution, etc.

---

### Post by towsonu2003 on 2006-02-08
[QUOTE=dejitarob]Yes, these vulnerabilities are for all versions of Firefox 1.x regardless of which platform, distribution, etc.[/QUOTE]
oh :) I meant: I wonder whether other distros use firefox in such a dependent way. What, for example, would happen if you uninstalled firefox in Slackware or Suse?

---

### Post by ice60 on 2006-02-14
have you all had Firefox updates? because i haven't had any system updates for about 5 days. i'm just wondering if i've missed some updates because i had a problem with my sources.list

---

### Post by towsonu2003 on 2006-02-14
[QUOTE=ice60]have you all had Firefox updates? because i haven't had any system updates for about 5 days. i'm just wondering if i've missed some updates because i had a problem with my sources.list[/QUOTE]
there are no updates for firefox that's in the repositories (1.0.7). And I'm pretty much hopeless that there will be any. Although it now is a security issue, it is too much integrated into ubuntu, so they can't easily update it. 

people using 1.5 are getting updates using the software's own update utility after some tweaks. see wiki.ubuntu.com/FirefoxNewVersion (section: updating)

---

### Post by ice60 on 2006-02-16
[QUOTE=towsonu2003]there are no updates for firefox that's in the repositories (1.0.7). And I'm pretty much hopeless that there will be any. Although it now is a security issue, it is too much integrated into ubuntu, so they can't easily update it. 

people using 1.5 are getting updates using the software's own update utility after some tweaks. see wiki.ubuntu.com/FirefoxNewVersion (section: updating)[/QUOTE]
thanks, i'm not sure what to do because i mainly use Opera, if anything happened to Opera i could always just use apt to install something else instead of having to use Firefox 1.0.7

it's made me realise i'm responsible for my computer, i'm not sure what i was thinking :confused: i really thought the Ubuntu maintainers looked after all the default program installs :rolleyes: at least i've woken up abit :-D

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=ice60]
: i really thought the Ubuntu maintainers looked after all the default program installs :rolleyes: at least i've woken up abit :-D[/QUOTE]
don't take my word for granted...

---

### Post by towsonu2003 on 2006-02-22
[https://launchpad.net/distros/ubuntu/+bug/32083](https://launchpad.net/distros/ubuntu/+bug/32083)

---


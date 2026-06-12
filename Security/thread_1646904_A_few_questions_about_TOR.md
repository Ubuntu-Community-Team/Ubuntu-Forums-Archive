---
title: "A few questions about TOR"
date: 2010-12-16
forum: Security
---

### Post by mehmeh12 on 2010-12-16
First off anonymous is Tor? I know that you basically connect to three relays via tls encryption but how do you verify this- running the traceroute command on tor dosent seem to work...the connection just times out...

Secondly where can i find the 'Terms of service' for TOR? Their website has a legal section and another section for 'abuse' but i cant seem to find any legally binding documents regarding the tos. My isp has a tos-why not tor?

---

### Post by mehmeh12 on 2010-12-16
And no offense to that guy who posted in one of my threads (his website got flagged down by web of trust) but are there any well know distros that include TOR by default in their live cd's?

---

### Post by bodhi.zazen on 2010-12-16
If you read the pages:

[http://www.torproject.org/docs/faq-abuse.html.en](http://www.torproject.org/docs/faq-abuse.html.en)

[http://www.torproject.org/eff/tor-legal-faq.html.en](http://www.torproject.org/eff/tor-legal-faq.html.en)

You will see:

> Please take a look at the Tor Legal FAQ, and contact EFF directly if you have any further legal questions.

So I would imagine questions about "terms of service" is a "further legal question" and you should contact EFF directly (rather then post on the Ubuntu forums).

Likewise we are here for technical support, ie getting tor up and running.

I suggest:

[http://www.torproject.org/projects/torbrowser.html.en](http://www.torproject.org/projects/torbrowser.html.en)

Or you can install and configure it yourself if you prefer:

[http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

---

### Post by mehmeh12 on 2010-12-17
Ok i tried out the tor browser on a usb key and it seems to work fine-but is it private-does using tor browser on a usb key only leaves traces on the usb key and not the main system? 

Speaking of traces does using a live cd on a computer DEFINITELY leaves no traces on the main system? 

In relation to a privacy distro live cd can anyone here comment on ubuntu privacy remix [https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)  ? just check the site at [https://www.privacy-cd.org/en/no-network](https://www.privacy-cd.org/en/no-network) and it seems you cant use this distro for network access. 

are there better or worse privacy live cd's out there? at the moment im having a look at distrowatch but most distros seem to be more general usage rather than privacy per se.

---

### Post by bodhi.zazen on 2010-12-17
> **mehmeh12 said:**
> Ok i tried out the tor browser on a usb key and it seems to work fine-but is it private-does using tor browser on a usb key only leaves traces on the usb key and not the main system? 

Speaking of traces does using a live cd on a computer DEFINITELY leaves no traces on the main system? 

In relation to a privacy distro live cd can anyone here comment on ubuntu privacy remix [https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)  ? just check the site at [https://www.privacy-cd.org/en/no-network](https://www.privacy-cd.org/en/no-network) and it seems you cant use this distro for network access. 

are there better or worse privacy live cd's out there? at the moment im having a look at distrowatch but most distros seem to be more general usage rather than privacy per se.

There are much much better methods of increasing privacy then using a live CD.

Use "private browsing" and I will try to finish my tutorial on privacy.

---

### Post by Agent ME on 2010-12-18
When using an Ubuntu Live CD, the only thing on the host computer that will have any traces left will be the swap drive if one exists. "sudo swapoff -a" will disable using it once you're logged on in the Live CD.

---

### Post by ottosykora on 2010-12-19
If you dont missuse the browser included , then nothing should be left, but sometimes people tend to feed it with dozens of extensions and while Torbutton will try to switch off such extensions, people tend to expect too much here.
Also close the browser properly, then all rests are delted, but swapping can have something in it depending on your ram size probably.
Also note, that tor will anonimize only websurfing, not simply all internet protocols at once.

---

### Post by qwertyomg on 2010-12-20
> **ottosykora said:**
> If you dont missuse the browser included , then nothing should be left, but sometimes people tend to feed it with dozens of extensions and while Torbutton will try to switch off such extensions, people tend to expect too much here.
Also close the browser properly, then all rests are delted, but swapping can have something in it depending on your ram size probably.
Also note, that tor will anonimize only websurfing, not simply all internet protocols at once.


Ive read the tor site but I find some things rather confusing. So tor will only encrypt the http and https internet browser protocols yes? 

What are protocols that Tor does not protect? 

If ive read the tor site correctly Tor basically puts 3 encrypted proxies in in front of your real ip address and the site you are viewing-so if would be like this-'Real ip address (you)-tor address 1-tor address 2-tor address 3-Website ip (eg google)'. Is this correct? 

Is there any benefit in adding more proxies while using tor?

---

### Post by bodhi.zazen on 2010-12-20
TOR is but one of many tools you need to deploy for privacy and you need to understand the limitations of TOR.

I highly suggest you read the TOR FAQ.

In terms of adding a proxy, a better question is what do you want to accomplish with that ?

See also: 

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

In terms of other protocols, what protocol are you wanting to privatize ? IRC ? FTP ? VNC ?

There are methods with each of these protocols, probably want to look at VPN or ssh.

---

### Post by StephenF on 2010-12-20
> **mehmeh12 said:**
> First off anonymous is Tor? I know that you basically connect to three relays via tls encryption but how do you verify this- running the traceroute command on tor dosent seem to work...the connection just times out...

I heard most nodes bounce around Washington D.C. where the U.S. intelligence agencies live. Make of that what you will but my guess is if Uncle Sam owns all the nodes your connection interacts with they will know who you are and what you are looking at.

---

### Post by ottosykora on 2010-12-25
@qwertyomg

well it will definitely serve all TCP traffic, but! it depends on client software. So while there is a straight forward way of using it for browsing, there is nothing for other things like mail or ftp . I simply could not find any useful client apps able to use it so simple as browsers do.

---

### Post by ottosykora on 2010-12-25
@ StephenF

>I heard most nodes bounce around Washington D.C. where the U.S. intelligence agencies live.<

then you have heard a big nonsense. Nobody prevents you to have a look where the nodes are, they are listed even on the GUI vidalia for everyone. So look and see how many are in US. You will see it is small minority.

Then even if someone 'owns' or operates a node, it is simply not possible to trace or decrypt the traffic in any reasonable time to be able to use it. It is encrypted by asymetric cryptography, session keys lasting for seconds only. 

So dont belive or spread such 'news' unless you have some clear evidence.

---

### Post by Habeouscorpus on 2010-12-25
If I might add my piece? TOR is great for basic privacy things. Say, you have a weird, legal obsession that might get you laughed at. TOR would save you there. Firefox+TOR+torbutton=All you need. 

But if you're doing illegal stuff? I wouldn't recommend it. Millions of things can kill you: saved files, bookmarks, logging into services in the TOR state, Flash cookies (that don't get deleted in the browser), fonts, system time, time zone, etc. 

It's good up to a point. But then it gets to be a little more trouble then it's worth.

But, you can encrypt all traffic. just set local proxy settings to localhost:8118 and you're good. It's slow, but you don't throw your ip out there for everyone to see and remember. That, and it's a pain to set up. Oi.

---

### Post by bodhi.zazen on 2010-12-26
> **Habeouscorpus said:**
> If I might add my piece? TOR is great for basic privacy things. Say, you have a weird, legal obsession that might get you laughed at. TOR would save you there. Firefox+TOR+torbutton=All you need. 

But if you're doing illegal stuff? I wouldn't recommend it. Millions of things can kill you: saved files, bookmarks, logging into services in the TOR state, Flash cookies (that don't get deleted in the browser), fonts, system time, time zone, etc. 

It's good up to a point. But then it gets to be a little more trouble then it's worth.

But, you can encrypt all traffic. just set local proxy settings to localhost:8118 and you're good. It's slow, but you don't throw your ip out there for everyone to see and remember. That, and it's a pain to set up. Oi.

torbutton helps with some of that, but I tend to agree. People are overly reliant on TOR.

I do have a privacy page, I should add ssh tunnels =)

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

You also have to watch DNS lookups

---

### Post by Soul-Sing on 2010-12-26
The weak part of secure and private or even "anonymous" browsing is the webbrowser set-up. A standard profile leaks badly.

In stead of a focus on TOR, you could take a look at JONDO, it comes with a promise of private and secure webbrowsing.( Which is not anonymous webbrowsing)
JONDO as a project has made a great come back. Has a possibility to use it for free, and comes with JONDOfox a very "safe" and private firefox profile/set up.
JONDO is supported by several ubuntu forums. And in imho deserves the support.
: [http://anonymous-proxy-servers.net/en/software.html](http://anonymous-proxy-servers.net/en/software.html)
: [http://anonymous-proxy-servers.net/en/help/firststeps2.html](http://anonymous-proxy-servers.net/en/help/firststeps2.html)
(adding the Jondo repository to Ubuntu)

weakpoints: slow 
strongpoint: great software and comes with a very private firefoxprofile by default, for secure and private webbrowsing.

---

### Post by bodhi.zazen on 2010-12-26
> **leoquant said:**
> The weak part of secure and private or even "anonymous" browsing is the webbrowser set-up. A standard profile leaks badly.

In stead of a focus on TOR, you could take a look at JONDO, it comes with a promise of private and secure webbrowsing.( Which is not anonymous webbrowsing)
JONDO as a project has made a great come back. Has a possibility to use it for free, and comes with JONDOfox a very "safe" and private firefox profile/set up.
JONDO is supported by several ubuntu forums. And in imho deserves the support.
: [http://anonymous-proxy-servers.net/en/software.html](http://anonymous-proxy-servers.net/en/software.html)
: [http://anonymous-proxy-servers.net/en/help/firststeps2.html](http://anonymous-proxy-servers.net/en/help/firststeps2.html)
(adding the Jondo repository to Ubuntu)

weakpoints: slow 
strongpoint: great software and comes with a very private firefoxprofile by default, for secure and private webbrowsing.

And how does it stand up to fingerprinting ?
does it break "basic functions" most people expect such as javascript, flash, cookies (need cookies to log into many web sites), etc ?

When you "install" the browser or proxy from the tar ball, does it install in $HOME or onto the system ?

---

### Post by Soul-Sing on 2010-12-26
Referer-Management

> With it, the Referer is not simply deleted as some webservices are not available without it. Rather, the Referer will or will not be set depending on the context of a particular request
User Agent-Management

> Information regarding users surfing the web may not only be gathered analyzing the Referer but examing the individual User Agent header as well. Therefore, we built an uniform User Agent which all users of JonDo are sending along while requesting pages on the WWW. If a user wants to connect to the Tor network instead of using JonDo the User Agent is rebuilt again, this time matching the one issued by the Tor project and its browser add-on, Torbutton. And, additionally, if someone wants to configure a proxy manually then she has the opportunity to choose between different User Agents, i.e. Unchanged (leaving the default setting), JonDo and Tor:
Mitigating cache attacks

> Protecting search queries at your workplace
n order to mitigate the risk that an outsider might get to know the queries entered into the browser's searchbar, JonDoFox erases them just after they were submitted. Furthermore, the search history gets deleted every thirty minutes. By this means it can on the one hand not happen anymore that the last search query is visible to everyone having access to the user's browser session. On the other hand JonDoFox minimizes the possibility that entries in the search history may compromise the user without loosing the search history feature completely.

Control Cookies with CS-Lite

Filter advertisements with AdblockPlus

Control active contents and enforce SSL with NoScript

Controlling JavaScript

Protection against dangerous flash videos: Downloading videos with UnPlug

> To prevent having to activate dangerous Flash in your browser, you should always download web videos to your hard drive and play them from there. This also saves you the additional traffic which would be needed to view a streaming video again. Besides some links to video download sites, JonDoFox contains the download tool UnPlug for this purpose. If you are visiting e.g. a YouTube page, just click on the menu entry (marked in red) in your Tools menu and select the video you would like to download:

this information provides information about the jondofirefox profile and is quoted directly from the relevant website.
Afaik it is a firefoxprofile only, but isn't installed in /home.
You got two firefox installs: the default one, and jondofox.

---

### Post by bodhi.zazen on 2010-12-26
Hmm ... 


They want $$ for a "premium" membership and that would speed up your connection. They limit how much you can use the network.

The other information you provided was fairly "standard" and so I will stay with my current set up and if needed would prefer TOR.

I agree with your what you are saying though, many people user TOR without knowing the details.

Personally I do not car much about my ip address, ip address is cheap.

Privoxy + NoScript + some browser settings (block cookies, better privacy, clear your cache and browsing history, etc) does a really nice job, the only "leak" would be an ip address, but since most people get an ip via an ip provider, via dhcp, an ipaddress is, IMO, fairly meaningless (I think people get too concerned about their IP address and loose sight of all the other leaks).

I am satisfied with what I "lead" to proxy judges and fingerprinting, with my settings I am as low as 1 in 300. To keep java and javascipt working I have to raise that to 1 in 2000.

With that in mind, I would live to see a posting of the privacy you get from a proxy judge and independent fingerprinting with ff + tor + torbutton vs this new fee for service :p

---

### Post by ottosykora on 2010-12-26
Well yes, I met lot of people who belived that by installing TOR with all that vidalia etc, they automaticaly have some kind of VPN to th erest of the world.

Well the tunneling or VPN seems to have some magic aura around it, since there many people who think: when I install VPN on my computer then all I do is secret.
They do not relize that all such things are just two ends communication.

Some people think, the TOR button in Firefox will hide the whole computer and they think that they communicate with some ultimate invisible tunnel with the google search website.

All I am trying to tell them, yes the communication betwenn the TOR nodes is encrypted, but at the end it has to go unencrypted to the called webserver.

Also , yes one an set up the local proxy (polipo, privoxy) so that it will capture all traffic, but this is kind of manual work, most people will not follow, they will just click the TOR button and be happy. This will serve the http, but not much more in itself. Therefore my warnings.
The TOR button will at least attempt to disable some plugins and addons which like to comunicate themselves with the net , will try to switch off some scripting etc. Again fine for avarage user.
But we have to make the avarage user aware of the fact, that at this moment he is only obfuscating his browsing , not more.
He can have more, but it is not delivered in form of one click feature.

---

### Post by bodhi.zazen on 2010-12-26
Define "average user". Most users can not be bothered with such privacy issues or rapidly become frustrated with these tools (most average users expect flash / java / javascript / embeded video / etc to "just work").

I agree setting up a proxy server is a bit of work, but from a sys admin perspective it is easier. I can "shield" all boxen and clients on my LAN this way, otherwise I have to go box-by-box, user-by-user, client-by-client. With a proxy server I can offer some (not perfect mind you) privacy to all users all browsers with minimal effort.

Also using these tools, you stand out like a sore thumb on any type of fingerprinting, assuming you do not take further measures, lol.

For the average user I advise :

Noscript + hide user agent + better privacy + clear your history.

good balance of privacy without too much hassle. If one feels he or she needs more, there is a lot of learning required.

---

### Post by ottosykora on 2010-12-26
@Habeouscorpus

>just set local proxy settings to localhost:8118 and you're good.<

well in theory this should work, but in practice I was motly not able to use it for anything. Mailservers for example will just drop with 'timeout', even simple POP3 is not able to cope with it. FTP is also mostly not building up connection, it it conects then subsequent tasks and command time out.
How do you manage to make it some kind of useful for anything else then http?

---

### Post by Habeouscorpus on 2011-01-07
I was mainly talking about webbrowsing. (I do my email online, not through local programs, so it slipped my mind... :P)

There is a way, but it is complicated and really, really tricky. Your best bet is to have firefox+torbutton for your tor things, and then another browser for legit traffic.

---


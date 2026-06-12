---
title: "Use a Blocklist on P2P or be Tracked 100% of the Time!"
date: 2007-10-11
forum: The Cafe
---

### Post by starcraft.man on 2007-10-11
[Article]("http://arstechnica.com/news.ars/post/20071010-p2p-researchers-use-a-blocklist-or-you-will-be-tracked-100-of-the-time.html")

I just happened across this article on Ars. I think it's pretty disturbing, though it really just confirms the paranoia I've had for a while. What I find more interesting is the top 12 of them seem to be operating out of bogon ranges. Almost like they have something to hide... So, how exactly did they get these ranges? I thought they were off limits to everyone until assigned.

Anyway, I figured I ought to bring this to people's attention (especially casual users who might not know). While I don't really condone illicit behaviour on the networks I don't think innocent and everyday folks should just be tracked willy nilly because these companies believe we are all guilty as sin the minute we connect. The ironies of ironies being that some these companies then turn around and use p2p as a back end to many legitimate video streaming services, jerks.

For those wishing it, there are fairly effective blocklists available. The most prominent being peerguardian on Windows (I don't think their Linux client works that well last I checked). There is an alternative called [MoBlock]("http://moblock.berlios.de/") but when I tried it I had mixed results. Instead, I just use simple blocklists that work with integrated client IP filters. [Bluetack hosts a blocklist]("http://www.bluetack.co.uk/config/splist.zip"), you can download it separately and import locally to you client or do it automatically from such clients as Ktorrent (as seen below).

For access to the Ktorrent IP Filter go Settings > Configure Ktorrent > Plugins > Load IP Filter. Then go to the IP Filtering Tab and check use filter and download the listed one (by default it's set to bluetack I believe). If an error is returned then you probably just need to register for the site (it's free registration) and try again.

Have a nice day and I hope this crusade doesn't get any worse. Next thing you know these companies will expect spy software installed locally on your machine, your router and your damn modem. Why don't these guys just hire the KGB while they are at it...

---

### Post by Dimitriid on 2007-10-11
Very interesting and useful, thanks.

---

### Post by pelle.k on 2007-10-11
> There is an alternative called MoBlock but when I tried it I had mixed results.
When did you try it? There's been som recent changes to get it in good shape, but it should be fairly stable by now. As long you you run gutsy,feisty there are even native repos for you to utilize.
btw, **moblock** is a command line application. It *doesn't* mix very well with iptable firewalls such as firestarter though....
[http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

If you wan't something grapical (GUI), then try **ipblock**. It also has the advantage to work *with* an iptables firewall (such as firestarter).
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by diskotek on 2007-10-11
f'rst of all thank you for this topic. i found it very useful.

i found a esaier solution for deluge users (what a good client).

there is a plug in that allows you install ipfilter. you can easily install it via "plug-ins" and configure it. 

here is the ip listsfor this plug-in: [http://dev.deluge-torrent.org/wiki/BlocklistPlugin](http://dev.deluge-torrent.org/wiki/BlocklistPlugin)

note: however i downloaded the list viw url, deluge didn;t imported them yet.. anyway, i;m working on it. so may be it;s not the easy way!

---

### Post by Crashmaxx on 2007-10-11
How often are blocklists updated? And therefore, how often to I need to load the list again?

Azureus seemed to load the list every start up, but KTorrent only has me load it once. Am I fine as long as it is loaded, or do I need to do it again after a while to update it?

---

### Post by xpod on 2007-10-11
> For access to the Ktorrent IP Filter go Settings > Configure Ktorrent > Plugins > Load IP Filter. Then go to the IP Filtering Tab and check use filter and download the listed one (by default it's set to bluetack I believe). If an error is returned then you probably just need to register for the site (it's free registration) and try again.

I usually always have the problem downloading the blocklist via ktorrent itself but rather than sign up just downloading it from the site manually,then using it seems to always work fine.

---

### Post by starcraft.man on 2007-10-11
> **Dimitriid said:**
> Very interesting and useful, thanks.
Your welcome.

> **pelle.k said:**
> When did you try it? There's been som recent changes to get it in good shape, but it should be fairly stable by now. As long you you run gutsy,feisty there are even native repos for you to utilize.
btw, **moblock** is a command line application. It *doesn't* mix very well with iptable firewalls such as firestarter though....
[http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

If you wan't something grapical (GUI), then try **ipblock**. It also has the advantage to work *with* an iptables firewall (such as firestarter).
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)
Hmmm, I'll have to try it again some time this week then. Thanks for the notice.

> **Crashmaxx said:**
> How often are blocklists updated? And therefore, how often to I need to load the list again?

I believe the lists are updated daily on bluetack, but there aren't that many additions/changes from day to day in general. If your really paranoid I'd say once a week, probably once or twice a month is sufficient for most. As was noted in the report, it's really a handful of large ranges already identified and in the list that catch most naive and casual users.

> Azureus seemed to load the list every start up, but KTorrent only has me load it once. Am I fine as long as it is loaded, or do I need to do it again after a while to update it?

I'd say yes your fine. I assume Azureus was pulling it down again on every startup which seems a bit overkill. While the list changes daily the most common ones are fairly constant.

---

### Post by FuturePilot on 2007-10-11
Give ipblock a try. I just tried it. It's very similar to Peer Guardian

---

### Post by teh'p3nsi0n3r on 2007-10-11
> **FuturePilot said:**
> Give ipblock a try. I just tried it. It's very similar to Peer Guardian

yea i just tried ipblock i couldnt get moblock to work, but ipblock seems like it will do the job, also using the bluetack list on the ipfilter in ktorrent :)

---

### Post by Kvark on 2007-10-11
The article says 12-17% of the users are blacklisted. How accurate are those blacklists, can over 12% of all P2P users really be working as spies?

The research is done on Gnutella while you are talking about BitTorrent here. I think there is less spying on torrents because with torrents they need to get and connect to a separate .torrent file for each file they want to spy on. If they see someone on one torrent they only have one instance of infringement. With other P2P programs they can see all files someone is sharing at once so they get many instances of infringement right away.

Blocking the spies on torrents doesn't even help if it is enough to make a file available. By the time they try to connect to you they already know that you are connected to the torrent for that file and are offering them parts of that file. With other P2P programs they don't know which files you are making available until after they connect to you so blocking helps there. If they have to download a small part of the file from you to prove that a small part of what you offered really was the real thing then blocking helps with torrents too. If they have to download the whole file from you to prove that the whole file you offered was the real thing then they can't prove anything over torrent since they don't get the whole file from the same user.

Well, there is no need to worry about these things when there is open source software and free culture to share instead.

---

### Post by Red.Heron on 2007-11-14
I have a BIG problem with Bluetack. As such, I won't ever use their lists again. I'm working on finding people to compile our own lists, but without being able to do the necessary millions of WHOIS lookups every week, it'll be difficult to get something like this accomplished.

One month after the MediaDefender email leak, 2% of their IP addresses were on Bluetack's lists.

However, tor servers and the Relakks privacy service were both on the blocklist.

The blocklists block 33% of all addresses on the internet for one reason or another.

They block the uTorrent site because the developer of uTorrent created a DLL file (not related to torrents or P2P in any way, FWIW) and sold it to one of the subsidiary companies of a known anti-P2P network. The uTorrent creator tried to talk to the Bluetack folks and was told he was permanently on the list because of his decision to sell an unrelated piece of software to a company that probably wasn't using it for anything P2P-related.

They block a bunch of IP addresses that are mislabeled because the *former* owners of those IP addresses used them for anti-P2P uses.

As of today, they *don't* block all of the MediaDefender IP addresses.

As of today, they *don't* block the RIAA's lawyers site.

As of today, they *don't* block the MPAA's monkies in 12 countries.

I'm thinking that Bluetack doesn't really know what they're doing, but that's just my own two cents' worth.

It would be better to compile our own lists and then post them up, with a date that the IP was last checked as well as who owns it and why it was listed.

---

### Post by PartisanEntity on 2007-11-14
> **Red.Heron said:**
> 

However, tor servers and the Relakks privacy service were both on the blocklist.

That's interesting, why is Relakks on their blocklist?

---

### Post by Joedude on 2007-11-14
I just wait until they come knocking on my door.

---

### Post by frodon on 2007-11-14
> **starcraft.man said:**
> I just use simple blocklists that work with integrated client IP filters. [Bluetack hosts a blocklist]("http://www.bluetack.co.uk/config/splist.zip"), you can download it separately and import locally to you client or do it automatically from such clients as Ktorrent (as seen below).For those interested you can also handle this automatically using a perl script to convert the list into iptables rules and a cron job to download the list on a regular basis and refresh the iptables rules.
If there's many users interested into this i can try to create a tutorial for this with the needed perl script.

All you need is a list presented in a known way, converting this into iptables rules is just scripting, however i think it would take a lot of time to load such a big list.

---

### Post by pelle.k on 2007-11-14
It does indeed, and for that matter queuing stuff to userspace to do the filtering, like moblock/iplist does is much more practical and "pretty", than doing it the hard way. moblock/iplist does it with very little cpu usage btw.

---

### Post by boast on 2007-11-14
yeah ive been running moblock on my torrentflux server since I put up last year.


It doesn't guarantee anything, but its better than nothing.

---


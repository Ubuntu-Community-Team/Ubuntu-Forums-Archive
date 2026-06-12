---
title: "Allow access by MAC address"
date: 2010-09-19
forum: Security
---

### Post by k33bz on 2010-09-19
Is there a way I can set up my server or even router to only allow access from certain MAC addresses?

---

### Post by macem29 on 2010-09-19
don't know about all routers, but the Lynksys stuff I prefer definitely allows MAC address filtering

---

### Post by k33bz on 2010-09-19
What about Netgear? Or should I use Ascend Pipeline 50? (Only ask cause I have one here at home)

---

### Post by NFblaze on 2010-09-19
I'm not totally sure but on the server you maybe able to use iptables.

Though on the routers you can use Mac Filtering if your router supports it. If not you should check out 3rd party router firmwares (like dd-wrt and Tomato) that may enable support for it.

---

### Post by k33bz on 2010-09-19
Ok, I do have MAC filtering available on my router. So question is if I have port forwarding enabled to route ssh to my server, only the MAC addresses allow to have access are the only ones that can be forwarded to my server?

---

### Post by cariboo on 2010-09-19
Spoofing a mac address is pretty trivial, please don't rely on mac address filtering for security. [These]("http://www.google.ca/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=spoof+mac+address+howto") are the results I get when doing a quick search on spoofing a mac address.

---

### Post by k33bz on 2010-09-19
> **cariboo907 said:**
> Spoofing a mac address is pretty trivial, please don't rely on mac address filtering for security. [These]("http://www.google.ca/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=spoof+mac+address+howto") are the results I get when doing a quick search on spoofing a mac address.

That I do know is out there, it is just one of the many security things I will be doing to my server. IP address filtering is out of the question since my laptop and wifes laptop will most of the time be using different IP addys. We do alot of moving and traveling around both for personal and business.

So no worries MAC filtering is not the only thing I will be doing to secure my server.

---

### Post by bodhi.zazen on 2010-09-19
Honestly, for ssh, all you need are to :

1. use keys, disable password logins.

2. A few "simple" iptables rules.

---

### Post by k33bz on 2010-09-19
Can you give me some links on both of those suggestions?

---

### Post by CharlesA on 2010-09-19
Check [here]("https://help.ubuntu.com/community/SSH") for some info on configuring OpenSSH server.

---

### Post by FuturePilot on 2010-09-19
MAC address filtering on routers is usually related to wireless access. It has nothing to do with who can access a machine through a forwarded port. And MAC addresses get stripped over NAT anyways.

---

### Post by cprofitt on 2010-09-19
> **bodhi.zazen said:**
> Honestly, for ssh, all you need are to :

1. use keys, disable password logins.

2. A few "simple" iptables rules.


Bodhi -- got link to the 'simple' rules?

---

### Post by CharlesA on 2010-09-19
> **cprofitt said:**
> Bodhi -- got link to the 'simple' rules?

I am almost positive one of the rules is this:

```
# 10 minute lockout if trying to bruteforce
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP
```

I use that one. :)

---

### Post by bodhi.zazen on 2010-09-19
> **cprofitt said:**
> Bodhi -- got link to the 'simple' rules?

Yes, they are in my iptables-save

[http://bodhizazen.net/adblock/iptables.strict](http://bodhizazen.net/adblock/iptables.strict)

```

sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m tcp -m state --state NEW -m recent --set --name SSH --rsource [FONT=monospace]
sudo iptables [/FONT]-A INPUT -p tcp -m tcp --dport 22 -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP [FONT=monospace]
sudo iptables [/FONT]-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
```

You need a more liberal hit count (8-20) if you scp or svn+ssh . If yo udo not do these things, you can lower it to 1-3.

The rules will lock you out for 10 min, which is sufficient to deter the script kiddies without locking yourself out (for too long);

For additional info see :

[http://bodhizazen.net/Tutorials/ssh/](http://bodhizazen.net/Tutorials/ssh/)

Near the lower third.

---

### Post by cprofitt on 2010-09-19
Awesome -- thanks Bodhi.

---

### Post by bodhi.zazen on 2010-09-19
> **cprofitt said:**
> Awesome -- thanks Bodhi.

You are most welcome, hope those rules serve you well.

---

### Post by FuturePilot on 2010-09-19
> **bodhi.zazen said:**
> Yes, they are in my iptables-save

[http://bodhizazen.net/adblock/iptables.strict](http://bodhizazen.net/adblock/iptables.strict)

```

sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m tcp -m state --state NEW -m recent --set --name SSH --rsource [FONT=monospace]
sudo iptables [/FONT]-A INPUT -p tcp -m tcp --dport 22 -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP [FONT=monospace]
sudo iptables [/FONT]-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
```

You need a more liberal hit count (8-20) if you scp or svn+ssh . If yo udo not do these things, you can lower it to 1-3.

The rules will lock you out for 10 min, which is sufficient to deter the script kiddies without locking yourself out (for too long);

For additional info see :

[http://bodhizazen.net/Tutorials/ssh/](http://bodhizazen.net/Tutorials/ssh/)

Near the lower third.

Nice. I'm assuming this could easily be adapted for other services as well?

---

### Post by CharlesA on 2010-09-19
> **FuturePilot said:**
> Nice. I'm assuming this could easily be adapted for other services as well?
It depends on the service, but they probably can.

---

### Post by bodhi.zazen on 2010-09-20
> **FuturePilot said:**
> Nice. I'm assuming this could easily be adapted for other services as well?

Yes, it could be adapted for any service. Set a unique name for each service ( --name SSH) 

The limits on apache would likely need to be much more liberal . Apache can handle thousands of requests in a minute, for apace some people use

```
iptables -I INPUT -p tcp -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

This was suggested by [HermanAB]("http://ubuntuforums.org/member.php?u=44990") (and others if you google search) and works well for apache.

IMO apache will easily handle 100 connections / min, so if 30 / min is too strict loosen . As apache is much more "public" then ssh, no need to track and temp block ip addresses, IMO, so pick your poison.

---

### Post by FuturePilot on 2010-09-20
> **bodhi.zazen said:**
> Yes, it could be adapted for any service. Set a unique name for each service ( --name SSH) 

The limits on apache would likely need to be much more liberal . Apache can handle thousands of requests in a minute, for apace some people use

```
iptables -I INPUT -p tcp -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

This was suggested by [HermanAB]("http://ubuntuforums.org/member.php?u=44990") (and others if you google search) and works well for apache.

IMO apache will easily handle 100 connections / min, so if 30 / min is too strict loosen . As apache is much more "public" then ssh, no need to track and temp block ip addresses, IMO, so pick your poison.

Cool. Thanks!

---

### Post by bodhi.zazen on 2010-09-20
> **FuturePilot said:**
> Cool. Thanks!

You are most welcome, I like iptables so ask away =)

---

### Post by k33bz on 2010-09-22
> **bodhi.zazen said:**
> You are most welcome, I like iptables so ask away =)

I am most definitely thanking you for your advice on the keys. Just in the last three days (I just checked my auth.log, ya I know I should do it more often) I have had over 1,500 attempts to get into my system VIA ssh. I dont even leave my server on all the time, maybe 10 - 12 hours a day. So much thanks :)

---


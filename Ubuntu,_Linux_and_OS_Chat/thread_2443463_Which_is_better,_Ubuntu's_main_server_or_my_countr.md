---
title: "Which is better, Ubuntu's main server or my country's server?"
date: 2020-05-15
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-05-15
Just got an 500  Internal Server Error when I tried to update my system, so changing to Ubuntu's main server from my country's server fixed the issue.

My question is, which is better really, Ubuntu's main server or my country's server, what's the difference between the two servers and is it okay for me not to switch back to my country's server.

Thanks.

---

### Post by DuckHook on 2020-05-15
You are fine using the Ubuntu main server. It is the grand-daddy of all repos, so you can't go wrong with it.

That said, it may not be the fastest for you. Vanilla Ubuntu has a method for determining the fastest server for your locale. Settings &#8594; About &#8594; Software Updates &#8594; Ubuntu Software &#8594; Download from: &#8594; Other &#8594; Select Best Server. Frequently, this is not your country's server.

It is possible that mirrors will not synchronize with the main repo as quickly as we may like. Once they get out of sync, problems such as the one from which you appear to have suffered will materialize. If so, you might still be better off with a mirror that is geographically closer to you than the main repo. But if you are getting acceptable download speeds from the main repo, then you will have to decide.

It is a rough rule of netiquette that one should try to offload as many updates from the main repos as possible so as not to overwhelm the upgrade system at one point. But if your local mirrors are especially lagging, then you may not have a choice.

Like many things within the FOSS ecosystem, it's a judgment call that is left largely up to you.

---

### Post by oldfred on 2020-05-15
List of mirrors, speeds & days behind on updates.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

And the mirror I found, is not on above list so DuckHook's method may be better. That was how I found the ones I use. But try several times to see if consistent.

---

### Post by ardouronerous on 2020-05-15
Thanks for the explanation.

I wish there was an automated failsafe where, if my country's server gets a "500  Internal Server Error", then instead of failing to download updates, the updater will try to find a working mirror that's close to your location and download from that, while maintaining that the default server for your system is still your country's server.

---

### Post by ardouronerous on 2020-05-15
> **oldfred said:**
> List of mirrors, speeds & days behind on updates.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

And the mirror I found, is not on above list so DuckHook's method may be better. That was how I found the ones I use. But try several times to see if consistent.

That is most informative thank you.

---

### Post by Hwæt on 2020-05-15
My personal preference is the local mirror. IIRC at one point the Ubuntu master used to be rate capped at 50kb/s. But that may no longer be the case.

---

### Post by aswadt on 2020-05-26
[COLOR=#444444][FONT=&amp]Today we will be reviewing the major differences between CentOS and Ubuntu in a web [/FONT][/COLOR][paystub]("https://www.walmartone.vip/")[COLOR=#444444][FONT=&amp] hosting environment. Although this is not a fully comprehensive analysis of every single aspect of the numerous in-depth features of each operating system.[/FONT][/COLOR]

---


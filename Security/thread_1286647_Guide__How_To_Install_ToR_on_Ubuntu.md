---
title: "Guide : How To Install ToR on Ubuntu"
date: 2009-10-09
forum: Security
---

### Post by auraithx on 2009-10-09
Can't copy/paste this here as there are lots of embedded images but here is a tutorial on howto install ToR on Ubuntu

[http://blackopsecurity.net/wiki/index.php/How_To_Install_%28Ubuntu%29](http://blackopsecurity.net/wiki/index.php/How_To_Install_%28Ubuntu%29)

---

### Post by Sarmacid on 2009-10-09
Just skimmed through your guides, seem good, with lots of screenshots. However I wanted to point out a mistake you have. In the first step of the installation you have Sudo with capital S. Other than that they seem great.

---

### Post by auraithx on 2009-10-09
> **Sarmacid said:**
> Just skimmed through your guides, seem good, with lots of screenshots. However I wanted to point out a mistake you have. In the first step of the installation you have Sudo with capital S. Other than that they seem great.

Thanks, fixed. :guitar:

---

### Post by cdenley on 2009-10-09
Why compile from source? It isn't in ubuntu's repos anymore because it wasn't being maintained well. Tor has it's own repo, though.
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)
No need to compile, and it will be upgraded as updates are released.

---

### Post by auraithx on 2009-10-09
> **cdenley said:**
> Why compile from source? It isn't in ubuntu's repos anymore because it wasn't being maintained well. Tor has it's own repo, though.
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)
No need to compile, and it will be upgraded as updates are released.

Because that's exactly how they compromised JAP. They put backdoors in the binaries. Since ToR isn't in the repos it is just as easy compiling from source.

---

### Post by Sarmacid on 2009-10-09
Compiling from source is how you get the latest versions asap.

---

### Post by cdenley on 2009-10-09
> **Sarmacid said:**
> Compiling from source is how you get the latest versions asap.

If you want to check daily if a new version was released, and if it was, download the source, then compile. Much easier to let ubuntu's update manager handle that. Also, it appears that repo is updated "asap". According to their changelog, 0.2.2.3-alpha was released 9/23. The ubuntu package for that version was added 9/23.

---

### Post by cdenley on 2009-10-09
> **auraithx said:**
> Because that's exactly how they compromised JAP. They put backdoors in the binaries. Since ToR isn't in the repos it is just as easy compiling from source.

So who is going to add backdoors in their software repository? You can trust the source code they distribute, but not their signed packages? I'm not familiar with the JAP binaries you are referring to, but I fail to see how Tor's repo is any more untrustworthy than any Tor source you find, unless you personally audit all code before you compile it.

---

### Post by auraithx on 2009-10-09
> **cdenley said:**
> So who is going to add backdoors in their software repository? You can trust the source code they distribute, but not their signed packages? I'm not familiar with the JAP binaries you are referring to, but I fail to see how Tor's repo is any more untrustworthy than any Tor source you find, unless you personally audit all code before you compile it.
You don't think there are people who audit source code for an **anonymity program** like ToR? I personally know people who do and the government would not risk their investigation by publishing source code with a backdoor in it. Any backdoor would get brought to to the public eye within a few hours of it being released and everyone would know something is up.

---

### Post by cdenley on 2009-10-09
> **auraithx said:**
> You don't think there are people who audit source code for an **anonymity program** like ToR? I personally know people who do and the government would not risk their investigation by publishing source code with a backdoor in it. Any backdoor would get brought to to the public eye within a few hours of it being released and everyone would know something is up.

So you're saying the project's package maintainer might build packages using altered source code? I guess that is a valid point, but you can make the same argument about all of ubuntu, and I doubt anyone compiles their whole desktop from scratch.

---

### Post by auraithx on 2009-10-09
> **cdenley said:**
> So you're saying the project's package maintainer might build packages using altered source code? I guess that is a valid point, but you can make the same argument about all of ubuntu, and I doubt anyone compiles their whole desktop from scratch.

Yes, but ToR is much more likely to be pressured by the government into putting a backdoor in - than another program is, like the calculator. 

And I know plenty of people who compile everything from source.

---

### Post by ackanao on 2009-10-09
> **auraithx said:**
> Because that's exactly how they compromised JAP. They put backdoors in the binaries. Since ToR isn't in the repos it is just as easy compiling from source.

Please don't spread FUD like this - there's no backdoor in Tor and there was no backdoor in JAP either. Like any other responsible company they complied with perfectly legal court order:

> In 2006, there has been only one single surveillance court order to single Mix operators. A few exactly specified web addresses were affected. The observation has been stopped after the court order expired (one month).

Here's an Wikipedia article about this:
[http://en.wikipedia.org/wiki/Java_Anon_Proxy]("http://en.wikipedia.org/wiki/Java_Anon_Proxy")

And here's what they have to say about law enforcement and data retention:
[https://www.jondos.de/en/lawEnforcement]("https://www.jondos.de/en/lawEnforcement")

What did you expect from them - to protect child molestors ??? Because that's the reason why they decided to activate Logging functions on their servers.

---

### Post by auraithx on 2009-10-09
> **ackanao said:**
> Please don't spread FUD like this - there's no backdoor in Tor and there was no backdoor in JAP either. Like any other responsible company they complied with perfectly legal court order:

Uhh....DUHHHHH

> What did you expect from them - to protect child molestors ??? Because that's the reason why they decided to activate Logging functions on their servers.

Irrelevant - it could be pedos or it could be a Chinese citizen trying to bypass their governments firewall, either way they compromised their software and ToR would do the same if ordered by court. 

...which is why you compile from source.

*sigh*

---

### Post by cdenley on 2009-10-09
> **auraithx said:**
> 
...which is why you compile from source.


So you think tor will be legally obligated to install a backdoor in the source their binaries are built from, but not the source they distribute?

---

### Post by auraithx on 2009-10-09
> **cdenley said:**
> So you think tor will be legally obligated to install a backdoor in the source their binaries are built from, but not the source they distribute?

I don't think the feds will want ToR to publish the source code of an altered version of ToR that includes a backdoor. And if they did it would get picked up on pretty fast by the online community.

Which is basically exactly what I said the first time you asked me that question.

---

### Post by cdenley on 2009-10-09
> **auraithx said:**
> I don't think the feds will want ToR to publish the source code of an altered version of ToR that includes a backdoor. And if they did it would get picked up on pretty fast by the online community.

Which is basically exactly what I said the first time you asked me that question.

Would the source code in the repo contain a backdoor in your hypothetical scenario?

---

### Post by auraithx on 2009-10-09
> **cdenley said:**
> Would the source code in the repo contain a backdoor in your hypothetical scenario?

afaik the repos have .debs not source code.

---

### Post by ackanao on 2009-10-09
Well since you did your code audit, tell me did you check all Tor nodes operators and their Tor setup? There's no difference whether your Tor client/server setup is "clean" or not if all Tor nodes are malicious, backdoored or owned by goverment, agencies or whatnot. If what you're saying is true, what's the point of compiling from source?

The main threat to your anonymity are malicious Tor nodes - whether your Tor setup is backdoored or not is absolutely irrelevant if what you're saying is true.

---

### Post by cdenley on 2009-10-09
> **auraithx said:**
> afaik the repos have .debs not source code.
Apparently not.
> 
If you want to build your own debs from source you must first add an appropriate deb-src line to sources.list.

deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main

deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-<DISTRIBUTION> main


---

### Post by auraithx on 2009-10-09
> **ackanao said:**
> Well since you did your code audit, tell me did you check all Tor nodes operators and their Tor setup? There's no difference whether your Tor client/server setup is "clean" or not if all Tor nodes are malicious, backdoored or owned by goverment, agencies or whatnot. If what you're saying is true, what's the point of compiling from source?

The main threat to your anonymity are malicious Tor nodes - whether your Tor setup is backdoored or not is absolutely irrelevant if what you're saying is true.

So because there's flaws in one part of the system - we should just ignore all security precautions? 

The chances of all three nodes in a chain being malicious is very slim. + with SSL encryption they stil cannot see what you are doing - only trace you. **and** they would need to have access to the server of the websites you're accessing too.

I'm not saying ToR is without it's fallacies - all programs are, but that is no reason to be careless in other areas.

Read; [http://forum.blackopsecurity.net/viewtopic.php?f=32&t=7](http://forum.blackopsecurity.net/viewtopic.php?f=32&t=7)

> It is not illegal for them to use a network they own to do traces, but it is illegal for them to use a stolen botnet to do so. It costs a lot more to legitimately have access to 400 nodes than it does to illegally have access to 400 nodes on a botnet. LE could do this attack, but they would need to use owned machines, the machine costs alone would cost thousands of dollars a month where as a botnet would cost a few grand up front. It may be illegal for LE to do surveillance on the data that passes through exit nodes, but this depends on jurisdiction likely. I know a college was doing surveillance on exit node data for a research project and they got bitched at but not in any trouble and were determined to not be violating ethics. LE might have a harder time getting away with it, as it could easily violate wiretapping laws if they do it with out a warrant.

---

### Post by ackanao on 2009-10-09
Your assumption was that the Tor binaries are backdoored - given that Tor servers are run on Windows XP/Vista/Server2003/2008, *nixes and various Linux distributions, it is safe to assume that in most cases Tor binaries are used to install Tor - in that case Tor network is heavily compromised - hence, there's no difference whether your Tor is clean or not, since such a powerful adversary already know everything you do when you're using Tor. In your scenario, the best way to protect yourself is not to use Tor at all.

> The chances of all three nodes in a chain being malicious is very slim. + with SSL encryption they stil cannot see what you are doing - only trace you. and they would need to have access to the server of the websites you're accessing too.

There's no need for "three nodes in a chain" - your anonymity can be compromised by one, two or all three nodes if your Tor and your OS are not setup correctly; Exit nodes see all traffic, you may be leaking personally identifying informations like your IP... Adversary may own an Entry and Exit node, also there's a risk from colluding Tor routers etc.

There are also various attack metods published but only few observed in wild and as far as I know it never resulted with total breakdown of your anonymity - In most cases you were the victim of the MiTM attack or your login credentials were harvested by evil exit nodes (Dan Egerstad).

About the link you posted: 

I really doubt that Tor developers are unaware of that hypotetical scenario; Even the small number of colluding Tor nodes are detected by Tor users in Apr. 2007:

[http://archives.seul.org/or/talk/Apr-2007/msg00035.html]("http://archives.seul.org/or/talk/Apr-2007/msg00035.html")

To be honest, attack described is just a speculation and nothing more, but the important thing is that the OP is talking about a "**A custom software that should be programmed**" - "**backdoored Tor**" was never mentioned.

One more important thing is that Tor was never designed to protect Tor users from the global adversary and your hypotetical scenario describes that kind of threat.

---

### Post by auraithx on 2009-10-09
> Your assumption was that the Tor binaries are backdoored - given that Tor servers are run on Windows XP/Vista/Server2003/2008, *nixes and various Linux distributions, it is safe to assume that in most cases Tor binaries are used to install Tor - in that case Tor network is heavily compromised - hence, there's no difference whether your Tor is clean or not, since such a powerful adversary already know everything you do when you're using Tor. In your scenario, the best way to protect yourself is not to use Tor at all.

I still fail to see your point. Do you think there is **no benefit whatsoever** in compiling from source and making sure your version isn't backdoored? So what if other nodes on the network could be compromised, they also might not be. It is just a flawed argument all round.

> There's no need for "three nodes in a chain" - your anonymity can be compromised by one, two or all three nodes if your Tor and your OS are not setup correctly; Exit nodes see all traffic, you may be leaking personally identifying informations like your IP... Adversary may own an Entry and Exit node, also there's a risk from colluding Tor routers etc.
So you can leak info if it's not set-up right? So what? My site is aimed at helping new users set up their ToR correctly. And once again, just because there are attacks against ToR does not make it completely useless.

I suggest reading over this; [How ToR works]("http://blackopsecurity.net/wiki/index.php/ToR")

---

### Post by ackanao on 2009-10-09
I never said that Tor is useless, quite the contrary: I think that it is one of the best anonymity networks that you can use.

Your argument is also wrong: You choose to protect yourself from hypothetical backdoored Tor - Maybe there is a backdoor in Tor but then again it is far more reasonable to assume that there's no backdoor in Tor code.

There are some benefits when you choose to compile Tor from source, for example: 

**CircuitBuildTimeout** value is hardcoded to 30; If you want to speed-up Tor you need to change this and then you can set desired value in **torrc** file;

Depending on your threat assesment you can configure Tor to use 2 hops only;

You can contribute and help with Tor development;

...

And of course you can audit the code to be sure that there's no backdoor in Tor (if you really need to).

I never said that your guide is "no good", in fact, there's nothing wrong with it - but I had to object to your notion that there may be a backdoor in Tor binaries. I have one suggestion: Since Tor is switching to polipo maybe you can improve your guide by adding the instructions on how to install, configure and use polipo with Tor?

---

### Post by auraithx on 2009-10-09
> Your argument is also wrong: You choose to protect yourself from hypothetical backdoored Tor - Maybe there is a backdoor in Tor but then again it is far more reasonable to assume that there's no backdoor in Tor code.

My argument is there is no need to assume that it is not backdoored when it is easy enough to compile it from source. Even if theres only a 0.01% chance ToR will be infiltrated 

> I have one suggestion: Since Tor is switching to polipo maybe you can improve your guide by adding the instructions on how to install, configure and use polipo with Tor?

Sure, We have only been up for a week or so but I plan to turn us into an online community of experts that will constantly keep the less computer-literate secure. You are more than welcome to join the forum and submit your own polipo/ToR guide. ;)

[http://forum.blackopsecurity.net](http://forum.blackopsecurity.net)

---

### Post by ackanao on 2009-10-09
Well, my English is not good enough and I'm struggling here to explain myself better. Besides, I'm a "slightly paranoid human being" - I lurked this forum for a long time and only recently I decided to join the Ubuntu community and I'm trying to be useful as much as I can.

Anyways, thanks for invitation - who knows, maybe you'll see me posting on your forum. :)

About polipo:
Here's the good guide for an average Tor user - basically:

Install polipo (**sudo apt-get install polipo**)
Copy the "**conifg**" file to polipo folder
Restart polipo (**sudo /etc/init.d/polipo restart**).

[http://www.torproject.org/docs/tor-doc-unix.html.en]("http://www.torproject.org/docs/tor-doc-unix.html.en")

I switched to polipo only recently (didn't compile it from source) and it looks like it's faster than privoxy.

---

### Post by auraithx on 2009-10-10
> **ackanao said:**
> Well, my English is not good enough and I'm struggling here to explain myself better. Besides, I'm a "slightly paranoid human being" - I lurked this forum for a long time and only recently I decided to join the Ubuntu community and I'm trying to be useful as much as I can.

Anyways, thanks for invitation - who knows, maybe you'll see me posting on your forum. :)

About polipo:
Here's the good guide for an average Tor user - basically:

Install polipo (**sudo apt-get install polipo**)
Copy the "**conifg**" file to polipo folder
Restart polipo (**sudo /etc/init.d/polipo restart**).

[http://www.torproject.org/docs/tor-doc-unix.html.en]("http://www.torproject.org/docs/tor-doc-unix.html.en")

I switched to polipo only recently (didn't compile it from source) and it looks like it's faster than privoxy.

Also, it should be noted while polipo is faster that privoxy, it is less secure (is as good at cleansing data)

Also - we're coding a ToR breaker (codenamed Shallot) based on those techniques I posted earlier.
[http://forum.blackopsecurity.net/viewtopic.php?f=44&t=46](http://forum.blackopsecurity.net/viewtopic.php?f=44&t=46)

---

### Post by uplink3r on 2010-03-12
in karmic koala the config is in /etc/polipo and is called "config"
so after adding polipo repository...

```

wget https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf
sudo mv polipo.conf /etc/polipo/config
```

that screwed me up for a while

Then you install this for firefox: [https://addons.mozilla.org/en-US/firefox/addon/2275](https://addons.mozilla.org/en-US/firefox/addon/2275)

---


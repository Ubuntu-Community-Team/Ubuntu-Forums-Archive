---
title: "making my ubuntu transparent"
date: 2009-07-30
forum: Security
---

### Post by phaceone on 2009-07-30
Hello community,

i'm develeping an individual intrusion detection solution for my company. I decided to use ubuntu 8.10 as sensor operating system, because i like it :-) and my image ist very compatible to almost all hardware i can use. Ok, as a part of my solution i've installed Snort via synaptic, and started to use it with community roles.  sometimes my ubuntu alerts itsself when snort reports that this system tries to connect to snmp 161 on several clients in neighborhood, and somtimes to the nets broadcast adress (snmp too)....does anyone know about default running ubuntu processes that do so? or can anyone give me a starting point, where i can read about: configuring ubuntu to make it say nothing? you know, i'm a little bit afraid, that i cannot determine where those active network actions are coming from. is snort usually safe ? have ever been backdoors implemented into snort distributions ?...ok at the and i'll configure the iptables, so that nothing will be forwarded except of my management server commucication, but before that i want to be sure that my ubuntu is quiet....thanks for all comments!

---

### Post by igorzwx on 2009-07-30
"is snort usually safe ?"
[http://www.google.com/search?q=snort%20vulnerability&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=snort%20vulnerability&ie=UTF-8&oe=UTF-8)

---

### Post by phaceone on 2009-07-30
> **igorzwx said:**
> "is snort usually safe ?"
[http://www.google.com/search?q=snort%20vulnerability&ie=UTF-8&oe=UTF-8]("http://www.google.com/search?q=snort%20vulnerability&ie=UTF-8&oe=UTF-8")

ok thank you. maybe there are vulerbilities about snort...but can you imagine that there are there possiblby backdoors in the binaries from the ubunu mirrors ? or please tell me, what kind of process scans snmp in the neighborhood ?
..please don't give me google links...i know what i'm doing, thanks.

---

### Post by igorzwx on 2009-07-30
do not be naive.
snort is a security risk

some general info about other things
[http://ubuntuforums.org/showthread.php?t=1226286](http://ubuntuforums.org/showthread.php?t=1226286)

---

### Post by phaceone on 2009-07-30
> **igorzwx said:**
> do not be naive.
snort is a security risk

some general info about other things
[http://ubuntuforums.org/showthread.php?t=1226286](http://ubuntuforums.org/showthread.php?t=1226286)

how could it be, that someone calls his product as a de facto standard when the ids is an de facto security hole. what would you do, if you had to develope an ids ? seems nothing to rely on ?

---

### Post by igorzwx on 2009-07-30
What is reliable in this imperfect world?

---

### Post by phaceone on 2009-07-30
> **igorzwx said:**
> What is reliable in this imperfect world?

i've learnded some things in my life where i can rely on, for sure. but instead of making fun of my question, is it so hard to give me an answer......i've seen some things about snort to laugh about. i cannot believe...for example, when i send an icmp packet across the sniffers nose that is bigger that 100k snort terminates with segmentation fault. every time this happens my program will restart it. also snort community rules are producing a ton of false positive, for example the netbios things when windows clients are on. my own program tries to report all changes to the normal state of the network....but i want to use a signature based tool as well, because i'm not able to  implement all possible attack sigs...if i was able to .... i'm forced to have the 30years hackers experience, but my goal is communcation and productivity

---

### Post by igorzwx on 2009-07-30
it is not fun at all.
snort is the first thing to hack.
and antivirus programs too.
The less apps you have installed the better security.

---

### Post by igorzwx on 2009-07-30
From my subjective point of view,
the best security approach is this:
**[*Practical UNIX* and *Internet Security* | O'Reilly Media]("http://oreilly.com/catalog/9781565921481/")**

This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more **...**
oreilly.com/catalog/9781565921481/ - [Cached]("http://209.85.129.132/search?q=cache:S8ZqyAGhsCwJ:oreilly.com/catalog/9781565921481/+practical+internet+and+unix+security&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:oreilly.com/catalog/9781565921481/")

---

### Post by The Tronyx on 2009-07-30
> **igorzwx said:**
> From my subjective point of view,
the best security approach is this:
**[*Practical UNIX* and *Internet Security* | O'Reilly Media]("http://oreilly.com/catalog/9781565921481/")**

This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more **...**
oreilly.com/catalog/9781565921481/ - [Cached]("http://209.85.129.132/search?q=cache:S8ZqyAGhsCwJ:oreilly.com/catalog/9781565921481/+practical+internet+and+unix+security&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:oreilly.com/catalog/9781565921481/")

I feel like I have seen a lot of posts from you lately and unfortunately, I must say that a majority of them seem to be far from helpful and consist of nothing more than some google link that _looks_ like it might actually facilitate an answer to the question however it is far from it.

> 
snort is the first thing to hack.
...
The less apps you have installed the better security. 


This post almost saddens me.  I know we all like to be helpful but as someone who posts in this section fairly often, please do not contribute these posts if you cannot provide useful information.  Secure computing is a fairly important topic and providing useful information to new comers seeking advice is paramount.  

First, an attacker has no way to know that snort is listening since it is a passive IDS.  On its own, it does not illicit any outbound responses.  This holds true to most intrusion detection systems.  The only real way to detect an intrusion detection from the outside, in a black box scenario, is if the IDS is acting as an IPS and actively deploying IPtables rules, mod_security rules, in response to the incoming traffic.  Even then, fingerprinting the IDS for a proper vulnerability would be pretty close to impossible.

Regarding that nonsense about "the less apps you have installed..." that also saddens me.

This is largely a true statement but you fail to recognize that which every competent security-minded individual must understand.  This is the understanding that systems must provide usability in conjunction with security.  If the system is jam packed with applications there is an increase in potential exploitability however depending on the function of the server, this may hinder its usability very much (were it to go without these applications essential to the end-user).

@ the op, in accordance with what has been said by igorzwz, if you want a very secure server, lock it in a closet and install nothing to it.  Surely it won't be compromised however it's usability is non-existent.  The purpose of an IDS is NOT to make sure that nothing can access your network, it is to inform you of the threats and possible compromises facing your network so that you can act accordingly, never forget that.

I would like to preface this by saying that given enough time, anything can be hacked (relatively).  Let's think of an IDS like a chain attached to a motorcycle.  You have a chain that can withstand bolt cutters for 5 seconds.  This chain sucks and you do not want to use it.  You then have a chain that can withstand 4 minutes of bolt cutters.  Now, in the end, your bike can still get stolen but there is a huge difference between 3 seconds and 4 minutes.  What good is a chain if it's just going to get stolen?  Simply put, hopefully someone notices in those 4 minutes and can stop it before they steal your motorcycle.  This is akin to someone probing your network.  If you can identify the threats posed by attackers early on, you can prevent them rather than falling victim to them.

There is also this madness about, "IS SNORT ACTUALLY SECURE!?!?!" followed by a google post with about 5 million results.  This may seem convincing that snort is a useless insecure piece of trash to someone who doesn't read between the lines but you must look at 2 very important things.

1) The search being run is "snort vulnerability"

I lol'ed IRL when I saw that someone had tried to use that as a convincing argument.  That shouldn't need any explaining.

2) Whenever there is/was/will be a vulnerability with Snort, due to its purpose and wide use, it is natural for it to gain massive amounts of attention.

If you are looking for more accurate and reputable information pertaining to snort itself being secure, please do not be persuaded by links that are haphazardly distributed like candy to the children on Halloween.  I can almost assure that these links are likely done for the sake of bossing post counts.

I encourage you to access [http://milw0rm.com/search.php](http://milw0rm.com/search.php) (search for snort) and nvd.nist.gov and judge for yourself whether or not you think snort is competent enough to be deployed on your network.

Lastly, my opinion is that it is secure to use from the repositories and more than suitable to be used on a corporate network.  I have multiple snort boxes deployed on both internal and external network components for my employer and it would be very difficult to do my job as well as I do without them.

---

### Post by cprofitt on 2009-07-30
The most secure computer in the world is the one that is disconnected from the network and power... then again that is the worlds most useless computer.

It is not the quantity of the applications installed that makes a computer secure. A knowledgeable user who takes reasonable precautions and avoids doing stupid things is the single largest component to security. While there are differences is OSes a 'stupid user' doing 'stupid things' will always trump technological excellence.

---

### Post by phaceone on 2009-07-31
> **The Tronyx said:**
> 
Lastly, my opinion is that it is secure to use from the repositories and more than suitable to be used on a corporate network.  I have multiple snort boxes deployed on both internal and external network components for my employer and it would be very difficult to do my job as well as I do without them.
ok, thank you very much for taking a little bit of time for this post. as you said before, i don't want to make one server secure, i want to have the possibility to track system malfunctions and hopefully no intrusions. for detecting malfunctions of systems or creating an very detailed communications diagram for this network, an ids seems to be a good solution, too.
...there is just one question remaining: how can i track the process that that scans the neighborhood for snmp servers? it is just an out-of-the box ubuntu installation. is there a tool out there, that can log which process registeres sockets, that are idetified by connection rules or somithing like that?

---

### Post by phaceone on 2009-07-31
ok, thank you very much for taking a little bit of time for this post. as you said before, i don't want to make one server secure, i want to have the possibility to track system malfunctions and hopefully no intrusions. for detecting malfunctions of systems or creating an very detailed communications diagram for this network, an ids seems to be a good solution, too.
...there is just one question remaining: how can i track the process that that scans the neighborhood for snmp servers? it is just an out-of-the box ubuntu installation. is there a tool out there, that can log which process registeres sockets, that are idetified by connection rules or somithing like that?
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7708922") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7708922")

---


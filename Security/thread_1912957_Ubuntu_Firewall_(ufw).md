---
title: "Ubuntu Firewall (ufw)"
date: 2012-01-21
forum: Security
---

### Post by 0011235813 on 2012-01-21
Hello, I recently visited this site; [https://www.grc.com](https://www.grc.com) and used a service called shields up! (I did not use tor for this). I passed all the scans performed (I did all the test there). I then decided to try the same tests with firewall on and off. I used the terminal with 
```
sudo -s
```
```
ufw enable
```
```
ufw default deny
```
```
ufw logging on
```
I then turned it off:
```
ufw disable
```
It did not make **any** difference. My question is, if Ubuntu passed all the firewall tests from this reputable site, without ufw, then what the heck does ufw actually do?!

PS: I read bhodizazens sticky on firewall, but I did not understand what it was actually supposed to do (the firewall).

Can anyone enlighten me on this matter?

---

### Post by BlinkinCat on 2012-01-21
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

A little reading matter - :)

---

### Post by haqking on 2012-01-21
> **0011235813 said:**
> Hello, I recently visited this site; [https://www.grc.com](https://www.grc.com) and used a service called shields up! (I did not use tor for this). I passed all the scans performed (I did all the test there). I then decided to try the same tests with firewall on and off. I used the terminal with 
```
sudo -s
```
```
ufw enable
```
```
ufw default deny
```
```
ufw logging on
```
I then turned it off:
```
ufw disable
```
It did not make **any** difference. My question is, if Ubuntu passed all the firewall tests from this reputable site, without ufw, then what the heck does ufw actually do?!

PS: I read bhodizazens sticky on firewall, but I did not understand what it was actually supposed to do (the firewall).

Can anyone enlighten me on this matter?

First of all i would not put grc into the reputable site category.

Second is all it does it scan for open ports (which are just ports with services listening on them)

By default there arent any, so UFW enabled or not makes no difference from that perspective.

Third UFW is not a firewall per se, it is merely an interface for netfilter/IPTables which is the firewall built into the Linux kernel.

And finally read the link above and configure it to suit your particular environment and services etc.

Enjoy
Cheers

---

### Post by 0011235813 on 2012-01-21
> **haqking said:**
> First of all i would not put grc into the reputable site category.
No? Oh OK, I just couldn't find any other sites that tested the firewall on Linux. Please tell me if you know any more reputable sites.

Second is all it does it scan for open ports (which are just ports with services listening on them)


By default there arent any, so UFW enabled or not makes no difference from that perspective.[/QUOTE]
So then a virus or malicious program would have to make their own connection right? Which would destroy any need for a firewall as the chances of getting infected on Vanilla Ubuntu is slim enough, let alone with modifications.


Third UFW is not a firewall per se, it is merely an interface for netfilter/IPTables which is the firewall built into the Linux kernel.[/QUOTE]
Yes, I know that. I was just referring to ufw as a firewall for convenience and simplicity's sake.

And finally read the link above and configure it to suit your particular environment and services etc.[/QUOTE]
Yes, I've done that. 

Enjoy
Cheers[/QUOTE]
So I guess I'm making a fuss over nothing? Since the only way I can be taken over by a hacker is by getting infected with malware?

---

### Post by Dangertux on 2012-01-21
> **0011235813 said:**
> Hello, I recently visited this site; [https://www.grc.com](https://www.grc.com) and used a service called shields up! (I did not use tor for this). I passed all the scans performed (I did all the test there). I then decided to try the same tests with firewall on and off. I used the terminal with 
```
sudo -s
``````
ufw enable
``````
ufw default deny
``````
ufw logging on
```I then turned it off:
```
ufw disable
```It did not make **any** difference. My question is, if Ubuntu passed all the firewall tests from this reputable site, without ufw, then what the heck does ufw actually do?!

PS: I read bhodizazens sticky on firewall, but I did not understand what it was actually supposed to do (the firewall).

Can anyone enlighten me on this matter?

Weeee! Okay -- check it out, grc and pretty much any other external port scanning site or utility is going to scan interface that is assigned your external IP. Which due to the prevalence of SOHO routers (that ugly little linksys thing on your desk) is probably NOT your Ubuntu machine.

This means two things for you. One it is not accurately portraying your system's firewall (which I believe good ole Steve actually says on his "reputable"\\\site.)

The second is your router is what is "passing" the test.

Also it's UncomplicatedFireWall not Ubuntu FireWall for UFW.

Hope this helps.

EDIT : I just read your post before this...I guess you didn't understand what my sticky post was saying.

You SHOULD configure a firewall.

Also -- modifying Ubuntu (for most people) will make it less secure.

---

### Post by haqking on 2012-01-21
Any site like GRC just scans for listening services, you can do the same thing yourself with nmap or similar.

GRC is not so much disreputable, i just meant they do nothing special that is all, and have made the whole open/closed/stealth port thing a bit hyped over what they truly mean.

As for only way being malware, far from it.

Linux is as susceptible to compromise as any other OS, regardless of the believe what is on the box crew who spout the whole Linux is secure thing.

System security is down to the user and or admin.  Linux and Windows are on par when it comes to security overall, though most malware is Windows based but malware is not the be all and end all of system security, infact far from it, malware and specifically viruses have more payloads which are nuisance based and not based around system compromise.

You can be compromised through thousands of ways which are not all OS specific and often browser based or application based vulnerabilities or exploits which abstract from the OS security itself.

have good browsing habits, use common sense, use tools such as tight inbound and outbound firewall rules, apparmor, SELinux, NOScript etc.

End user systems are a fine balance of ease of use, functionality and security, as soon as you move towards on you leave the others further behind, which is why Windows/Mac/Linux all have a roughly equal security footing overall, the rest is upto you.

read the Basic Security wiki for a good primer. 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Enjoy

edit. Ninja'd by DT

---

### Post by 0011235813 on 2012-01-21
> **Dangertux said:**
> Weeee! Okay -- check it out, grc and pretty much any other external port scanning site or utility is going to scan interface that is assigned your external IP. Which due to the prevalence of SOHO routers (that ugly little linksys thing on your desk) is probably NOT your Ubuntu machine.
OK so it is scanning my router... But then, wouldn't that mean that a hacker who wants to attack my machine would smack into the router's firewall? Thus making system firewall utterly pointless? (Assuming Virgin Media firewall is any good?)

This means two things for you. One it is not accurately portraying your system's firewall (which I believe good ole Steve actually says on his "reputable"\\\site.)

The second is your router is what is "passing" the test.[/QUOTE]
OK... So VM's firewall is good then?

Also it's UncomplicatedFireWall not Ubuntu FireWall for UFW.

Hope this helps.

EDIT : I just read your post before this...I guess you didn't understand what my sticky post was saying.

You SHOULD configure a firewall.[/QUOTE]
I have, I'm just wondering what on Earth it's actually doing- from what I can gain, a firewall in Ubuntu is only good if my machine has already been compromised. 

Also -- modifying Ubuntu (for most people) will make it less secure.[/QUOTE] Changing sudo timeout to 0 minutes is bad? What about routing connections through DNS? Using a more secure browser (Opera)? Disabling JavaScript? Deleting cookies on startup? Using proxies for browser and mail client? Encrypting confidential directories? Tell me if I'm doing anything wrong here...

---

### Post by 0011235813 on 2012-01-21
> **haqking said:**
> Any site like GRC just scans for listening services, you can do the same thing yourself with nmap or similar.

GRC is not so much disreputable, i just meant they do nothing special that is all, and have made the whole open/closed/stealth port thing a bit hyped over what they truly mean.>  They do nothing special? OK, I never *asked* for anything *special* as such, only something that works... From what I can gain, this service is a bit of a false friend?

As for only way being malware, far from it. Can you elaborate on that please?

Linux is as susceptible to compromise as any other OS, regardless of the believe what is on the box crew who spout the whole Linux is secure thing. Linux is secure... For many reasons.

System security is down to the user and or admin.  Linux and Windows are on par when it comes to security overall, though most malware is Windows based but malware is not the be all and end all of system security, infact far from it, malware and specifically viruses have more payloads which are nuisance based and not based around system compromise.[/QUOTE] I'll respectfully disagree. Not to act like a troll, but I'm pretty sure Linux destroys Windows. After years and years of using Windows, I can pretty much say that it's security is... Pretty darn awful. It's attacked by everyone, updates are slow and infrequent, it makes you superuser, it lacks many built in security features, etc. etc.

You can be compromised through thousands of ways which are not all OS specific and often browser based or application based vulnerabilities or exploits which abstract from the OS security itself.

have good browsing habits, use common sense, use tools such as tight inbound and outbound firewall rules, apparmor, SELinux, NOScript etc.[/QUOTE] I have apparmor and profiles as well, and JavaScript is disabled in Opera (except my whitelists of course).   

End user systems are a fine balance of ease of use, functionality and security, as soon as you move towards on you leave the others further behind, which is why Windows/Mac/Linux all have a roughly equal security footing overall, the rest is upto you.

read the Basic Security wiki for a good primer. 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Enjoy

edit. Ninja'd by DT[/QUOTE]

---

### Post by haqking on 2012-01-21
> **0011235813 said:**
> Linux is secure... For many reasons.

 **I'll respectfully disagree. Not to act like a troll, but I'm pretty sure Linux destroys Windows. After years and years of using Windows, I can pretty much say that it's security is... Pretty darn awful. It's attacked by everyone, updates are slow and infrequent, it makes you superuser, it lacks many built in security features, etc. etc.**
I have apparmor and profiles as well, and JavaScript is disabled in Opera (except my whitelists of course).   


You can disagree all you like, respectfully you are the one asking the basic firewall questions ;-)

educate then you can debate.

And when responding try to make your posts a little clearer as you are not quite using the quote feature correctly and makes it difficult to read

peace

---

### Post by 0011235813 on 2012-01-21
> **haqking said:**
> You can disagree all you like, respectfully you are the one asking the basic firewall questions ;-)

educate then you can debate.

And when responding try to make your posts a little clearer as you are not quite using the quote feature correctly and makes it difficult to read

peace

1. I'm the one asking a basic firewall question, your problem? I'm **trying** to educate, no need to be rude. Not everyone is an avid computer geek, and I wouldn't insult you if you were asking a *basic* question about octaves, or nebula's, or whatever.

2. How am I supposed to use the quote feature? I've been to other forums, and "[/quote]" seems to work fine there...

---

### Post by Dangertux on 2012-01-21
Trying to read your post is difficult, you know there is a multi-quote function right? Anyways, I think the point is that neither Linux nor Windows are inherently secure, the fact that you may or may not have a proper knowledge of how to apply the proper security controls in a given operating system is irellevant to its overall security posture. So nothing really "destroys" anything else. 

You are taking proactive measures by utilizing Mandatory Access Controls (Apparmor+Profiles). It could be argued that Opera is not necessarily more secure than Firefox or Chrome but that is a whole different debate.

As far as Virgin Mobile's firewall versus iptables/netfilter. I would be willing to be they are essentially the same. As you said you read my other post, though I don't believe you understood it. I explained NAT routing, why it's not the end all be all solution and that most NAT routers use netfiler (some use PF). 

It seems like you want to feel good about your OS, and that's fine. However, if you want a realistic answer you've gotten it, several times.

Hope this helps.

ps : 0+0 != 1

---

### Post by haqking on 2012-01-21
> **0011235813 said:**
> 1. I'm the one asking a basic firewall question, your problem? I'm **trying** to educate, no need to be rude. Not everyone is an avid computer geek, and I wouldn't insult you if you were asking a *basic* question about octaves, or nebula's, or whatever.

2. How am I supposed to use the quote feature? I've been to other forums, and "

I wasnt being rude, i said respectfully.

You were disagreeing with me on a subject which by your own admission you have little knowledge of so therefore i was pointing you to educate a little more before disagreeing with someone on a subject.

I applaud you educating yourself and i push everyone to do so so congrats.

the basic security wiki link i posted above is a good starting point for you.

And you used the quote feature fine this time round, if you look at your posts above they were a little hard to read that was all i meant.

no offence was meant, peace

---

### Post by 0011235813 on 2012-01-21
> **Dangertux said:**
> Trying to read your post is difficult, you know there is a multi-quote function right? Anyways, I think the point is that neither Linux nor Windows are inherently secure, the fact that you may or may not have a proper knowledge of how to apply the proper security controls in a given operating system is irellevant to its overall security posture. So nothing really "destroys" anything else. 
Sorry, missed the multiquote thing. :(

You are taking proactive measures by utilizing Mandatory Access Controls (Apparmor+Profiles). It could be argued that Opera is not necessarily more secure than Firefox or Chrome but that is a whole different debate.[/QUOTE] I'm curious as to how secure Opera is... I've heard it's the most secure,because of  obscurity, 256-bit encryption support etc. 

As far as Virgin Mobile's firewall versus iptables/netfilter. I would be willing to be they are essentially the same. As you said you read my other post, though I don't believe you understood it. I explained NAT routing, why it's not the end all be all solution and that most NAT routers use netfiler (some use PF). 

It seems like you want to feel good about your OS, and that's fine. However, if you want a realistic answer you've gotten it, several times.

Hope this helps.

ps : 0+0 != 1[/QUOTE]

---

### Post by 0011235813 on 2012-01-21
> **haqking said:**
> I wasnt being rude, i said respectfully.

You were disagreeing with me on a subject which by your own admission you have little knowledge of so therefore i was pointing you to educate a little more before disagreeing with someone on a subject.

I applaud you educating yourself and i push everyone to do so so congrats.

the basic security wiki link i posted above is a good starting point for you.

And you used the quote feature fine this time round, if you look at your posts above they were a little hard to read that was all i meant.

no offence was meant, peace
I openly admit I have little knowledge on Linux firewalls, but that's only natural considering I've only used Linux for a couple of months and Windows for years. And by the way, I **do** know a lot about computer hardware :) Start a chat about multi-agent systems if you don't believe me;)

But back on topic, am I to understand that the conducted test was invalid? Is there any other type of scan that could identify the security of my firewall? Also, why does my firewall turn itself off every time I log off?

---

### Post by Dangertux on 2012-01-21
Security through obscurity is a load of garbage. The only person it may be obscure to is the person using it. Someone targeting it will have taken the time to research their chosen victim.

As far as 256 bit encryption for SSL/TLS that requires the site you're connecting to support that as well (most don't).

Also Firefox has supported 256 bit SSL since 2010.

Also for quoting you're missing the leading tag

EDIT : we're a little out of sync here. 

It's not necessarily an invalid test, but it wasn't testing what you thought it was.

Also -- you can use nmap like haqking said to scan machines internal to your network. As for your firewall turning off no it doesn't if configured properly.

---

### Post by haqking on 2012-01-21
> **0011235813 said:**
> I openly admit I have little knowledge on Linux firewalls, but that's only natural considering I've only used Linux for a couple of months and Windows for years. And by the way, I **do** know a lot about computer hardware :) Start a chat about multi-agent systems if you don't believe me;)

But back on topic, am I to understand that the conducted test was invalid? Is there any other type of scan that could identify the security of my firewall? Also, why does my firewall turn itself off every time I log off?

a firewall is the same thing in windows/mac or linux, they do the same thing and the principles are the same.

The test was merely a scan of your public IP as already said, and you could do the same with nmap or similar.

it merely looks at your public IP, most likely your router and sees if any services are listening on it and thats it, and certainly doesnt mean your system is not able to be compromised, it means there is no service listening on a port or appears not to be and thats it.

As for turn off ? if you are logged off how do you know ?

You mean you have to renable UFW when logging back on ? or are you using GUFW which has some bug in it about showing it as off.

As for the security of your firewall, do you have services running which you are concerned about ? if so configure them with the appropriate rules in the links provided as a tutorial, if you dont or arent then there is nothing for it to protect apart from the basic stuff which you again you can configure from the links provided.

A firewall is still not the be all and end all of system security though to be clear, with tight inbound and outboudn rules does not mean someone cant get in, it is a broad subject with no clear answer as online nothing is 100% secure

Cheers

---

### Post by 0011235813 on 2012-01-21
> **Dangertux said:**
> Security through obscurity is a load of garbage. The only person it may be obscure to is the person using it. Someone targeting it will have taken the time to research their chosen victim.

As far as 256 bit encryption for SSL/TLS that requires the site you're connecting to support that as well (most don't).

Also Firefox has supported 256 bit SSL since 2010.

Also for quoting you're missing the leading tag

EDIT : we're a little out of sync here. 

It's not necessarily an invalid test, but it wasn't testing what you thought it was.

Also -- you can use nmap like haqking said to scan machines internal to your network. As for your firewall turning off no it doesn't if configured properly.
I know about specific targeting, but quite simply, I don't have any enemies, so I'm not particularly worried about that. I do think obscurity is a good security measure, even if it's not as a result of good programming. McAfee has a database of 71000 (71*10^3) Windows viruses in their database, it's safe to say there are even more viruses out there in the wild. How many does Linux have? I couldn't find any definitive statistics on this, but they range from a few hundred to a few thousand.

Am I to guess.... 
```
sudo apt-get install nmap
```
?
I installed nmap, do I have to look for the log? How does this program work?

---

### Post by 0011235813 on 2012-01-21
> **haqking said:**
> a firewall is the same thing in windows/mac or linux, they do the same thing and the principles are the same.

The test was merely a scan of your public IP as already said, and you could do the same with nmap or similar.

it merely looks at your public IP, most likely your router and sees if any services are listening on it and thats it, and certainly doesnt mean your system is not able to be compromised, it means there is no service listening on a port or appears not to be and thats it.

As for turn off ? if you are logged off how do you know ?

You mean you have to renable UFW when logging back on ? or are you using GUFW which has some bug in it about showing it as off.

Cheers
Yes, I have to re-enable it every time. Any reason why? Is this the default setting? Or a bug?

---

### Post by haqking on 2012-01-21
> **0011235813 said:**
> Yes, I have to re-enable it every time. Any reason why? Is this the default setting? Or a bug?

are you talking about UFW, i know that is what you said in OP but sometimes people refer to GUFW which is a GUI for UFW and has a bug which shows it as off i believe (i dont use it so not 100% on that but know there is a bug)

if it is UFW then when you log on and type ```
sudo ufw status
```

it says it not active ?

though looking back at your original post, your last command turned off the firewall, ya know that right ?

---

### Post by Dangertux on 2012-01-21
> **0011235813 said:**
> Yes, I have to re-enable it every time. Any reason why? Is this the default setting? Or a bug?

Something is wrong because

```

sudo ufw enable

```

Will also enable the upstart job for UFW to start at boot time.

You can confirm this with

```

sudo ufw status

```

Anyway, I'm not sure that your information about viruses is correct (since some of it is an assumption), but viruses are only a small percentage of threats that actually affect you.

As far as security through obscurity, it's a whole different debate and I'm not getting into it because it's irellevant as it's opinion and no tangible argument can be made for or against obscurity.

Hope this helps.

---

### Post by 0011235813 on 2012-01-21
> **Dangertux said:**
> Something is wrong because

```

sudo ufw enable

```

Will also enable the upstart job for UFW to start at boot time.

You can confirm this with

```

sudo ufw status

```

Anyway, I'm not sure that your information about viruses is correct (since some of it is an assumption), but viruses are only a small percentage of threats that actually affect you.

As far as security through obscurity, it's a whole different debate and I'm not getting into it because it's irellevant as it's opinion and no tangible argument can be made for or against obscurity.

Hope this helps.
Yes, whenever I suspend, log out or shut down, I use 
```
sudo ufw status
``` 
and I get an "inactive" message, I have to enable it every time.

---

### Post by Dangertux on 2012-01-21
> **0011235813 said:**
> Yes, whenever I suspend, log out or shut down, I use 
```
sudo ufw status
```and I get an "inactive" message, I have to enable it every time.

You should file a bug report.

---

### Post by 0011235813 on 2012-01-21
> **Dangertux said:**
> You should file a bug report.

Where do the bug reports get filed? Sorry for silly question :)

---

### Post by collisionystm on 2012-01-21
> **0011235813 said:**
> Hello, I recently visited this site; [https://www.grc.com](https://www.grc.com) and used a service called shields up! (I did not use tor for this). I passed all the scans performed (I did all the test there). I then decided to try the same tests with firewall on and off. I used the terminal with 
```
sudo -s
``````
ufw enable
``````
ufw default deny
``````
ufw logging on
```I then turned it off:
```
ufw disable
```It did not make **any** difference. My question is, if Ubuntu passed all the firewall tests from this reputable site, without ufw, then what the heck does ufw actually do?!

PS: I read bhodizazens sticky on firewall, but I did not understand what it was actually supposed to do (the firewall).

Can anyone enlighten me on this matter?


[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000060]Your system has achieved a **perfect** "TruStealth" rating. **Not a single packet**  — solicited or otherwise — was received from your system as a result of  our security probing tests. Your system ignored and refused to reply to  repeated Pings (ICMP Echo Requests). From the standpoint of the passing  probes of any hacker, this machine does not exist on the Internet. Some  questionable personal security systems expose their users by attempting  to "counter-probe the prober", thus revealing themselves. But your  system wisely remained silent in every way. Very nice.[/COLOR][/SIZE][/FONT]

:D

---

### Post by haqking on 2012-01-21
> **collisionystm said:**
> [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000060]Your system has achieved a **perfect** "TruStealth" rating. **Not a single packet**  &#8212; solicited or otherwise &#8212; was received from your system as a result of  our security probing tests. Your system ignored and refused to reply to  repeated Pings (ICMP Echo Requests). From the standpoint of the passing  probes of any hacker, this machine does not exist on the Internet. Some  questionable personal security systems expose their users by attempting  to "counter-probe the prober", thus revealing themselves. But your  system wisely remained silent in every way. Very nice.[/COLOR][/SIZE][/FONT]

:D

I dont know why it always says that, i think it is supposed to say:

> We did nothing special towards your network or computer and discovered little or nothing useful, what we did see was likely your external IP and your router so this gives little or no indication to the security of your OS or machine connected to the internet.

From the standpoint of the hacker he knows how useless our service is and so is joyful at the now unfounded confidence you have in your online security.

The fact you used our service means you know little or nothing about system security in the first place so we can say what we like and you will believe us.

Thanks for using our service, frankly we are surprised we dont charge you.



;-)

Peace

---

### Post by collisionystm on 2012-01-21
> **haqking said:**
> I dont know why it always says that, i think it is supposed to say:

We did nothing special towards your network or computer and discovered  little or nothing useful, what we did see was likely your external IP  and your router so this gives little or no indication to the security of  your OS or machine connected to the internet.

From the standpoint of the hacker he knows how useless our service is  and so is joyful at the now unfounded confidence you have in your online  security.

The fact you used our service means you know little or nothing about  system security in the first place so we can say what we like and you  will believe us.

Thanks for using our service, frankly we are surprised we dont charge you. 			 		


;-)

Peace


lol... whattt??? Are you insinuating I am not safe? :o

My god. I really thought my kmart netgear router was a god damn fortress. *tear*

---

### Post by haqking on 2012-01-22
> **collisionystm said:**
> lol... whattt??? Are you insinuating I am not safe? :o

My god. I really thought my kmart netgear router was a god damn fortress. *tear*

nah you are ok, if it is from Kmart it is bulletproof ;-)

---

### Post by Dangertux on 2012-01-22
Clearly you guys haven't been to the kmart near me, most things there NEED to be bulletproof (otherwise they don't last long) ;-)

Also OP in the last command in your first post you are disabling ufw, are you doing that set of commands everytime you use it?

```

sudo ufw disable

```

Will disable ufw and stop it from running at boot time. Where...

```

sudo ufw enable

```

Will have the opposite effect.

---

### Post by 0011235813 on 2012-01-22
> **Dangertux said:**
> Clearly you guys haven't been to the kmart near me, most things there NEED to be bulletproof (otherwise they don't last long) ;-)

Also OP in the last command in your first post you are disabling ufw, are you doing that set of commands everytime you use it?

```

sudo ufw disable

```

Will disable ufw and stop it from running at boot time. Where...

```

sudo ufw enable

```

Will have the opposite effect.

Uh no, I only use 
```
sudo ufw disable
``` 
in that particular test. Otherwise, I don't use it. I'm serious; every time I log out, suspend or shut down, the firewall turns off.

PS: You guy's have a bad sense of humour. I don't even know what Kmart is, some sort of packet manager for KDE?

---

### Post by Ms. Daisy on 2012-01-22
> **0011235813 said:**
> 
PS: You guy's have a bad sense of humour. I don't even know what Kmart is, some sort of packet manager for KDE?
I hope you were kidding.  If not, you don't have Google?

---

### Post by 0011235813 on 2012-01-22
> **Ms. Daisy said:**
> I hope you were kidding.  If not, you don't have Google?

Of course I was kidding. I may not live in the US, but that doesn't mean I'm a bloody fool.

---

### Post by haqking on 2012-01-22
> **0011235813 said:**
> Uh no, I only use 
```
sudo ufw disable
``` 
in that particular test. Otherwise, I don't use it. I'm serious; every time I log out, suspend or shut down, the firewall turns off.

PS: You guy's have a bad sense of humour. I don't even know what Kmart is, some sort of packet manager for KDE?

Do you have firestarter installed by any chance ? or any other firewall interface ?

I know firestarter conflicts with UFW and it wont be active upon a reboot ?

---

### Post by 0011235813 on 2012-01-22
> **haqking said:**
> Do you have firestarter installed by any chance ? or any other firewall interface ?

I know firestarter conflicts with UFW and it wont be active upon a reboot ?

I **do** have firestarter installed, I should have known, a program that hasn't been touched since 2005 probably isn't ideal for security. time to use:
```
sudo apt-get autoremove firestarter
```
:)

---

### Post by haqking on 2012-01-22
> **0011235813 said:**
> I **do** have firestarter installed, I should have known, a program that hasn't been touched since 2005 probably isn't ideal for security. time to use:
```
sudo apt-get autoremove firestarter
```
:)

Indeed, i bet that solves the issue, it is known bug with firestarter installed.

firestarter is out of date and buggy for sure, and causes conflicts with UFW.

If you get it solved, post back and mark the thread as solved.

Cheers

---

### Post by 0011235813 on 2012-01-22
> **haqking said:**
> Indeed, i bet that solves the issue, it is known bug with firestarter installed.

firestarter is out of date and buggy for sure, and causes conflicts with UFW.

If you get it solved, post back and mark the thread as solved.

Cheers

Yes, the problem is now solved. I guess I have to use the edit function? Or is there a different way?

---

### Post by haqking on 2012-01-22
> **0011235813 said:**
> Yes, the problem is now solved. I guess I have to use the edit function? Or is there a different way?

cool glad you got it sorted.

use the thread tools menu towards the top and choose solved.

Cheers

---


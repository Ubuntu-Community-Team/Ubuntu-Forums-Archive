---
title: "fav. internet security?"
date: 2011-10-18
forum: Security
---

### Post by Matrix01 on 2011-10-18
which one is your favorite internet security software?

---

### Post by crazy bird on 2011-10-18
> **Matrix01 said:**
> which one is your favorite internet security software?
 
For what? Virusses? Trojans? Spyware? Malware? Never used any internet security software on my Ubuntu systems!
 
Ubuntu isn't in any way like Windows which is like an open barrel where you can dump all your virusses and trojans and malware and spyware in. Basicly, Linux is much safer then Windows due to the different kernel architecture and better rigth managementsystem.

---

### Post by Matrix01 on 2011-10-18
For all of above.
I am used to Windows, and new to ubuntu, just installed Natty Sunday.

Good to know that
Thank u.

---

### Post by Leaf on 2011-10-18
Clamav is a unix virus scanner, it's in the software center.

---

### Post by crazy bird on 2011-10-18
> **Leaf said:**
> Clamav is a unix virus scanner, it's in the software center.
 
Like i said, you really don't need any kind of security: no firewall, no anti-virus, no anti-trojans/spyware/malware. Installing these kind of tools is like installing an airbag in your car which already has been fully equipped with airbags. 
 
Anti-virus is only needed when you exchange files with Windows users. And even so, it is the responsibility of the Windows user to have max. protection against virusses/trojans/spyware/malware . It is not the responsibility of Linux users to protect Windows systems of Windows users. If you want anti-virus and you still use Windows formatted (external) drives, then clamav is good enough. It is available in the repository and it even has a graphical interface.
 
But seriously, you really don't need anti-virus! I know you're used to it having such protection as a former Windows user, but for Linux it is not required.

---

### Post by CharlesA on 2011-10-18
My favorite security software is my brain. :)

Just need to install a USB port somehow..

---

### Post by crazy bird on 2011-10-18
> **CharlesA said:**
> My favorite security software is my brain. :)

Just need to install a USB port somehow..

:lolflag:

I see what your point is!
It's mostly the stupidity of people which is a danger for their own system. Accepting stuff without checking, clicking links without thinking, doing things whit harms their system. Luckily most of that kind stupidity is what Linux protected against with a better rigth management system.

---

### Post by Dangertux on 2011-10-18
I'm not entirely sure I would say you don't need a firewall (at the very least that's not inline with anything close to best practices)

People who say that don't understand how a system compromise actually occurs. I would personally suggest a firewall with both restrictive inbound and outbound policies. That being said, I wouldn't bother with AV or Anti-Malware on Linux, they're mostly all garbage anyway.

Hope that helps

---

### Post by bodhi.zazen on 2011-10-18
> **Matrix01 said:**
> For all of above.
I am used to Windows, and new to ubuntu, just installed Natty Sunday.

Good to know that
Thank u.

Most of the things you were taught about Windows security, or at least the things you are asking about, do not apply to Linux.

Start with the security sticky.

From there it sort of depends on your user case. Assuming you are a Desktop user behind a firewall (router) I would suggest you learn apparmor and use NoScript.

From there you need to understand, there are many security tools at your disposal, but they all have a bit of a learning curve.

Personally I like snort and ossec, but I do not use them on a desktop.

---

### Post by crazy bird on 2011-10-19
> **Dangertux said:**
> I'm not entirely sure I would say you don't need a firewall 
 
In my understanding a firewall is not needed since Linux does not open ports which you don't need. In it's basic settings, Linux already set up a basic defence by doing this. Install Ufw and you see what i mean.

---

### Post by dusanyu on 2011-10-19
A simple NAT firewall (this is what hone routers use) and common sense is all you need

Clam AV can be useful as one or two viruses do exist for Linux but if you only install software from signed sources they wont hit you

---

### Post by satanselbow on 2011-10-19
> **CharlesA said:**
> 

Just need to install a USB port somehow..

Hey I did that last weekend! 

... oh no... wait a mo... that was on the scooter... sorry...

There gotta be a schematic somewhere online surely!

---

### Post by CharlesA on 2011-10-19
> **crazy bird said:**
> In my understanding a firewall is not needed since Linux does not open ports which you don't need. In it's basic settings, Linux already set up a basic defence by doing this. Install Ufw and you see what i mean.

Different distros have different services installed by default. Some of them might need to be firewalled. If you are behind a router, that shouldn't be a big deal tho.

> **satanselbow said:**
> Hey I did that last weekend! 

... oh no... wait a mo... that was on the scooter... sorry...

There gotta be a schematic somewhere online surely!

Lol. Reminds me of [this]("http://xkcd.com/644/").

---

### Post by n0zqh1 on 2011-10-19
I use clamTK to scan for viruses when I want to move something to windows from linux

---

### Post by Dangertux on 2011-10-21
> **crazy bird said:**
> In my understanding a firewall is not needed since Linux does not open ports which you don't need. In it's basic settings, Linux already set up a basic defence by doing this. Install Ufw and you see what i mean.

Ok -- well I will have to disagree with you on that.

You were correct when you said it sets up a basic defense, and I mean extremely basic. Neither a NAT router nor a default U FW configuration will protect you against MOST threats the average home user will encounter.

Take the following situation for example. User unintentionally browses a malicious website with an unconfined browser such as Firefox, now this website loads a javascript that exploits a vulnerability in Firefox (there have been plenty take your pick) if you want to make the noscript argument even though the debate was about firewalls change browse to malicious site to downloads a package from a malicious or cracked ppa. 

In either case, exploit code runs, injects payload into memory. Payload is a reverse shell , as opposed to a typical bind shell. Neither a typically configured firewall nor a NAT router will protect you against this because it is YOUR machine that ultimately solicited the connection.

If you want to understand this more in depth I wrote about it a while back here : [http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/](http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/)

In any case, Linux is nice but don't let it lull you into a false sense of security.

Hope that helps :-)

---

### Post by Matrix01 on 2011-10-21
will u tell me whatwhat ufw is?

> **crazy bird said:**
> In my understanding a firewall is not needed since Linux does not open ports which you don't need. In it's basic settings, Linux already set up a basic defence by doing this. Install Ufw and you see what i mean.

---

### Post by CharlesA on 2011-10-22
> **Matrix01 said:**
> will u tell me whatwhat ufw is?
[Uncomplicated FireWall]("https://help.ubuntu.com/community/UFW").

---

### Post by bodhi.zazen on 2011-10-22
> **CharlesA said:**
> If you are behind a router, that shouldn't be a big deal tho.

You just have to take care that UPnP is disabled. Otherwise your router may be one big security hole, especially with VNC.

---

### Post by CharlesA on 2011-10-22
> **bodhi.zazen said:**
> You just have to take care that UPnP is disabled. Otherwise your router may be one big security hole, especially with VNC.
Yep, that's true.

I totally forgot about uPNP, but that's probably cuz I run with it disabled.

---

### Post by Dangertux on 2011-10-22
Ok I would love to agree, but I really can't. 

How is it you can rely so much on NAT routing to protect you? If you REALLY think that sitting behind a NAT router makes it so a connection can't be made, how exactly is it you're browsing this site right now? 

Did your router magically forward whatever oddball unregistered port your browser decided to open a connection to this site with? 

[http://en.wikipedia.org/wiki/Reverse_connection](http://en.wikipedia.org/wiki/Reverse_connection)

Anyway, +1 on disabling UPnP.

---

### Post by Matrix01 on 2011-10-23
what is UPnP?

---

### Post by Dangertux on 2011-10-23
> **Matrix01 said:**
> what is UPnP?

Universal plug and play. It's basically a method by which a router can receive information to selectively route packets based on an application or another network device.

---

### Post by lisati on 2011-10-23
IMO one of the biggest threats to security is an apparent scarcity of good sense, which leaves a system open to PEBKAC and Eye-Dee-Ten-Tee errors.

A simple but potentially frustrating technique is leaving ALL network connections disconnected and/or disabled.

---

### Post by bodhi.zazen on 2011-10-23
> **Dangertux said:**
> Ok I would love to agree, but I really can't. 

How is it you can rely so much on NAT routing to protect you? If you REALLY think that sitting behind a NAT router makes it so a connection can't be made, how exactly is it you're browsing this site right now? 

Did your router magically forward whatever oddball unregistered port your browser decided to open a connection to this site with? 

[http://en.wikipedia.org/wiki/Reverse_connection](http://en.wikipedia.org/wiki/Reverse_connection)

Anyway, +1 on disabling UPnP.

I agree, a firewall is a tool, and IMO it is of limited value for most desktop users.

The #1 use I see on these forums would be to keep you VNC server behind a firewall (as VNC is still the #1 crack it is somewhat relevant).

But a firewall does nothing for firefox exploits.

---

### Post by Matrix01 on 2011-10-23
What are NAT routing and IMO?

---

### Post by Dangertux on 2011-10-23
Network Address Translation or (Network allocation table) and in my opinion.

---

### Post by Ms. Daisy on 2011-10-24
I just read the security sticky.  It says > By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration. That seems to agree mostly with crazy bird. The way I'm reading that is if you don't have a server installed, then you really don't need a firewall.  But you've got one anyway (iptables) that you could enable if you're of the paranoid flavor (like me).

But that's just a firewall.  As Dangertux and bodhi.zazen alluded to, there are a lot of vectors for attack. It doesn't matter what OS you're running when it comes social engineering & the like. 

If a user has an all-in-one virus/firewall/spyware/etc. program, maybe they become complacent and too trusting of the software. Just a thought, but maybe in some situations a user will act more intelligently without that safety net.

And come on, a wireless adapter is way more versatile than USB in the brain, guys.

---

### Post by Dangertux on 2011-10-24
> **Ms. Daisy said:**
> 
But that's just a firewall.  As Dangertux and bodhi.zazen alluded to, there are a lot of vectors for attack. It doesn't matter what OS you're running when it comes social engineering & the like. 

If a user has an all-in-one virus/firewall/spyware/etc. program, maybe they become complacent and too trusting of the software. Just a thought, but maybe in some situations a user will act more intelligently without that safety net.

And come on, a wireless adapter is way more versatile than USB in the brain, guys.

I am inclined to feel somewhat misquoted on this, save that I wasn't actually quoted. This does not entirely encapsulate what I was trying to say. Warning ahead of time, this topic has gone beyond frustration for me, so if I sound terse I apologize in advance.

There are three giant misconceptions that I have issue with.

1 -- The open ports argument. This would be a fantastic argument if you were talking about a production server.  A production system will sit there, and fulfill its purpose. It will be maintained by (hopefully) competent system administrators. If all is as it should be it will have a very limited set of services that are well secured, confined in some way shape or form (apparmor, dac, chroot, a combination of all 3, or whatever your poison may be), and updated with the latest security patches. In this case a firewall might not be necessary.

That being said, this case has absolutely NOTHING to do with the average desktop user. The average desktop use case will likely be running no services, with the exception that new, budding linux enthusiasts tend to move far too rapidly (in my opinion) toward remotely administering their systems. For argument's sake though, we will say there are no services running, as this is the default.  However, the one thing desktop users all have in common is quite simply this. They love to utilize rich, exciting media. Whether it be a video in VLC , some music in Banshee, a paper they are reading in evince, or a website in Firefox. These are all potential security threats, if created maliciously these avenues ALL can lead to system compromise.  In the event something along those lines were to occur, running without a firewall of any kind, would leave you entirely unprotected. Continuing that thought, EVEN IF you ran a firewall and NAT router (firewall is assumed to be in default UFW configuration) you would STILL not be adequately protected to insure a complete compromise did not occur.

As I've eluded to earlier, inbound firewall rules will not and can not affect a reverse connection. Which in terms of a compromised application is a very likely end. Strong, outbound rules are also needed, and even then they are not a guarantee to avoid compromise. In addition to that paying attention to things like Apparmor and file permissions are STILL very important to minimize the impact of a potential compromise.

The above points are taking into account only a SMALL portion of attack vectors available to a potential attacker. 

2 -- No...utilizing the DROP function of iptables, does NOT make you invisible to an attacker. In fact it doesn't make your system look any different than if it had REJECT rules or no firewall and no services. There is no such THING as a stealthed port, Steve Gibson did a wonderful job selling millions of copies of Zone Alarm, but he pretty much misinformed the world.

3 -- Linux is NOT some amazingly indestructible tank, neither is Ubuntu. They are both relatively easy to compromise and are essentially on par with Windows 7 in terms of security. In some ways Windows 7 is ahead of the curve, for instance local escalation on a Windows desktop is MUCH more difficult than Linux. However in other ways it is behind the curve, for instance injecting code into a DLL to bypass ASLR is MUCH easier on Windows 7 than it is to bypass ASLR on Linux.

In the end, nobody can take any steps toward a more secure operating system for you. IF you are truly serious, paranoid, or enthusiastic, only you can educate yourself.

---

### Post by CharlesA on 2011-10-24
I don't feel like quoting the whole post, but well said, dangertux.

I don't really have anything else to add to that outside of me switching from using DROP to using REJECT for my firewall rules - makes troubleshooting a whole heck of a lot easier.

---

### Post by bodhi.zazen on 2011-10-24
dangertux - I did not want to quote the entire post either.

For all of those reasons I encourage people to do the following.

If it makes you feel better, configure your firewall.

If you want to increase your security, learn apparmor or selinux (or similar) and learn to read the logs. You can not spot unusual activity if you do not know what is normal.

All to often we see people posting output of various tools (rkhunter comes to mind) asking us to tell them if their system is "OK". How should we know ?

My point is that if you are a paranoid penguin, you need to go way beyond a firewall.

> To [s]infinity[/s] iptables ... and beyond

~ Buzz Lightyear

---

### Post by lisati on 2011-10-24
> **Dangertux said:**
> 
In the end, nobody can take any steps toward a more secure operating system for you. IF you are truly serious, paranoid, or enthusiastic, only you can educate yourself.
I'm inclined to agree here, that educating yourself should be a high priority.

---

### Post by Ms. Daisy on 2011-10-24
Dangertux, you quoted me in your post, so I assume you were directing most of that at me. I think we actually **agree**.  Clearly I failed to make my point.   
 

 > **Dangertux said:**
> 2 -- No...utilizing the DROP function of iptables, does NOT make you invisible to an attacker. In fact it doesn't make your system look any different than if it had REJECT rules or no firewall and no services.Did I misunderstand the sticky?  Iptables is NOT a firewall that's already installed with Ubuntu but is disabled by default? So what ARE the preferred firewalls for Ubuntu?
 

 > **Dangertux said:**
> The above points are taking into account only a SMALL portion of attack vectors available to a potential attacker.  That was precisely my point.  There are so many ways for your system to be compromised.  Even with the very best firewall on the planet (if such a thing even exists), you're still vulnerable to a hundred other things regardless of your OS.

> **Dangertux said:**
> 3 -- Linux is NOT some amazingly indestructible tank, neither is Ubuntu. They are both relatively easy to compromise and are essentially on par with Windows 7 in terms of security... running without a firewall of any kind, would leave you entirely unprotected.  Not my point at all.  Here it is in more precise words.  I was a clueless Windows user 6 months ago.  I paid for the popular virus/firewall software and installed it.  And that's where it ended.  I put all my faith in the software.  I didn't understand the hundreds of ways my computer could be hijacked.  I think I was like the majority of Windows users in that I didn't want to be bothered with the details.  I just needed it to work so I could get my job done.  And predictably my system was breached.  **So what I'm proposing is simply that a user doesn't take a blind faith approach towards security software, and they certainly shouldn't take a blind faith approach to an operating system.  I'm saying that this blind faith MAY be worse than having no perceived safety net and being forced to pay attention.**    
 

 > **Dangertux said:**
> In the end, nobody can take any steps toward a more secure operating system for you. If you are truly serious, paranoid, or enthusiastic, only you can educate yourself. 100% agree.  In fact I'm spending nearly every waking moment doing so in spite of the  steep learning curve for Linux & security in general.  The volume of literature I need to read is daunting.  You spoke about inbound & outbound rules, Apparmor and file permissions.  I have no idea how to implement those. Now that you mentioned them (thank you) I'll certainly be researching them.

---

### Post by Dangertux on 2011-10-24
> **Ms. Daisy said:**
> Dangertux, you quoted me in your post, so I assume you were directing most of that at me. I think we actually **agree**.  Clearly I failed to make my point.   
 

 Did I misunderstand the sticky?  Iptables is NOT a firewall that's already installed with Ubuntu but is disabled by default? So what ARE the preferred firewalls for Ubuntu?
 

  That was precisely my point.  There are so many ways for your system to be compromised.  Even with the very best firewall on the planet (if such a thing even exists), you're still vulnerable to a hundred other things regardless of your OS.

Not my point at all.  Here it is in more precise words.  I was a clueless Windows user 6 months ago.  I paid for the popular virus/firewall software and installed it.  And that's where it ended.  I put all my faith in the software.  I didn't understand the hundreds of ways my computer could be hijacked.  I think I was like the majority of Windows users in that I didn't want to be bothered with the details.  I just needed it to work so I could get my job done.  And predictably my system was breached.  **So what I'm proposing is simply that a user doesn't take a blind faith approach towards security software, and they certainly shouldn't take a blind faith approach to an operating system.  I'm saying that this blind faith MAY be worse than having no perceived safety net and being forced to pay attention.**    
 

  100% agree.  In fact I'm spending nearly every waking moment doing so in spite of the  steep learning curve for Linux & security in general.  The volume of literature I need to read is daunting.  You spoke about inbound & outbound rules, Apparmor and file permissions.  I have no idea how to implement those. Now that you mentioned them (thank you) I'll certainly be researching them.

Let me clarify, so that it doesn't feel like I'm dumping a ton of frustration on one poster, since that's not the case. I quoted you simply in regards to the part I felt I was misquoted. The vast majority of the rest of the post was aimed toward the "linux is impervious" crowd.

If I made it seem like iptables is NOT a built in firewall I am sorry. Yes, Linux does have a firewall built into the kernel in the form of netfilter/iptables. However it is important to understand that by default iptables and Ubuntu's front end for it (UFW) are by default neither enabled, nor when enabled do they have very restrictive rules. My point in mentioning it is to say simply that

```

sudo ufw enable

```is not a particularly effective method for protecting yourself. Also the assumption that a NAT router (also based off iptables 99% of the time) is any more effective in its default configuration is false.

I do agree with you that taking anything on blind faith is silly, and I highly encourage users especially those who are security conscious to educate themselves. The plain fact is that most people are trying to defend themselves against something they don't understand.

> 
It is said that if you know your enemies and know yourself, you will  not be imperiled in a hundred battles; if you do not know your enemies  but do know yourself, you will win one and lose one; if you do not know  your enemies nor yourself, you will be imperiled in every single battle.

~Sun Tzu
As far as apparmor and file permissions go I believe they are mentioned in the sec stickies, if not they are just a google search away.

I just wish to convey to users not to delude themselves into a false sense of security. I can do all the demos, explain all the theory, but if you choose not to better yourself and your system that is ultimately your loss.

---

### Post by Ms. Daisy on 2011-10-24
No worries.  We agree after all. 
BTW excellent quote.  I'll be stealing that.

---

### Post by Soul-Sing on 2011-10-25
> In the end, nobody can take any steps toward a more secure operating system for you. IF you are truly serious, paranoid, or enthusiastic, only you can educate yourself.

If you are serious and enthusiastic, you know when to stop the security rat race that never ends.
If you are paranoid, that race never ends, and leaves you without any joy. There's no end to educate yourself on security related 
matters. It is 24 hours a day task. I have no time and energy to do that.
Please do know when and where to stop, and enjoy Linux.
(offtopic, sorry bout that.)

---

### Post by Ms. Daisy on 2011-10-25
> **leoquant said:**
> If you are serious and enthusiastic, you know when to stop the security rat race that never ends. If you are paranoid, that race never ends, and leaves you without any joy. There no end to educate yourself on security related matters. It is 24 hours a day task. I have no time and energy to do that. Please do know when and where to stop, and enjoy Linux. (offtopic, sorry bout that.)Totally agree.  There's a concept in security that you can't possibly defend yourself against everything.  And there are diminishing returns for doing so anyway.  So you have to be smart.  Figure out:
1. what are my vulnerabilities?
2. who or what is likely to attack me?
3. what do I have to lose if I get cracked?
4. how much time, effort & cash do I have available to defend myself?

I'm paraphrasing the concept, there's a little more to it.  But you get the idea.  Once you answer these questions, it is a much easier job coming up with a sensible security plan that won't take 24/7 effort to give you comfort. You won't spin your wheels defending against something that will probably never happen.

---

### Post by Dangertux on 2011-10-25
> **Ms. Daisy said:**
> Totally agree.  There's a concept in security that you can't possibly defend yourself against everything.  And there are diminishing returns for doing so anyway.  So you have to be smart.  Figure out:
1. what are my vulnerabilities?
2. who or what is likely to attack me?
3. what do I have to lose if I get cracked?
4. how much time, effort & cash do I have available to defend myself?

I'm paraphrasing the concept, there's a little more to it.  But you get the idea.  Once you answer these questions, it is a much easier job coming up with a sensible security plan that won't take 24/7 effort to give you comfort. You won't spin your wheels defending against something that will probably never happen.

This is where you get into risk management, this is a whole different ball game 

On  a simplified level you have in terms of monetary loss

Exposure Rate (to threat) * Value of Asset/Information = Single Loss Expectancy

This is simplified, and doesn't really factor into personal  data, I mean really you may have nothing of value or something you have may be priceless to you.

So a qualitative method would be appropriate

For instance say you have family photos on your hard drive that are priceless to you. The cost of loss would be devestating. Measures that you could take to mitigate the risk would be something along these lines

- Redundant current backups
- Proper security of home directory (file permissions, application confinement, strong passwords, encryption, etc)
- Proper education, understand threats that can affect the 'asset' in question, and how to reduce exposure.

On the not being too paranoid thing, EVERYONE MUST BE AS PARANOID AS ME! (I kid I kid...). Really based on what I said earlier, the level of paranoia should be directly proportional to the threat of loss.

Hope this helps.

---

### Post by bodhi.zazen on 2011-10-25
> **leoquant said:**
> If you are serious and enthusiastic, you know when to stop the security rat race that never ends.
If you are paranoid, that race never ends, and leaves you without any joy. There no end to educate yourself on security related 
matters. It is 24 hours a day task. I have no time and energy to do that.
Please do know when and where to stop, and enjoy Linux.
(offtopic, sorry bout that.)

Sort of yes and sort of no.

The first step in security is an analysis of the risk. How valuable is your data ? A Linux Desktop is a less valuable target then a bank server is less valuable then some military targets.

My impression on these forums is that we are mostly talking about Ubuntu desktops of relatively little value.

Thus, for most users, the defaults may be sufficient.

If we examine the desktop threats, the most common crack is a VNC server with a weak password. Enabling a firewall does not help much as anyone wanting to use VNC is going to open the port, but it can help limit connections or prevent unwanted connections if a new user inadvertently enables VNC.

Second would be SSH. Use keys and disable password authentication or use strong passwords.

So the most common threats / exploits we see on these forums boil down to 2 very basic security features:

[list][*]Use strong passwords/[*]Do not install servers without understanding how to secure them.[/list]

A firewall can sometimes help with #2.

Beyond that, next biggest threat is your browser. Firefox, for example, has a huge list of vulnerabilities. IMO this can be mitigated with NoScript + apparmor.

Those steps are going to cover the vast majority of users here.

Now that is not the same as claiming Linux is invulnerable. If you have data or a server of value, then you need to go further.

First would be online commerce. If you are doing online purchasing, use ssl (https).

If it goes beyond that, and what I think is the elephant in this conversation, is how to manage a high risk set of data, high risk server, or "vulnerabilities".

Vulnerabilities are reported every day:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

In addition there are Vulnerabilities that have not yet been reported, are unknown. 

Crackers then leverage vulnerabilities to gain unauthorized access.

Protecting high risk targets is indeed a full time job and whole books have been written on the subject. This is when security becomes a never ending process as you suggest.

You can "simplify" this and get people started by :

1. Teach them to monitor the various vulnerability reporting sites (like the one I gave you for Ubuntu).

2. Teach people to read the logs.

3. Teach people to keep their systems up to date, at least with security patches.

4. Teach people to use tools such as apparmor or selinux or pax (grsecuity) or similar types of technology.

5. Teach people how to use intrusion detection (NIDS and HIDS) such as snort and OSSEC.

By default, Ubuntu uses apparmor.

It is going to be extremely rare anyone on these forums would need to go beyond the steps I listed in this post and everything I listed in this post is, IMO, very reasonable and can be implemented with a few hours of reading.

Similarly, doing all the things in this post will not offer you complete protection, but it is a good head start.

Note also that I made no mention of root kit detection, antivirus, and minimal mention of a firewall. While all those things can help a little, they do not help as much, and would not be where I would start.

rootkits are complex and unless you have some expertise and, IMO, it would be a mistake to rely on rkhunter or chkrootkit to detect root kits. I know of no authoritative work that suggests you use these tools.

One example :
[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)
[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)

Again, forensic analysis is complex and can not really be simplified to "run rkhunter".

There are no know active viruses on Linux. If you share files with Windows, run antivirus on Windows. On the linux side, security updates are sufficient.

That covers "the basics" and should be a sufficient **start** for those who are interested without falling into paralysis of feeling there is nothing to be done because security is either too complex or never ending.

---

### Post by Dangertux on 2011-10-25
+1 to what bodhi.zazen said, some good advice in there.

I have done some testing with rkhunter and so long as the rootkit in question is signatured rkhunter does a pretty good job. That being said it really shines when it comes to unhiding processes and ports. This may be the first step to letting you know of potential "rootkit like" activity at which point you can put more thorough forensic measures into place to determine the origin of the activity.

Again, a lot of that will have to be done manually as there isn't a comprehensive signature database of Linux based rootkits, and the ease by which it is to develop them, and the many avenues given for hooking the linux kernel or various system calls makes it hard to match an unsignatured root kit.

Hope this clarifies on rkhunter a little bit.

---

### Post by ##Villain on 2011-10-26
New user here, so if IPtables isn't a firewall, then what is it exactly?

---

### Post by Dangertux on 2011-10-26
No..iptables is a firewall, not sure where that came from but I must have worded something really weird. Again

iptables IS a firewall.

---

### Post by bodhi.zazen on 2011-10-26
> **##Villain said:**
> New user here, so if IPtables isn't a firewall, then what is it exactly?

iptables is a front end for netfilter which is the firewall used by Linux.

Everything else (ufw,gufw,guarddog,firestarter) are front ends for iptables.

See also: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Reddoug on 2011-10-27
A lot of good info here. What about using IPcop? Would it do any better than IPtables or work any different? I have setup IPcop on an old machine but do not have it connected to my network yet. 

Reddoug

---

### Post by CharlesA on 2011-10-27
> **Reddoug said:**
> A lot of good info here. What about using IPcop? Would it do any better than IPtables or work any different? I have setup IPcop on an old machine but do not have it connected to my network yet. 

Reddoug
Does the same thing, pretty much. IPcop has a web interface and does a bit more then just working as a firewall doesn't it?

---

### Post by haqking on 2011-10-27
> **CharlesA said:**
> Does the same thing, pretty much. IPcop has a web interface and does a bit more then just working as a firewall doesn't it?

IPCop is a distro in itself to work as a firewall.

Which is different to firewalling a host OS, most users have a firewall on their home routers, doesnt mean that IPTables or similar shouldnt be used on the host aswell.

Security is a layered approach.

---

### Post by Dangertux on 2011-10-27
Not to argue semantics but if you really want to get into what is the firewall in Linux the actual kernel is due to the added functionality from the netfilter/iptables framework. Anyway that is beside the point. (although kernel level filtering is an advantage over third party firewalls)

As far as IPCop and things of that nature go they possess the same inherant flaws in their default configurations. The problem once again is NOT the software or hardware. This is what I'm trying to impress. Whether you're interfacing directly with netfilter, using a router or something like IPCop , or UFW. The implications are the same. Where security is failing is people's lack of understanding in what they are defending against.

It comes back around to a very Windows-esque mentality. Stick some software that says it's going to protect you on it, and forget about it. Unfortunately if you're serious about security that isn't going to happen. 

Utilizing a security application improperly is as useless as not utilizing it at all. You can't use it properly unless you're aware of what you're using it to prevent.

---

### Post by CharlesA on 2011-10-27
> **haqking said:**
> IPCop is a distro in itself to work as a firewall.

Which is different to firewalling a host OS, most users have a firewall on their home routers, doesnt mean that IPTables or similar shouldnt be used on the host aswell.

Security is a layered approach.

Yep. Also +1 to the layers.

> **Dangertux said:**
> Utilizing a security application improperly is as useless as not utilizing it at all. You can't use it properly unless you're aware of what you're using it to prevent.

Huge +1 too. Why bother with security if you aren't going to learn about it.

---

### Post by taseedorf on 2011-10-27
> **crazy bird said:**
> Like i said, you really don't need any kind of security: no firewall, no anti-virus, no anti-trojans/spyware/malware. Installing these kind of tools is like installing an airbag in your car which already has been fully equipped with airbags. 
 
Anti-virus is only needed when you exchange files with Windows users. And even so, it is the responsibility of the Windows user to have max. protection against virusses/trojans/spyware/malware . It is not the responsibility of Linux users to protect Windows systems of Windows users. If you want anti-virus and you still use Windows formatted (external) drives, then clamav is good enough. It is available in the repository and it even has a graphical interface.
 
But seriously, you really don't need anti-virus! I know you're used to it having such protection as a former Windows user, but for Linux it is not required.


First and foremost... <snip>  You DO need a firewall (there are MANY TCPIP attacks Linux is subject to...not to mention buffer overflows, spoofing, etc).... also, linux DOES have viruses and linux DOES have spyware

You only do NOT need these protection tools if you don't think you do - but over course, if you don't know, you probably do.

I have personally never used a Linux antivirus on my personal computers....however, I know enough not to get a virus typically.

---

### Post by Dangertux on 2011-10-27
> **taseedorf said:**
> First and foremost... <snip>  You DO need a firewall (there are MANY TCPIP attacks Linux is subject to...not to mention buffer overflows, spoofing, etc).... also, linux DOES have viruses and linux DOES have spyware

You only do NOT need these protection tools if you don't think you do - but over course, if you don't know, you probably do.

I have personally never used a Linux antivirus on my personal computers....however, I know enough not to get a virus typically.

While I agree with you, I'm just going to warn you now. You're arguing with yourself. I've tried this argument so many times on this forum, and despite how many times you explain, show, demonstrate, and reiterate what a few of us are saying here. People will believe what they want.

I've all but given up, my only hope is that when people legitimately ask and are given a legitimate answer that they will heed that advice. 

Whether or not a person needs it or not depends entirely on their tolerance for risk. If they have a high tolerance let them do what they want. Truth  is there is a lot of misinformation and assumptions about how secure linux, or anything else for that matter is. This can't be helped, because those saying "it's secure" don't even know what they're saying it's secure from. The saddest part is sometimes it comes in the form of someone who has a large number of posts, or may even be on the forum staff. This hurts the overall level of knowledge in the community. Then again, who are we to change anything right? As I said people will believe what they want.

Just my thoughts.

---

### Post by bodhi.zazen on 2011-10-27
> **taseedorf said:**
> First and foremost... <snip>  You DO need a firewall (there are MANY TCPIP attacks Linux is subject to...not to mention buffer overflows, spoofing, etc).... also, linux DOES have viruses and linux DOES have spyware

You only do NOT need these protection tools if you don't think you do - but over course, if you don't know, you probably do.

I have personally never used a Linux antivirus on my personal computers....however, I know enough not to get a virus typically.

It would help if you would use specific examples of various vulnerabilities and what you can do to help protect against such vulnerabilities.

Education is the best defense and I would suggest you keep in mind, we do have users on these forums new to Ubuntu, and many users in this section are new to security.

Some of the vulnerabilities you mention can be partially or fully addressed by a firewall, but, as Dangertux has been pointing out, a firewall does not help much, if at all, against spoofing (social engineering) or firefox vulnerabilities (malicious java scripts, buffer overflows).

---

### Post by bodhi.zazen on 2011-10-27
Apparmor, selinux, and grsecurity are much better defensive tools against buffer overflows.

Selinux :

Vulnerability

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

Selinux to the rescue: 

[http://danwalsh.livejournal.com/45194.html](http://danwalsh.livejournal.com/45194.html)

```
# paxtest
Executable anonymous mapping             : Killed
Executable bss                           : Killed
Executable data                          : Killed
Executable heap                          : Killed
Executable stack                         : Killed
Executable anonymous mapping (mprotect)  : Killed
Executable bss (mprotect)                : Killed
Executable data (mprotect)               : Killed
Executable heap (mprotect)               : Killed
Executable stack (mprotect)              : Killed
Executable shared library bss (mprotect) : Killed
Executable shared library data (mprotect): Killed
Writable text segments                   : Killed
Anonymous mapping randomisation test     : 16 bits (guessed)
Heap randomisation test (ET_EXEC)        : 13 bits (guessed)
Heap randomisation test (ET_DYN)         : 25 bits (guessed)
Main executable randomisation (ET_EXEC)  : 16 bits (guessed)
Main executable randomisation (ET_DYN)   : 17 bits (guessed)
Shared library randomisation test        : 16 bits (guessed)
Stack randomisation test (SEGMEXEC)      : 23 bits (guessed)
Stack randomisation test (PAGEEXEC)      : No randomisation
Return to function (strcpy)              : Vulnerable
Return to function (memcpy)              : Vulnerable
Return to function (strcpy, RANDEXEC)    : Killed
Return to function (memcpy, RANDEXEC)    : Killed
Executable shared library bss            : Killed
Executable shared library data           : Killed
```

If you are talking "zero day exploits" , you really need to teach Ubuntu users to use apparmor.

---

### Post by Dangertux on 2011-10-27
> **bodhi.zazen said:**
> Apparmor, selinux, and grsecurity are much better defensive tools against buffer overflows.

Selinux :

Vulnerability

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

Selinux to the rescue: 

[http://danwalsh.livejournal.com/45194.html](http://danwalsh.livejournal.com/45194.html)

If you are talking "zero day exploits" , you really need to teach Ubuntu users to use apparmor.



Sigh...If only it were that easy my friend. I have wracked my brain over a way to communicate to brand new users how to create apparmor profilks easily under Ubuntu. It just doesn't seem to happen that way, even with the simplest application confinement.  

Thanks for those links I was looking for that BH presentation, couldn't find the slides. It's actually quite valuable in this discussion, as it (though technical) does show that SELinux can aid a lot (Apparmor as well) but in relation to the presentation, it clearly demonstrates that while escalation is possible, it is much more difficult. Though I'm sure some over-dedicated ROP genius will find another way to circumvent SELinux it's still great.

---

### Post by OpSecShellshock on 2011-10-27
> **Dangertux said:**
> Sigh...If only it were that easy my friend. I have wracked my brain over a way to communicate to brand new users how to create apparmor profilks easily under Ubuntu. It just doesn't seem to happen that way, even with the simplest application confinement.  

Thanks for those links I was looking for that BH presentation, couldn't find the slides. It's actually quite valuable in this discussion, as it (though technical) does show that SELinux can aid a lot (Apparmor as well) but in relation to the presentation, it clearly demonstrates that while escalation is possible, it is much more difficult. Though I'm sure some over-dedicated ROP genius will find another way to circumvent SELinux it's still great.

For what it's worth I thought your example with Chromium was excellent, but I guess I'm not really a new user.

Part of the difficulty is in definitions, I think. When a lot of people, new or not, say "secure" they seem to mean unlikely to get Windows malware. Yeah, that's true without Windows VMs or emulators running I suppose. Even then, which kind do they mean? That borne by removable storage? Delivered by the web? Email attachments?

Even then there's more to it than that. And every specific thing, while it needs to be defended against in its own way, still can't really be treated as discrete from all the other concerns. Maybe instead of asking "is the OS secure?" and then we provide an answer to the best of our ability, we can encourage a changing of the question. Something like, "how well am I positioned regarding x specific risk?" And then build from there.

Sensitive personal data stored on the local disk of a day-to-day use computer? Sure, we could say encrypt, but we could just as well ask why it's being stored there at all when it's not in use. No data, no risk (not exactly, but without overcomplicating it).

Have more than one computer? Why not dedicate one to doing business/sensitive things and the other to fun? Still won't save you from the negligence of third parties you trust your info to, but nothing really can.

Worried about the state intercepting your every packet? Nothing I can do for you.

I guess where I'm going with this is maybe there's an opportunity to tease out users' specific concerns and identify the ways of addressing them. A lot of them may not even know the right questions to ask.

---

### Post by bodhi.zazen on 2011-10-27
> **Dangertux said:**
> Sigh...If only it were that easy my friend. I have wracked my brain over a way to communicate to brand new users how to create apparmor profilks easily under Ubuntu. It just doesn't seem to happen that way, even with the simplest application confinement.

It is not easy, but I would hold out many of your posts as examples of how to work with new users.

If you feel overwhelmed, take a break for a while. We have an endless mass of new users and the questions will keep coming until we educate them all.

If you educate them properly, they will help you out, as they too can then answer questions.

---

### Post by haqking on 2011-10-27
> **OpSecShellshock said:**
> 


I guess where I'm going with this is maybe there's an opportunity to tease out users' specific concerns and identify the ways of addressing them. A lot of them may not even know the right questions to ask.

The trouble is no matter how hard we try to abstract the complex from security, it is not really achieveable as security is complex topic encompassing multiple domains of knowledge, even in the security industry security professionals often have chosen domains of speciality due to the broad spectrum of technologies and knowledge required.

new users who we need to put the security concepts over too, dont have the foundational concepts to truly understand them (and i dont mean this detrimentally to anyone).  

Linux is in a good place security wise for the new user, however is often undone very quickly through the "lets play" attitude which of course is welcomed and alot of the time the reason we use Linux.

All we can ever really do for the benefit of a new user is to put across to them that nothing is 100% secure and that security comes down to common sense and education, if you are bothered about it then you will educate yourself, if you dont want to or cant be bothered then your security will lapse and any answer to any security related question is effectively moot from that point on.

We can throw any firewall/IDS/IPS/AV solution or argument or explanation at them but it wont help secure the system unless they know what they are securing themselves against which comes back to the education.

However hopefully this community and threads such as these offer some of that education, so we are on the right track ;-)

just my 2 cents

---

### Post by CharlesA on 2011-10-27
Speaking as someone who is trying to get into the security field - I have found there is a hell of a learning curve.

Oh and +1 to Haq, Bodhi and Op. :)

---

### Post by Dangertux on 2011-10-27
@OpSecShellshock - Thanks for the compliment I appreciate it :-)

@bodhi.zazen - Thanks for the support :-) (ps : no I haven't forgotten I owe you something ;-))

@haqking - You rock, you just do , thanks for listening to all my "OMG ANOTHER FW THREAD" rants ;-) 

@Everyone in this thread and all the others like it - hopefully this is an example of exactly how nit picky and in depth a sec discussion can get and this is basic stuff :-/

I hope I haven't been coming across as over-zealous, terse, or otherwise a giant (explicative deleted). I do consider this very serious, and I just want people to have accurate information that is on par with the quality of what I've seen this fine community provide over the past 6 or so months.

---

### Post by haqking on 2011-10-27
> **Dangertux said:**
> 

I hope I haven't been coming across as over-zealous, terse, or otherwise a giant (explicative deleted).

no not at all, which is strange as i know you are...LOL

---

### Post by Ms. Daisy on 2011-10-27
> **CharlesA said:**
> Speaking as someone who is trying to get into the security field - I have found there is a hell of a learning curve.  Holy cow, truer words have never been spoken.     To illustrate my occasional frustration when overwhelmed with a complex new processes, I have translated the post  by bodhi.zazen into what I see as a new user. 

```
# mysterioustest
  Executable seems bad                      : Killed (my computer?)
 Executable bs                            : Killed (my crap?)
 Executable blah blah blah                : Killed (the executable?)
 Executable seems good (protectsme)       : Killed (a protection?)
 Executable bs (protectscrap)             : Killed (the hacker?)
 Executable hug (momprotectsme)           : Killed (the boogeyman)
 Anonymous mysterious randomisation test  : 16 bits (the program guessed?)
 Heap of confusion test (ET_EXEC)         : 13 bits (I could guess)
 Heap of alien test (ET_GOHOME)           : 25 bits (of recees pieces)
 Main executable thingamajig (ET_EXEC)    : 16 bits (guessed)
 Main scary sounding thing (ET_DYING)     : 17 bits (guessed)
 Shared overdue book test                 : 16 bits (guessed)
 Stack sandwich test (SEGMHUNGRY)         : 23 bites (taken)
 Stacked chick test (GAWKEXEC)            : No stacked chicks :(
 Return a mystery (strangecpy)            : Vulnerable (oh no!)
 Return an enigma (mysterycpy)            : Vulnerable (now what?)
 Return to normal (EXECRANDOMSTUFF)       : Killed 
  Return to plate (ralphcpy, GAGEXEC)       : Killed (my appetite)
 Executable shared bs                     : Killed (the crap?)
 Executable return library book           : Killed (the librarian?)
```(For the record, bodhi.zazen has created several posts I found invaluable. I'm just being goofy here)

---

### Post by haqking on 2011-10-27
> **Ms. Daisy said:**
> Holy cow, truer words have never been spoken.     To illustrate my occasional frustration when overwhelmed with a complex new processes, I have translated the post  by bodhi.zazen into what I see as a new user. 

```
# mysterioustest
  Executable seems bad                      : Killed (my computer?)
 Executable bs                            : Killed (my crap?)
 Executable blah blah blah                : Killed (the executable?)
 Executable seems good (protectsme)       : Killed (a protection?)
 Executable bs (protectscrap)             : Killed (the hacker?)
 Executable hug (momprotectsme)           : Killed (the boogeyman)
 Anonymous mysterious randomisation test  : 16 bits (the program guessed?)
 Heap of confusion test (ET_EXEC)         : 13 bits (I could guess)
 Heap of alien test (ET_GOHOME)           : 25 bits (of recees pieces)
 Main executable thingamajig (ET_EXEC)    : 16 bits (guessed)
 Main scary sounding thing (ET_DYING)     : 17 bits (guessed)
 Shared overdue book test                 : 16 bits (guessed)
 Stack sandwich test (SEGMHUNGRY)         : 23 bites (taken)
 Stacked chick test (GAWKEXEC)            : No stacked chicks :(
 Return a mystery (strangecpy)            : Vulnerable (oh no!)
 Return an enigma (mysterycpy)            : Vulnerable (now what?)
 Return to normal (EXECRANDOMSTUFF)       : Killed 
  Return to plate (ralphcpy, GAGEXEC)       : Killed (my appetite)
 Executable shared bs                     : Killed (the crap?)
 Executable return library book           : Killed (the librarian?)
```(For the record, bodhi.zazen has created several posts I found invaluable. I'm just being goofy here)


mysterioustest is commonly known trojan exploiting lots of well known vulnerabilities ;-)

---

### Post by Matrix01 on 2011-10-27
I got this Netbook, HP Mini on December,

installed 11.04 less than a week ago,
and
use WiFi at wherever available, work, coffee shop, etc.

i used to have Dell desktop and AOL hooked with telephone modem over ten years ago.

> **bodhi.zazen said:**
> Most of the things you were taught about Windows security, or at least the things you are asking about, do not apply to Linux.

Start with the security sticky.

From there it sort of depends on your user case. Assuming you are a Desktop user behind a firewall (router) I would suggest you learn apparmor and use NoScript.

From there you need to understand, there are many security tools at your disposal, but they all have a bit of a learning curve.

Personally I like snort and ossec, but I do not use them on a desktop.

---

### Post by bodhi.zazen on 2011-10-27
> **Ms. Daisy said:**
> Holy cow, truer words have never been spoken.     To illustrate my occasional frustration when overwhelmed with a complex new processes, I have translated the post  by bodhi.zazen into what I see as a new user. 

```
# mysterioustest
  Executable seems bad                      : Killed (my computer?)
 Executable bs                            : Killed (my crap?)
 Executable blah blah blah                : Killed (the executable?)
 Executable seems good (protectsme)       : Killed (a protection?)
 Executable bs (protectscrap)             : Killed (the hacker?)
 Executable hug (momprotectsme)           : Killed (the boogeyman)
 Anonymous mysterious randomisation test  : 16 bits (the program guessed?)
 Heap of confusion test (ET_EXEC)         : 13 bits (I could guess)
 Heap of alien test (ET_GOHOME)           : 25 bits (of recees pieces)
 Main executable thingamajig (ET_EXEC)    : 16 bits (guessed)
 Main scary sounding thing (ET_DYING)     : 17 bits (guessed)
 Shared overdue book test                 : 16 bits (guessed)
 Stack sandwich test (SEGMHUNGRY)         : 23 bites (taken)
 Stacked chick test (GAWKEXEC)            : No stacked chicks :(
 Return a mystery (strangecpy)            : Vulnerable (oh no!)
 Return an enigma (mysterycpy)            : Vulnerable (now what?)
 Return to normal (EXECRANDOMSTUFF)       : Killed 
  Return to plate (ralphcpy, GAGEXEC)       : Killed (my appetite)
 Executable shared bs                     : Killed (the crap?)
 Executable return library book           : Killed (the librarian?)
```(For the record, bodhi.zazen has created several posts I found invaluable. I'm just being goofy here)

ROFL !!!!

That is almost as good as these bash alises

```
alias do_want='sudo apt-get install'
alias do_not_want='sudo apt-get remove'
alias i_can_haz='sudo apt-get install'
alias im_in_yur='cd'
alias kthxbai='exit'
alias invisbl='fg' #send job to foreground
alias visabl='echo'
alias caturday='date'
alias not_amuzed='killall'
alias oh_noez='reboot'
alias nomnomnom='rm'
alias rly='sudo'
```

At any rate , we are discussing cracking and leveraging exploits, and how to stop them.

There are several options, selinux, apparmor, and my post is referring to pax.

There are others as well

[http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html](http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html)

gsecurity is a kernel patch, pax kills bad acting applications.

We are discussing #5 on the above link:

```
Prevention of arbitrary code execution, regardless of the technique used (stack smashing, heap corruption, etc)
```

So look here

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Which leads to this report

[http://www.ubuntu.com/usn/usn-1232-1/](http://www.ubuntu.com/usn/usn-1232-1/)

> It was discovered that the X server incorrectly handled certain malformed
input. An authorized attacker could exploit this to cause the X server to
crash, leading to a denial or service, or possibly execute arbitrary code
with root privileges.

As you can imagine "possibly execute arbitrary code with root privileges" is , um, not good. 

"arbitrary code with root privileges" == [pwned](http://www.urbandictionary.com/define.php?term=pwned) as we say in "the business" :twisted:

pax would (hopefully) stop the execution of such arbitrary code , and pax test simulates such an event.

selinux would do the same.

so would apparmor.

These tools , unlike tools such as antivirus, work on zero day exploits.

So you then turn the tables, and the cracker is the one who is pwned.

You hope, unless the attacker knows you are running pax, and in that case she ....

You get the idea, there is no real end to pwnage .

If you use Ubuntu, learn apparmor. You can at least enable the default profiles with just an hour or two of reading.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

[http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

So to answer your question, "Killed" == pwned another cracker

---

### Post by OpSecShellshock on 2011-10-27
> **CharlesA said:**
> Speaking as someone who is trying to get into the security field - I have found there is a hell of a learning curve.

Oh and +1 to Haq, Bodhi and Op. :)

Indeed. Whatever you do, don't go into incident response. It's like being punched in the face by the same 5 guys 100 times a day while being told that the appropriate headgear just isn't in the budget. I love it, of course.

---

### Post by haqking on 2011-10-27
> **OpSecShellshock said:**
> Indeed. Whatever you do, don't go into incident response. It's like being punched in the face by the same 5 guys 100 times a day while being told that the appropriate headgear just isn't in the budget. I love it, of course.

:lolflag:

that made me smile

---

### Post by Dangertux on 2011-10-27
I love where this thread went. 

For the OP or whoever it was back there who asked about public wifi look into ssh tunneling or VPN.

---

### Post by haqking on 2011-10-27
> **Matrix01 said:**
> I am on Netbook, HP Mini,

installed 11.04 less than a week ago,
and
use WiFi at wherever available, work, coffee shop, etc.

The best security in this instance as always is common sense.

As DT mentions above there some secure solutiuons such as ssh or VPN.

However do not use these public connections for banking or connections that share your personal data.

if you dont know or trust the gateway through which you access the big bad net then be forewarned

---

### Post by CharlesA on 2011-10-27
> **OpSecShellshock said:**
> Indeed. Whatever you do, don't go into incident response. It's like being punched in the face by the same 5 guys 100 times a day while being told that the appropriate headgear just isn't in the budget. I love it, of course.
Was thinking more along the lines of security analyst or pen tester.

That one doesn't sound that pleasant at all.

---

### Post by Matrix01 on 2011-10-28
how do u find clamav?
i did not see it in software center.
[ATTACH]205654[/ATTACH]

> **Leaf said:**
> Clamav is a unix virus scanner, it's in the software center.

---

### Post by Ms. Daisy on 2011-10-28
> **bodhi.zazen said:**
> So you then turn the tables, and the cracker is the one who is pwned.

You hope, unless the attacker knows you are running pax, and in that case she ....

You get the idea, there is no real end to pwnage .

If you use Ubuntu, learn apparmor. You can at least enable the default profiles with just an hour or two of reading.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

[http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

So to answer your question, "Killed" == pwned another cracker Oooohhhh!  I like the sound of that :twisted: Thank you, that was the piece of information I was missing.

---

### Post by haqking on 2011-10-28
> **Matrix01 said:**
> how do u find clamav?
i did not see it in installed softwares.
[ATTACH]205654[/ATTACH]

You are looking in the installed software, you need to search for it and install it.

Full of false positives though, but better than nothing if you share windows files

---

### Post by dfarrell07 on 2011-10-31
HTTPSEverywhere by the EFF and AdBlockPlus are a must. NoScript is good. I don't use anything else and feel safe enough.

---


---
title: "Browser security side trip"
date: 2011-08-25
forum: Security
---

### Post by nec207 on 2011-08-25
So if I understand it you got browser space and OS space . If I go to a web site that as flash ,Java,Java-script,Active-X or scripts there is potential for malware to get on the computer.
 
Why not the OS and AV like Norton or Kaspersky block it ??? It cannot block it !!! if it block flash ,Java,Java-script,Active-X or scripts on the page than most web sites would not work !!
 
But the OS you got user level and system level. The malware I got was in user level.
 
What is the difference of OS X user level and system level vs windows user level and system level .
 
Why have user level and system level at all.
 
Why not the browser sandbox or OS sandbox block it ? It cannot if it block it than most web sites would not work.
 
So the point of a being very secure goes out the window here.It would not better if I was using windows,Linux,Unix or OS X or any other OS as no  OS can block it.

---

### Post by Dangertux on 2011-08-25
> **nec207 said:**
> So if I understand it you got browser space and OS space . If I go to a web site that as flash ,Java,Java-script,Active-X or scripts there is potential for malware to get on the computer.
 
Why not the OS and AV like Norton or Kaspersky block it ??? It cannot block it !!! if it block flash ,Java,Java-script,Active-X or scripts on the page than most web sites would not work !!
 
But the OS you got user level and system level. The malware I got was in user level.
 
What is the difference of OS X user level and system level vs windows user level and system level .
 
Why have user level and system level at all.
 
Why not the browser sandbox or OS sandbox block it ? It cannot if it block it than most web sites would not work.
 
So the point of a being very secure goes out the window here.It would not better if I was using windows,Linux,Unix or OS X or any other OS as no  OS can block it.

Despite how "secure" an operating system is made, people are still involved. I'm not trying to be a butthead here, but the truth of the matter is no OS is going to do everything for you. You have to have some level of competence to avoid most threats. 

As far as NOTHING being able to protect you, this is untrue. Browser based vulnerabilities can be mitigated through the use of addons like NoScript/NotScripts , and mitigated through the use of things like a sandbox or vm, or application level firewalling such as Apparmor/SELinux. 

As far as Anti-Virus and Firewalls go you really need to understand what they look at. They are not a catch all. However, a lot of anti-malware solutions are starting to come with browser addons to help mitigate browser based threats. For the most part Anti-Virus is going to be looking at what hits your hard drive. Firewalls will be looking at your network activity. What happens in a browser really isn't the responsibility of these programs. Also , there are MANY ways of getting around a traditional AV/Firewall combination. 

In the end, you are going to have to be able to look at what is happening on your system and determine if it is something that you approve of. This, in my opinion is the true strength in the security of open source software. There are no secrets, and you can see exactly what is happening at any given point. This is not so in closed source software. The rest is just security features, you name them, it can all be bypassed, DEP/ASLR, Firewalls, Anti-Virus, Browser Addons, encryption, VM's , sandboxes, app firewalls, the list goes on. A feature or function can always be made to fail. The question is are you knowledgeable enough to know what is really happening with your system?

This is just my opinion, because the truth is the one thing in the equation that can't be analyzed is human behavior (and that statement is only partially true). If you're smarter than the average victim, you likely won't become one.

---

### Post by nec207 on 2011-08-25
>  
As far as NOTHING being able to protect you, this is untrue. Browser based vulnerabilities can be mitigated through the use of addons like NoScript/NotScripts , and mitigated through the use of things like a sandbox or vm, or application level firewalling such as Apparmor/SELinux. 

 
Can you elaborate here.

---

### Post by Dangertux on 2011-08-25
> **nec207 said:**
> Can you elaborate here.

Yes -- it's quite simple.

I am saying, you take the best measures you can to protect yourself. 

For example, an anti-malware solution, firewall, necessary browser addons (IE: NoScript), application firewall (IE: Apparmor, or for you Windows folks Trustware's Bufferzone), lack of executable memory (DEP), and randomized information in the heap and stack(ASLR), and you put them all together with decent personal habits.  For example, if some random person asks you on Facebook to help their farm and the link contains a parameter with a url including a javascript at a domain hosted in russia, probably not the best thing to click.  When you put all of this together, you get a fairly decent security model for a home system. 

In the end the most important of all of those factors for the average home user, is common sense. 60% of the time the threats you will encounter will likely require your interaction. So if you use common sense you're already ahead of the game, a few browser addons and a decent system configuration should put the "which OS is the most secure" argument to bed. Unless of course you're all running production servers in your homes (I doubt this)

Side Note : The above example was made without a chosen platform in mind, so please don't lecture me on how you don't need an anti-malware solution for Linux. 

Hope this helps.

P.S : after reading all that and checking it all off the list -- make sure your password isn't mYd0gSk1p

---

### Post by nec207 on 2011-08-25
sorry I was saying to elaborate what is in bold.
 
>  
**As far as NOTHING being able to protect you, this is untrue. Browser based vulnerabilities can be mitigated through the use of addons like NoScript/NotScripts , and mitigated through the use of things like a sandbox or vm, or application level firewalling such as Apparmor/SELinux. **
****
 
And because I'm new to security would you say the security + book or CISSP book is where I should start?

---

### Post by Dangertux on 2011-08-25
> **nec207 said:**
> sorry I was saying to elaborate what is in bold.
 
[/B]
 
And because I'm new to security would you say the security + book or CISSP book is where I should start?

Ummm... I did elaborate on what is in bold. Now you are asking an entirely different question. 

Define security? That is a really broad topic.

What are you securing?

A home PC? 
A home network?
A small business?
A web application that accepts payment card information and gets usage from 400,000 visitors per day?
An enterprise network containing thousands of desktop systems, roaming clients, telecommuters, production servers, and a bunch of network devices including NACs , routers, switches, NAS, and a really old token ring device nobody really knows how to work, as well as a VoIP system that isn't in production anymore? 

You see how this quickly goes from 0 to 60. I think you really need to focus on a singular topic. As far as Sec+ and CISSP go.

CISSP is going to focus more on upper level management of enterprise class resources and things like incident response, compliance audits, risk management matrices, threat matrices and the like.Think CTO's and senior auditors.

Sec+ is more along the lines of general security, think system administrators, and things like the Triple A model, different types of encryption methods (symetric, asymetric), authentication methods (KERBEROS, TASACS, etc). Types of firewalls, The OSI model...

Honestly, of the two I wouldn't recommend either based on the questions you're asking, I would start with basic system architecture and work my way up to more advanced topics. Before you can focus on securing something you need to know how it works in the first place.  

Perhaps a basic book on Linux security, if you insist on diving right into sec.

---

### Post by nec207 on 2011-08-25
>  
Honestly, of the two I wouldn't recommend either based on the questions you're asking, I would start with basic system architecture and work my way up to more advanced topics. Before you can focus on securing something you need to know how it works in the first place. 
 
Perhaps a basic book on Linux security, if you insist on diving right into sec.
 

 
Base on the questions I'm asking in this thread and other threads here .I think I need a basic book for a newbie.
 
Asking questions what is spyware,adware,worm,trojan and virus and other malware what it is and how it travels on the internet.Why my computer is getting malware and why the OS and browser is not blocking it and a tone other questions here in this thread and other threads I need a starting point .
 
**> [B]As far as NOTHING being able to protect you, this is untrue. Browser based vulnerabilities can be mitigated through the use of addons like NoScript/NotScripts , and mitigated through the use of things like a sandbox or vm, or application level firewalling such as Apparmor/SELinux. **[/B]
 
 
Well that is the thing because I don't understand basic security I'm having hard time to understand what you are saying above in bold**.**

---

### Post by Dangertux on 2011-08-25
> **nec207 said:**
> Base on the questions I'm asking in this thread and other threads here .I think I need a basic book for a newbie.
 
Asking questions what is spyware,adware,worm,trojan and virus and other malware what it is and how it travels on the internet.Why my computer is getting malware and why the OS and browser is not blocking it and a tone other questions here in this thread and other threads I need a starting point .
 

 
 
Well that is the thing because I don't understand basic security I'm having hard time to understand what you are saying above in bold**.**

Ok , well I'm not trying to sound "holier than thou" or anything ; but I can kinda tell you got a little lost in this discussion. 

Definitely start with a beginner level book or better just start researching on the internet (it's free and all).

If you're just looking to learn about basic home networking security there are NUMEROUS resources on this forum alone for that. If you're wanting to get more into advanced topics, work your way up from the basics. Don't start with security in mind. Start by learning how a system works. Your mind will naturally start gravitating toward understanding why the system doesn't work as well as it should. Then once you become very familiar with how the system you are learning about works. Start applying security principles. Start learning about how malware actually works, different types of exploitation methods, then look at how that system is effected by them. When you move on to your next topic, take what you learned with you. You will soon find there is a lot of common ground when it comes to poorly designed systems.

---

### Post by nec207 on 2011-08-29
To understand basic hardware,software,OS,troubleshooting and networking the A+ is the best .The network+ is good for a small office or home that need more information on networking.
 
I believe the security + is for the home and small office.The vey basic security .I think most large company will ask for the MSCE.But before one can get a MCSE you have to have the A+ network+ and security + .
 
I know some people that are taking a 5 year degree of CISCO routing that are specializing in networking both windows and Linux and Unix.
 
I have seen some degree say network specialist ,security specialist , PC repair and troubleshooting specialist , help desk specialist so on.
 
I think Dell ,Best Buy and most computer stores say they have PC repair tech working there and malware tech that lock down your computer and remove malware.
 
No idea of cert or degree these people have.
 
May be the A+  , network+ , and security + is the best way for me to go?? I think Mike Meyers wrote some books on basic security for home use and a small office.
 
Or may be I should just take a degree in security ???

---

### Post by Dangertux on 2011-08-29
> **nec207 said:**
> To understand basic hardware,software,OS,troubleshooting and networking the A+ is the best .The network+ is good for a small office or home that need more information on networking.
 
I believe the security + is for the home and small office.The vey basic security .I think most large company will ask for the MSCE.But before one can get a MCSE you have to have the A+ network+ and security + .
 
I know some people that are taking a 5 year degree of CISCO routing that are specializing in networking both windows and Linux and Unix.
 
I have seen some degree say network specialist ,security specialist , PC repair and troubleshooting specialist , help desk specialist so on.
 
I think Dell ,Best Buy and most computer stores say they have PC repair tech working there and malware tech that lock down your computer and remove malware.
 
No idea of cert or degree these people have.
 
May be the A+  , network+ , and security + is the best way for me to go?? I think Mike Meyers wrote some books on basic security for home use and a small office.
 
Or may be I should just take a degree in security ???

Places like best buy will hire kids in high school. I doubt their qualifications. Their middle level management probably has SOME college and maybe A+. Retail is not ever going to be a place to find vastly experienced technicians. You get what you pay for. 

As far as the path of certifications I suggest looking at what employers want for different jobs.  It will usually give you a hint of the path you should take in getting your certs based on the job you want. IMO don't focus so much on certs but focus on what you actually know. Certs come with knowledge and experience not the other way around. Despite what some folks around here seem to think. 

College is always a plus , but even then is no substitute for the knowledge and ability that comes from actually performing the tasks.

---

### Post by 98cwitr on 2011-08-29
Google chrome scans web code by default :-\"

---

### Post by bodhi.zazen on 2011-08-29
> **nec207 said:**
> So if I understand it you got browser space and OS space . If I go to a web site that as flash ,Java,Java-script,Active-X or scripts there is potential for malware to get on the computer.
 
Why not the OS and AV like Norton or Kaspersky block it ??? It cannot block it !!! if it block flash ,Java,Java-script,Active-X or scripts on the page than most web sites would not work !!
 
But the OS you got user level and system level. The malware I got was in user level.
 
What is the difference of OS X user level and system level vs windows user level and system level .
 
Why have user level and system level at all.
 
Why not the browser sandbox or OS sandbox block it ? It cannot if it block it than most web sites would not work.
 
So the point of a being very secure goes out the window here.It would not better if I was using windows,Linux,Unix or OS X or any other OS as no  OS can block it.

selinux (sesandbox) would block this in an instant, well at least keep it confined to the sandbox, which is then deleted when you close ff.

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

Whit I think you are asking about is sort of the point of MAC (selinux / apparmor).

---

### Post by cariboo on 2011-08-29
Please keep this discussion about Ubuntu, a discussion on Windows security doesn't belong here.

---

### Post by nec207 on 2011-09-02
First off I was looking for a security book that will answer alot of my questions here at ubuntuforums and cover basic security for the home and small office.No where I'm saying here it as to cover so much information where it like some one working for a large corporation.There as to be the basic before one cam than move on and learn more about it.
 
 
That why a basic security book will be better.
 
>  
selinux (sesandbox) would block this in an instant, well at least keep it confined to the sandbox, which is then deleted when you close ff.
 
[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)
 
Whit I think you are asking about is sort of the point of MAC (selinux / apparmor). 

 
A browser is an application that runs above the OS level we talk about this in past here. No mattet if I use Chrome, Firefox, Safari ,Opera or several other browsers. Those choices can make no difference in what happens when you or I visit a compromised website do to the **internet cashing of sites** and need to run **Java,Java-scrip,flash ,scripts and rich HTML** so on:( is run in **browser layer** or in **some cases talk to the OS** and is **not on the page it self.** This is a big problem .
 
I could use windows 3.1 computer or os2 warp with no plugins ,no flash,no script nothing and I mean nothing just plain monochrome browser , **I would have got no malware** .But yet again the **web site would not work**._Where Java,Java-scrip,flash ,scripts and rich HTML so on can be used for good or bad._
 
This is do to if the OS blocks this or the sandbox or AV like Norton or Kaspersky than most web sites would not work.Most web sites like this web site at ubuntuforums you need Java,Java-scrip,flash ,scripts and rich HTML so on .
 
I'm just saying it does not matter what OS you use, what browsers, what sanbox or what AV if it blocks it the web sites would not work.So it does not block it.

---

### Post by cariboo on 2011-09-02
> This is do to if the OS blocks this or the sandbox or AV like Norton or Kaspersky than most web sites would not work.Most web sites like this web site at ubuntuforums you need Java,Java-scrip,flash ,scripts and rich HTML so on .

Safe web browsing, has more to do with common sense, then relying on programs that automatically protect you from yourself. As we all know anti-malware programs don't work at the best of times.

Most of this is moot when using a Linux variant, almost all malware is aimed at Windows users. I'd recommend, that you use a Linux variant to smartly browse the internet.

---

### Post by Dangertux on 2011-09-02
> **cariboo907 said:**
> Safe web browsing, has more to do with common sense, then relying on programs that automatically protect you from yourself. As we all know anti-malware programs don't work at the best of times.

Most of this is moot when using a Linux variant, almost all malware is aimed at Windows users. I'd recommend, that you use a Linux variant to smartly browse the internet.

I disagree, but only because you threw browsing into the mix. Especially when it comes to the average home user. If you really look at the threats confronting you the most devastating are going to be cross platform browser based exploits.

Example : which is more valuable to you?  Your personal files stored on your PC or your banking information?

In this case your banking information can be vulnerable (not saying it is,  it's obviously case by case depending on the institution's level of security) to cross platform exploitation, such as but not limited to XSS, CSRF , sessions riding, CSTA , etc.

In this particular case an application like noscript could be very useful.

When you start talking about anti-malware you're talking about applications that deal with data that actually hits your hard drive. At very least I feel both should be used in concert. However, I believe that writing them off completely because you use Linux, or any other supposedly secure operating system or browser would be foolish.

That is my opinion.

---

### Post by nec207 on 2011-09-03
> **Dangertux said:**
> I disagree, but only because you threw browsing into the mix. Especially when it comes to the average home user. If you really look at the threats confronting you the most devastating are going to be cross platform browser based exploits.
 
Example : which is more valuable to you? Your personal files stored on your PC or your banking information?
 
In this case your banking information can be vulnerable (not saying it is, it's obviously case by case depending on the institution's level of security) to cross platform exploitation, such as but not limited to XSS, CSRF , sessions riding, CSTA , etc.
 
In this particular case an application like noscript could be very useful.
 
When you start talking about anti-malware you're talking about applications that deal with data that actually hits your hard drive. At very least I feel both should be used in concert. However, I believe that writing them off completely because you use Linux, or any other supposedly secure operating system or browser would be foolish.
 
That is my opinion.
 
Yes but what does that have to do with my questions above?

---

### Post by bodhi.zazen on 2011-09-03
> **nec207 said:**
> Yes but what does that have to do with my questions above?

There is nothing you can do about people putting up malignant code on untrusted web sites.

What you can do is:

1. Not visit those sites.

2. Run your browser in some kind of a sandbox, a VM, live CD, apparmor, or selinux so that although your browser session may have been affected, the browser has no access to change system files or access your personal files.

What more do you expect ?

You want to use flash, javascript, java, etc, but you know they are insecure or add vulnerabilities. You want to visit shady sites, but you know they are insecure.

---

### Post by Dangertux on 2011-09-04
> **bodhi.zazen said:**
> There is nothing you can do about people putting up malignant code on untrusted web sites.

What you can do is:

1. Not visit those sites.

2. Run your browser in some kind of a sandbox, a VM, live CD, apparmor, or selinux so that although your browser session may have been affected, the browser has no access to change system files or access your personal files.

What more do you expect ?

You want to use flash, javascript, java, etc, but you know they are insecure or add vulnerabilities. You want to visit shady sites, but you know they are insecure.


This is very true but my point is there IS something you can do about people exploiting vulnerabilities in normal websites. You don't have to visit a "shady" site just to get owned. 

Unforunately the obvious problem is then, no site can be trusted, thus the configuring of something like noscript can become painful rapidly.

---

### Post by nec207 on 2011-09-05
For the billion time asking here what books should newbie to networking ,Security and malware get to understand basic Security and alot of the questions I have been asking here.
 
Sure I could do my own amazon search and get this or that
 
That see
 
CompTIA-Security
[http://www.amazon.com/CompTIA-Security-Certified-Ahead-SY0-201/dp/1439236364/ref=sr_1_1?ie=UTF8&qid=1315255752&sr=8-1](http://www.amazon.com/CompTIA-Security-Certified-Ahead-SY0-201/dp/1439236364/ref=sr_1_1?ie=UTF8&qid=1315255752&sr=8-1)
 
Security-Engineering
[http://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/0470068523/ref=sr_1_7?ie=UTF8&qid=1315255752&sr=8-7](http://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/0470068523/ref=sr_1_7?ie=UTF8&qid=1315255752&sr=8-7)
 
More
[http://www.amazon.com/Web-Application-Hackers-Handbook-Discovering/dp/0470170778/ref=sr_1_8?ie=UTF8&qid=1315255752&sr=8-8](http://www.amazon.com/Web-Application-Hackers-Handbook-Discovering/dp/0470170778/ref=sr_1_8?ie=UTF8&qid=1315255752&sr=8-8)
 
More
[http://www.amazon.com/Computer-Information-Security-Handbook-Kaufmann/dp/0123743540/ref=sr_1_11?ie=UTF8&qid=1315255752&sr=8-11](http://www.amazon.com/Computer-Information-Security-Handbook-Kaufmann/dp/0123743540/ref=sr_1_11?ie=UTF8&qid=1315255752&sr=8-11)
 
Myths Security Computer
[http://www.amazon.com/Myths-Security-Computer-Industry-Doesnt/dp/0596523025/ref=sr_1_30?ie=UTF8&qid=1315255899&sr=8-30](http://www.amazon.com/Myths-Security-Computer-Industry-Doesnt/dp/0596523025/ref=sr_1_30?ie=UTF8&qid=1315255899&sr=8-30)
 
Network Security Bible
[http://www.amazon.com/Network-Security-Bible-Eric-Cole/dp/0470502495/ref=sr_1_43?ie=UTF8&qid=1315255956&sr=8-43](http://www.amazon.com/Network-Security-Bible-Eric-Cole/dp/0470502495/ref=sr_1_43?ie=UTF8&qid=1315255956&sr=8-43)
Malware Analysts
 
[http://www.amazon.com/Malware-Analysts-Cookbook-DVD-Techniques/dp/0470613033/ref=sr_1_1?ie=UTF8&qid=1315256009&sr=8-1](http://www.amazon.com/Malware-Analysts-Cookbook-DVD-Techniques/dp/0470613033/ref=sr_1_1?ie=UTF8&qid=1315256009&sr=8-1)
 
Malware Fighting Malicious 
[http://www.amazon.com/Malware-Fighting-Malicious-Ed-Skoudis/dp/0131014056/ref=sr_1_4?ie=UTF8&qid=1315256009&sr=8-4](http://www.amazon.com/Malware-Fighting-Malicious-Ed-Skoudis/dp/0131014056/ref=sr_1_4?ie=UTF8&qid=1315256009&sr=8-4)
 
 
And millions more books I could get!!!
 
But I was looking for advice here for good book to start with.
 
 
So again for the billion time asking here what book will explain basic security .
 
 
Before you say what security I mean basic security.
 
--Understanding malware like virus ,worms ,trojans, scrips ,spyware ,adware so on. 
--How malware spreads and why we get malware
--how to lock down your computer
--understanding expliots and why computers get malware.
--Understanding OS and OS layers and things like UAC, Discretionary access control ,sandbox ,permissions ,ACLs ,MIC so on.
 
-- Understanding flash , javascript ,Java , script or active-x s so on and how to tighten this up in the OS.
 
--how a firewall works and why we need one.
-- how to secure the router.
-- Why OS get malware and why some OS more than others
--the basics.

---

### Post by Dangertux on 2011-09-05
> **nec207 said:**
> For the billion time asking here what books should newbie to networking ,Security and malware get to understand basic Security and alot of the questions I have been asking here.
 
Sure I could do my own amazon search and get this or that
 
That see
 
CompTIA-Security
[http://www.amazon.com/CompTIA-Security-Certified-Ahead-SY0-201/dp/1439236364/ref=sr_1_1?ie=UTF8&qid=1315255752&sr=8-1](http://www.amazon.com/CompTIA-Security-Certified-Ahead-SY0-201/dp/1439236364/ref=sr_1_1?ie=UTF8&qid=1315255752&sr=8-1)
 
Security-Engineering
[http://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/0470068523/ref=sr_1_7?ie=UTF8&qid=1315255752&sr=8-7](http://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/0470068523/ref=sr_1_7?ie=UTF8&qid=1315255752&sr=8-7)
 
More
[http://www.amazon.com/Web-Application-Hackers-Handbook-Discovering/dp/0470170778/ref=sr_1_8?ie=UTF8&qid=1315255752&sr=8-8](http://www.amazon.com/Web-Application-Hackers-Handbook-Discovering/dp/0470170778/ref=sr_1_8?ie=UTF8&qid=1315255752&sr=8-8)
 
More
[http://www.amazon.com/Computer-Information-Security-Handbook-Kaufmann/dp/0123743540/ref=sr_1_11?ie=UTF8&qid=1315255752&sr=8-11](http://www.amazon.com/Computer-Information-Security-Handbook-Kaufmann/dp/0123743540/ref=sr_1_11?ie=UTF8&qid=1315255752&sr=8-11)
 
Myths Security Computer
[http://www.amazon.com/Myths-Security-Computer-Industry-Doesnt/dp/0596523025/ref=sr_1_30?ie=UTF8&qid=1315255899&sr=8-30](http://www.amazon.com/Myths-Security-Computer-Industry-Doesnt/dp/0596523025/ref=sr_1_30?ie=UTF8&qid=1315255899&sr=8-30)
 
Network Security Bible
[http://www.amazon.com/Network-Security-Bible-Eric-Cole/dp/0470502495/ref=sr_1_43?ie=UTF8&qid=1315255956&sr=8-43](http://www.amazon.com/Network-Security-Bible-Eric-Cole/dp/0470502495/ref=sr_1_43?ie=UTF8&qid=1315255956&sr=8-43)
Malware Analysts
 
[http://www.amazon.com/Malware-Analysts-Cookbook-DVD-Techniques/dp/0470613033/ref=sr_1_1?ie=UTF8&qid=1315256009&sr=8-1](http://www.amazon.com/Malware-Analysts-Cookbook-DVD-Techniques/dp/0470613033/ref=sr_1_1?ie=UTF8&qid=1315256009&sr=8-1)
 
Malware Fighting Malicious 
[http://www.amazon.com/Malware-Fighting-Malicious-Ed-Skoudis/dp/0131014056/ref=sr_1_4?ie=UTF8&qid=1315256009&sr=8-4](http://www.amazon.com/Malware-Fighting-Malicious-Ed-Skoudis/dp/0131014056/ref=sr_1_4?ie=UTF8&qid=1315256009&sr=8-4)
 
 
And millions more books I could get!!!
 
But I was looking for advice here for good book to start with.
 
 
So again for the billion time asking here what book will explain basic security .
 
 
Before you say what security I mean basic security.
 
--Understanding malware like virus ,worms ,trojans, scrips ,spyware ,adware so on. 
--How malware spreads and why we get malware
--how to lock down your computer
--understanding expliots and why computers get malware.
--Understanding OS and OS layers and things like UAC, Discretionary access control ,sandbox ,permissions ,ACLs ,MIC so on.
 
-- Understanding flash , javascript ,Java , script or active-x s so on and how to tighten this up in the OS.
 
--how a firewall works and why we need one.
-- how to secure the router.
-- Why OS get malware and why some OS more than others
--the basics.

I like the fact that you used bullet points... Have you considered just using those as google search terms and reading that instead of a book? Most of the information will be just as accurate and probably more current.

---


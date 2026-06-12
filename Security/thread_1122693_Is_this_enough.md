---
title: "Is this enough?"
date: 2009-04-11
forum: Security
---

### Post by mrnotsure on 2009-04-11
Hey guys I just installed Debian 5.0 Lenny and I am wondering if this is enough security. So far I have

Installed OSSEC-HIDS and made a startup script for it.
Activated SELinux
Firestarter Starts every time I boot
I scheduled a popup message reminder to tell me to scan with rkhunter once a week.

So what do you think? Can you guys recommend some more stuff for me or is this enough? Thanks!

---

### Post by FrankT-Qc on 2009-04-11
Well... for many setups, it's almost overshooting...

About SELinux, you'll have to do some profiling before it really hardens your installation.

About Firestarter, the fact that it runs is pretty much meaningless... What counts is the settings you put in there which are translated to Netfilter/iptables directives... If you're into it deep enough to learn SELinux, you might also want to drop Firestarter and use iptables directly.

Besides... Do you really need all that ?? (Well, if not, it's still fun playing with this stuff !)

---

### Post by mrnotsure on 2009-04-11
> **FrankT-Qc said:**
> Well... for many setups, it's almost overshooting...

About SELinux, you'll have to do some profiling before it really hardens your installation.

About Firestarter, the fact that it runs is pretty much meaningless... What counts is the settings you put in there which are translated to Netfilter/iptables directives... If you're into it deep enough to learn SELinux, you might also want to drop Firestarter and use iptables directly.

Besides... Do you really need all that ?? (Well, if not, it's still fun playing with this stuff !)To tell you the truth, I'm sorta a you know security freak lol. Also about the iptables configuration, I can say I use to do that a while back but man its hard to find any good iptables configurations out there so I thought I would use firestarter but now I'm not sure. If you can recommend me to a good iptables configuration I will appriciate it greatly:popcorn:;)!

Also if you can tell me more about this hardening I will be sure to check it out!

Edit: Also i'm reading on the SELinux Setup page and it says "If no critical audit errors appear in your syslog and you feel comfortable with SELinux, enable enforcing mode" I am a bit confused, how would I check for audit errors? What would they look like?

---

### Post by hyper_ch on 2009-04-11
if you're a security freak then you should first check out how the tools work and not blindly use them... I am of the opinion that you very likely don't need to bother with firestarter or iptables at all.

---

### Post by bodhi.zazen on 2009-04-11
> **hyper_ch said:**
> if you're a security freak then you should first check out how the tools work and not blindly use them... I am of the opinion that you very likely don't need to bother with firestarter or iptables at all.

+1  

These things are tools and by your posting style it seems you are installing them with lotle or no understanding of how they work or how to use them or even why you are using them.

First I suggest you do some reading. You can start here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Then [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

then read about selinux. I will refer you to the Debian forums for how selinux works on Debian. Ubuntu uses Apparmor and there is a stick at the top of these forums on how to use that.

Then read about OSSEC.

If you have ubuntu specific questions, come back and ask.

---

### Post by cwsnyder on 2009-04-11
If you are using a router, remember that it is likely a GNU/Linux based computer with a firewall installed, and don't forget to secure it, also.

If you really are a security freak, you can:
a) disconnect from the Internet entirely, or
b) at least lock down all ports not needed by your computer connecting to the Internet as a server for outside users.  If you are not acting as a web server, lock all outside ports, including not leaving bit-torrent ports open.

Don't forget clamav.

Also, _don't use root or sudo_ unless and until needed to install updates.  Don't have any other Internet facing applications open when installing updates.

Have I forgotten anything?):P

---

### Post by kponds on 2009-04-11
First step in determining if it is enough is to determine what it needs to be -- what exactly are you securing.

But I have seen servers which if compromised would have a loss expetancy in the multimillions that have less strong security products installed.

But the thing to remember is, IDS, rootkit detection, even firewalls, they do not give you security.  They enforce the security that you build and maintain.

Did you log into this forum with the same password that your sudoer has?  Do you run packages and scripts without validating them?  Do you have code executing processes which rely on remote code without authenticating the source?  If the answer to any of these is yes, you just completely invalidated your super-cool security products.

A wise man once said "Security is a process, not a product", and the truest and most misunderstood thing in all of security is that security products are the icing on the cake that you build out of secure computing practices.  Companies have wasted millions and millions of dollars trying to figure this one out.

---

### Post by mrnotsure on 2009-04-12
I have programmed a server for 5+ MMORPG's (I even helped blizzard a while back , just a little) and have setup and built servers for companys. I am not argueing, I just think you guys should stop assuming so fast that I have no clue what i'm doing. I have been using linux for quite some years, but as far as security goes I have not had time to manage any of my linux machines because I was using windows most of the time, most companys request me to use windows for odd reasons.

So why would I ask you guys about security if I have built many servers, its a simple answer, I have not enough experience in the linux security feild so I thought I'd drop by to ask what security measures should I take, etc.

And as far as reading goes, thats all I have been doing. I'm not going to post a topic asking for help if I haven't read up at all. I have been researching HIDS and NIDS and I know both those can be worthless if a proper iptables was not configured. And I do know you have to configure SELinux policy to make it have any effect, so far I'm having issues with that. I might move to APPARMOR for an alternative.

---

### Post by kponds on 2009-04-12
Ok.

> Is this enough?

Yes.


Better?

---

### Post by bodhi.zazen on 2009-04-12
> **FreezingHazard said:**
> I have programmed a server for 5+ MMORPG's (I even helped blizzard a while back , just a little) and have setup and built servers for companys. I am not argueing, I just think you guys should stop assuming so fast that I have no clue what i'm doing. I have been using linux for quite some years, but as far as security goes I have not had time to manage any of my linux machines because I was using windows most of the time, most companys request me to use windows for odd reasons.

So why would I ask you guys about security if I have built many servers, its a simple answer, I have not enough experience in the linux security feild so I thought I'd drop by to ask what security measures should I take, etc.

And as far as reading goes, thats all I have been doing. I'm not going to post a topic asking for help if I haven't read up at all. I have been researching HIDS and NIDS and I know both those can be worthless if a proper iptables was not configured. And I do know you have to configure SELinux policy to make it have any effect, so far I'm having issues with that. I might move to APPARMOR for an alternative.

To me it appears you are ranting at us.

If you want assistance please be more specific, What are you trying to secure ? A desktop ? A server ? What services are you running ?

Your set up is "over kill" for a desktop behind a router with no services running.

I have no idea what servers you are runing, your network architecture, or how you secured your server.

These things are all tools and we have no way to evaluate your question without specifics.

I am going to close this thread now as you question has been asked and answered. If you have a specific question feel free to ask.

---


---
title: "Why all Linux firewalls are snake oil (for desktop)"
date: 2006-12-04
forum: The Cafe
---

### Post by zetetic on 2006-12-04
In my opinion, Linux firewalls don't do much to protect your computer. As far as I know (please correct me if I'm wrong) they are all snake oil.

As far as I know (again correct me if there is out there a good firewall I haven't heard about) Linux firewalls don't allow you to setup application rules/outbound application filtering, only protocol rules!

The true is: without application level filtering, a firewall is almost useless. It doesn't protect you from trojan horses, keyloggers, spyware, backdoors, and so on.

The real protection is program-level control, so that only those applications you trust are allowed to access the Internet! Offcourse this requires cryptography signatures of all applications you allow internet access.

Such as Steve Gibson states, it is no longer true that all of the potential problems reside outside the computer. Your Internet connection flows both ways... so must your security.

Not only must our Internet connections be fortified to prevent external intrusion, firewalls must also provide secure management of INTERNAL EXTRUSION.

Any comprehensive security program must safeguard its owner by preventing Trojan horses, viruses, and spyware from using the system's Internet connection without the owner's knowledge. 

Scanning for the presence of Trojans, viruses, and spyware is important and effective, but if a piece of malware does get into your computer you want to expose it immediately by detecting its communication attempts and  cut it off from communication with its external agencies.

Most personal Windows software firewalls provide — or attempt to provide — application-based management and control of outbound Internet communications. Do I need to give examples? Ok, I give some: ZoneAlarm, NIS, Look 'n' Stop, Outpost, Kaspersky Anti-Hacker.

Linux firewalls, on the contrary, offer NO PROTECTION and control against the very real threat represented by outbound Trojan, virus, and spyware communications. They don't offer any application outbound control!

What's Wrong With these Linux firewalls?

- External Intrusion versus Internal Extrusion

It is good to have a firewall protecting your system from external intrusion, but the fact is, if you are not actively offering public access services, there's really not much an outsider can do to you.

However, the typical Internet user is under much greater threat from the malicious intent of programs which are inadvertently loaded into their machines. Trojan horses, eMail viruses, and Adware/Spyware are flying across the Internet with ever-increasing frequency and they are becoming much more clever. And, predictably, the latest ones have now become "firewall aware" and are using some simple tricks to penetrate personal firewalls!
Therefore, any truly useful firewall must be able to not only block external intrusion, but also INTERNAL EXTRUSION!

We need Linux firewalls which are able to give us application-based management and control of outbound Internet communications! And we need them now!

For Ubuntu users the risk will be even greater, cause Ubuntu will ship proprietary drivers by default... any binary driver can be spyware, a rootkitt or a trojan... (Lexmark drivers, for instance, and some Epson drivers, already phone home).

zetetic

---

### Post by tribaal on 2006-12-04
Maybe you should read a little more about the way security is handeled in Linux before making asumptions.

You should start [here]("http://www.psychocats.net/ubuntu/security"). While Asiu sais himself he's not a security expert, but he does have a gift for writing and explaining in layman's words.

- trib'

---

### Post by PriceChild on 2006-12-04
The linux kernel itself is a firewall.

Ubuntu has no open ports as default.

If you start an application up... be prepared for it to do whatever its programmed to, including openning up ports.
   - If you don't trust said application, don't open it.
- Programs can't "just start" in Linux... so you shouldn't worry about random things openning ports.

'nuf said.

---

### Post by zetetic on 2006-12-04
PriceChild said:

«If you don't trust said application, don't open it.»

This is the worst way of dealing with security one can imagine.

Security can't rely simple on the user not opening an apllication he doesn't trust.

If in order to get security all we need to do would be not opening applications we don't trust, even Windows would be a completely secure system.

The truth is: your way of dealing with security issues could only be effective if all users were good developpers and had the time to analise the source code of all Linux programs! Kind of impracticable.

The truth is: Linux is very secure and much secure then Windows when we are talking about external intrusion, but much less secure than Windows (with a good firewall such as Outpost, ZoneAlarm, etc) when we are talking about internal extrusion!

Who is the culprit for this situation? Linux snake oil firewalls...

And with the upcoming proprietary drivers by default, I predict a security nightmare for Ubuntu users.

zetetic

---

### Post by PriceChild on 2006-12-04
What I meant was... In my opinion you can trust everything you get from the standard Ubuntu repositories.

It "should" be secure when installed.

If you edit these programs, they may be unsecure.

If you add extra programs, from universe, 3rd party etc. you may be unsecure.

Don't run anything you're not sure about, but if you have Ubuntu installed then you should trust main.

---

### Post by tribaal on 2006-12-04
You seem to imply that a fair proportion of software calls home.
This is wrong.

As I said above, you also should sort ou the virus/malware thing - it's so improbable it hurts (only proof-of concept viruses exist, and with very little propagation ability).

What is your firewall supposed to protect you from, then?
And don't you think that of all Ubuntu/linux users, someone would eventually notice something is calling back home, and the security team would patch it (if open source) or remove it from the repos (the only plausible large scale distribution vector)?

Anyway, read a little (or a little more) about linux security, you'll see the way iptables work is far from being snake oil.

Cheers.

- trib'

EDIT: > Don't run anything you're not sure about, but if you have Ubuntu installed then you should trust main.
That's what I was trying to express, but I failed my "English written communication" roll... ;)

---

### Post by ice60 on 2006-12-04
netfilter/iptables is a great firewall :) it does all the stuff needed and it's not snake oil, you just need a front end for it. 

program-level control isn't anything to do with a firewall, that's just bloat FW makers have added to keep up with the jones. if you want that you should look into HIPS software.

here's a frontend you might like though :)
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

one of the popups
[http://tuxguardian.sourceforge.net/screenshot.png](http://tuxguardian.sourceforge.net/screenshot.png)

---

### Post by zetetic on 2006-12-04
PriceChild, tribaal and other friends:

Please don't think I'm trying to bash Linux. I simple love Linux and the fisrt day I've installed Linux was the last day I've ever used Windows! (and I was a Windows (and DOS) power user for more than 15 years...).

That said, I know Linux is very secure when we are talking about external intrusion. The problem is when we are dealing with internal extrusion.

The point is we do need firewalls capable of given protection against internal extrusion, by doing application outgoing control/filtering.

And I think we have the right (and the duty) of alerting people for this Linux security flaw.

The only reason this security flaw haven't already turned into a serious or dramatic flaw is because almost all Linux applications are open source... And so it's difficult for a malware application beeing much time out there without beeing detected by a developper that one day decides to scrutinize it.

But with the rising introduction of closed source software in Linux (such as the upcomming binary drivers in Ubuntu Feisty) the situation can dramatically change, and then we can face a security nigthmare (without really good Linux firewalls).

Zetetic

---

### Post by zetetic on 2006-12-04
Thanks for your reply ice60!

I will give those applications a try!

Nevertheless I think a good firewall should give both external intrusion protection and internal extrusion protection (traffic flows in both aways).

regards,
zetetic

---

### Post by kuja on 2006-12-04
I think this way of handling security is plenty good. You almost make it sound like people want to use these insecure applications. So long as the mainstay of a persons software is provided by the vendor (read as: ubuntu) you don't really have anything to worry about. I'm confident that the Ubuntu devs will look out for our security now and in the future.

---

### Post by RMorris78 on 2006-12-04
if you use firestarter, you can set rules for incoming and outgoing traffic.

---

### Post by xhaan on 2006-12-04
> **zetetic said:**
> [...]

First, you're using the "snake oil" term incorrectly. Even if iptables didn't have application based control, it is still very good at everything else it does and is therefore not "snake oil".

Second, iptables DOES have application based filtering if you have the owner match extension, and even better, it can match UID, GID, PID and SID. You could deny everything from getting out except what you want to use.

---

### Post by PriceChild on 2006-12-04
Install firestarter, set it up to block everything but your whitelist and add things where necessary...

If you really want to.

I repeat my point. If you don't trust software like nvidia binary drivers and think they'll "call home" THEN DON'T INSTALL THEM.

---

### Post by zetetic on 2006-12-04
RMorris78's said:

«if you use firestarter, you can set rules for incoming and outgoing traffic.»

Did you read my posts? I'm talking about application outbound filtering/control, not about protocol/ports outbound control. Firestarter only has rules for protocols/ports, not for applications. There are a bunch of security articles written by security experts on the web, so please read them.

Protocol/ports control is snake oil... every malware application can use any port... It's crazy to open a port for every application that decides to use it.

zetetic

zetetic

---

### Post by ciscosurfer on 2006-12-04
> **zetetic said:**
> RMorris78's said:

«if you use firestarter, you can set rules for incoming and outgoing traffic.»

Did you read my posts? I'm talking about application outbound filtering/control, not about protocol/ports outbound control. Firestarter only has rules for protocols/ports, not for applications. There are a bunch of security articles written by security experts on the web, so please read them.

Protocol/ports control is snake oil... every malware application can use any port... It's crazy to open a port for every application that decides to use it.

zetetic

zeteticI hear your concerns, but others have already posted links that should help you out.  See xhaan's post; see ice60's post.

If you really want true (read: better) security, buy a consumer hardware firewall (incidentally, many of them use a modified Linux kernel) or better yet, a really expensive one from Cisco :-).

There's really nothing snake oily about Linux firewalls -- it's how you use and implement them that make them effective.  Also of note, is that they've been a part of Linux for a while in many forms: ipfwadm, ipchains, iptables.  Notice also that Firestarter and TuxGuardian are merely GUI front-ends to said applications.

---

### Post by Tomosaur on 2006-12-04
> **zetetic said:**
> PriceChild said:

«If you don't trust said application, don't open it.»

This is the worst way of dealing with security one can imagine.


Actually, that's probably the best way of handling security, aside from mandatory virus checks and whatnot. The only way you're going to get malware arsing around on your computer is through something far more pervading than a process starting itself up. It's going to need to hook into a different application in order for it to do what it wants to do, and if it succeeded in doing that, then your firewall would be useless anyway. You're safe, chill out.

---

### Post by zetetic on 2006-12-04
xhaan wrote:

«Second, iptables DOES have application based filtering if you have the owner match extension».

Could you please ellaborate on that, or give further information?

Or are you talking abot manually creating/editing iptables? The vast majority off Ubuntu users (or of almost anyother Linux distro) don't have the knowledge (nor the time or patience) required to manually edit/create iptable rules.

So we really need a front-end application capable of protecting against internal extrusion, with application oubound filtering/rules.

zetetic

---

### Post by ciscosurfer on 2006-12-04
@zetetic,

Out of curiosity, can you describe when the events you speak of have personally effected your computer and what happened when they did?
  
I was going to say: If you're that paranoid, maybe you shouldn't use your computer at all...go watch a movie or something.  Ooops.  I said it.  Don't take offense now, I'm only playing around :-).

---

### Post by zetetic on 2006-12-04
PriceChild wrote:

«If you don't trust software like nvidia binary drivers and think they'll "call home" THEN DON'T INSTALL THEM.»

Well, Ubuntu Feisty will install binary video drivers by default... 
So I will not be allowed to not install them!...

So Ubuntu Feisty has the potential to be a security/privacy nightmare (at least for the vast majority of its users, cause almost everybody uses ATI or Nvidia graphics cards)...

zetetic

---

### Post by Tomosaur on 2006-12-04
> **zetetic said:**
> PriceChild wrote:

«If you don't trust software like nvidia binary drivers and think they'll "call home" THEN DON'T INSTALL THEM.»

Well, Ubuntu Feisty will install binary video drivers by default... 
So I will not be allowed to not install them!...

So Ubuntu Feisty has the potential to be a security/privacy nightmare (at least for the vast majority of its users, cause almost everybody uses ATI or Nvidia graphics cards)...

zetetic

Nobody is forcing you to use Feisty. If you don't agree with the direction Feisty is taking, then by all means stick with Dapper or Edgy or whatever you're running now.

---

### Post by zetetic on 2006-12-04
ciscosurfer wrote:

«If you really want true (read: better) security, buy a consumer hardware firewall».

Hardware firewalls are completely blind. They only offer good protection for external intrusion. They are not able to give application outbound control/filtering. Once you open one port you open it for any application/malware that decides to use thar port.

If you really want to know something about hardware firewalls go (for instance) to grc.com.

zetetic

---

### Post by ciscosurfer on 2006-12-04
> **zetetic said:**
> ciscosurfer wrote:

«If you really want true (read: better) security, buy a consumer hardware firewall».

Hardware firewalls are completely blind. They only offer good protection for external intrusion. They are not able to give application outbound control/filtering. Once you open one port you open it for any application/malware that decides to use thar port.Right.  That must be why the Fortune 500 uses them.  And why I've never had any trouble using mine.> If you really want to know something about hardware firewalls go (for instance) to grc.com.If *you* really want to know about hardware firewalls, get a degree in computer science or information technology, grab some well-known and industry-recognized security certificates and become a security admin.  My real-world experience can back this up.  Or I suppose you can just read some good documentation on it and then get back to me.  The security hardware available these days works quite well and does their job quite well...application and port control, both inbound and outbound can be effectively mitigated.

[And while I do applaud Steve Gibson, he's not the end-all and be-all of information security knowledge]("http://www.grcsucks.com/").  His podcasts are good though :D.  And I like his Shields UP!! web app.

@Tomosaur, 

> Nobody is forcing you to use Feisty. If you don't agree with the direction Feisty is taking, then by all means stick with Dapper or Edgy or whatever you're running now.Good post my good man!

---

### Post by zetetic on 2006-12-04
ciscosurfer wrote:

«Out of curiosity, can you describe when the events you speak of have personally effected your computer and what happened when they did?»

Do a search on these forums (and on google) and you will see how much people had their systems compromized by trojans and rootkits.

I'm only using Linux since about 6 weeks... But do you really thinks that rootkits, trojans, or other kind of malware inform the victim that he is beeing hacked??

Virus and ad-ware are different animals, because they are destructive or because (in the later case) they exist to be visible.

But trojans, spyware and rootkits are mainly ways of stealing/compromising privacy. They make everyting they can to remain undetected.

I'm not paranoid. But I think you are naif or don't give a sh** to your privacy (don't take offense now, I'm also playing around).

zetetic

---

### Post by ciscosurfer on 2006-12-04
> **zetetic said:**
> ciscosurfer wrote:

«Out of curiosity, can you describe when the events you speak of have personally effected your computer and what happened when they did?»

Do a search on these forums (and on google) and you will see how much people had their systems compromized by trojans and rootkits.

I'm only using Linux since about 6 weeks... But do you really thinks that rootkits, trojans, or other kind of malware inform the victim that he is beeing hacked??

Virus and ad-ware are different animals, because they are destructive or because (in the later case) they exist to be visible.

But trojans, spyware and rootkits are mainly ways of stealing/compromising privacy. They make everyting they can to remain undetected.

I'm not paranoid. But I think you are naif or don't give a sh** to your privacy (don't take offense now, I'm also playing around).

zeteticHahahah. :lol::lol::lol:  I really was just poking fun, but apparently you are not.

I'm not naive, and I do give a spit: I run Ubuntu ;)

---

### Post by xhaan on 2006-12-04
> **zetetic said:**
> xhaan wrote:

«Second, iptables DOES have application based filtering if you have the owner match extension».

Could you please ellaborate on that, or give further information?

Or are you talking abot manually creating/editing iptables? The vast majority off Ubuntu users (or of almost anyother Linux distro) don't have the knowledge (nor the time or patience) required to manually edit/create iptable rules.

So we really need a front-end application capable of protecting against internal extrusion, with application oubound filtering/rules.

zetetic

Owner match is an extension to iptables which is in the kernel. I think it's already compiled in for Ubuntu.

I've never really used frontends for iptables so I don't know if there's one that handles owner match, though to filter a PID reliably you'd make a small script that greps the PID of the process you want to allow or block, sticks it in a variable and then makes a rule with it.

iptables itself is pretty powerful, I don't like the frontends for it though so I don't use them.

---

### Post by ciscosurfer on 2006-12-04
> [...]Do a search on these forums (and on google) and you will see how much people had their systems compromized by trojans and rootkits.[...]The question now becomes: what on Earth sort of software are you installing onto your machine?  Trojans and rootkits are real threats, but they are so minimal (so far) in the *nix realm, that it's nearly laughable.

If you don't know where the software comes from or don't trust it, DON'T INSTALL IT.

Common sense and a little trust goes a long way (and by 'trust' I mean from official sources)...can something sneak its way in somehow, I suppose.  But that happens so very rarely, if ever -- I've never heard of such a case.

Security is about making informed descisions and being an empowered user (or admin).  If you feel that Ubuntu is not safe for you, then don't use it.

Let's not bicker zetetic.  Let's try to have a civil discourse.  I will admit that I came across a little harsh.  And for this, I apologize (sincerely).  Sometimes it is easy to "lash out" (by lashing out, I'm referring to what I have said so far in my posts), but that's no excuse, just an explanation.

---

### Post by darkhatter on 2006-12-04
> **zetetic said:**
> In my opinion, Linux firewalls don't do much to protect your computer. As far as I know (please correct me if I'm wrong) they are all snake oil.

As far as I know (again correct me if there is out there a good firewall I haven't heard about) Linux firewalls don't allow you to setup application rules/outbound application filtering, only protocol rules!

The true is: without application level filtering, a firewall is almost useless. It doesn't protect you from trojan horses, keyloggers, spyware, backdoors, and so on.

The real protection is program-level control, so that only those applications you trust are allowed to access the Internet! Offcourse this requires cryptography signatures of all applications you allow internet access.

Such as Steve Gibson states, it is no longer true that all of the potential problems reside outside the computer. Your Internet connection flows both ways... so must your security.

Not only must our Internet connections be fortified to prevent external intrusion, firewalls must also provide secure management of INTERNAL EXTRUSION.

Any comprehensive security program must safeguard its owner by preventing Trojan horses, viruses, and spyware from using the system's Internet connection without the owner's knowledge. 

Scanning for the presence of Trojans, viruses, and spyware is important and effective, but if a piece of malware does get into your computer you want to expose it immediately by detecting its communication attempts and  cut it off from communication with its external agencies.

Most personal Windows software firewalls provide — or attempt to provide — application-based management and control of outbound Internet communications. Do I need to give examples? Ok, I give some: ZoneAlarm, NIS, Look 'n' Stop, Outpost, Kaspersky Anti-Hacker.

Linux firewalls, on the contrary, offer NO PROTECTION and control against the very real threat represented by outbound Trojan, virus, and spyware communications. They don't offer any application outbound control!

What's Wrong With these Linux firewalls?

- External Intrusion versus Internal Extrusion

It is good to have a firewall protecting your system from external intrusion, but the fact is, if you are not actively offering public access services, there's really not much an outsider can do to you.

However, the typical Internet user is under much greater threat from the malicious intent of programs which are inadvertently loaded into their machines. Trojan horses, eMail viruses, and Adware/Spyware are flying across the Internet with ever-increasing frequency and they are becoming much more clever. And, predictably, the latest ones have now become "firewall aware" and are using some simple tricks to penetrate personal firewalls!
Therefore, any truly useful firewall must be able to not only block external intrusion, but also INTERNAL EXTRUSION!

We need Linux firewalls which are able to give us application-based management and control of outbound Internet communications! And we need them now!

For Ubuntu users the risk will be even greater, cause Ubuntu will ship proprietary drivers by default... any binary driver can be spyware, a rootkitt or a trojan... (Lexmark drivers, for instance, and some Epson drivers, already phone home).

zetetic

I'm going to say this once. your I.S.P. knows every single thing that you do online. the second you plug your network card in or you wireless card, you can be watched. If you are that scared, I suggest you unplug your computer.

---

### Post by Henry Rayker on 2006-12-04
> **zetetic said:**
> Do a search on these forums (and on google) and you will see how much people had their systems compromized by trojans and rootkits.

I just did...well, just on these forums...and I can't find anyone who has had an Ubuntu system (truly) compromized by trojans or rootkits. I found a couple false-positives and a couple people who thought they had a trojan because their mouse was jumpy (turned out to be a GNOME problem). Your credibility just went out the window.

Unless you can point me to a thread I overlooked, I would like to assert that you are pulling facts out of your ***.

---

### Post by ciscosurfer on 2006-12-04
> **darkhatter said:**
> I'm going to say this once. your I.S.P. knows every single thing that you do online. the second you plug your network card in or you wireless card, you can be watched. If you are that scared, I suggest you unplug your computer.darkhatter is watching us! *scary_music_plays_in_background*

Do you work for an ISP?  And you are correct about your assertions in terms of monitoring, etc.

---

### Post by ZylGadis on 2006-12-04
zetetic, I may sound like an elitist here, but you should really read some stuff before making ridiculous assumptions. I will say this just once: **GNU/Linux is not Windows, and it should not be.**

Configure iptables successfully (if you can) and if you still think like you do, take a damn course on TCP/IP networking and another one on *nix processes.

This is what comes with bringing a hacker's OS to the (Windows-infected) masses. Gosh.

---

### Post by addicted68098 on 2006-12-04
Having an external firewall has been very nice (mostly because Windows sucks), the only likely threat is someone picking you out of the crowd to hack,

---

### Post by kakalaky on 2006-12-04
Yeah, all those windows firewalls are so much more secure since you allow ie in the firewall and other programs can use ie to start a connection.

---

### Post by zetetic on 2006-12-04
kakalaky said:

«Yeah, all those windows firewalls are so much more secure since you allow ie in the firewall and other programs can use ie to start a connection.»

I've never allowed internet explorer on the firewall. But that doesn't matter anyway. It's pretty obvious you've never heard about application control, memory space protection, process control, and so on...

Have you ever heard about programs like Processguard, for instance?

You also don't know what a leaktest if and what you can do to be protected against those king of attacks.

It seems it's almost impossible to protect a Linux system the way you can (try to) protect a Windows machine.

The problem with windows is that almost all security applications are closed source, and also the operating system is closed source. So you have to trust a buch of software, starting with Microsoft crap.

zetetic

---

### Post by kakalaky on 2006-12-04
I know about all that.  Unfortunately half of the people coding firewalls haven't and they fail leak tests.

Edit:  Examples here - [http://www.firewallleaktester.com/termination.php]("http://www.firewallleaktester.com/termination.php")

---

### Post by 23meg on 2006-12-04
*waits eagerly for LordHunter317 to drop in*

---

### Post by zetetic on 2006-12-04
darkhater wrote:

«I'm going to say this once. your I.S.P. knows every single thing that you do online.»

You are totally missing the point here. Nevertheless I can assure you there are apllications that will prevent your ISP to know what are you doing online.

Programs like JAP.

Don't we have applications like that on Linux? If this is true, then too bad for Linux... Windows wins here hands down.

zetetic

---

### Post by kebes on 2006-12-04
I feel like this thread is getting a little bit out of hand. I think we are all agreeing that Ubuntu, by default, is very secure. The kernel-level firewalling will block un-requested access. Also, if you only use software from Ubuntu repositories, it's very unlikely that you'll ever get a virus/trojan/rootkit/malware/etc.

That having been said, I think the points zetetic brings up are interesting. So allow me to re-phrase his question in another way:

Suppose there is an application that you want to run, but you don't want it to have access to the network. How would you block that application from accessing the network?[1] (You might want to do this if an application has some bug but is otherwise not malicious, or perhaps for testing, ...)

This is an honest question (related to zetetic's original point). Does anyone know how this would be done? (Or is there perhaps an easy way to launch an application in a sandbox?)


[1] It was mentioned that you can add the PID to iptables. Presumably this means creating a wrapper script that adds the PID everytime the application runs? (And then only using this script to launch the application.) Is there a way to make such a change permanent?

---

### Post by PriceChild on 2006-12-04
> **zetetic said:**
> darkhater wrote:

«I'm going to say this once. your I.S.P. knows every single thing that you do online.»

You are totally missing the point here. Nevertheless I can assure you there are apllications that will prevent your ISP to know what are you doing online.

Programs like JAP.

Don't we have applications like that on Linux? If this is true, then too bad for Linux... Windows wins here hands down.

zeteticI don't know what JAP is... but if they want to... they can find out what they're doing...

Heck.. if i reeeeeaaalllyyyy wanted to... I could probably find out what you're doing on the net right now... in 2 seconds I already have your IP address!

Again... If you don't trust it, don't use it... its the only 100% safe and guaranteed way.

---

### Post by ssam on 2006-12-04
one problem with application based firewalls.

it is quite common for scripts to call other programs to do work. many scripts use ```
wget
``` to receive (and send using HTTP GET and POST) data.
if you firewall blocked ```
wget
``` many things would break.
if you allow ```
wget
``` then a malicious program can use it.

this extends further. if you allow firefox to connect to the web then i can give you a malicious firefox extension. if apt-get/synaptic etc can connect then maybe i can fiddle with your source.list. if i have root on your machine, i could just turn your firewall off.

Until [RFC 3514]("http://www.faqs.org/rfcs/rfc3514.html") is universally implemented no firewall will be perfect.

---

### Post by zetetic on 2006-12-04
kakalaky wrote:

«I know about all that. Unfortunately half of the people coding firewalls haven't and they fail leak tests.»

I can assure you my windows machine passed ALL firewall leaktests!

I can be a little bit polemic, but trust me, I'm not a lier.

It's only a matter of getting a good firewall, leraning how to configure it properly. disabling a bunch of unecessary windows services and installing 1 or 2 good application firewalling/host intrusion detection programs (like GhostSecurity, Processguard, etc.).

Linux kernel is very secure, but it's not perfect. And Linux security applications have a long way to go if they want to be as good as some Windows applications. A long way indeed... Starting with firewalls and ending on anti-virus/anti-malware...

cheers,
zetetic

---

### Post by PriceChild on 2006-12-04
> **zetetic said:**
> I can assure you my windows machine passed ALL firewall leaktests!Did it now...

Have you tried the same test on a standard ubuntu box... and then one that you've messed with.

---

### Post by Henry Rayker on 2006-12-04
I don't think I much care whether or not Windows XP has more developed anti-virus applications...they need them because their core system is so weak...Linux possessing antivirus software that robust would be like having air conditioners in Antarctica.

You still haven't refuted my claim a page back. You claimed a search of this forum (as well as google) would turn up many users whose systems have been compromised by trojans/rootkits. I searched these forums (reading every first post in a search for virus as well as in a search for rootkit...then reading more of the thread when it was actually about the prospect of being infected through to resolution.) I found zero users who genuinely were posting about contracting a trojan or a rootkit requesting assistance. I found a couple cases of a false-positive as well as one person whose GNOME configuration was borked and the mouse was moving around randomly.

You made a claim without backing it up; I've called you out on that claim.

---

### Post by 23meg on 2006-12-04
> Don't we have applications like that on Linux? If this is true, then too bad for Linux... Windows wins here hands down.Check out Tor.

---

### Post by Virogenesis on 2006-12-04
1. Most sites contain an md5 sum, so you can infact check if the program is tainted or not.
2. Linux isn't windows, security is handled alot differently, windows has alot of problems dealing with security but alot are also down to the user.
This cannot be stopped.
3. Malware is locked into your home dir, any damage that takes places inside your home dir will not affect other uses on the system.
4. Steve Gibson is considered a joke by many black hats, 
5. A hardware firewall is a better solution, to any software based firewalls. 
[B]
Linux kernel is very secure, but it's not perfect. And Linux security applications have a long way to go if they want to be as good as some Windows applications. A long way indeed... Starting with firewalls and ending on anti-virus/anti-malware..[/B].
ermmm how often is windows patched? linux gets patched constantly.

Now please stop with this flamebait

---

### Post by Tomosaur on 2006-12-04
> **zetetic said:**
> kakalaky wrote:

«I know about all that. Unfortunately half of the people coding firewalls haven't and they fail leak tests.»

I can assure you my windows machine passed ALL firewall leaktests!

I can be a little bit polemic, but trust me, I'm not a lier.

It's only a matter of getting a good firewall, leraning how to configure it properly. disabling a bunch of unecessary windows services and installing 1 or 2 good application firewalling/host intrusion detection programs (like GhostSecurity, Processguard, etc.).

Linux kernel is very secure, but it's not perfect. And Linux security applications have a long way to go if they want to be as good as some Windows applications. A long way indeed... Starting with firewalls and ending on anti-virus/anti-malware...

cheers,
zetetic

You're missing the point. Linux does not NEED the features that windows security programs have. We don't suffer from the same vulnerabilities as Windows, which means that virtually the ONLY WAY you are going to suffer from viruses / malware is through YOUR OWN STUPIDITY.

---

### Post by PriceChild on 2006-12-04
I am closing this thread after discussion and agreement with other members of the staff team.

---

### Post by zetetic on 2006-12-04
Sorry for introducing this issue again. But it seems there are some people here that don't believe in free speech. That's why they are closing thread after thread without any reason for that.

If you think nobody can criticize Ubuntu or nobody can point security flaws or any other kind of flaws, you are wrong.

Maybe those "moderators" should work for Pravda (on former soviet union) but not for a Linux Forum.

I also want to assure you one thing: No dictator will be able to shut my mouth and refrain me telling people the true about the issues I decide to discuss.

I believe in free speech and if some dictators think they can stop me for discussing things they are wrong.

So here it goes:

In my opinion, Linux firewalls don't do much to protect your computer. As far as I know (please correct me if I'm wrong) they are all snake oil.

As far as I know (again correct me if there is out there a good firewall I haven't heard about) Linux firewalls don't allow you to setup application rules/outbound application filtering, only protocol rules!

The true is: without application level filtering, a firewall is almost useless. It doesn't protect you from trojan horses, keyloggers, spyware, backdoors, and so on.

The real protection is program-level control, so that only those applications you trust are allowed to access the Internet! Offcourse this requires cryptography signatures of all applications you allow internet access.

Such as Steve Gibson states, it is no longer true that all of the potential problems reside outside the computer. Your Internet connection flows both ways... so must your security.

Not only must our Internet connections be fortified to prevent external intrusion, firewalls must also provide secure management of INTERNAL EXTRUSION.

Any comprehensive security program must safeguard its owner by preventing Trojan horses, viruses, and spyware from using the system's Internet connection without the owner's knowledge.

Scanning for the presence of Trojans, viruses, and spyware is important and effective, but if a piece of malware does get into your computer you want to expose it immediately by detecting its communication attempts and cut it off from communication with its external agencies.

Most personal Windows software firewalls provide — or attempt to provide — application-based management and control of outbound Internet communications. Do I need to give examples? Ok, I give some: ZoneAlarm, NIS, Look 'n' Stop, Outpost, Kaspersky Anti-Hacker.

Linux firewalls, on the contrary, offer NO PROTECTION and control against the very real threat represented by outbound Trojan, virus, and spyware communications. They don't offer any application outbound control!

What's Wrong With these Linux firewalls?

- External Intrusion versus Internal Extrusion

It is good to have a firewall protecting your system from external intrusion, but the fact is, if you are not actively offering public access services, there's really not much an outsider can do to you.

However, the typical Internet user is under much greater threat from the malicious intent of programs which are inadvertently loaded into their machines. Trojan horses, eMail viruses, and Adware/Spyware are flying across the Internet with ever-increasing frequency and they are becoming much more clever. And, predictably, the latest ones have now become "firewall aware" and are using some simple tricks to penetrate personal firewalls!
Therefore, any truly useful firewall must be able to not only block external intrusion, but also INTERNAL EXTRUSION!

We need Linux firewalls which are able to give us application-based management and control of outbound Internet communications! And we need them now!

For Ubuntu users the risk will be even greater, cause Ubuntu will ship proprietary drivers by default... any binary driver can be spyware, a rootkitt or a trojan... (Lexmark drivers, for instance, and some Epson drivers, already phone home).

zetetic

---

### Post by tribaal on 2006-12-04
Please don't be a [troll]("http://en.wikipedia.org/wiki/Troll_%28Internet%29"). Thank you.

- trib'

EDIT: Anticipating your logical answer, Here's why your threads most certainly have been closed:

> As far as I know (please correct me if I'm wrong) they are all snake oil.

Well we did, yet you keep bringing up the subject...
Ok, I'll stop feeding the trolls now.

---

### Post by d3v1ant_0n3 on 2006-12-04
zetetic: Your other thread was probably closed for a reason. It certainly looked like flamebait to me, as do many of your posts that I've seen.

May I possibly suggest asking the mod who closed your other thread why it was done, rather than starting a new one, that will no doubt end up being closed also?

---

### Post by 23meg on 2006-12-04
You've been given at least two serious counter arguments, neither of which you've refuted. The first is the existence of the owner match extension for iptables, and the second is the fact that virtually nobody on these forums (or even virtually nobody using a desktop Linux OS) has suffered from any malware issues as a result of firewall shortcomings, as opposed to what you stated. 

You seem so sure of your argument that there isn't much to discuss with you. If you care to genuinely respond to others who raise arguments against yours instead of defending yours to death without any serious backing, you'll be taken more seriously and your threads won't be locked; the custom here is to lock threads that lead nowhere but bashing / trolling / flaming.

---

### Post by Daveski on 2006-12-04
This interests me. I have not searched for application level personal firewalls in Linux yet, but I do use Kerio Personal Firewall on my Windows machine which I think is excellent. What are other people's opinions on this? Can anyone point to this type of security application under Ubuntu / Linux?

I do not think this is trolling - or if it is, I would still be very interested in the thoughts of anyone who bites.

---

### Post by tribaal on 2006-12-04
His post has been debated ad nauseum [here]("http://ubuntuforums.org/showthread.php?t=312464").

Ubuntu comes with a very potent firewall built-in, you can find more info [here]("http://www.psychocats.net/ubuntu/security") and [here]("https://help.ubuntu.com/community/Security").

Hope this helps :)

- trib'

---

### Post by Daveski on 2006-12-04
> **tribaal said:**
> Hope this helps :)

- trib'

Certainly does. Thanks.

---

### Post by ciscosurfer on 2006-12-04
> **zetetic said:**
> Sorry for introducing this issue again. But it seems there are some people here that don't believe in free speech. That's why they are closing thread after thread without any reason for that.

If you think nobody can criticize Ubuntu or nobody can point security flaws or any other kind of flaws, you are wrong.

Maybe those "moderators" should work for Pravda (on former soviet union) but not for a Linux Forum.

I also want to assure you one thing: No dictator will be able to shut my mouth and refrain me telling people the true about the issues I decide to discuss.

I believe in free speech and if some dictators think they can stop me for discussing things they are wrong.

So here it goes:

In my opinion, Linux firewalls don't do much to protect your computer. As far as I know (please correct me if I'm wrong) they are all snake oil.

As far as I know (again correct me if there is out there a good firewall I haven't heard about) Linux firewalls don't allow you to setup application rules/outbound application filtering, only protocol rules!

The true is: without application level filtering, a firewall is almost useless. It doesn't protect you from trojan horses, keyloggers, spyware, backdoors, and so on.

The real protection is program-level control, so that only those applications you trust are allowed to access the Internet! Offcourse this requires cryptography signatures of all applications you allow internet access.

Such as Steve Gibson states, it is no longer true that all of the potential problems reside outside the computer. Your Internet connection flows both ways... so must your security.

Not only must our Internet connections be fortified to prevent external intrusion, firewalls must also provide secure management of INTERNAL EXTRUSION.

Any comprehensive security program must safeguard its owner by preventing Trojan horses, viruses, and spyware from using the system's Internet connection without the owner's knowledge.

Scanning for the presence of Trojans, viruses, and spyware is important and effective, but if a piece of malware does get into your computer you want to expose it immediately by detecting its communication attempts and cut it off from communication with its external agencies.

Most personal Windows software firewalls provide — or attempt to provide — application-based management and control of outbound Internet communications. Do I need to give examples? Ok, I give some: ZoneAlarm, NIS, Look 'n' Stop, Outpost, Kaspersky Anti-Hacker.

Linux firewalls, on the contrary, offer NO PROTECTION and control against the very real threat represented by outbound Trojan, virus, and spyware communications. They don't offer any application outbound control!

What's Wrong With these Linux firewalls?

- External Intrusion versus Internal Extrusion

It is good to have a firewall protecting your system from external intrusion, but the fact is, if you are not actively offering public access services, there's really not much an outsider can do to you.

However, the typical Internet user is under much greater threat from the malicious intent of programs which are inadvertently loaded into their machines. Trojan horses, eMail viruses, and Adware/Spyware are flying across the Internet with ever-increasing frequency and they are becoming much more clever. And, predictably, the latest ones have now become "firewall aware" and are using some simple tricks to penetrate personal firewalls!
Therefore, any truly useful firewall must be able to not only block external intrusion, but also INTERNAL EXTRUSION!

We need Linux firewalls which are able to give us application-based management and control of outbound Internet communications! And we need them now!

For Ubuntu users the risk will be even greater, cause Ubuntu will ship proprietary drivers by default... any binary driver can be spyware, a rootkitt or a trojan... (Lexmark drivers, for instance, and some Epson drivers, already phone home).

zeteticAh sheesh zetetic! ](*,)  Could it be possible that the admins are closing these threads possibly because you are inciting hostility?  No one here disagrees with you regarding free speech.  Afterall, free speech, open source, etc. are all values that I'm sure many, many of us here completely agree with, aim for, aspire to, etc.  It's the **tone** that you are using when you post that is creating such controversy.  Is discussion good?  You bet.  Are free thinking, free thought, free will (and whatnot) good for debate?  Sure they are.  But you are not taking into account other points of view, other stances, other opinions...it's "your way or the highway" and many of us here take that as a sign of arrogance and haughtiness.  I mean I'm seriously puzzled why you won't accept others' opinions on topics...you clearly state in the beginning of this thread as well as others I have read by you that you would like to be corrected if you are wrong> [...]As far as I know (please correct me if I'm wrong) they are all snake oil.[...]so we offer up other ideas, ourselves being free thinkers like you, but we get shot down as if our own opinions (and sometimes substantiated facts) are incorrect, irresponsibly rhetorted, or otherwise amiss.  Free discussion is one of the qualities that makes Ubuntu Forums such a fantastic place to post.  And in the spirit of the Forums, a certain level of respect for one another, and a modicum of deference should be observed for others' thoughts, feelings, opinions, and (in some cases) tested and expert advice.  Please continue to post on the forums, but please do it in a way where you aren't bashing forum posters left and right.  

Debate is good.  Discussion is good.  Please try to adhere to the "humanity for others" Ubuntu slogan.  Do we sometimes slip up and make comments that we regret?  Of course we do, we're only human.  It's when we go on tirades, rants, and raves when our opinions usually get left in the dust and certain other opinions are forged based on those actions.

---

### Post by tageiru on 2006-12-04
> **zetetic said:**
> As far as I know (again correct me if there is out there a good firewall I haven't heard about) Linux firewalls don't allow you to setup application rules/outbound application filtering, only protocol rules!

Well, how about you start implementing it?

Just don't make the same mistake most Window firewall vendors do, relying on the user to make a destinction between friendly and unfriendly applications, because that is the real snake oil, users will press 'ok' regardless.

Perhaps something similar to SELinux with pre-defined rules is a good way to solve this.

---

### Post by 23meg on 2006-12-04
> **tageiru said:**
> Well, how about you start implementing it?
It's already implemented, in the form of the owner match extension and some other patches. Frontends such as Fireflier also support per application filtering.

---

### Post by PriceChild on 2006-12-04
To clarify, I closed the tread earlier because of the "flamebait" ideas which other members had already pointed out.

The original poster WAS informed... yet still decided to post this copy.

I have been backed up by 3 moderators and 2 administrators on this issue.

End of.

---


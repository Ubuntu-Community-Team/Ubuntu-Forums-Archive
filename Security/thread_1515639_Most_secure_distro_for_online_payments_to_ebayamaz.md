---
title: "Most secure distro for online payments to ebay/amazon"
date: 2010-06-22
forum: Security
---

### Post by Ulysses_ on 2010-06-22
Currently using linux mint. While it's nice I have the feeling all those bells and whistles must be exposing a large attack surface. 

What is the most secure distro known to man, but which is still capable of making payments to amazon and ebay?

---

### Post by ajgreeny on 2010-06-22
I suspect that distro would be so locked down that you would never want to use it.

Just make sure that you have a fully updated system and also that all the standard warnings are followed, ie. it is an https site etc etc, and everything should be fine.  I know of at least one person who normally runs Windows of one sort or another who has a Linux OS as well solely for on-line banking, as he is not prepared to do it with Windows.  The Linux he uses is, surprise, surprise, Ubuntu.

Is he paranoid?  I don't know, but it says something about our favourite OS, I think.

---

### Post by Ulysses_ on 2010-06-22
> **ajgreeny said:**
> I suspect that distro would be so locked down that you would never want to use it.

I do not want to use it for day to day tasks, mint is for those.  I only want it once every couple of months, just to make a payment and that's it.

> Just make sure that you have a fully updated system and also that all the standard warnings are followed, ie. it is an https site etc etc

Thanks for the input but I disagree with this.  I hope you do not mind.  People you see posting questions here may have more experience that it appears at first sight.

---

### Post by bodhi.zazen on 2010-06-22
See this discussion

[http://ubuntuforums.org/showpost.php?p=9459358&postcount=4](http://ubuntuforums.org/showpost.php?p=9459358&postcount=4)

---

### Post by partsdale on 2010-06-22
What about paypal?

---

### Post by Ulysses_ on 2010-06-22
Forgot that. Yes, paypal too.

---

### Post by Ulysses_ on 2010-06-22
> **bodhi.zazen said:**
> See this discussion

[http://ubuntuforums.org/showpost.php?p=9459358&postcount=4](http://ubuntuforums.org/showpost.php?p=9459358&postcount=4)

Thanks, I would add "use a good vpn".  But still there are so many features in ubuntu that make a large attack surface for vulnerability researchers.  I don't want instant messaging for example, in the virtual machine I use for paying online, once every two months.

---

### Post by OpSecShellshock on 2010-06-22
It makes more sense to start by examining the conditions under which online monetary transactions are dangerous than to try to find the way that's the most safe. Even Windows is perfectly fine as long as it doesn't have a data-stealing trojan, a DNS-hijacking trojan, some kind of messed up browser plug-in, or a corrupted hosts file or something. For the most part, a fresh install of anything with up-to-date software and a least-privilege-necessary user account that's on a wired connection behind a hardware firewall with no ports forwarded and UPnP disabled should be fine. I still wouldn't personally use Windows or OSX if there were other options available, simply because there could be unnecessary services and processes running by default that, even if not precisely vulnerable, still make me uneasy because I can't explain them.

Mostly, it's not the OS, but the applications and users who create the risk of personal data loss. Um, so long as the payee in this scenario doesn't get breached. I would say that if you don't have access to a wired connection, or if the wireless access point/router is not under your own administrative control, just don't do anything sensitive using a computer and the internet.

---

### Post by Ulysses_ on 2010-06-22
Returning to the topic, hasn't anyone seen a security-oriented distro?  

None that claims to be more secure than default ubuntu?  

A blind google search returned the following, surely we can do better than just use any random one of these:

[http://www.livecdlist.com/purpose/security](http://www.livecdlist.com/purpose/security)

---

### Post by bodhi.zazen on 2010-06-22
> **Ulysses_ said:**
> Returning to the topic, hasn't anyone seen a security-oriented distro?  

None that claims to be more secure than default ubuntu?  

A blind google search returned the following, surely we can do better than just use any random one of these:

[http://www.livecdlist.com/purpose/security](http://www.livecdlist.com/purpose/security)

lolwut ?

[http://spins.fedoraproject.org/security/](http://spins.fedoraproject.org/security/)

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

[http://www.engardelinux.org/](http://www.engardelinux.org/)

Engarde is the most secure Linux OS I have used. It is designed for servers mind you and is almost certainly too secure for your use (online banking).

---

### Post by Ulysses_ on 2010-06-22
Engarde seems super secure, but is a desktop and a browser included?

---

### Post by bodhi.zazen on 2010-06-22
> **Ulysses_ said:**
> Engarde seems super secure, but is a desktop and a browser included?

No, I doubt you could start X if you tried. You would need to start writing selinux policies.

---

### Post by Bachstelze on 2010-06-22
Paranoid much? I've done amazon/ebay payments in Windows countless times, never got a problem...

---

### Post by oldsoundguy on 2010-06-22
THINK on this:

Your on line is secure if using Linux .. provided YOU are secure. (that includes your practices!)

For on line financial transactions, you are using a browser.  The OS has little or no bearing on the transaction.

https indicates that the site you are visiting is using encryption.  PERSONALLY, I NEVER do a financial transaction of ANY kind unless that is the URL.

BUT, your on line transaction(s) are only as secure as THE OTHER END.

Both my bank and my investment house are UNIX/Linux driven systems. (so is the NYSE) Trust that a lot more than a Windows driven server. 

As to eBay and Pay Pal .. they too, are NOT Windows driven.  (too many crashes .. too many hacker attempts many years back and the went with Sun for a while) .. not sure what system they have now, but it has not crashed or been attacked in YEARS.

---

### Post by bruno9779 on 2010-06-22
Backtrack would be what you are looking for IMHO.

It has a DE, and very high security features and configurations

For example, networking is disabled by default, you have to enable it from command line every time

---

### Post by Ulysses_ on 2010-06-22
Sounds like backtrack is the one then, thanks.

Oldsoundguy, the main issue for me is not transaction security but keyloggers that one might get from other sites before making a payment at a legitimate site.  I also have man-in-the-middle concerns, but that's another story.  These can probably be totally beaten by downloading the browser or liveCD from a trusted connection, so the certificates are not messed with.

---

### Post by wilee-nilee on 2010-06-22
> **Ulysses_ said:**
> Sounds like backtrack is the one then, thanks.

Oldsoundguy, the main issue for me is not transaction security but keyloggers that one might get from other sites before making a payment at a legitimate site.  I also have man-in-the-middle concerns, but that's another story.  These can probably be totally beaten by downloading the browser or **liveCD** from a trusted connection, so the certificates are not messed with.

Use this.

---

### Post by d3v1150m471c on 2010-06-22
The bells and whistles...talking cows in the terminal and a convenient taskbar menu is hardly a security risk. No offense but I think you're a bit paranoid. If someone is going to exploit something it'll be your browser, which almost all operating systems have, or they'll exploit ebay or amazon directly. In that event you're prettymuch screwed anyways as you cannot control amazon's security.

---

### Post by oldsoundguy on 2010-06-22
> **Ulysses_ said:**
> Sounds like backtrack is the one then, thanks.

Oldsoundguy, the main issue for me is not transaction security but keyloggers that one might get from other sites before making a payment at a legitimate site.  I also have man-in-the-middle concerns, but that's another story.  These can probably be totally beaten by downloading the browser or liveCD from a trusted connection, so the certificates are not messed with.

Not much chance getting a keylogger on YOUR computer unless YOU install it yourself.  Linux is NOT Windows .. single click installing or piggyback installing of ANY malware is not a concern in Linux.

Now, a keylogger on the OTHER END is not under your control, and if THEY get socked .. nothing you can do about it and no way to test.  

HENCE https!

---

### Post by d3v1150m471c on 2010-06-22
Why would backtrack be anymore secure? It still uses iptables like every other distro.

---

### Post by Ulysses_ on 2010-06-23
> **d3v1150m471c said:**
> The bells and whistles...talking cows in the terminal and a convenient taskbar menu is hardly a security risk.

Never noticed any talking cow in mint, I was on about the range of internet-facing applications and services that come with mint that I do not need. Any linux hardening guide starts with "disable unnecessary services".  To that I would add "remove unnecessary packages".

> If someone is going to exploit something it'll be your browserSo then there's no need to disable internet facing services, right? ;)

> No offense but I think you're a bit paranoid.No offence but I recommend you make no assumptions about who is posting questions here, they might be doing more dangerous things than yourself and they might have more experience than yourself.

---

### Post by yeleek on 2010-06-23
You are paranoid.

Suggest if you really are serious about understanding the threat level to a sensible LINUX used then you read up for [CEH]("http://www.eccouncil.org/certification/certified_ethical_hacker.aspx"), [Crest]("http://www.crest-approved.org/") & [GIAC]("http://www.giac.org/certifications/security/GPEN.php").

No system is truly secure, **_All_** have vulnerabilities and there is always residual risk.  However if you are sensible and have a reasonably locked down machine - such as provided by the links by bodhi.zazen you will be fine.

Software keyloggers on linux (or hardware keyloggers) are the least of your problem - afterall I'd have to penetrate your system or gain physical access.  Should worry far more about things like SSLSniff and ARP spoofing, neither of which require software installs on your machine nor would they be obvious to a joe bloggs user.

---

### Post by OpSecShellshock on 2010-06-23
Actually, in addition to the sticky, read this:

[http://www.schneier.com/blog/archives/2010/05/worst-case_thin.html](http://www.schneier.com/blog/archives/2010/05/worst-case_thin.html)

Everyone else should read it, too.

---

### Post by Ulysses_ on 2010-06-23
> **yeleek said:**
> Should worry far more about things like SSLSniff and ARP spoofing, neither of which require software installs on your machine nor would they be obvious to a joe bloggs user.  A quick intro what those are?  

I'll read that worst-case thinking article later.  I'm not sure it applies to me, it seems assumptions here are unstoppable about what other people do on the internet, ''they don't do the same things you do'' will never be enough as an answer.

---

### Post by yeleek on 2010-06-23
SSLSniff - 'These allow for completely silent MITM attacks against SSL/TLS in the NSS, Microsoft CryptoAPI, and GnuTLS stacks — ultimately allowing for SSL communication in Firefox, Internet Explorer, Chrome, Thunderbird, Outlook...............'
[http://www.thoughtcrime.org/software/sslsniff/](http://www.thoughtcrime.org/software/sslsniff/)

ARP Spoofing - you need to know your OSI model to fully understand this
[http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)
[http://en.wikipedia.org/wiki/ARP_spoofing](http://en.wikipedia.org/wiki/ARP_spoofing)

I repeat what I've said earlier read and complete this from bodhi.zazen, and you'll be fine.  
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

If you want to learn about websecurity, you could do worse then lookign at this (run it in a vm).
[http://www.owasp.org/index.php/Category:OWASP_WebGoat_Project](http://www.owasp.org/index.php/Category:OWASP_WebGoat_Project)

Hopefully the message is now received though re Linux security for home users.

---

### Post by snowpine on 2010-06-23
Call your credit card company. Explain that you are worried about online fraud; ask what they can do to protect you. If you're not satisfied with the answer, switch banks. Take a walk. Smell a flower. Don't let paranoia consume you. ;)

---

### Post by surfer on 2010-06-23
personally, i use [http://www.heise.de/ct/projekte/Sicheres-Online-Banking-mit-Bankix-284099.html]("http://www.heise.de/ct/projekte/Sicheres-Online-Banking-mit-Bankix-284099.html"), german only, sorry. its a live system that can be run off a cd (or, in my case, a write protected usb stick).

this way you ensure that your operating system and browser are not compromised to start with. no more (and no less) than that. the rest is up to you.

but any (configurable) live-system will provide that service. i'm even thinking about making a custom one with [http://www.geekconnection.org/remastersys/ubuntu.html]("http://www.geekconnection.org/remastersys/ubuntu.html").

---

### Post by mikewhatever on 2010-06-23
You can use a live cd/usb just for online banking. Just boot from it and go straight to the banking site. The benefit is obvious, permanently installing anything (keyloggers and what not) is not possible since the live cd is read only.

---

### Post by snowpine on 2010-06-23
> **mikewhatever said:**
> You can use a live cd/usb just for online banking. Just boot from it and go straight to the banking site. The benefit is obvious, permanently installing anything (keyloggers and what not) is not possible since the live cd is read only.

+1; and if you are truly paranoid, you'll want to use a Live CD with the latest Firefox security patches. The easiest way to do this is to download the Daily Build Live CD from the development branch, burn a new Live CD every day. Certainly don't use a 10.04 Live CD; think how many new vulnerabilities there must be in the 2 months since Lucid was released!!! :(

---

### Post by Ulysses_ on 2010-06-23
To certain 'kind' hearts that have been name-calling in my threads:   

Why don't you go give your words of wisdom to the owner of wikileaks and his visitors below, so they learn too from your wisdom and not get paranoid.

[http://ubuntuforums.org/showpost.php?p=9488348&postcount=12](http://ubuntuforums.org/showpost.php?p=9488348&postcount=12)  

**Administrators**: can any teenage ''expert'' come into my threads and name-call?  If there are no rules about name-calling, such as calling people crazy (paranoid) at any mention of security better than these ''experts'' are used to, do I have your permission to insult them back?

---

### Post by yeleek on 2010-06-23
You have assumed that everyone responding to you is either 

A) a teenager

or

B) Not involved in IT Security.

Perhaps the various people, myself included, who have said you are paranoid are trying to encourage you to a) relax b) learn this stuff yourself so that c) you actually understand the means via which such hacking incidents occur.

I would add - imho discussing trying to use measures to evade detection by government agencies is a) irresponsible b) naive c) arrogant

---

### Post by malspa on 2010-06-23
Yeah, don't feel bad, I'm "paranoid" about doing anything involving money online, and I freely admit it.  I try to avoid it whenever I can.

---

### Post by snowpine on 2010-06-23
> **Ulysses_ said:**
> Administrators: can any teenage 'expert' come into my threads and name-call?  If there are no rules about calling people crazy (paranoid), do I have your permission to insult name-callers back?

I truly apologize if the word "paranoid" in my previous post caused you offense. I meant "paranoid" only in the colloquial sense of "worried about things the average person doesn't worry about" rather than any clinical assumption about your mental health (which I would not be qualified to make anyway, not being a health/medical professional). :)

I stand by my previous assertion that, if you are worried about your financial privacy online, your first conversation should be with your bank, not with a Linux user forum. The Linux operating system comes with no warranty whatsoever and will not come to your defense if you are the victim of fraud. Your financial institution, however, is accountable to you, and they have an entire department that deals with this type of question all day, every day.

Hopefully some of the links provided will assuage your concerns that Linux Mint is a vulnerable, easily compromised operating system because it has an IM client. I also thought the Live CD suggestion was a good one. If you are truly worried about this stuff, walk down to your friendly local bookstore and pay cash; don't use Amazon. Best of luck! :)

---

### Post by bodhi.zazen on 2010-06-23
> **Ulysses_ said:**
> To certain 'kind' hearts that have been name-calling in my threads:   

Why don't you go give your words of wisdom to the owner of wikileaks and his visitors below, so they learn too from your wisdom and not get paranoid.

[http://ubuntuforums.org/showpost.php?p=9488348&postcount=12](http://ubuntuforums.org/showpost.php?p=9488348&postcount=12)  

**Administrators**: can any teenage ''expert'' come into my threads and name-call?  If there are no rules about name-calling, such as calling people crazy (paranoid) at any mention of security better than these ''experts'' are used to, do I have your permission to insult them back?

I think this thread has run it's course.

Honestly I do not think anyone intended any offense.

With that in mind, you do come across as someone who is new to Linux and  that you are bringing a "Windows mentality" with you.

You should start by reading the links I gave you. 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

And secure your browser:

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

And review the comments on my previous post on this subject :

[http://ubuntuforums.org/showpost.php?p=9459358&postcount=4](http://ubuntuforums.org/showpost.php?p=9459358&postcount=4)

The ""simple" facts are:

1. By default, there are no significant listening services, so there really is nothing to firewall. This is not Windows.

If you feel you must have a firewall, open a terminal and enter:

```
sudo ufw enable
```

The defaults are more then sufficient for the vast majority of Desktop users.

2. Ubuntu is secure out of the box.

[http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/](http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/)

3. If you wish to harden Ubuntu, start with the links at the top of this section, learn to use Apparmor, and read, read, read.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

4. Honestly, most of the problems with online banking are covered already if you follow the advice in the security sticky and the thread I gave you on apparmor.

Threats such as social engineering and phishing are many times more common then exploits to the Operating System.

There are things you can control, use https, use NoScript, use Apparmor, etc (see the firefox thread).


5. If you have a specific question on a specific issue, start a new thread.

---


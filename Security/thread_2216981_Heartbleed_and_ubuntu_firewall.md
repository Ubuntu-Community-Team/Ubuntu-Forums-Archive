---
title: "Heartbleed and ubuntu firewall"
date: 2014-04-15
forum: Security
---

### Post by jsvidyad on 2014-04-15
Hello,

    I use ubuntu 12.04 desktop version on my desktop. I do not run any servers on my desktop. I use ufw/Gufw to manage the firewall on this particular desktop. My question is regarding the news about the heartbleed openSSL vulnerability affecting firewalls. For example, look at this site : [http://www.huffingtonpost.com/2014/04/10/heartbleed-computer-bug_n_5129848.html](http://www.huffingtonpost.com/2014/04/10/heartbleed-computer-bug_n_5129848.html) . 

    Do I need to be worried about this? Does the heartbleed vulnerability in any way affect the netfilter/iptables firewall on ubuntu 12.04 or the ufw/Gufw firewall on ubuntu 12.04 ?

---

### Post by pqwoerituytrueiwoq on 2014-04-15
only SSL was vonerable, if it was not using ssl it was not vonerable
it was only 1 version of openssl that had the issue
if your system is uptodate you are secure

---

### Post by SeijiSensei on 2014-04-15
> "I am waiting for a patch," said Jeff Moss, a security adviser to the U.S. Department of Homeland Security and founder of the Def Con hacking conference. Def Con's network uses an enterprise firewall from McAfee, which is owned by Intel Corp's security division.

He said he was frustrated because people had figured out that his email and Web traffic is vulnerable and posted about it on the Internet - but he can't take steps to remedy the problem until Intel releases a patch.

Why the hell is he running a proprietary McAfee router when he could be running Linux and have fixed the problem already?  Yet another good example of the problems involved when you rely on proprietary systems.  I fixed the OpenSSL bug on half a dozen CentOS machines in an hour or two once the patched version was released.

I wouldn't be surprised to learn that Linux is running under the hood of that firewall either.  Last time I looked at a [Barracuda mail filtering appliance]("http://www.newegg.com/Product/Product.aspx?Item=9SIA2GW0T21584") it was running Linux and SpamAssassin.  I built a box for a client for considerably less that performs the same tasks and many others as well including a Squid proxy that [scans]("http://squidclamav.darold.net/") every downloaded web object for viruses on the fly. No annual licensing or per-seat fees either.

---

### Post by 1clue on 2014-04-16
[http://heartbleed.com](http://heartbleed.com)

Only web sites with SSL are vulnerable.  SSH and VPNs are not, unless they incorporate http in some fashion and the http is using openssl-based encryption.

FWIW if you're affected there are 3 steps to fixing the problem, and they MUST be handled in order:
[LIST=1]
[*]Software update to safe versions.
[*]Replace your SSL certificate
[*]Force a password change for all users of the site.
[/LIST]

If some financial institution or online store recommends you change your password ASAP, I strongly recommend you take care of it right away.

---

### Post by jsvidyad on 2014-04-16
Hello,

     According to news reports, this heartbleed vulnerability was around for more than two years. That's why the news articles about the heartbleed vulnerability affecting firewalls got me worried. So, I'd like to know if the heartbleed vulnerability, in any way, affected the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu in the past. Did the heartbleed vulnerability  make either or both of the netfilter/iptables firewall or the ufw/Gufw firewall also vulnerable to security exploits and loopholes which could have been exploited by hackers/crackers in the past? Please note that I run ubuntu 12.04.

     The second question is, if I update my ubuntu 12.04 system and make it up to date with the latest version of openSSL released by ubuntu, will it plug any security loopholes in the netfilter/iptables firewall and the ufw/Gufw firewall, if there were any security loopholes or vulnerability in those firewalls due to heartbleed? Does the netfilter/iptables firewall or the ufw/Gufw firewall  on ubuntu depend on openSSL in any way?

---

### Post by ian-weisser on 2014-04-17
> **jsvidyad said:**
>  So, I'd like to know if the heartbleed vulnerability, in any way, affected the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu in the past.

No.
Iptables does not use SSL for anything, and never did.
The 'ufw firewall' is, of course, also the very same iptables...which still doesn't use SSL.

---

### Post by 1clue on 2014-04-17
You're right in that having non-vulnerable code now does not eliminate risk if you ever had vulnerable code in the last two years.  If you ever had vulnerable code, you need to make sure that you follow the necessary steps.  Any SSL certificate which was enabled in conjunction with a flawed openssl needs to be replaced.

It's just that this bug has nothing to do with what you're asking.

---

### Post by jsvidyad on 2014-04-17
> **1clue said:**
> You're right in that having non-vulnerable code now does not eliminate risk if you ever had vulnerable code in the last two years.  If you ever had vulnerable code, you need to make sure that you follow the necessary steps.  Any SSL certificate which was enabled in conjunction with a flawed openssl needs to be replaced.

It's just that this bug has nothing to do with what you're asking.

   You mean to say that the heartbleed vulnerability has nothing whatsoever to do with either the netfilter/iptables firewall or the ufw/Gufw firewall on ubuntu??

---

### Post by RadicaX on 2014-04-17
Yes, it has absolutely nothing to do with that. SSL is what you see when you get that little pad lock when you go to a website. It is information that is encrypted. Basically, if you use say Yahoo, that is something you need to change your password for. Does not matter what kind of firewall you have. Because it does not effect you, your personal computer. Not really.

---

### Post by jsvidyad on 2014-04-17
So, what about those news articles that I came across which said that the heartbleed vulnerability affected firewalls? Are they misleading?

---

### Post by jsvidyad on 2014-04-18
Hello,

     In any case, the heartbleed vulnerability did not affect the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu in the past and does not affect the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu at present, right? 

Once I update my ubuntu desktop (including installing the latest openSSL package), I should be protected from any potential threats from the heartbleed vulnerability, right?

Sorry!!!  I am just worried ever since the news articles about the heartbleed vulnerability came out and I became especially worried once I saw the news articles which claimed that the heartbleed vulnerability affects firewalls. I haven't turned on my ubuntu desktop for the past few days. I am using a windows 7 computer right now as I sit typing in the public computer cluster of my university.

---

### Post by jsvidyad on 2014-04-18
Hello,

In any case, the heartbleed vulnerability did not affect the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu in the past and does not affect the netfilter/iptables firewall or the ufw/Gufw firewall in ubuntu at present, right? 

Once I update my ubuntu desktop (including installing the latest openSSL package), I should be protected from any potential threats from the heartbleed vulnerability, right?

Sorry!!! I am just worried ever since the news articles about the heartbleed vulnerability came out and I became especially worried once I saw the news articles which claimed that the heartbleed vulnerability affects firewalls. I haven't turned on my ubuntu desktop for the past few days. I am using a windows 7 computer right now as I sit typing in the public computer cluster of my university.

---

### Post by SeijiSensei on 2014-04-18
It sounds like you've only been reading news stories in the mainstream media.  Most of those people are clueless about the technical issues involved and have a bias in favor of over-reaction and fear-mongering. Did you read the discussion at heartbleed.com yet?  If you want to understand what this is all about, you need to do some research and tone down the paranoia.  As I said before, this was a specific exploit that targeted a specific bug in the OpenSSL code.  

In fact while it makes sense to upgrade your copy of OpenSSL, this is not really a problem for desktop systems.  The problem concerns servers, not desktop clients.

As for firewalls, those comments applied to commercial products from companies like McAfee, some of which use OpenSSL for things like VPN tunnels.  Again, they have nothing to do with Ubuntu or iptables.

---

### Post by Mama_Hadija on 2014-04-18
i think more than anything this vulnerability tells us that the model that ubuntu is using is the best open source model. they have revenue streaams and funding coming from cnonical so they can have a larger dedicated team on top of the open source community esnrung the safety of the platform.

---

### Post by 1clue on 2014-04-18
Look at that heartbleed website I posted above.  That's the authoritative site for what's vulnerable.  It's just the mechanism that provides encryption for https.

I suppose that something like a home wireless router has an https server on it for management, if that uses openssl of the wrong version then that would need an update.

Technically that https server is not a part of the firewall.  It's just an interface through which to configure the firewall.  That's the only way I can think of that heartbleed would affect a firewall.

---

### Post by RadicaX on 2014-04-18
> **SeijiSensei said:**
> It sounds like you've only been reading news stories in the mainstream media.  Most of those people are clueless about the technical issues involved and have a bias in favor of over-reaction and fear-mongering. Did you read the discussion at heartbleed.com yet?  If you want to understand what this is all about, you need to do some research and tone down the paranoia.  As I said before, this was a specific exploit that targeted a specific bug in the OpenSSL code.  

In fact while it makes sense to upgrade your copy of OpenSSL, this is not really a problem for desktop systems.  The problem concerns servers, not desktop clients.

As for firewalls, those comments applied to commercial products from companies like McAfee, some of which use OpenSSL for things like VPN tunnels.  Again, they have nothing to do with Ubuntu or iptables.

Seiji said it, the mainstream media is over reacting on the issue. Fear Sells, it gets people to watch, especially if they hope for a fix, or want to see what can be done for the fix. (Though the patch is already out mind you). It is not really something that affects the average user's desktop. It does affect things that use SSL, like Seiji pointed out, some products by some companies, which relied on it.

ufw/gufw, does not use openssl, thus the heartbleed bug does not affect it. Websites are at risk, not you. So change your passwords, because it is their stuff that COULD have been compromised. Meaning they might of found your password on say "insert social media site here" and can now log onto your account, and get your information. 

Another reason not to use the same password for your computer as websites.

---

### Post by 1clue on 2014-04-18
I'm not sure if it's overreacting.  It's a huge problem, but there is a straightforward fix for it.

Mainstream media understands neither the technology involved nor the steps necessary to fix it.  Therefore they can't be relied upon to relay the story accurately.

Again, go to the source to figure out what's going on.  [http://www.heartbleed.com](http://www.heartbleed.com)

---

### Post by SeijiSensei on 2014-04-19
> **1clue said:**
> I'm not sure if it's overreacting.  It's a huge problem, but there is a straightforward fix for it.

Yes, it is a huge problem; Bruce Schneier called it "[catatrosphic](https://www.schneier.com/blog/archives/2014/04/heartbleed.html)."  But most mainstream media only focused on what it might mean for ordinary people worried about their credit card and banking information being exposed.  The commentary in the days after the bug was disclosed tended to be a litany of things that might be affected like the firewall stories the OP cited.  Just because some device like a McAfee firewall or a Cisco router included OpenSSL code didn't really matter from the perspective of ordinary users.  Instead it just fed the unsurprising Luddite reactions that I saw around the Internet after the flaw was announced.

I'll modify my earlier comment about clients after reading this: [http://blog.meldium.com/home/2014/4/10/testing-for-reverse-heartbleed](http://blog.meldium.com/home/2014/4/10/testing-for-reverse-heartbleed).  So it makes sense for desktop users to update their OpenSSL implementations.  Still "reverse heartbleed" depends on your connecting to a compromised server, and there are additional reasons described in that posting that limit its potential for abuse even in that situation.

---

### Post by cogset on 2014-04-19
Right,I've been reading around to try and get some sense out of what has happened:as far as I can tell,the remarks about clueless fear-mongering are true,as unfortunately are the claims about the extent of the damage done.
If I got this right,what many "tech" sites actually fail to explain is that -sadly- there's apparently very little (if anything at all) that the average home computer user can do about this,as the security hole has been affecting a large number of servers world wide,possibly stealing the encryption keys for secure SSL connections from the above servers,consequently stealing all kinds of personal data,and that's simply not something that you can patch from your home computer.
After reading the first news bout Heartbleed,I've rushed to install the patched version of openssl,only to realize later on that the real issue was not so much with my computer as it was with who knows how many websites that I've been visiting in the last months.
That's really disappointing:at the time of the announcement,as far as I can understand the secure protocol on which we all rely for secure connection had been effectively broken for a long time.
And one can only speculate about who has been exploiting that hole and for what purposes.

---

### Post by jsvidyad on 2014-06-30
Hello,

    I am the original poster of this thread. Sorry that I am posting here after such a long time.  I was really busy with work on my thesis and just finished. 

     I have been using windows 7 all this time and have not used my ubuntu machine at all. Yes, I used libre-office on windows to type my thesis. So, before I start using my ubuntu machine again, I'd like to get a couple of things clarified. 

    From the posts in this thread, I got the idea that the heartbleed vulnerability does not (and did not) in any way affect the ufw/Gufw firewall or the netfilter/iptables firewall on ubuntu. Is that right?

    Also, if I update my ubuntu system to the latest version of the packages and make my system up to date, I should be protected from the heartbleed and reverse heartbleed vulnerabilities, right??

---

### Post by bashiergui on 2014-07-01
> From the posts in this thread, I got the idea that the heartbleed vulnerability does not (and did not) in any way affect the ufw/Gufw firewall or the netfilter/iptables firewall on ubuntu. Is that right?Yes > Also, if I update my ubuntu system to the latest version of the packages and make my system up to date, I should be protected from the heartbleed Yes > and reverse heartbleed vulnerabilities, right??kind of, but not really. You have no control over the servers you browse to. All you can do is update your system. If you installed all the updates in the last two months you have done all you can do.

---


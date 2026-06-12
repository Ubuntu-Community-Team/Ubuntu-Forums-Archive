---
title: "Self hosting"
date: 2014-05-24
forum: The Cafe
---

### Post by fmfrisch2 on 2014-05-24
**Okay, here's the deal:**
*I've decided to leave Google for good.* I've used several of their services but I'm alright with just replacing it with email. I've also started to become more and more interested in open hardware and the idea behind federated systems. Together with an anger over the NSA scandal and a fat rebate on Raspberry Pi or pcDuino3, I feel like self hosting would solve all my needs and interests at the same time.

**My needs: **
I need an email server, a sparkleshare (or similar) instance and a social media pod.
The email would need to be IMAP, and would only service my own personal needs. This email address would not be used on any internet forms etc, purely for personal communication with friends or family. The amount of email would as such be limited. The fileshare wouldn't have to be bigger than 2GB. I would sync a small personal library of academic articles and my own work. We're talking ~100 files, docs and pdfs. Version handling very important though. I want to work on a file change computer and continue. I can't have bugs were recent changes get overwritten by the server on my local instance and so on. The social media pod is for me and close family only. There will tops be 10 people ever on it. The pod need not be connected to the rest of the federated system. But it would be fun if it was.

**User cases:**
I would connect to my IMAP server through an email client on my computer and my phone. At times I would also need to use a third party computer to access it through a web interface. My Ubuntu One replacement is only going to sync between one computer and the server. Just one client. No mobile integration needed, just a web interface to access files. My social media pod is more fun than serious. Three brothers and their families want to be able to connect with their parents. I've looked into pump.io and Diaspora. Thing is, the user case is more for sharing pictures, and media rather than talking (which phones and email already gives us the ability to do - twitter style communication only makes sense when you want to talk to strangers). Movim seems the be the better option.[B]

What I'm not asking:[/B]
I've previously ended up in debates on whether leaving google is good or not and whether it is necessary. I have reasons to do it that goes beyond the NSA scandal. Humour me, assume I have good reasons. This is all theoretical, I'm moving after this summer and that is when I'll start this project. I realize the ISP, static IP and related issues are relevant, but I don't know how that'll look. So lets leave that for now.

**My questions:**
_I'm an idiot._ From what I've understood running an email server isn't exactly something made for an idiot. I've read that for someone like me it's more trouble than it's worth. What do you think? How many hours upkeep? How much downtime should I expect? Etc. Will it ever be even close to as reliable as gmail? Or will I be that guy that has his own email but emails with gmail instead because it never works?
What would you use? I'm looking at sparkleshare for Ubuntu One replacement and Movim for a social media pod (love the idea of it being built over XMPP). 
Is it possible to fit all of this onto a small open hardware device? Does RasPi or pcDuino have enough horse power? If not is there anything like it that does?

[I]Feel free to answer any question I have been to dumb to ask. I'm guessing there is about a million.
[U]
I am of course looking to deploy this on a Ubuntu Server.[/U]
[/I]

---

### Post by buzzingrobot on 2014-05-24
Been there, done that, have no intention of ever doing it again. Big, expensive, time-consuming pain. No payoff.

For starters, you get to stay current with every new security issue and shell into your server to patch it when the patch shows up.

Remember, any mail you send to anyone using Gmail ends up on a Google server anyway. That's how mail works.

Mail is not point-to-point private communication.  No matter who's running the server.

---

### Post by Habitual on 2014-05-24
Keep out. There be dragons.
Don't do it.

I have a belief that if you become a store detective, everyone becomes a shoplifter.

Security is a process, not an application, and it is FULL TIME JOB.

---

### Post by fmfrisch2 on 2014-05-25
*You are not telling me what I want to hear!* 

I guess I  knew this from what I've read. Mostly I was looking for that one pat on  the back amongst 100 nay-sayers that would help me legitimizing setting  up my own server.

Dammit!

I guess I'll hook up my  RaspberryPi/pcDuino3 to my TV and install XBMC instead. Not nearly as  fun though. I don't even know if I'll be able to enjoy my HD streaming  off of my hand seized completely quiet mini-media center when I think of  what,

 *could've been...*

---

### Post by Old_Grey_Wolf on 2014-05-25
I couldn't vote because it is not yes or no. 

As soon as you install a server, then expose it to the Internet, you face security issues. Setting up a server and locking it down is not a secure it and forget it situation. New vulnerabilities are discovered and must be patched. 

A home server is not something everyone should attempt. If you are willing to keep up-to-date with the vulnerabilities and patches/workarounds; then, try it at your own risk.

---

### Post by CharlesA on 2014-05-25
> **Old_Grey_Wolf said:**
> I couldn't vote because it is not yes or no. 

As soon as you install a server, then expose it to the Internet, you face security issues. Setting up a server and locking it down is not a secure it and forget it situation. New vulnerabilities are discovered and must be patched. 

A home server is not something everyone should attempt. If you are willing to keep up-to-date with the vulnerabilities and patches/workarounds; then, try it at your own risk.

This.

I host email for my website and it was a bit of a pain in the backside to get set up and configured. Owncloud was dead simple, thankfully, but you do have to stay up to date with patches and that can be a full time job, depending on how often you check for updates.

---

### Post by mastablasta on 2014-05-26
and let's not even start with UPS and power etc. to have the uptime. Also RaspberyPi is small, consumes little power yet it is not powerfull and has many limitations.

i am not sure why you want to do all this on a home server, but in my opinion it would be easier to get a good host and encrypt your own stuff.  or at least put it's access (let's say pictures) behind a password. emails and such can be encrypted before sendign them out with a thunderbird addon.

there are many cloud hosts that also offer encrpyted file service for free. ok these clouds are not ideal solution, but at least they make it easy to share pics and such among family members. you sitll need backups anyway...

---

### Post by jjthomas on 2014-05-26
I put my first BBS together in the mid 80's, I've had a website since the late 90's.  At one point,  the website server was an old computer sitting on the top of the stairs.

Currently my websites are hosted by the fine folks at KnowHost.com.  Been there for several years, very happy.  I am thinking of bringing my website into my house, and that is why this thread caught my attention. 

Although I am not familiar with sparkleshare or social media pod, but your needs seem simple enough.

If you put server out on the Internet, it will be connected to the world... which has a lot of bad guys.  You will also need to become familiar with DNS.  Email is not that hard to configure, but, you have to pay attention to what you are doing.  DNS is not fun and is difficult to troubleshoot.  You need to keep up to date on the security of whatever you are running on the server.   Backups are critical, very critical.

Your questions:  If you say you're an idiot, people are going to label you as such.
I was clueless when I set up my first email server.  I've set up several since.  Same with my first Apache server.  Now I just whip it out with one eye closed.  DNS still kicks my tail, but I'm getting better at it.  We all started with no knowledge, we gained the knowledge by trying and failing.  Some of us, many times (DNS)! [/soapbox]

Upkeep is going to be a moving target.  I had one of my accounts hacked (brute-force), it took me 5 seconds to change the password.  Another time, I spent 30 hours, spread over a couple of days, to clean up after my website got hacked.  I both instances, my site was up and running.  I get a report daily and if anything is wrong, I log in and fix it.

Reliability will depend on your hardware and your maintenance skills.  I had a UPS fail and I had to reinstall my OS.  I built a server that had two completely identical computers, running off two different power lines and separate UPS's.  Oh and a third one stashed in a closet.  

My suggestion would be to build your home server and give it a try.  Keep you google stuff where it is for now.  As you gain more confidence, move things over to your home server.

Keep in mind that anything you put on your server can be downloaded and passed around the Internet.

As a final thought, most ISP's will not let your run a server.

Good luck.

-JJ

---

### Post by rewyllys on 2014-05-26
Over two years ago,when I changed our ISP for the second time in less than 4 years, my wife's complaints about having to change her primary email address crescendoed to a new high. Thus was I led to realize that I needed to set up for her a primary email address that would be permanent and not dependent on our family's  choice of ISP for basic Internet service. 
 
For a variety of reasons, I did not want to rely on free email services such as gmail and hotmail. After researching various possibilities, I chose the services offered by [Simple Online Solutions]("http://www.simpleurl.com/"). 

In brief, I registered a new Web domain via SOS and set up an email address for my wife at this new domain.  The domain registration cost US$132 for 10  years and can be renewed. The annual operating cost of my wife's permanent email address is US$12, i.e., a dollar a month. The total cost works out to be US$2.10 a month.  That's well worth it to me for my wife's convenience (and -- for me -- the absence of complaints from her).

We've used SOS for over 2 years now, and their service has been both friendly and flawless.

There are other vendors that provide services similar to those of SOS.  IMHO, using any of them would be likely to be more convenient and safer than trying to set up my own email server.

---

### Post by fmfrisch2 on 2014-05-27
*Cool, so many good replies!*
[B]
Why I want to do this
[/B]I started to get off on why I wanted to do this just to realize that only approximately half a comment was asking me why. So I pasted my answer [here]("https://pad.riseup.net/p/r.4dd03c65869e377057cd2784b52aa5f5"). It's not too relevant, please don't get this thread off topic by commenting on my reasons. 
  
[B]My needs explained
[/B]I feel like I should have been more clear on my email needs. I have a 'personal professional' email account on Outlook, when Microsoft re-branded hotmail I was like an eagle and registered a killer Outlook email address. This will remain the same. I also have professional email for business through my company, of course this will remain the same. Lastly I have a junk gmail and hotmail account. These are the ones I usually fill out internet forms etc with. The Gmail account has also been the account I've used for personal correspondence, this is what I'm looking to self-host. (the personal correspondence). 

We all know how often we should be calling out mother. We all also know how often it actually happens. We're looking at an email account receiving and sending a total of 30 emails a week, tops (not all to my mother, I promise). 

Someone talked about the power of Raspberry Pi, this is one of my main questions and concerns. Would a RasPi even be able to run these three things (email server, social media pod and a fileshare).

I've been looking into Kolab which is a super cool groupware project. It would be 3000% more than I need (the whole 'over kill' mentality is what I'm trying to get away from), but does anyone have any experience? It would combine email with OwnCloud as I understand it (looking at the latest versions).

---


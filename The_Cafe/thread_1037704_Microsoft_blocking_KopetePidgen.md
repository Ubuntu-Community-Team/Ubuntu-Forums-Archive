---
title: "Microsoft blocking Kopete/Pidgen?"
date: 2009-01-12
forum: The Cafe
---

### Post by MisterFlibble84 on 2009-01-12
Is anyone else having trouble connecting to MSN with Kopete and Pidgen?

Pidgen won't log in, and Kopete logs in but won't pull up my contacts list.

(aMSN works)

---

### Post by Bachstelze on 2009-01-12
Yeah, those issues are very common. Nothing we can do, sadly...

EDIT: Well, the [web messenger]("http://webmessenger.msn.com/") still works. ^^"

---

### Post by shafi on 2009-01-12
> **MisterFlibble84 said:**
> Is anyone else having trouble connecting to MSN with Kopete and Pidgen?

Pidgen won't log in, and Kopete logs in but won't pull up my contacts list.

(aMSN works)

Sometimes this happen, but its not too often, after a restart you should be able to log in, I think this happen due to network problem, sometimes.

---

### Post by kavon89 on 2009-01-12
Today I have been having a problem logging onto MSN. Some error "Unable to retrieve MSN Address Book"

Microsoft must have released a new protocol update, which broke whichever one Pidgin uses.

---

### Post by -grubby on 2009-01-12
It works here.

---

### Post by jrusso2 on 2009-01-12
Working here also

---

### Post by hivelocitydd on 2009-01-12
msn regularly does things to break compatibility with 3rd party software, usually upgrading to the latest gets it working again (or a new release soon does)

---

### Post by Mr. Picklesworth on 2009-01-12
> **HymnToLife said:**
> Nothing we can do, sadly...

Well, there is one thing you can do. Convince all your contacts to switch to Jabber / XMPP (particularly easy if they use Google for email). It's a superior system anyway, and has full support on a vast range of devices. Admittedly hasn't worked for me, but I try.

---

### Post by jrusso2 on 2009-01-12
I usually use google talk which is jabber but its on google's server.

---

### Post by RichardLinx on 2009-01-12
I've been having issues with msn on Pidgin today as well. Emesene is working fine though.

---

### Post by some_random_noob on 2009-01-12
> **kavon89 said:**
> Today I have been having a problem logging onto MSN. Some error "Unable to retrieve MSN Address Book"

Microsoft must have released a new protocol update, which broke whichever one Pidgin uses.

I have had the exact same error happening to me today (which is a first! Usually I get other annoying errors). What's the best alternative to this? Everyone uses MSN, so how do I escape it without being incompatible?

---

### Post by MisterFlibble84 on 2009-01-12
Same error.

Tried the Pidgin 2.5.2 from Ubuntu and the 2.5.3 from Getdeb, and both have the same problem. :(

---

### Post by FuturePilot on 2009-01-12
Yeah same problem here. Unable to retrieve address book. Most of my contacts are on Jabber anyway so it's not that big of a deal for me.

---

### Post by Polygon on 2009-01-12
its also getting that error for me. luckily i dual boot vista so im just using the offical msn client until the pidgin devs release 2.5.4 which fixes that among other things

i think it has to do with them using an older application ID which microsoft finally got around to shutting down (the old one was for MSNP14 and the newest one is 15 or something)

---

### Post by adamlau on 2009-01-12
Just built 2.5.3 with the only diff from my last build being:

```
--disable-msnp15
```

MSN address book retrieval is now working, issue is likely related to MSNP15.

---

### Post by 3rdalbum on 2009-01-12
I have Meebo.com installed in Prism, as a backup messenger. When they've got Facebook Chat support again I'll switch full-time to Meebo.

---

### Post by cristianrosa on 2009-01-12
Check this thread 

[http://ubuntuforums.org/showthread.php?t=1037515&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=1037515&highlight=pidgin)

---

### Post by binbash on 2009-01-12
This happens often, the pidgin releases solve that kind of issues.

---

### Post by mcduck on 2009-01-12
I suppose Microsoft just made one of their semi-frequent little changes to annoy everybody using any other client than their own.

Pidgin doesn't connect, and same thing with Adium on my mac.

Oh how I wish my friends would stop using MSN, most of them already have gmail accounts so they could just as well use gtalk, but no. :P

---

### Post by pluckypigeon on 2009-01-12
I have this problem and so does my girlfriend who uses xp (separate Internet connections and providers)

---

### Post by Brynster on 2009-01-12
I use Empathy it seems ok at the moment

---

### Post by uberdonkey5 on 2009-01-12
> **some_random_noob said:**
> I have had the exact same error happening to me today (which is a first! Usually I get other annoying errors). What's the best alternative to this? Everyone uses MSN, so how do I escape it without being incompatible?

After a virus infected many of my friends computers through MSN (I was using linux by then), most of them chat to me through skype or gmail (not sure how MSN virus occurred). I never use pidgeon even, just direct gmail and skype for linux.

I think the best solution is actually to stop using MSN cos
1. microsoft will keep trying to exclude (or at least won't cater) to 3rd party applications and
2. MSN is likely to be the largest target for viruses/unwanted chatters!

I think MSN is one of the mosr rubbish packages ever produced.It slows your computer down enormously, has rubbish effects and background, and the smilies are distracting and annoying rather than useful!

---

### Post by RobsterUK on 2009-01-12
> **kavon89 said:**
> Today I have been having a problem logging onto MSN. Some error "Unable to retrieve MSN Address Book"

+1

Also having this error with Pidgin.

There is a ticket open on the Pidgin bug tracking system, but the Pidgin web server seems to have become overloaded, possibly due to the increased traffic resulting from this problem.
[http://developer.pidgin.im/ticket/8087](http://developer.pidgin.im/ticket/8087)

---

### Post by ww711 on 2009-01-12
> **RobsterUK said:**
> +1

Also having this error with Pidgin.

There is a ticket open on the Pidgin bug tracking system, but the Pidgin web server seems to have become overloaded, possibly due to the increased traffic resulting from this problem.
[http://developer.pidgin.im/ticket/8087](http://developer.pidgin.im/ticket/8087)

Am another Pidgin/MSN user held hostage to the logging/network situation.

---

### Post by mcduck on 2009-01-12
I got Pidgin working by installing the "msn-pecan"-package, changing the account protocol from MSN to WLM and restarting Pidgin..

---

### Post by Mmmbopdowedop on 2009-01-12
> **mcduck said:**
> I got Pidgin working by installing the "msn-pecan"-package, changing the account protocol from MSN to WLM and restarting Pidgin..

Yeah, this worked for me too, was just reading the thread.

Working fine for me at the moment, just have duplicate contacts in my list for some reason, suppose I can live with it. :)

---

### Post by ithanium on 2009-01-12
it works with msn-pecan :D

---

### Post by mrgnash on 2009-01-12
Switch to Jabber/Google Talk -- problem solved.

---

### Post by fiona-conn on 2009-01-12
I've tried Windows Live Messenger on my Vista setup, and on Ubuntu, I've tried Emesene, aMSN, Pidgin and Empathy. Each time, I am getting messages about server/network errors.

x_x 

I also tried the Pidgin fix, to no avail, sadly. =\

---

### Post by MisterFlibble84 on 2009-01-12
Installing msn-pecan and changing it from an MSN to WLM account logged me back in.

Thanks! :guitar:

---

### Post by jeremy on 2009-01-12
msn-pecan has solved the problem for me :)

Well, it has made pidgin work again, but the real problem (Micro$oft) is still there unfortunately :(

---

### Post by geoken on 2009-01-12
> **jeremy said:**
> msn-pecan has solved the problem for me :)

Well, it has made pidgin work again, but the real problem (Micro$oft) is still there unfortunately :(

I like how changes in MSN = the evilness of microsoft, while seemingly arbitrary changes in Linux app's are fine.

Can I start calling the ffmpeg devs evil because a while back they arbitrarily changed the identifiers for some codecs which made a lot of ffmpeg based gui convertors fail?

It seems ridiculous because API instability (for seemingly arbitrary reasons) is so prevelant on Linux that it's pretty much a running joke with most people who do cross platform development.

---

### Post by Mr. Picklesworth on 2009-01-12
Although, in fairness, API changes tend to be documented ahead of time in the better projects (eg: with the APIs that people should actually be using).

MSN was never meant to have alternative clients and Microsoft has no interest in that happening. Jabber, on the other hand, is an open protocol so you can use whatever client you want *smoothly* and it works across different servers instead of being centralized.

---

### Post by SuperSonic4 on 2009-01-12
Kmess 2 isn't working but emesene is, I'll just wait for the svn of kmess to be updated

---

### Post by Mr. Picklesworth on 2009-01-12
Oh, one observation:
Empathy with telepathy-butterfly (from the [Telepathy PPA]("https://launchpad.net/~telepathy/+archive")) seems to have survived happily without any hickups.

If you use specifically MSN, I really recommend Emesene ( if you don't like Empathy :( ). It doesn't have the best user interface, but it's aimed straight at MSN so it does a great job of suporting the protocol. Essentially does everything but video chat, which is "coming soon".

---

### Post by SomeGuyDude on 2009-01-12
> **geoken said:**
> I like how changes in MSN = the evilness of microsoft, while seemingly arbitrary changes in Linux app's are fine.

I think it's because the "M$ is evil" meme is so ubiquitous on here that everyone assumes issues like this are because some evil MS developer went into the code and purposefully did this to screw over Linux users, whereas when an API muff-up happens in Linux everyone assumes it was a mistake.

It's almost a compliment to Microsoft. You don't make mistakes, you execute evil plans perfectly.

---

### Post by ww711 on 2009-01-12
MSN/Pidgin is available again now for me. Not sure about anyone else.

---

### Post by RiceMonster on 2009-01-12
> **SomeGuyDude said:**
> I think it's because the "M$ is evil" meme is so ubiquitous on here that everyone assumes issues like this are because some evil MS developer went into the code and purposefully did this to screw over Linux users, whereas when an API muff-up happens in Linux everyone assumes it was a mistake.

It's almost a compliment to Microsoft. You don't make mistakes, you execute evil plans perfectly.

+1

Anyway, pidgin's not working for me right now either, so I'll just use emesene and live without aim for the time being.

---

### Post by Half-Left on 2009-01-12
> **SomeGuyDude said:**
> I think it's because the "M$ is evil" meme is so ubiquitous on here that everyone assumes issues like this are because some evil MS developer went into the code and purposefully did this to screw over Linux users, whereas when an API muff-up happens in Linux everyone assumes it was a mistake.

It's almost a compliment to Microsoft. You don't make mistakes, you execute evil plans perfectly.

Deveopers do what they are told from the evil top, it's a know fact Microsoft tried to block third party msn apps because of so called 'security'

Microsoft have done alot to harm and stop competition in ways like this right from the 90's to the current day.

---


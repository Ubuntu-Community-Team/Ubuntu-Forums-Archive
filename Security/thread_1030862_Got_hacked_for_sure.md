---
title: "Got hacked for sure"
date: 2009-01-04
forum: Security
---

### Post by bth73 on 2009-01-04
This is from my post on Ultimate 2.0 forums. link to entire post a bottom
Postby bth73 on Mon Jan 05, 2009 12:59 am
Hi, everyone, I'm back. ABSOLUTELY had a security breach. I just got off the phone with my credit card company, and somebody's been trying to use my card to buy stuff out of china and france. I have used my card in the past with no problem, but I used it during the time that I had this problem and someone snagged it from my keystrokes or something. Last use was at TigerDirect.com to buy a computer kit for a friend.
My hard drive is fine, only a few months old. nothing wrong with any hardware.
My notice to all is that my linux system got hacked and yours might get hacked too.
I've allready wrote my hard drive to 0000's and started over with new passwords. New credit card on it's way.
Wish I knew how they got me. Jihad on hackers and thieves - cut their f*#%$@ heads off. Damn pussies.
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a)

---

### Post by albinootje on 2009-01-04
> 
My notice to all is that my linux system got hacked and yours might get hacked too.
I've allready wrote my hard drive to 0000's and started over with new passwords. New credit card on it's way. Wish I knew how they got me.
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a)

This is really a silly posting by the guy whose computer got broken into.

Instead of zeroing out the hard disk this person should have let it examined by forensic Linux experts. 
He could at least cloned the hard disk to some disk image.

We also don't know anything about the web surf behavior of this person.
Therefore pointing any finger towards Linux security is not valid at all imho.
Even when you use OpenBSD your credit card details can be stolen, it all depends on behavior of the end user.

---

### Post by Boelcke on 2009-01-04
Or maybe your waiter copied the number down while he had your credit card.  It could be as simple as that.

There are many ways to loose your credit card number.  It's inherently unsafe and unprotected.

Jumping to conclusions is flamebait, and a waste of your precious time.

---

### Post by BLTicklemonster on 2009-01-04
... wow, you guys are really helpful.

---

### Post by melojo on 2009-01-04
Can you post any logs to back up your suspicion?

---

### Post by bth73 on 2009-01-04
Sorry, just a newbee sort of. Got no patience or time. no records. From description of root kits, I think that's what happened. was using a simple password, same for years. Don;t use credit card very often. Did order heart meds from canada, but should be legit, I'll see in about 15 days.

---

### Post by bodhi.zazen on 2009-01-05
> **bth73 said:**
> This is from my post on Ultimate 2.0 forums. link to entire post a bottom
Postby bth73 on Mon Jan 05, 2009 12:59 am
Hi, everyone, I'm back. ABSOLUTELY had a security breach. I just got off the phone with my credit card company, and somebody's been trying to use my card to buy stuff out of china and france. I have used my card in the past with no problem, but I used it during the time that I had this problem and someone snagged it from my keystrokes or something. Last use was at TigerDirect.com to buy a computer kit for a friend.
My hard drive is fine, only a few months old. nothing wrong with any hardware.
My notice to all is that my linux system got hacked and yours might get hacked too.
I've allready wrote my hard drive to 0000's and started over with new passwords. New credit card on it's way.
Wish I knew how they got me. Jihad on hackers and thieves - cut their f*#%$@ heads off. Damn pussies.
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444&st=0&sk=t&sd=a)

I am sorry this happened to you and yes it is true Linux can be hacked.

Still, what makes you so sure your system was cracked ? Are you running any servers (ssh ?). You say you have a simple password, did you enable the root account ? Did you disable any security features ? Does anyone have physical access to your box ? There are physical key loggers ...

At any rate we should all be more security conscious.

---

### Post by jrusso2 on 2009-01-05
Its also just as possible the person who works for Tiger took it and passed it along or sold it.

---

### Post by mvellone on 2009-01-05
Just because someone compromised your account doesn't mean they stole it from your computer. You probably got jacked by a waiter or a drive through worker, anyone who had access to your card is suspect.

---

### Post by Masuran on 2009-01-05
> **bth73 said:**
> Did order heart meds from canada, but should be legit, I'll see in about 15 days.

Real smart... Let me guess, you got a mail saying you could find cheap heart meds on that site? 

You have no proof your computer got hacked. Like someone else said, some waiter probably copied your card number.

---

### Post by bth73 on 2009-01-07
Is this comp infected?
This is off my other comp:Intel(R) Celeron(R) CPU 2.20GHz
Memory	1031MB (371MB used)
	Linux 2.6.27-9-generic (i686)
Compiled	#1 SMP Thu Nov 20 21:57:00 UTC 2008
C Library	GNU C Library version 2.8.90 (unstable)
Distribution	Ubuntu 8.10
Operating System	Ubuntu 8.10
System Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
syslog	
klog	
hplip	HPLIP system user
avahi-autoipd	Avahi autoip daemon
gdm	Gnome Display Manager
pulse	PulseAudio daemon
saned	
messagebus	
polkituser	PolicyKit
avahi	Avahi mDNS daemon
haldaemon	Hardware abstraction layer
clamav	
chipcard	Chipcard-Tools Daemon Account
vde2-net
	
this is from ckrootkit :
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... You have     1 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
chkdirs: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5288])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

---

### Post by albinootje on 2009-01-07
> **bth73 said:**
> Is this comp infected?
-- cut --
this is from ckrootkit :
Checking `lkm'... You have     1 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
eth0: PACKET SNIFFER(/sbin/dhclient3[5288])

Please do a search for "false positives chkrootkit".
And see here :
[http://www.chkrootkit.org/faq/#6](http://www.chkrootkit.org/faq/#6)
[http://www.electricmonk.nl/log/2007/11/29/chkrootkit-false-positives-filtering/](http://www.electricmonk.nl/log/2007/11/29/chkrootkit-false-positives-filtering/)

---

### Post by kmj1268 on 2009-02-03
Interesting Thread...
I have worked in security for around 10 years and been in IT for quite sometime longer that that.  I certainly dont claim to be an expert in how a computer got hacked and there is definitely some good advice, HOWEVER  and I say that boldy.... perhaps it would be more helpful for those of you that want to be a little harsh on bth73 here... to give some strong advice on what he should look for to know if his computer was hacked.  I think that's where a lot of us security guys can be a little on the wrong side of the fence, we let our arrogance be more destructive instead of constructive.......

While I agree with what's being said, its not necessarily what you say but it's how you say things are what solution do you offer to the equation...


Good points I see here are....
it would have been very advantageous to have had your hard drive removed and had someone knowledgeable of forensics to make a bit for bit copy of your machine.

I would have probably also recommended doing some memory dumps of your processes and what's going on with the kernel.

Next, I would have hooked up your external interface of your machine into a hub and used another secure machine (using a linux distro like backtrack) to run a continuous tcpdump with a large external drive to capture the traffic.  The purpose of this would be to get a good capture to obtain any botnet traffic or any trojan activity dialing home.  If you see traffic out to China Telcom and you didnt have any browser open, you probably have something to worry about.  I also highly recommend a program like NetWitness which can read your capture file.  If you are not sure how to run these tools find a buddy that is familiar or pay a security forensics guy to do it for you.  They can tell you for sure.

I hope this helps.

Best of luck to you....
JMK, CISSP

---

### Post by jerome1232 on 2009-02-04
The fact is you really should've done the above, who knows if you did get hacked you might've found out how it happened, posted the results and the system could've been patched against the exploit.

I think it was probably a phishing scam or one of the 10 billion other ways a person can get ahold of your credit card number. ;)

---

### Post by tubezninja on 2009-02-05
> **kmj1268 said:**
>  HOWEVER  and I say that boldy.... perhaps it would be more helpful for those of you that want to be a little harsh on bth73 here... to give some strong advice on what he should look for to know if his computer was hacked. 

Well, I'd certainly like to, but considering bth73 said in his first post that he's already zeroed out his hard drive and re-installed, we will probably never know what happened because the evidence has been destroyed.  And given he's already professed that he did this out of impatience, I doubt we can cajole this person to donate his hard drive and a few thousand dollars to a data recovery center to reconstruct what he zeroed out.  Not that I'd reasonably ask him to do this, but the point remains: there's not very much we can help the OP with now that the data's been wiped, is there?

Are we being harsh?  Absolutely.  He panicked nad decidedd to tell everyone to WATCH OUT!  YOUR LINUX BOX COULD BE HACKED TOO!  And yet has no evidence at all to show for it,  not even something that can be analyzed, so that if it WAS as a result of a compromise, people at least know what to look out for.

>  I think that's where a lot of us security guys can be a little on the wrong side of the fence, we let our arrogance be more destructive instead of constructive.......

It's always easy to get on the high horse, isn't it?  I don't see arrogance here, so much as frustration.  The OP isn't asking for help.  He's just spreading FUD by saying "My notice to all is that my linux system got hacked and *yours might get hacked too*" without ever saying how.  

Gee, *that's* helpful.  Thanks for the tip.

Even more suspect is that he went to some questionable eb site to buy "legal" heart meds from Canada, and doesn't suspect that transaction one bit.  What's wrong with this picture?

---

### Post by zerofool2005 on 2009-02-09
Sounds more like the shop you ordered from had its db dumped. Or you just entered it on a fake site. A lot of "med" sites will process your orders. but also steal you cc info and make even more money from you

---


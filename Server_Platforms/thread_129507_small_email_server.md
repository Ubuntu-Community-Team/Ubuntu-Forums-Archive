---
title: "small email server"
date: 2006-02-13
forum: Server Platforms
---

### Post by blu.gecko on 2006-02-13
I have a 800mhz 1gig ddr133 80gig hd. I have aprox. 20 clients who would like to have company email.

I would like to setup a small email server, but the only software I have
ever ran was nuonce.net or bluequartz.org, I dont feel comfertbale with this software and would like to have a upto date secure mail box.

could someone lead me in the proper direction, webmail is not needed but it would be a nice bonus.

thanks.

blu

---

### Post by TTT_travis on 2006-02-13
Hey you might want to check out this thread it has some good starting tips:

[http://ubuntuforums.org/showthread.php?t=11371](http://ubuntuforums.org/showthread.php?t=11371)

---

### Post by heimo on 2006-02-13
[This guide]("http://flurdy.com/docs/postfix/") is excellent. I've used it twice and recommend it. Your hardware will be most probably more than enough, but you would certainly benefit of having backup mx. Also if I'd be setting up such system, I'd definitely require it to have raid (in this case raid 1/mirroring would do) array and regular backups.

---

### Post by MJN on 2006-02-14
[quote=heimo] ... but you would certainly benefit of having backup mx.[/quote] 
For what reason? A sending MTA will retry again later if your mailserver is down (spambot probably won't so even better ;)).

If your primary, and only, mailserver runs the risk of being out-of-action for longer than the aforementioned queuing then you probably ought to be thinking twice about even running your own mail server for *business* use...

Mathew

---

### Post by heimo on 2006-02-14
MJN, you're correct.

---

### Post by MJN on 2006-02-14
It is a commonly held belief that a backup MTA is required, indeed in many cases it can of course be beneficial e.g. high volume, geographic dispersion, and 'because you can'!

When I started running my own mail server (just for fun/personal use) I took advantage of my DNS provider offering a backup MTA. However, when I introduced greylisting to cut down on spam I was finding, as many do, that the backup MTA was being used by spammers (despite it having a less-preferential weighting) and given that I could not greylist on that server I was allowing spam through. I then opted to get rid of the backup MTA and, to the best of my knowledge, have not lost a single piece of mail.

Another argument for having a backup MTA is to make up for badly-configured MTAs that either don't retry later or are too impatient. However, I've never been a supporter of making allowances for those that don't 'play by the rules' - I'd much rather that (in this case) their customers complain to them that their mail is getting bounced. I concede others might have a different opinion on this though.

Mathew

Mathew

---

### Post by heimo on 2006-02-14
And that's why it's neccessary to be in control of your own backup mx (if you have one), because you basicly need same configuration as on your primary mx. Otherwise it'll be abused by spammers. But as stated, it's questionable if one needs backup mx.

---

### Post by robert_pectol on 2006-02-15
MJN, 
That's funny you mention it 'cause I had to do the same thing with our backup MX.  I had meticulously set up all sorts of blacklisting and bayesian filtering on our main server.  I lacked the energy and will to repeat it on the backup server (also some other technical issues became obstacles) so I left it as a basic, minimally configured backup mailserver for our domain, with no filtering, etc.  In no time, our backup MX started handling more mail than our primary!  Spam was infiltrating our users' Inboxes like mad!  In frustration, I removed the backup MX entry from our zone and disabled the backup mailserver.  Things have been humming along nicely ever since (about 2 years ago).  Anyway, thought I'd pass along my story.  :)

---

### Post by blu.gecko on 2006-02-15
Thanks for the well guided how-to on the email server,

Currently I was trying to setup a email server with nuonce.net "bluequartz"
but I was having password issues, and it installs more than what I was looking for,
apache, and more, I may upgrade the system to a intel p4 board/ 2.4ghz 478 CPU
1024 DDR 400, currently I only have 1 80gig sata150 but it is better than what I have now, I just have to decide if I really need my desktop around. I have a 160gig sata150 but I did a MS scan on the drive and it said that it wasnt healthy, I dont know if this is a MS thing, or if the drive is truely bad, it was given to me.

matt:rolleyes:

---


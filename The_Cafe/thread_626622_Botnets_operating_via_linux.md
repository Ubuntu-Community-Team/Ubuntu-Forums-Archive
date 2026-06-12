---
title: "Botnets operating via linux?"
date: 2007-11-29
forum: The Cafe
---

### Post by Bannor on 2007-11-29
[http://www.theregister.co.uk/2007/10/03/ebay_paypal_online_banking/](http://www.theregister.co.uk/2007/10/03/ebay_paypal_online_banking/)

> eBay: Botnets are Linux-happy
By Cade Metz in Santa Clara
Published Wednesday 3rd October 2007 03:30 GMT
eBay may soon offer online banking. It would seem.

This afternoon, while fielding questions about PayPal at Santa Clara University conference obsessed with "trust online," chief information security officer Dave Cullinane seemed to indicate eBay is interested in extending the popular online payment system to its logical conclusion.


"What we're trying to do is provide a trusted payment system that's within the community that constitutes eBay Inc., trying to be all things, but we aren't the bank yet," he said, before adding "Did I say yet?"

Cue audience laughter. But you have to wonder. Before joining eBay, Cullinane was the CISO at Washington Mutual, one of the largest banks in the US.

Or maybe we're just having fun.

During his hour-long keynote, Cullinane stuck mostly to generalizations when discussing eBay's security practices, but he had a few interesting things to say about his time with Washington Mutual.

At one point, he said, the bank spent a month as the largest phishing target in the country, and in fighting this ongoing problem, it has shutdown countless phishing sites surreptitiously installed on countless machines across the net.

"These things are incredibly sophisticated, and when they take over a computer, most [users] don't know it," he said. "With every single phishing site [Washington Mutual has] shutdown, not one person was aware been aware that their machine was compromised and used for phishing. That includes university servers and company servers and personal PCs and all sorts of things."

More interesting is that most of the compromised machines were not Windows machines. "The vast majority of [the phishing sites] we saw were on rootkit-ed Linux boxes, which was rather startling. We expected a predominance of Microsoft boxes and that wasn't the case."

This pleased Microsoft's head of Silicon Valley PR, who served as a conference sponsor.

Botnets are obviously a big problem for eBay as well, but Cullinane wouldn't quite say how big. "We see botnet attacks that are massive in their size and scope. We did a preliminary analysis and found over - I guess I'm not supposed to say that, what the number is - but we found a huge number of bots aimed specifically at eBay, trying to do things specifically to us."

The problem has become so bad that eBay operates under the assumption that every personal PC is infected, he says. "With the desktop, we're starting to run on the assumption that anyone who's trying to contact us from their own personal desktop is probably coming from a compromised computer." ®

Is this article to be believed?  Where can I go to check my linux systems?

---

### Post by p_quarles on 2007-11-29
Well, yeah, of course Linux boxes can be rootkitted, and once they are it's really hard to check them for anything. 

If you practice good security (strong passwords, security updates, not installing random binary files), you're very likely safe. If you have any concerns, though, you can try monitoring the local network for unexpected activity. You could also type "localhost" into your browser to find out if you're inadvertently hosting a web site.

---

### Post by timcredible on 2007-11-29
sounds like bs.  i'd love to hear some actual facts about what he said.  the part about an ms person being there as the sponsor could easily be the reason for the guy saying that linux machines are at fault.  i work in IT, and where i work, there's a lot of people that keep up to date with sans and other security information on a daily basis, and if there problems with linux being compromised like that, they'd be rubbing it my face 2 seconds after it happened.

---

### Post by tehet on 2007-11-29
That's a bad article with a bad title. It's about phishing, not botnets. If I were to set up a phishing site, I'd go to a cheap provider for hosting it. Big chance they run linux.

---

### Post by samjh on 2007-11-29
> **timcredible said:**
> sounds like bs.  i'd love to hear some actual facts about what he said.  the part about an ms person being there as the sponsor could easily be the reason for the guy saying that linux machines are at fault.  i work in IT, and where i work, there's a lot of people that keep up to date with sans and other security information on a daily basis, and if there problems with linux being compromised like that, they'd be rubbing it my face 2 seconds after it happened.

Linux rootkits are not bs at all.  It's old news, so probably not something your colleagues would bring up out of spite.

From SANS: [http://www.sans.org/reading_room/whitepapers/linux/901.php](http://www.sans.org/reading_room/whitepapers/linux/901.php)

Other references:
[http://www.linuxsecurity.com/content/view/127202/171/](http://www.linuxsecurity.com/content/view/127202/171/)
[http://www.usenix.org/publications/login/1999-9/features/rootkits.html](http://www.usenix.org/publications/login/1999-9/features/rootkits.html)

There are tools like chkrootkit and rkhunter, which help detect rootkits in Linux and Unix systems.

The level of complacency around here is truly terrible.  Linux isn't invulnerable, nor does restrictions to user-level access guarantee security.  Plenty of harm can be done at user-level without even a hint of trying for root access.

---

### Post by p_quarles on 2007-11-29
> **timcredible said:**
> sounds like bs.  i'd love to hear some actual facts about what he said.  the part about an ms person being there as the sponsor could easily be the reason for the guy saying that linux machines are at fault.  i work in IT, and where i work, there's a lot of people that keep up to date with sans and other security information on a daily basis, and if there problems with linux being compromised like that, they'd be rubbing it my face 2 seconds after it happened.
The fact that the event was MS-sponsored definitely casts some doubt on Callinane's statements . . . but it is true that poorly tended *nix boxes are highly vulnerable to that kind of attack. 

As for the market share, that's really difficult to tell. I know that my own server has had the fortune of becoming a target for a bunch of bots that identify themselves as running RedHat 7.3. Whether or not they are actually running on that is an open question. I highly doubt that E-Bay is putting its resources into scanning tens of thousands of attackers to find out if they're spoofing their agent IDs. Callinane indicates that they spent more time on getting them shut down. 

Will 2008 be the year of Linux on the botnet? :D That depends entirely on the security precautions users take.

---

### Post by Sporkman on 2007-11-29
I'm sure it has occured to hackers that applying misdirection re their assets' source OSs would be useful...

---

### Post by isecore on 2007-11-29
Rootkits are unfortunately a reality on Linux/BSD/Unix-boxen as well. That's where the term originated.

I'm very skeptical to the whole statement by Mr Ebay, especially since it was a Microsoft-sponsored event and he wouldn't want to upset their main investor.

But none the less, the more popular Ubuntu/Linux becomes with the general populace, the more focus has to be put on making it bullet-proof. People migrating from Windows don't generally have the experience or attitude towards security that most older Linux-users do. They will happily run whatever command is suggested or download whichever script is posted. This doesn't mean they're stupid, they're just putting too much faith in having an idiot-proof system that actually isn't idiot-proof.

Linux/UNIX/et al are by nature more secure than Windows-equivalents. That is not a myth. What is a myth however is that Linux is more secure regardless of what the user does. Linux is powerful, and with that power comes a certain degree of responsibility. Newbies rarely understand this, and when we try to explain it to them they will just respond "but I thought it was better and that I didn't have to worry about all the other crap?".

Anyhoo, kinda lost track there. As long as the user is somewhat aware of what's going on I very much doubt that Linux represents a majority of botnets and phishing sites. Windows is by design less secure in that sense. The major security issue with Linux is the user, and like I said, the more newbies coming to Linux the more secure the system has to be.

---

### Post by plun on 2007-11-29
I believe this article from LWN is more accurate about Linux and Botnets

"The desktop infection methods are not typically as useful for Linux boxes and so bot herders have turned to web application exploits as a means for collecting subverted machines. **Attacking servers has the additional advantage that they are usually machines with much greater resources: faster network connectivity, more storage, faster processors, etc**. The attacks are largely targeted at everyone's favorite Internet security whipping boy, PHP applications. Open source PHP applications are the main target as they are ubiquitous and typically easy to exploit as some recent research indicates. An additional benefit of targeting a higher level application is that it is a cross-platform exploit; the operating system and web server software are immaterial if the target is a PHP application. "

[http://lwn.net/Articles/222153/](http://lwn.net/Articles/222153/)

---

### Post by bonzodog on 2007-11-29
I think one of the other things to consider is that quite a few botnets are hosted on hackers own linux boxes, as the hackers can just acquire old hardware and make it a bot machine. 

I know some botnet masters who actually own small clusters of machines with botnets on them, and have convinced others to join the gang and only activate the botnet after an IRC meeting in which the hackers all agree to give up a small amount of bandwidth for the night, then activate the bot's themselves, in a deliberate attempt at an 'enemy' site. Typically, these hackers have access to good bandwidth, and then can throttle the amount that the bot is using.

---


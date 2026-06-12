---
title: "Just wondering - Own server vs AWS (Amazon)"
date: 2015-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by shawnblanchette on 2015-08-11
I know there will be vary different opinions on the subject. It's almost like asking a political party question, which should never be done on a forum.

Which is better to use, your own physical server running whatever you want (most would likely vm a server on the machine with a couple of backups) OR AWS? Please, no other cloud services. This is purely physical vs AWS.

I'm a small business. Sure, we can run our own physical server, I can continue to administer it, and our real only costs are Internet and vary small electric increase (barely noticeable). I have security concerns, several reasons for downtime (hardware failure, Internet down for whatever reason, prolonged electric loss, etc.), someone breaking in to the office and stealing the server(s), fire damaging the server(s), slow Internet, etc. It's definitely cheaper in the long run, as so long as the hardware holds up and I don't get DDOS'd too badly (although some providers will cover that if it's proven).

AWS is free for the first year (when I signed up). I administer the server. I don't have to worry about hardware failure, Internet going down because of bad or drunk driver or weather, or other things that can happen. I also don't have to worry so much about security, as Amazon has security built in to the thing. Sure, I need a firewall and to harden the server, but not I don't have to worry as much about security. I still have overage charge potential. Monthly fee can be higher than Internet in the office. The Internet will never get slow. Never! When I get mad at the server I can't throw it out the window (which is probably a good thing. Lol).


You may (will) have your own opinion(s) about the subject. I'd like to hear them, positive, negative, or mostly neutral. Even if you never used AWS. Even if you generally don't like Amazon. And please, let's respect every single opinion, even if it's completely wrong. We'll teach those wrong people. :)


Please enter comments below.

---

### Post by tgalati4 on 2015-08-11
For a small business, uptime is critical.  If your computer services are down (for whatever reason) then you lose money.  You could try setting up a hybrid system, running a local server has a snapshot/backup to the AWS server.  Or, continue to use your local hardware for 99% of your server needs and treat AWS as a backup.  You could split up your services and migrate them over from your local hardware to AWS over a time period, say 2 years.  Move one service at a time so that the transition is not disruptive. 

Let us know of your transition experiences.  AWS does have provisions for separating localities, so you can have multiple AWS locations in case one of their server farms goes down (like a natural disaster).

Because of the rise of micro-services, Docker, containers, Project Atomic, etc, the notion of maintaining a full AWS server may change in the next few years.

---

### Post by shawnblanchette on 2015-08-11
There's definitely truth there. I'm setting up completely on AWS instead of the old netbook I usually use (I'm not kidding!). I am utilizing their 1 year free, 750 hrs per month, EC2 VM. I obviously set up the Ubuntu server, 14.04. I am having a strange issue that I cannot figure out. It's not detrimental to my business operations at this time, because the real profit maker isn't ready yet. The issue is with MySQL/phpMyAdmin. I have the question in server section. No replies. I just may set up their e-commerce free software for now. I am okay using an HTML5 site I downloaded for free. I am modifying it right now. 

Other than that, I am vary happy with having another company host my server/VM. But I do like your idea of backing up on another machine. Perhaps I'll use my (small but good enough) NAS (software NAS on PC). One backup on AWS, one on my home office NAS. That's awesome! I don't even have to upgrade hardware like this! So long as we watch closely, AWS will save us money, time, downtime, security threats, slow Internet because of bad little boys downloading movies, etc. 


Thanks!

-Shawn

---


---
title: "Home router/FW/mail/web, etc"
date: 2009-09-18
forum: Server Platforms
---

### Post by bhart007 on 2009-09-18
Ok I know this type of question has been asked numerous times, and I promise i will search however while Ive got all this on my brain I wanted to post.

And this is for my house mind you so enterprise it is not ;p

Ive been an Untangle user now for almost 2 years.  Easy to setup, easy to administer, however lately either their updates have been sucking or something. Anyway I decided that I never really liked the interface and I have a second, more powerful box not doing anyhitng so why not replace it.

Anyway the feature I'm looking for would be Firewall, DNS caching, DHCP, Web filtering/proxy, Spam filtering.  A web server i think could be neat as I've wanted to stream mp3's from work but thats a tertiary concern.

So I looked at SME server, and IDK what it is but I just dont like it.  I def did not like the interface or that fact that there's no easy way to set FW rules, open ports, etc thru its web admin tool. So I found a tutorial on building what Im wanting for Ubuntu Server 6.10... I wonder how much of that stuff will come right over fully for 9.04?

Is there a way to use SpamAssassin to filter email traffic w/o the need for a Squirrelmail (insert other GPL mail server) setup locally?  Same goes for ClamAV scanning POP3/IMAP traffic?

Also Im REALLY liking Webmin.. Having trouble forwarding access to it from the outside world ATM (thru Untangle) but it is definately awesome.

---

### Post by bhart007 on 2009-09-18
OK I just found a tutorial for 9.04.. however after reading a little bit.. can anyone tell me which is better, ISPConfig or Webmin?

[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3")

---

### Post by openfly on 2009-09-18
Personally I prefer OpenBSD for this task.  PF is pretty phenomenal as a firewall / bandwidth shaping tool.  Linux in general isn't very intuitive and can be fairly buggy at times.  As much as I love Linux I don't think it's the right tool for a network routing job.

---

### Post by bhart007 on 2009-09-18
It's true that a smaller box running Pfsense or even M0n0wall might perform better in a firewall role, however in my circumstance I need a single solution for multiple roles.  I've used both before and they were awesome for what they did.  I'm just looking for more now.

---

### Post by openfly on 2009-09-18
If you aren't concerned about the googleplex reading your emails... and the all the associated possible problems with using them... you might consider offloading email to google apps.

I mean I understand if you want to host locally, but it's such an incredible pain managing an email server.  It doesn't make sense to do it for one person.... and spamassassin is going to CONSUME cpu resources.

btw look at MailScanner as an option.

---

### Post by b1rdman on 2009-09-18
Smoothwall Express 3.0 polar works real well.  I have been using now for about 5 years.  I run it by the shields up web site after every upgrade to test and tweak it if need be.  It has a Red hat  heritage.  My only complaint is that it is running the 26.16 kernel and I have been wanting to change to a usb modem that requires at the 26.19 kernel at the minimum for it to work.

[www.smoothwall.org](www.smoothwall.org)

Curtis

---

### Post by bhart007 on 2009-09-21
Ok I decided to go with a pfsense firewall, Ive used it in the past so theres some familiarity there.  Running it on a 1u P4 2.4gig with a gig of ram and a 40gig hdd.  Yeah I know over kill but its what Ive got.

Secondly I built an Ubuntu server 9.04 on an optiplx gx745, p4 3gig, 2gigs of ram and an 80gig hdd.  There again, yeah I know its overkill but this way I dont have to worry about anything consuming resources lol.

So far Ive installed Postfix, Squirrelmail, SpamAssassin, Apache2, MySQL, Procmail, and ISPConfig.

And to tell you the truth Im following a combination of two tutorials on the HowToForge website.  I dont have a clue what package is better however Im not asking cause I know theres alot of opinions and it mostly is based off a persons needs and/or comfort level ;p

So I think my issue at the moment is recieveing email on the new server.  And I'm not terribly sure where to look to determine whats actually going on.  Im using my ISP's server to send, I do have an MX record setup with no-ip and a valid ddns account.  Also Squirrelmail wont let me login, it complains about not being able to hit my mail server over imap (143). I dont know if the two are connected but Thunderbird complains about POP3 in the account I setup in it for the new server...so Im hoping its one thing affecting all three.

I know I havent provided enough info here to make an accurate guess but there again Im not sure what to post thats related.  I'll dig up whatever is needed.

Thanks!

---

### Post by bhart007 on 2009-09-21
Or should I start a new thread?

---

### Post by bhart007 on 2009-09-22
Hello?... McFly?

---

### Post by openfly on 2009-09-22
I think you should avoid running a mail server at all costs man.  That's still my opinion.

---

### Post by bhart007 on 2009-09-22
Nice.. so much for a helpful community.  Thanks for your input but I'll continue on.

---

### Post by hessiess on 2009-09-22
A lot of ISP's block port 25.

---

### Post by namakemono78 on 2009-09-29
Have you tried Astaro Security gateway ? [http://www.astaro.com/myastaro/sales_resources/business_briefings/asg_software_appliance]("http://www.astaro.com/myastaro/sales_resources/business_briefings/asg_software_appliance")

It is free for home users but limited to 10 ip's in the dhcp range. 
Excelent software, the nicest layout of a gateway I have ever used. 
Had to leave my box behind when i moved:(
Been trying to run one as a virtual appliance ever since I had to combine my server/gateway apps in one box. Just cant figure out the proper VMware network settings :(

        * Network Security 
        * Mail Security 
        * Web Security 
        * Easy Management
        * Astaro Up2Date Service 
        
Some people would probably say it's a bit overkill for homenetworks, but it's just a god d@mn beautiful piece of software :)

Well well, I guess IPTables will do for now.

---

### Post by bhart007 on 2009-10-02
I did check out Astaro when looking up other utm's.. I moved away from Untangle just because I wanted a bit more customized setup.  Well that an Untangles UI was fugly.

Astaro is still an option.. but setting it up manually is still an excellent learning experience.

---


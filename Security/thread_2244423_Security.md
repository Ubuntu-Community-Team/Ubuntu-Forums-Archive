---
title: "Security"
date: 2014-09-16
forum: Security
---

### Post by gordie692 on 2014-09-16
Hey guys me again for more info I've been reading the internet on security on Linux, Windows, firewalls, etc etc and All I really do is browse the net download a couple of songs and movies but more mostly browse the web and I do my banking I use to use chrome but now I'm using firefox. I hate EI but opera I like so I thinking on canning windows and running Ubuntu because as we speak I'm dual booting Ubuntu along with W7 and just wondering if Ubuntu would make my needs for the desktop I downloaded the ufw firewall from software center I do use chrome only for facebook twitter youtube and downloading and firefox for online banking and how secure is opera for online banking

---

### Post by TheFu on 2014-09-16
Seems you are excited about Linux and Ubuntu. Fantastic!  Glad you are here adding to the conversation.

From your description, you are performing high risk behaviors to the security of any operating system. Please be careful out there.

There isn't any "silver bullet" for security.  Being secure takes many different things:
* patched OS
* patched applications
* avoiding nasty parts of the internet
* avoiding high-risk internet activities
* avoiding high-risk programs (PDF files, Flash, Java-applets, and PHP-based websites not run by professionals)

ufw is just an interface over iptables. It is NOT the linux firewall. It is purely an interface which makes iptables rules easier.  You may want to use gufw.

For online banking, I boot into an ISO Linux that can't store anything, can't remember anything, and only gets used for financial purposes.  This is the recommendation of many, many respected security professionals, including Brian Krebbs. [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/)
[http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html](http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html) - from 2009.

Computer security is a moving target. Every day there are new attacks.  I've seen attacks for 2-factor-authentication recently which reduce the difficulty from impossible to "try these thousand pins" - poorly implemented "security solutions" are often less secure than a good password and careful management of our systems.

Whether Ubuntu can replace Windows as your desktop is a hard question.
[http://blog.jdpfu.com/2010/03/05/why-grandma-should-be-using-linux](http://blog.jdpfu.com/2010/03/05/why-grandma-should-be-using-linux) describes migrating a user from Windows to Linux with a few things to check.  I migrated my 79 yr old mother to Lubuntu years ago after she made 1 bad decision and clicked a link in an email from a granddaughter.  That was all it took to get hopelessly infected.  Since moving to Linux, she's not had any security-related issues, though she did die last year from unrelated causes.

I've included my signature which has many computer security links.  One of the best is the **Ubuntu Basic Security Page**.  I've written articles about computer security for years now.  [http://blog.jdpfu.com/tag/security](http://blog.jdpfu.com/tag/security) should provide a list.

Anyway - you didn't really ask a clear question, so I hope this helps with your research.  Please have great backups. Versioned backups are the #1 security tool and more important than anything else.

---

### Post by gordie692 on 2014-09-16
thanks for post even downloading is a thread or do you mean like those odd web sites the reason I like Ubuntu or any linux distro is it never slows down unlike Windows with all that spyware, adware, malware an antivirus crap and I have a couple of games I play still but to the most Linux can do all my needs to web browsing, emails, etc

---

### Post by gordie692 on 2014-09-16
How about accounts like steam or GOG.com are they even threats

---

### Post by whitesmith on 2014-09-17
Another possibility is to use a hosts file that is kept up-to-date. Garbage in, garbage out doesn't apply if the patient is protected with redirects to 127.0.0.1 in the case of suspicious sites. I have a rather large hosts file that I'm willing to share.

---

### Post by TheFu on 2014-09-17
> **whitesmith said:**
> Another possibility is to use a hosts file that is kept up-to-date. Garbage in, garbage out doesn't apply if the patient is protected with redirects to 127.0.0.1 in the case of suspicious sites. I have a rather large hosts file that I'm willing to share.

Uh ... I agree completely. [http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file) - notice the author of that article?  Been blocking unwanted parts of the internet for almost 20 yrs myself.  ;)

---

### Post by HermanAB on 2014-09-18
Uhmmm... I do military work, so I am very attuned to security issues at work.  For personal use, I recommend that you relax a bit though.

Just by using Ubuntu out of the box, your machine is enormously much more secure than a Windows system (various reasons).  So just relax and enjoy your 'new' computer.

---


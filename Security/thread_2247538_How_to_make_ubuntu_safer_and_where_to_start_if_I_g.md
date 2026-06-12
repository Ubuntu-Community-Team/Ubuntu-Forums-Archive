---
title: "How to make ubuntu safer and where to start if I get hack?"
date: 2014-10-08
forum: Security
---

### Post by nicolas24 on 2014-10-08
Hello,

In the last year I had recurrent problem at job with different server, the were modified by "hacker" to give different service.  Most of the time we get back on a backup because we are not sure of what they modified.  Right now I am admin of 4 web server and I had problem with all of them in the last year. 3 ubuntu, one osx.  All the server run apache, mysql, php, they are protected by a firewall of enterprise with different rule for the business, but the ftp+80 are accessible outside.  I do all update on the server, but some website could run on older version of joomla, wordpress, spip.  Some of the attack redirect our client to a website in russia who sell watch, other use my server as proxy, use the server to send spam, or just make the website not working because the hacker was able to modify *.php file on the website, but it seem to be all broke for no purpose.

So what is the best way to protect the server without to much complication and time and when the service is broken, how to find the source of the problem in an effective way?

Usually I look to the log, I look for the file modified in the last 1-2-3 days, and after I have difficulty to have good idea!

Thanks

---

### Post by matt_symes on 2014-10-08
Hi

That's a huge question and very much depends on your setup and what you have done to secure your systems already.

My advice is to ask your boss to hire a penetration tester on short term contact to find the vulnerabilities in your network and fix them. While the pen tester is there, learn as much from them as possible.

See if you can persuade your boss to put you on some security courses as well.

You'll get general advice on this forum such as, don't use ftp and different ways to lock down apache and php and ways to lock down your firewall, but honestly people get paid for the type of question you have asked on this forum.

See what others post though.

Kind regards

---

### Post by cariboo on 2014-10-08
If you can, stop using FTP, and use SFTP instead. There have been enough problems with insecure FTP servers, that is worth shutting them down.

---

### Post by bashiergui on 2014-10-08
> So what is the best way to protect the server without to much complication and time If you figure that out you can make loads of cash as a consultant. > and when the service is broken, how to find the source of the problem in an effective way?The effective way is to hire people deeply knowledgeable about system administration, incident response and digital forensics. That's also the expensive way. I have no idea how to do that cheaply.

---

### Post by Habitual on 2014-10-09
> **bashiergui said:**
> If you figure that out you can make loads of cash as a consultant. The effective way is to hire people deeply knowledgeable about system administration, incident response and digital forensics. That's also the expensive way. I have no idea how to do that cheaply. Ah, the old "Cheap, Fast, or Correct, pick any 2" conundrum.
My response would be Proactive is better than Reactive.

Keep software up to date.
Read disclosure mailings/boards. Subscribe or RSS feed a few, here's [one.]("http://www.mail-archive.com/bugtraq@securityfocus.com/")
Deny passwords to servers, use ssh-keys and don''t allow root to login.
**rsyslog to a remote host**.
fail2ban, logwatch, etc...
deny ftp in favor of sftp
[Harden apache and php and mysql]("https://www.linuxquestions.org/questions/linux-security-4/security-references-45261/#post2122954")

Server Security is a Full Time Job. Trust me.

---

### Post by open2reason on 2014-10-10
As seen on the net
> When a man with money meets a man with experience, the man with experience  leaves with money and the man with money leaves with experience.

As others have suggested you may well need to pay the going rate for the knowledge you lack as at this moment in time the bad guys know more than you do and from your point of view that is unacceptable. 

ATB

---


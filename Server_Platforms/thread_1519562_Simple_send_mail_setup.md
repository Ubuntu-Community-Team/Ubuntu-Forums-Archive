---
title: "Simple send mail setup"
date: 2010-06-28
forum: Server Platforms
---

### Post by duneratt on 2010-06-28
I have a "headless" box running Karmic on my home network, set up as a webserver (mostly). It sits behind a modem with a firewall and wireless internet from an area Provider. I virtual host a few websites and have SMF, KTools Photostore, and Coppermine running on Apache2, PHP, and MySQL. I used to have SendMail running fine but had to rebuild the box from scratch a few times and have since upgraded to Karmic. Now I can't get the email to work properly. I've put it off for a good while now to try and figure out how to keep the spammers from hijacking my box as their own personal mail server. I need to get it working though and have both SendMail and Exim4 installed. I got Exim4 to the point where I can send email command-line but can't get it to work for the SMF forum without getting a "connection refused" error. I'm not really a Linux guru so I mostly flail about as I try to set things up until something finally works... lol. Anyway, I hope I have the hosts file and everything set up correctly so that may be a problem and I have port 80 port-forwarded from the modem but not port 25. I have the send_path set to the SendMail folder. I did this after I set up Exim4 and tried its sendmail path to see if it would work. Should I set it back to the Exim4 SendMail folder? If anyone has any suggestions, I'm open to them. The main question I have is: How would someone who really knows what they are doing set up a mail "send only" configuration so that it would send emails via the above mentioned applications and possibly scale to a full mail service later? Am I way "off base"? What is a good and simple setup?

---


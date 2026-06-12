---
title: "SMTP Setup"
date: 2006-03-23
forum: Server Platforms
---

### Post by Freddie on 2006-03-23
I am trying to move all of my servers over to *nix platforms. It has been going quite well so far, but I am currently stuck trying to move my SMTP server over to Linux.

I have been following the Ubuntu server guide so far ([http://doc.ubuntu.com/ubuntu/serverguide/C/email-services.html](http://doc.ubuntu.com/ubuntu/serverguide/C/email-services.html)) and decided to install the Postfix server. I have followed the guide up to the part where you telnet your mail server (in my case, because I am working internally I did: telnet 192.168.0.5 25) and the output seems good. I am not sure what I need to do now.

I am on a static IP address, and have typed in my external host/domainname in place of mail.example.com throughout the guide. But I am now at a loss as to what I should do, or even if it is working properly. I under no circumstances want to make my SMTP server publically accessable after hering stores from friends about how they are often used by spammers to send junk, so I only want it to be accessable from my internal network (192.168.0.x).

How do I check to see if it is configured correctly is probably my frist question.
Thanks for all of your help.

---


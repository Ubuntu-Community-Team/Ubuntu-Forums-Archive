---
title: "Postfix logs"
date: 2006-03-31
forum: Server Platforms
---

### Post by s7eam on 2006-03-31
Can anybody help me with clarifying this postfix log (mail.log).
When I issued command **netstat -a** I sew that my port 25 was connected to IP address 216.163.188.58. The number 8 for IP-adderess in logs below is missing though.

I was not sending any mails from my server and the server is only used as webserver but I installed postfix for sendmail reason which enables me possiblity to send mail from contact form. I replaced my webadress with localhost below also.

Thank you in forward!

```
Mar 28 13:00:02 localhost postfix/qmgr[7573]: 5BF3C5D836F: removed
Mar 28 13:20:01 localhost postfix/pickup[7572]: A71815D836F: uid=109 from=<smmsp>
Mar 28 13:20:01 localhost postfix/cleanup[7710]: A71815D836F: message-id=<20060328112001.A71815D836F@localhost.localdomain>
Mar 28 13:20:01 localhost postfix/qmgr[7573]: A71815D836F: from=<smmsp@noreply@localhost>, size=662, nrcpt=1 (queue active)
Mar 28 13:20:03 localhost postfix/smtp[7712]: A71815D836F: to=<root@noreply@localhost>, orig_to=<root>, relay=eforwardct.name-services.com[216.163.188.5
8], delay=2, status=sent (250 Ok: queued as C66DF13B68B)
Mar 28 13:20:03 localhost postfix/qmgr[7573]: A71815D836F: removed
Mar 28 13:40:01 localhost postfix/pickup[7713]: EC4BB5D836F: uid=109 from=<smmsp>
Mar 28 13:40:01 localhost postfix/cleanup[7738]: EC4BB5D836F: message-id=<20060328114001.EC4BB5D836F@localhost.localdomain>
Mar 28 13:40:01 localhost postfix/qmgr[7573]: EC4BB5D836F: from=<smmsp@noreply@localhost>, size=662, nrcpt=1 (queue active)
Mar 28 13:40:03 localhost postfix/smtp[7740]: EC4BB5D836F: to=<root@noreply@localhost>, orig_to=<root>, relay=eforwardct.name-services.com[216.163.188.5
8], delay=2, status=sent (250 Ok: queued as 13ABBF7861)
Mar 28 13:40:03 localhost postfix/qmgr[7573]: EC4BB5D836F: removed
Mar 28 14:00:01 localhost postfix/pickup[7713]: 2F6C25D836F: uid=109 from=<smmsp>
Mar 28 14:00:01 localhost postfix/cleanup[7757]: 2F6C25D836F: message-id=<20060328120001.2F6C25D836F@localhost.localdomain>
Mar 28 14:00:01 localhost postfix/qmgr[7573]: 2F6C25D836F: from=<smmsp@noreply@localhost>, size=662, nrcpt=1 (queue active)
Mar 28 14:00:02 localhost postfix/smtp[7759]: 2F6C25D836F: to=<root@noreply@localhost>, orig_to=<root>, relay=eforwardct.name-services.com[216.163.188.5
8], delay=1, status=sent (250 Ok: queued as 58155DC1CC)
Mar 28 14:00:02 localhost postfix/qmgr[7573]: 2F6C25D836F: removed
Mar 28 14:20:01 localhost postfix/pickup[7713]: 7FC7E5D836F: uid=109 from=<smmsp>
Mar 28 14:20:01 localhost postfix/cleanup[7786]: 7FC7E5D836F: message-id=<20060328122001.7FC7E5D836F@localhost.localdomain>
Mar 28 14:20:01 localhost postfix/qmgr[7573]: 7FC7E5D836F: from=<smmsp@noreply@localhost>, size=662, nrcpt=1 (queue active)
Mar 28 14:20:13 localhost postfix/smtp[7788]: 7FC7E5D836F: to=<root@noreply@localhost>, orig_to=<root>, relay=eforwardct.name-services.com[216.163.188.5
```

---

### Post by s7eam on 2006-03-31
No one knows what this could mean?

---

### Post by LordHunter317 on 2006-04-01
Looks to me like someone is using your box as relay, possibly by compromising it.

---

### Post by s7eam on 2006-04-01
[QUOTE=LordHunter317]Looks to me like someone is using your box as relay, possibly by compromising it.[/QUOTE]

That's what I thought. When you look at the log the mails was sent like every second. Does this mean that my box was compromised or just deamon postfix?

I've checked my logs but I've not found any break into the system but I've seen some strange hack attempt on apache.

---

### Post by LordHunter317 on 2006-04-01
[QUOTE=s7eam]That's what I thought. When you look at the log the mails was sent like every second. Does this mean that my box was compromised or just deamon postfix?[/quote]It doesn't matter, the procedure is the same.  Cut it from the Internet, wipe it, and reinstall.  Audit everything before replacing it.

If you want ot figure out how they got in, take an image of the disk and do forensics on that.

---

### Post by s7eam on 2006-04-01
[QUOTE=LordHunter317]It doesn't matter, the procedure is the same.  Cut it from the Internet, wipe it, and reinstall.  Audit everything before replacing it.

If you want ot figure out how they got in, take an image of the disk and do forensics on that.[/QUOTE]

You've right!
I think I will do so before it's too late. 

Thank you for advices.

---

### Post by LordHunter317 on 2006-04-01
That being said, in all likelyhood, they got in through Apache, probably a PHP application.  

You don't appear to be an open relay from the logs you posted, and that's the most likely vector.  What did you have installed, specifically?

---

### Post by s7eam on 2006-04-03
I've been installed Apache2,PHP5,MySQL5,Postfix,proftpd,clamav,sshd and all dependencing packages. 

I've checked my logs on all deamons and the only failure I could possibly find could bee as you said through apache. My sshd doesn't allow root login and I allways choose strong passwords. Beside this I even changed default ports for the deamons like sshd and proftpd.

Before I switched to Ubuntu I ran FreeBSD as WWW server and OpenBSD as Firewall and never had any troubles. Now I have removed my OpenBSD firewall and instead using my Linksys WRT54G as firewall plus shorewall on Ubuntu. The reason why I switched to Ubuntu on the serverside was because of easy to maintain and I use it on my desktop computers as well so I gave it a chance on server side also. Well, I don't blame Ubuntu in any way I blame my self for not being carefull when it comes to hardening my box.

Now I run chrooted Apache instead and will keep my eye on the server more often and check if everything goes well. 

I'll also try to export logs to root-tail on my desktop so I can monitor it in real time. I just have to find out how to do this cause I've never tried this before.

---


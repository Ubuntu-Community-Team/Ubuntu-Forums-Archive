---
title: "SFTP Default Port Issue"
date: 2007-05-11
forum: Server Platforms
---

### Post by Dark Elitist on 2007-05-11
Hey all,

I was following the general recommendations to change the default ports of SSH, FTP, etc. to something less obvious and otherwise not standard and have encountered a problem as a result.

Regular FTP worked and SFTP (FTP over SSH2) worked fine, SSL and TLS never did.  I changed the default FTP port to 40605 and the SSH port to 40965.  After doing this, only FTP works but not SFTP.  SSH also worked fine.

To troubleshoot, I changed the default SSH port back to 22.  Still, no good.  Regular FTP works, SFTP doesn't.

I'm assuming there is some SFTP related configuration file that needs editing if the default FTP port is changed from 21 to something else?

Anyone have a solution?

Also, any guides to get SSL/TLS working properly?  Followed the one here, no luck.

---

### Post by MJN on 2007-05-11
'General' recommendations? I beg to differ on that one...

Sure, move the odd port if you're getting regular brute-force attacks (SSH for example) but don't consider it the be all and end all of security, indeed their is an argument that it's no security at all. But the other ports? SSL? Why?

I appreciate this doesn't answer your question, but I feel it's more important to get you to question your own motives rather than simply answering what you thought might be an 'innocent' question. Does that make sense? Hope it doesn't come across as patronising...

Having well known services on well known ports has many benefits, indeed it is why the whole concept came about.

Edit: Having re-read your post a couple of times I'm wondering now if I've got the wrong end of the stick and that you haven't been moving any SSL-related services around but that you're simply struggling to get them going in the first place?

Mathew

---

### Post by Dark Elitist on 2007-05-11
> **MJN said:**
> 'General' recommendations? I beg to differ on that one...

Sure, move the odd port if you're getting regular brute-force attacks (SSH for example) but don't consider it the be all and end all of security, indeed their is an argument that it's no security at all. But the other ports? SSL? Why?

I appreciate this doesn't answer your question, but I feel it's more important to get you to question your own motives rather than simply answering what you thought might be an 'innocent' question. Does that make sense? Hope it doesn't come across as patronising...

Having well known services on well known ports has many benefits, indeed it is why the whole concept came about.

Edit: Having re-read your post a couple of times I'm wondering now if I've got the wrong end of the stick and that you haven't been moving any SSL-related services around but that you're simply struggling to get them going in the first place?

Mathew

I know it is not the be all and end all of security, just something that seems to be recommended commonly.  I have already taken the other necessary steps for security.  You ask other ports, why?  I only changed the ports for SSH and FTP.  SSL/TLS support is good for older FTP clients in certain setups that don't quite support SFTP (FTP over SSH2).  Some web based FTP clients also don't support SFTP.

Yes, I know it has many benefits.  I did not just start using computers yesterday, only Linux.  :) 

In response to your edit, here is all I did:

1) Changed default FTP port.
2) Changed default SSH port.

After doing so, FTP and SSH still work fine, but SFTP which worked with the default port setup no longer works.  I was merely wondering how to fix this and assumed there is probably a configuration file that needs to be edited somewhere to specify to SFTP that the ports have changed so that it works again.

In regards to SSL/TLS, I was merely trying to install it and activate it following this forum's guide but to no avail does it work and that was just a bonus question.

Speaking of Bonus Questions, anybody know when the brute force prevention for SSH repository listed on UbuntuGuide.org will be up?

Also, any other security tools such as fail2ban to help with security?  Thanks!

---

### Post by MJN on 2007-05-12
Okay, I understand a bit more now.

Taking your queries in reverse order, fail2ban would indeed be a very good bet - does exactly what it says on the tin and does it well. Indeed, I'd recommend using it *instead* of moving ports....

I don't know about the brute force but with fail2ban you won't need it - it will satisfy the requirement. (Can you tell I like it? I used to use denyhosts but whilst it worked I much prefer the simplicity of fail2ban)

Regarding SFTP, which package of it are you using? Is it not the same as your FTP service?

Mathew

---

### Post by Dark Elitist on 2007-05-12
> **MJN said:**
> Okay, I understand a bit more now.

Taking your queries in reverse order, fail2ban would indeed be a very good bet - does exactly what it says on the tin and does it well. Indeed, I'd recommend using it *instead* of moving ports....

I don't know about the brute force but with fail2ban you won't need it - it will satisfy the requirement. (Can you tell I like it? I used to use denyhosts but whilst it worked I much prefer the simplicity of fail2ban)

Regarding SFTP, which package of it are you using? Is it not the same as your FTP service?

Mathew

Alright.  I put everything back on the default port and SFTP works fine.  I installed fail2ban - is there any custom configuration it needs or does the default satisfy?

The SFTP package I am using is the default one that came with proftpd or SSH, I forget which.  Seems to work fine with default ports and I guess that is more secure than SSL / TLS, although it would be nice to have it all working for backwards compatibility reasons.

Does fail2ban secure proftpd and apache2 also?  Any suggestions for keeping the aforementioned secure?  I followed a pretty good set of guides for apache2 and Nessus says it is alright so I think it is just proftpd and ssh I have to work on locking down a pinch more.

Btw.  I checked the logs of the computer in question and brute force attacks have been attempted from ip addresses in China and Russia.  :P  They all appear to have failed, so far at least!

---


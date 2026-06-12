---
title: "Dovecot and postfix"
date: 2014-06-09
forum: Server Platforms
---

### Post by hockey97 on 2014-06-09
Hi, well right now I have a problem. I don't know if the problem is with dovecot or postfix or both?? 

Well anyways, I can send an e-mail to my  e-mail address but when I use thunderbird or anything to check my mailbox I see it empty even though I tested it by sending an e-mail from gmail.com to my account. I get no error message  or get the mail sent back to my gmail account. So, I assume it went thru without any issues. However, dovecot will show my mailbox empty. 

Then if I try and send an e-mail out from my mail server aka postfix to gmail email account. I get a nice error message saying relay access denied. I can only send a message to e-mail accounts within my mail server. However, I still won't see the mailbox to hav an e-mail in it... however when sent... I would see in the sent folder my e-mail there. 

I am using ssl/tls for logging in. I would like to know what I can do to fix the problem. I am not using linux but using unix freebsd and I have tried their forums already and the help provided there didn't help any. If someone could give me any suggestions on where I should look to figure out how the mail is being delivered and what folder. I am assuming that postfix is storing the e-mails in another folder then what I have dovecot setup with. Also  if anyone can give me any suggestions to fix the sending the e-mail out on why I get a relay error message and how to fix it. I would appreciate it. I know this is a Ubuntu / linux form but I tried to ask here for any possible suggestions that would lead me to a solution to the problems I am having.

Thank you for your time... =P~

---

### Post by SeijiSensei on 2014-06-09
Your first stop should be your ISP. Most ISPs forbid servers on residential accounts and block access to port 25 (SMTP).  They also often block outbound connections to port 25 on remote servers to cut down on spam from infected Windows computers.  Call your ISP and ask about their policies with regards to mail servers.

---

### Post by hockey97 on 2014-06-09
No, that's perfectly fine. My servers are in my own datacenter. I am running them out from a commercial zone under my business name.  I got my server up and running before. I had freebsd 8.1 and on their forums they wouldn't give me advice unless I upgraded  to freebsd 8.4 and while the upgrade some stuff got messed up. 

My servers were running perfectly before but the postfix and dovecot got upgraded and I notice previous config settings were outdated and no longer needed. 

However, right now I decided to add SSL to my mail server. So, I followed tutorials and got it working. I can login to my mail server. It's just that I cannot send or receive e-mail... I can send mail only to my own mail server. If I try gmail, yahoo, aol. mail I get relay access denied error.  From my undestanding of this error... I am guessing it means that the e-mail is trying to be sent via gmail, or vice verse where gmail is trying to relay e-mail thru my mail server.

regardless I  don't get the e-mail sent back or at least can see it. I don't see it being sent to gmail, or aol, or yahoo etc. 
I would think the error relay denied means we cannot use their e-mail server to forward e-mail  to another destination.
I don't need to relay anything.  I just want to write an e-mail and send it directly to gmail.com or aol.com or yahoo.com etc.

My postfix config is setup like this: [http://www.purplehat.org/?page_id=8](http://www.purplehat.org/?page_id=8)

---


---
title: "catch-all configuration for postfix"
date: 2008-09-07
forum: Server Platforms
---

### Post by omid1979 on 2008-09-07
hi all , 
I am new to use ubuntu as my company mail server. 
we have local server that using MDaemon mail server and now I was migrate to ubuntu . I have a problem to configure catch-all on ubuntu postix mailserver , 
on our old server we have a catch-all account on our ISP mail server that when we have lost our connection , all of our mail stored on ISP mail server on sigle account ( [email]alluser@domain.com[/email]  ) and on first connection MDaemon mail server connect to ISP mail server using domain pop and received all mail and store to users local mailbox on mdaemon mail server ,
during this upgrade I was configure postfix to receive user's mail directly and it work fine , 
I want to enable my mailserver to work with ISP too . because we have some downtime on our Internet link and I don't want to have lost on my email , 
any one can give me a solution to have backup MX on our ISP and how I can enable post fix to connect every 1 hours to isp mail server and received mail and store them to local mail server .

I know our ISP mail server using MailEnable and I want to connect via pop3 to receive all mail from that one , 

waiting for your quick reply 

Regards 
Omid Hosseini

---


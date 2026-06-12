---
title: "Problem with email on my Ubuntu Server 12.04"
date: 2013-02-19
forum: Server Platforms
---

### Post by nightfly13 on 2013-02-19
Dear Community...
 
I setup an ubuntu server 12.04, behind an dynamic IP, so for that i use no-ip service to keep this site hosted on this server online... Until now i'm runing without any problem, but know i need to setup the email accounts, because the site need the registration confirmation and for that send an email for the new user....
 
With ISPconfig3 i setup one email account, but i have problems sending email for yahoo.com, gmail, etc, etc, on same cases the email send by me never reach the receipient :(
 
I try allot of thinks, but with no success... So my question is... I have another site, hosted in one hosting company with emailserver with a Static IP... My question is, can i setup, configure and use the email created on my own server with ISPConfig3, with the mailserver from my other site, outside of my server and who had an static ip????
 
It's possible???? Can anyone explain me how???? (Step by step, please)
 
 
Best Regards
João

---

### Post by GordThompson on 2013-02-20
> **nightfly13 said:**
> I setup an ubuntu server 12.04, behind an dynamic IP, so for that i use no-ip service to keep this site hosted on this server online... Until now i'm runing without any problem, but know i need to setup the email accounts, because the site need the registration confirmation and for that send an email for the new user....

With ISPconfig3 i setup one email account, but i have problems sending email for yahoo.com, gmail, etc, etc, on same cases the email send by me never reach the receipient
As you have noticed, if you have a machine with a dynamic IP address and it tries to send mail directly to recipients' mail servers then a great many of those messages will bounce. That's because mainstream mail servers reject messages originating from dynamic IP blocks on the assumption that they are spam.

> **nightfly13 said:**
> I try allot of thinks, but with no success... So my question is... I have another site, hosted in one hosting company with emailserver with a Static IP... My question is, can i setup, configure and use the email created on my own server with ISPConfig3, with the mailserver from my other site, outside of my server and who had an static ip????

It's possible????
I would be willing to bet that it's possible but it would require that you configure your "other server" to relay mail **only from your "dynamic IP server"**. Note that you don't want to configure your "other server" to relay mail from just anybody, because that would quickly be exploited as an "open relay" and it would get blocked too.

A better solution might be to determine the official mail server belonging to the ISP that administers your dynamic IP address, and configure your server to use that mail server as a "smarthost". However, note that if your server generates a lot of messages, or if it relays spam messages or spam backscatter (bounced spam), then your ISP may start blocking your messages itself.

Summary: 

1. If you set up a server on a dynamic IP address and try to use it to send mail you need to be very careful about what you send and how you send it.

2. If you have a mail server on a static IP address you need to be very careful about what you relay.

---


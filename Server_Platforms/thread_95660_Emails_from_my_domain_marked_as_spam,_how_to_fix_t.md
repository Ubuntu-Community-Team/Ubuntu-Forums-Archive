---
title: "Emails from my domain marked as spam, how to fix this?"
date: 2005-11-27
forum: Server Platforms
---

### Post by s0c0 on 2005-11-27
As noted in the title.  Emails coming from my domain are being marked as SPAM, at least when sending to yahoo.  I am infact using yahoo's domain/DNS serverice so this suprises me since they are hosting my MX record.  I am also using them as my relay.

For my email I am running a POP3 using dovecot + postfix for MTA.  I have taken precautions against being used by spammers by requiring SMTP authenication through SASL.

I have already emailed Yahoo in regards to this.  Is there anything else I can do?

Please advise.

---

### Post by ceejay13 on 2005-11-27
Are you authorising with the Yahoo SMTP server?

If not then I used [this article]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html") as my ISP server was reporting that relaying was not allowed.

---

### Post by LordHunter317 on 2005-11-27
Wait, your domain has been blackelisted even though you're sending mail through your ISP's mail servers?

---

### Post by cocophone on 2005-11-28
I have my domain hosted by yahoo.  Yahoo told me that I would not be able to use yahoo as a relay host with the hosting plan I have at yahoo. ( I have a low price plan).  I started using dyndns.com relay service.  It's called Mail Hop Outbound.   Its $14.95 a year for 150 relays a day. It works great and I got it to work on the first try with postfix.

---

### Post by s0c0 on 2005-12-01
> 
I have my domain hosted by yahoo. Yahoo told me that I would not be able to use yahoo as a relay host with the hosting plan I have at yahoo. ( I have a low price plan). I started using dyndns.com relay service. It's called Mail Hop Outbound. Its $14.95 a year for 150 relays a day. It works great and I got it to work on the first try with postfix.


Strange when I emailed Yahoo I blatantly told them that I was using them as my relay, but I don't think the person who read my email was too technical either as she did not come even remotely close to answering my question.

Are emails sent from your domain showing up SPAM-type folders (like Yahoo's bulk mail) for hotmail/yahoo type email services?

---

### Post by cocophone on 2005-12-01
What happened to me was that some email I was sending from my server running postfix was getting returned to me by the receipient's mail server.  

Their server was saying I was on a dynamic ip refused my email.

Since I started using the Mailhop from dyndns.com, I'm not getting any email returned.

Robert

---

### Post by ceejay13 on 2005-12-01
I had the same problem.  SORBS sees that you are in a dynamic range of IP and as Yahoo use this as one of their checks they then return your email and diplomatically tell you that you 'could' be spamming and as you are on a dynamic range of IP's they won't accept the mail.  (BTW SpamAssassin can also use the SORBS database - but just add it to their score rather than completely reject.) 

So, I then tried my ISP, who refused to be used as a relay until I logged in using my username and password when sending.  I believe some ISP's just need a read of your mailbox before sending mails.

All is OK now.  My hosted mail server is seen as being trustworthy.

---

### Post by s0c0 on 2005-12-02
Strange.  I have had no such problems as of yet.  I will change my relay though and use a mail-hop service like you had mentioned.

---


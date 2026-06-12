---
title: "Force SASL Authentication in POSTFIX for Mail Relay"
date: 2012-04-24
forum: Server Platforms
---

### Post by 95yj on 2012-04-24
I have a fairly new installation of Ubuntu server 11.04 with a barebones installation of POSTFIX.  I followed all the instructions in [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) and have it up and running using SASL authentication.  The main purpose of installing email on the server is to provide email relay from my network monitoring gear.  The relay is working fine and is restricted to only the networks and nodes that are allowed to send mail.  Authentication is working fine also.

I want to require SASL authentication and cannot find any documents on how to do this.  Currently I can send mail relay if I authenticate or with no authentication and this isn't as secure as I would like.

Does anyone have any documentation on the parameters required to force authentication for mail relay?

---

### Post by 95yj on 2012-04-25
Well, that was pretty simple even though I couldn't find the documentation and there were no answers on posts from the same question on this forum.

In etc/postfix/main.cf edit the restrictions line from:

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

to remove permit_mynetworks

---

### Post by webservervideos on 2012-04-25
> **95yj said:**
> Well, that was pretty simple even though I couldn't find the documentation and there were no answers on posts from the same question on this forum.

In etc/postfix/main.cf edit the restrictions line from:

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

to remove permit_mynetworks

not quite sure that 'forces' sasl...it just permits it without reject.

---

### Post by 95yj on 2012-04-25
> **webservervideos said:**
> not quite sure that 'forces' sasl...it just permits it without reject.

OK, what I am trying to accomplish is to only allow certain networks or nodes to be able to relay mail while requiring them to use SASL.  

Listing networks/nodes in the mynetworks statement appears to restrict mail relay to only those networks/nodes listed in the statement as verified by testing.  

Removing the permit_mynetworks and having permit_sasl_authenticated as the only permit in smtpd_recipient_restrictions appears to force mail relay to use authentication and reject relay when attempting to relay without authentication also verified via testing.

Correct me if I am mistaken and expound please.  Thanks much.

---


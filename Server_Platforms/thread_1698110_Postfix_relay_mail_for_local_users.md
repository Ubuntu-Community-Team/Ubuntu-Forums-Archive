---
title: "Postfix relay mail for local users"
date: 2011-03-01
forum: Server Platforms
---

### Post by NessDan on 2011-03-01
I have a mail server running Postfix and the problem I'm running into is that when trying to send mail, I get a "relay access denied" error.

Inside my main.cf, I did not specify 'smtpd_recipient_restrictions' so by default, the variable is:

```
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
```

The 'mynetworks' variable looks like this:
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

I use Thunderbird to log into my main user account (which I use for SSH and Mail) on the server. I can receive mail from the outside just fine, but sending mail non-locally ends up with a "Relay access denied." error.

Now, I just want to have Postfix allow authenticated users to send mail. Haven't I already authenticated myself by logging into the account during the Thunderbird Account Creation? Why is my mail not being relayed?

If any more information is needed, please let me know. I'd like to get this figured out soon!

---

### Post by dipeshmehta on 2011-03-01
Which guide did you followed setting up your server?  (It would help understanding your setup)

Anyway, you could setup sasl authentication for postfix/smtp and add following into smtpd_recipient_restrictions

```
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
```

---

### Post by NessDan on 2011-03-02
Thank you for the reply!

As to the guide I followed, I followed many, many different guides. I was having a constant problem with this so I switched between guide to guide but I only edited my main.cf (never touched Dovecot)

Compared to the stock settings for Postfix, the only things I changed were the TLS settings so I have encryption, set up the relayhost so I could relay mail through my ISP's SMTP server, and I've recently tried to set up SASL but I'm hesitant to go this way.

Reason I'm hesitant to go towards SASL is because to me, it seems like adding an extra layer of security on top of the normal user login. [From the tutorial I'm looking at]("http://www.postfix.org/SASL_README.html") and to my understanding, doesn't SASL require me to have a separate file with authenticated user accounts? In some private/auth folder? Please let me know if I'm being misled and if so, I'll gladly follow the link I posted (or whatever you have to tell me!)

---

### Post by Blues- on 2011-03-03
Completing a postfix setup using multiple guides can sometimes have bad side effects ...

Of all the postfix installations I've setup .. I always use flurdy's guide as a reference.  It's complete and very thural.

Flurdy's postfix guide is here => [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Cheers,
Blues-

---


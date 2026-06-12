---
title: "Exchange middle man, POP3 and SMTP via Gmail"
date: 2012-07-12
forum: Server Platforms
---

### Post by moorsey on 2012-07-12
Hi all,

I have no idea if something like this is possible, but thought it was worth asking.

An organisation I volunteer for decided to turn off POP3 and possibly SMTP access to emails this week.  We have Outlook Web Access and oddly, they have left Exchange access turned on.

I have previously been managing all email sending and receiving out of my Gmail account, which is VERY handy, proper SMTP sending via the orgs servers etc.

Now, I can still setup a forward in Outlook Web Access to my Gmail, but this is not ideal, as replies go back to my address, rather than the senders address, without first editing etc, so quick replies from my phone are in the past.  Senders email addresses are also masked and replaced with display names from the address book, so a bit of guessing when replying is required.

TL:DR
Is there a way to setup software on Linux, postfix or other, to receive Exchange emails and allow Gmail to collect them via POP3?  Retaining email addresses?

Many thanks

---

### Post by moorsey on 2012-07-14
bummer, SMTP has now been turned off, so I really need to do something, to save my sanity.

Gmail can do spoof sending still, but everyone gets the "sent on behalf of" message, as it is really from my Gmail.

Any ideas folks?

Cheers

---

### Post by moorsey on 2012-09-13
Well, this has come back to haunt me.

SMTP has been back on since after I posted this, but this week, it's gone off again, maybe for good this time.

Any tips on getting this setup appreciated

Martin

---

### Post by moorsey on 2012-09-13
thought I would clarify this.

POP3 is now not an issue, as the forwarding from the new Outlook Web service works well.

What I cannot do anymore is log into my gmail, select my organisations email as the "from" address and send mail via their servers.  The only avenue they have left open is Exchange, not SMTP, which now fails.

So I would like to put my home postfix server in as the SMTP details in Gmail, then for this message to be relayed via Exchange to my organisations servers, so it is sent truly from that email address.

Hope I'm making sense

---

### Post by SeijiSensei on 2012-09-14
If you cannot send via SMTP from GMail, why do you think you can send from the Postfix server?

Why not just use Outlook Web Access?

Is this something you have discussed with the organization's IT admin?

---

### Post by lisati on 2012-09-14
> **SeijiSensei said:**
> Is this something you have discussed with the organization's IT admin?
+1
If there's a problem with your access to someone else's machine or services, it's always good to keep communication open with those who can, for whatever reason, block your access. The last thing you want is for them to mistakenly believe that you're a troublemaker.

---

### Post by moorsey on 2012-09-18
Thanks for the replies guys.

Yes, you are both quite right and I have logged a ticket with the IT guys to try and get this turned back on.  I am just preparing for the worst and looking at possible work arounds.  This may be a grey area I guess, but it is purely for convenience.  They still allow mail forwarding rules to send mail to 3rd party accounts, so I don't quite understand their restriction on POP3 and SMTP.

Maybe I have mis-understood how Exchange works.  I thought sending mail over Exchange uses the Exchange protocol, hence why I thought I could send from postfix, avoiding the use of SMTP.

---


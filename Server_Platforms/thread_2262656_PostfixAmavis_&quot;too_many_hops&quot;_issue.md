---
title: "Postfix/Amavis &quot;too many hops&quot; issue"
date: 2015-01-26
forum: Server Platforms
---

### Post by jmaciak1987 on 2015-01-26
Ever since adding Amavis/Spamassassin/clamav/postgrey to my postfix server, I'm getting slammed with "Undelivered Mail Returned to Sender".

Specifically:
```
554 5.4.0 Error: too many hops (in reply to end of DATA command)
```

Our setup: We use Gmail as our external mail handler. Mail goes to Google, if Google doesn't have that address (person@example.org), it then goes to Mailarmory (which is an external spam filtering service), then it goes to our local mailserver (hostname "Blackhole") that holds a ton of aliases which point any [EMAIL="person@example.org"]person@example.org[/EMAIL] not on Google to the appropriate place (i.e. [EMAIL="person@harvard.edu"]person@harvard.edu[/EMAIL]). 

We're trying to get rid of Mailarmory and let our local mailserver do the filtering. I installed and configured Amavis and all its friends according to this guide: [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

Watching the mail.log, mail is coming in and out of the local mail server (Blackhole). Spam is being tagged appropriately, although the filter seems a bit lax at the moment. My biggest problem is the amount of "Undelivered Mail Returned to Sender" messages I'm getting that have the "too many hops" error.

Mailarmory is still in place at the moment because this is a production environment and we've only deleted a few of the whitelisted addresses at Mailarmory as a test.

My only theory at the moment is that there is a loop created between the local mail server Blackhole and Mailarmory, but I'm not sure why exactly.

I've attached my main.cf, master.cf, and an excerpt of mail.log showing what happens when one of these messages gets delivered with the "too many hops" error. If any other info is needed, please let me know.

Thanks!

---

### Post by SeijiSensei on 2015-01-26
It's quite common to have undelivered mail if you block spammers.  If the spammer sends mail to a non-working or blocked address, the server will send a non-delivery notice to the sender.  Since most senders are forged, these notices bounce as well.  Most of us just accept this problem as the alternative is not send non-delivery notices which breaks the SMTP standard.

---

### Post by SeijiSensei on 2015-01-26
It's quite common to have undelivered mail if you block spammers.  If the spammer sends mail to a non-working or blocked address, the server will send a non-delivery notice to the sender.  Since most senders are forged, these notices bounce as well.  Most of us just accept this problem as the alternative of not sending non-delivery notices breaks the SMTP standard.

---

### Post by jmaciak1987 on 2015-01-26
Hrm, I see. It is possible to suppress these messages?

---

### Post by CharlesA on 2015-01-26
I've got spamassassin and amavis set up on my mail server, but I don't recall seeing any messages like that.

My set up is a bit different and my email addresses aren't really out in public, so I'm not getting much spam (yet).

---

### Post by SeijiSensei on 2015-01-26
I run a couple of mail servers that probably handle in the hundreds of spams every day.  (I have clients whose email addresses were posted on their websites and now get spammed incessantly as a result.)  I probably see a few dozen such bounce messages stuck in my outbound queues at any time.

As for managing the problem, it's pretty hard to do.  We had some persistent spamming hosts that generated a lot of this traffic that I've specifically blocked.  The domain registrar-servers.com was especially annoying.  On a client's site, we block most two-letter country-code domains because they are a small US health-care provider that doesn't conduct legitimate correspondence with foreign entities.  As you can imagine, blocking connections from machines in domains like .ru, .th, .in, and the like will enormously reduce spam.

One solution is not to bounce spams but just accept and tag them or route them into a quarantine or black hole.  Another option if your list of users is manageable is to whitelist those addresses on the inbound SMTP server and reject any messages to accounts that don't match.  That can be a pain to administer, though, if the list of valid accounts changes often.  Basically the more stuff you can block at the SMTP level, the better off you are, as long as you insure you aren't blocking legitimate accounts by mistake.  False positives at the SMTP level are really bad since no one on your end will be notified that a legitimate message was not delivered, and the sender is left wondering why his old friend [email]sara@example.com[/email] isn't accepting mail.

---

### Post by jmaciak1987 on 2015-01-27
Thanks, I'm going to take a look at accepting the spam and routing it to a black hole.

---

### Post by jmaciak1987 on 2015-01-27
So I see what's happening. Basically when an e-mail (spam or legit) is sent to an address that does not exist on our domain (lets says [EMAIL="doesnotexist@example.org"]doesnotexist@example.org[/EMAIL]), it just gets bounced back and forth between our local postfix server and google until it hits 50 hops. It seems like it doesn't know what to do with it. Is this a postfix setting that is incorrect? If the address doesn't exist, can we just shitcan the email? Or maybe just send a bounce to the sender??

EDIT: removed example.org from *transport* and things are working great now. Any explanation on this? I had to leave it in *relay_domains* otherwise the server rejected emails.

---

### Post by lisati on 2015-01-27
It has been a while since I've seen "too many hops" in an error message.

Just to clarify, when we're talking "bounce" in this thread are we talking about a rejection during the SMTP connection or a situation where a mail is accepted for delivery and then rejected (possibly after scanning for malware or other problems)? Some see the "accept for delivery and then bounce" approach as risky, because of the risk of forged sender credentiials being used, e.g. as described [here]("https://www.spamcop.net/fom-serve/cache/329.html#bounces").

---

### Post by jmaciak1987 on 2015-01-27
A bounce being a rejection because the address doesn't exist.

See my last post. I fixed the issue but I'd like to know a bit more about the relation between transport and relay_domains within Postfix.

example.org was in /etc/postfix/transport as: example.org smtp:[smtp.gmail.com]
 
And also in relay_domains as: example.org                 relay

  

I removed example.org from *transport* and things are working great now. Any explanation on this? I had to leave it in *relay_domains* otherwise the server rejected emails.

---

### Post by lisati on 2015-01-27
> **jmaciak1987 said:**
> A bounce being a rejection because the address doesn't exist. 
The reason for the bounce or rejection was irrelevant to my question. Timing matters: see the page I linked to. If you're rejecting after accepting the message for processing, not only do you run the risk of sending the bounce message to the wrong person, more header information will be added. 

The fact that you've indicated that the non-delivery report is going back and forth between your server and Google's server suggest to me that maybe you've got things set up to accept a message for processing before it is rejected, and have created what I'd call a "Backscatter loop". By default, Postfix usually rejects unkonwn recipients before the complete message is accepted. Have you done anything which could have changed this behaviour?

---

### Post by jmaciak1987 on 2015-01-28
> **lisati said:**
> Have you done anything which could have changed this behaviour?

Not to my knowledge. However, I did inherit the administration of this server so I'm not sure exactly what was configured before I took it over. Is there a specific config file I should look in?

---


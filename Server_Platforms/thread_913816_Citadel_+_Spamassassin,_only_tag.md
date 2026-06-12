---
title: "Citadel + Spamassassin, only tag"
date: 2008-09-08
forum: Server Platforms
---

### Post by LarsEriksson on 2008-09-08
Hello. I have a working setup with Citadel groupware as mailserver, i have also installed Spamassassin and it seems to work, but.
Mails marked as spam just seems to be lost in space, i cant find in any log if they are deleted, rejected, or whatever. So, what i want to do is to _only_ tag the subject of mails that ar marked as spam by SA, i.e. "[SPAM] Hello Lars!".

In /etc/mail/spamassassin/local.cf  i have this setting:
rewrite_header Subject [SPAM]
But it does not seem to do anything, can anyone help me out here?

---

### Post by LarsEriksson on 2008-09-11
Still no luck, still trying to get the configuration right.
Ive read somewhere that all mails that have passed through spamassassin should be tagged in the header with a message from spamassassin, like:
X-Spam-Checker-Version: SpamAssassin 3.1.0 (2005-09-13) on yourdomain.com
But i cant find any message like that in my mail headers in the inbox.

And some mails, i.e. from a customer in china, is rejected, that person only gets a reply that says their mail was rejected because it was classified as spam by my server.
Still cant find anything in the logs.

---

### Post by windependence on 2008-09-11
Lars, check with HermannAB here on this board. I have not seen him here today but he is usually on this board and is very well versed in Citadel support. He should be able to point you in the right direction.

-Tim

---

### Post by HermanAB on 2008-09-12
Citadel behaves like a Spam Assassin Client. Normally the client is Spamc.  In this case, Citadel does it all.  The behaviour of Citadel is binary: Accept or Reject.  

This means that spam is not stored, it is rejected.

See this:
[http://www.citadel.org/doku.php/faq:spam:spamassassin#spamassassin](http://www.citadel.org/doku.php/faq:spam:spamassassin#spamassassin)

Large mail servers can receive thousands of times more spam than real mail and storing them all is impractical and would be a terrible waste of resources.  Therefore Citadel simply rejects all spam.  This is very efficient and if someone complains, then you can add a whitelist entry to the bottom of /etc/mail/spamassassin/local.cf

For example, my mail server receives 99.999% spam.  It cannot store 10,000 junk messages per hour.  In fact, my mail server doesn't even have the horse power or the bandwidth to process it all, so the spam reject behaviour of Citadel is very good and keeps the server and my customers happy.

If you integrate ClamAV with SpamAssassin as suggested in the manual, then the same thing will happen with viruses.  They will simply be rejected and you'll never see them.

Rejecting mail is a good thing.  The sender knows immediately that his mail was rejected and he can then pick up the phone and call, or change his email so it doesn't look spammy, or clean up his PC if it is full of viruses.

I hope that helps!

Cheers,

Herman

---

### Post by LarsEriksson on 2008-09-12
Thanks for your reply, and i know that rejection has its advantages.
But i actually only want to tag the mails. This gives the end user a better feeling of control and so on, and we dont get that much spam either. perhaps 100 per day, maximum and we have a very powerful server as well so that is not a problem.

Ive read somewhere that postfix could be used "between" Citadel and the outside, how can i do that?

---

### Post by LarsEriksson on 2008-09-15
Ok, found this:
[http://www.citadel.org/doku.php/faq:installation:configuring_postfix_to_validate_email_addresses_against_a_citadel_server](http://www.citadel.org/doku.php/faq:installation:configuring_postfix_to_validate_email_addresses_against_a_citadel_server)
But im stuck at > Take the main.cf from the last box(or add the matching lines to your config), replace 777 with your port and sample.yourcitadel.org with your hostname. Make Postfix reload its config using &#8220;postfix reload&#8221; as root on your shell. Use &#8220;tail -f /var/log/mail&#8221; or &#8220;tail -f /var/log/mail/current&#8221; depending on your syslog facility to check the effort:
I really dont understand, where should i put 777? and sample.yourcitadel.org?
As it is now, when i try to start postfix i only get:
> Sep 15 09:58:07 web postfix/master[15610]: fatal: bind 0.0.0.0 port 25: Address already in use (of course)
Is there any better guide how to setup this configuration, for a beginner like me?

---

### Post by LarsEriksson on 2008-09-25
Is there noone who has this setup?

This is really starting to be a problem, a _lot_ of mail we get is being rejected because the system thinks its spam, but its not. And since it is rejected there is no way to learn the system that it is not spam.
I cant add all the senders adresses to whitelist, its just too many.

---

### Post by artcancro on 2008-10-22
Not to worry ... Citadel just added a new function to tag spam instead of rejecting it.  It'll be in the very next release.  Then you can combine that with the built-in inbox rules editor to do whatever you want with your spam.

Incidentally, the same developer who did that also wrote another module to directly attach Citadel to ClamAV, so you won't have to do ClamAV scans via SpamAssassin anymore.

All of that having been said, though, if you're getting too much mail rejected by SpamAssassin then you might consider making your filters a little less aggressive.

---

### Post by Railsbuntu on 2008-10-26
Hi,

Actually rejecting spam is better than tagging it as spam, tagging simply clutters your inbox with very annoying subjects, actually the **** SPAM **** emails get more attention as it catches your eye better which defeats the purpose of spam filtering.

---


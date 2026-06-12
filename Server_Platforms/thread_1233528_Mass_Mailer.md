---
title: "Mass Mailer"
date: 2009-08-06
forum: Server Platforms
---

### Post by uge on 2009-08-06
Hi guys,

I'm looking for a good mass mailer, if possible with a PHP graphic interface.

I'm running Ubuntu Server 64, 8.04 LTS.
No GUI. (That's why I'd like a PHP graphic interface for the software)

The reason I want a mass mail is because in my business we have some customers, more specifically real estate agents, who "opt-in" on our website to see our seasonal offers.

The guy in charge is using a Windows Based program called "Group Mail" but license has expired and before renewing it (500$) I figured I could look for a similar or greater piece of software in the multiverse ;)

So what I would need it to do is
1) Let us upload a CSV list with emails, names, etc.
2) Create an email with fields where we can put the name of the person, etc...
3) Set the smtp server, delay between sent
4) Be able to see the logs (failed, success, etc.)
5) If possible, be able to re-send automatically the failed ones

Of course, what I want is one email per recipient... so every recipient get one personalised emails.

Bonuses would be if it would manage "Opt-outs" automatically (right now we manage them manually) and if it would clean the list from the "delivery failed" reply messages.



Any ideas ??


And by the way, this is 100% legit. Our list is very small and made only of people who clearly opt-ed in by going by themselves on our website, seeing a little box where you can put your email if you want to receive our seasonal offers, and putting their email there by themselves, and finally clicking submit.


Thanks !!!

---

### Post by HermanAB on 2009-08-06
Citadel of course.  It has an integrated web interface and it can do mailing lists.  It will take you about 20 minutes to run the Easy Install script.

---

### Post by lykwydchykyn on 2009-08-06
I set up PHPlist for our public library newsletters, it seems to meet these requirements.  It took a bit of finagling to get the bounceback processing working, but I think that was due to our spam filter.

---

### Post by uge on 2009-08-06
> **HermanAB said:**
> Citadel of course.  It has an integrated web interface and it can do mailing lists.  It will take you about 20 minutes to run the Easy Install script.

Hey Citadel seems to ROCK

it supports many things that I wanted to have in my office...

shared calendars + contacts... and stuff like that !

But does it really support mass mailing with individually personnalised messages ?

---

### Post by avdzm on 2009-11-25
Hey Uge,

How's Citadel working out?

---

### Post by Johnsie on 2009-11-25
I wrote my own that uses the php mail function

---


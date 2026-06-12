---
title: "google apps + mailman"
date: 2008-06-25
forum: Server Platforms
---

### Post by janskey on 2008-06-25
hi all,

currently we have our email hosted in google apps. so basically we get <user>@company.com emails from google. what if we want a mailing list that can archive our mails, which mailman and google groups is sufficient. but we want our mails list to be [email]devs@company.com[/email] which is a problem with google groups because you have @groups.google.com at the end of mail and we want to brand it. i'm thinking of mailman but we don't want @lists.company.com emails. we want to achive something like [email]dev@company.com[/email]

So is it possible to filter mails in MX? For example if its for a mailing list it will go to mailman and if its for person it goes to the maillist? I can create mail list in google apps though but we want to have a archive style like in mailman and groups.google, any advice?

---

### Post by CaveMole on 2010-11-15
I, too am looking for new ways to handle mailing lists.
I used to host a mailserver and mailman, but the maintenance and spam filtering are too big a burden for me.

Still new to google apps...  but it seems like most of your problems
could be handled by a forward.
Simply forward [email]list@mydomain.com[/email] to [email]list@lists.mydomain.com[/email].

It still can show some google addresses in the path, but only
advanced users who read mail heders will see this.

Keep us informed.

Google groups may be fine for me, but I have 3 requrements that might get tricky:

  1) CANNOT force users to get google accounts
  2) need to let list admin add/remove users WITHOUT user confirmation
  3) Need to have list admin approve all new user requests

---

### Post by SeijiSensei on 2010-11-15
> **CaveMole said:**
> Still new to google apps...  but it seems like most of your problems could be handled by a forward.
Simply forward [email]list@mydomain.com[/email] to [email]list@lists.mydomain.com[/email].

That sounds like the best solution to me if you're really opposed to setting up a subdomain for the listserver.  I host a number of lists for a nonprofit.  They're all in lists.example.com so they can be sent directly to the listserver for processing while mail for example.com goes to my client's internal mailserver.

Most mailing list software gives you a substantial amount of control over how messages are addressed.  I have another list I run for my college graduation class that is at [email]listname@example.com[/email] which then forwards to [email]listname@lists.example.com[/email].  The outbound messages have From and Reply-To headers (yes, I use one of those, and I understand the arguments both for and against) use the @example.com form.

I've run lists on both **majordomo** and **majordomo2**.  The latter is a substantial rewrite and pretty full-featured, but documentation outside the application itself is scant.  The built-in help files are quite extensive though.  I've not used something like **mailman** because I have written a number of applications over the years to archive the mail using **hypermail** and to manage the lists over the web.  I did take a brief glance at **sympa** and might look at it again in the future.  Majordomo2 comes with a number of cgi-bin scripts to implement a web interface, but I've not tried using them to replace my home-grown applications.

As for spam, it presents less of a problem if you're running a closed-subcription list since the spammers won't be subscribed.  The "owner-listname" admin addresses, on the other hand, get a lot of spam which poses a bigger problem.  I don't want to block legitimate messages for my admins so I filter those addresses (and all my other mail) pretty heavily using **mailscanner+spamassassin+clamav**.  (All the list addresses have been visible on the web for a long time, so they get heavily spammed by now.)

---


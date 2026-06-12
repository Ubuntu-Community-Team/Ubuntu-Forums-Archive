---
title: "Ubuntu Mail server as a false positive spam catcher"
date: 2010-05-21
forum: Server Platforms
---

### Post by gannster on 2010-05-21
I have a CISCO ASA with CSC configured as my gateway.  It has a spam filter provided by Trendmicro that has only three actions available. Ignore it, delete it, or flag it with a keyword in the subject line, and let it go forward. 

It is currently deleting about 100,000 messages a month with it's current configuration.  Sadly, some of those turn out to be false positives that are lost forever.


I want to be able to catch those false positives without burdening my existing server.

I have downloaded and install Ubuntu Server 10.04 32 bit on an idle Intel box.  During setup, I chose e-mail as the only server option to include.  I have confirmed that the Ubuntu email server on the can send email to my domains email server.

Well, that was the easy part.

Now I am left with wanting to examine email when they arrive. 

If [A] they are addressed to actual domain users and flagged as spam by the ASA, then keep the messages in a way that I can access them, review and forward messages as necessary.

If [B] they are addressed to actual domain users and not flagged as spam, then simple forward them automatically to my domain server. 

If neither [A] nor [B], ie the messages are not addressed to mailboxed users within the domain, delete them.

So far my web searches around this topic haven't helped me much.  Most detailed write ups  about Ubuntu/Linux as an email server go along the line of "getting started" with the goal of that server being the only server.  Other pages describe applying a spam filter to arriving mail, but this isn't my goal either. Also, I have read brief things like "use package X to allow your email server to access ldap/mysql." 

Any guidance is appreciated.  Especially in the area of what and how to accomplish this.

---

### Post by BoneKracker on 2010-05-21
procmail (or maybe maildrop)

Procmail is kind of a pain to get a feel for it (arcane configuration syntax), but I have never found anything that offers as much flexibility.  There are a host of "mail filters" of different types you can plug into it that will do everything from rewriting headers, rerouting delivery, canning spam, checking for malware, changing the oil, etc., on inbound, outbound, or machine-local mail of any format.

You can also call out to any script or executable you want, so it can basically do anything you want.

Overview:
[http://en.wikipedia.org/wiki/Procmail](http://en.wikipedia.org/wiki/Procmail)

There is a link there to their home page.  Search the web for howtos, examples, etc.

Also, even if you don't like this product (e.g., can't stomach its configuration syntax), this is a good starting point -- look at what it's "competitors" are).

One additional thing: your choice should take into account what server you are using.  Some servers have built-in or add-on utilities that are nicely-integrated that will meet your needs.

It may also be helpful to understand a bit about UNIX email terminology.  Procmail is born of the context of Unix-style mail systems (i.e., sendmail).  The main architectural elements of UNIX mail are the MTA (mail transfer agent), MDA (mail delivery agent), and MUA (mail user agent).

A MUA is basically a mail client, although in pure UNIX mail architectures, they couldn't "submit" mail directly to MTAs (e.g. SMTP server); they handed it off to an MDA, which did that for them (carrying out other filtering tasks in the process).  The MDA also received mail inbound from MTAs to the system and delivered it to user mailboxes (carrying out other filtering tasks in the process).  Hence "Mail Delivery Agent").

Now, most modern email clients directly submit their own messages, and most have built-in filtering capability.  However, centralized filtering is still necessary, so there is still a role for that MDA function.

Procmail is an MDA.  While not all Linux email servers adheres to this architecture (many of the latest "mail servers" combine MTA and and some MDA functionality or have their own optional MDA of limited capability), you may still see the terms "MTA", "MDA", and "MUA".

That ought to be enough to help get you started in your search.  For example, look for "Linux mail filtering software" and/or "linux mail delivery agents".  If you've already selected a particular server, you might want to narrow your search to those that are known to work with your server.

Here's another quick-start on Linux mail and MDAs:
[http://en.wikipedia.org/wiki/Mail_delivery_agent](http://en.wikipedia.org/wiki/Mail_delivery_agent)

Here's a different approach to mail filtering:
[http://www.gentoo.org/doc/en/mailfilter-guide.xml](http://www.gentoo.org/doc/en/mailfilter-guide.xml)

---

### Post by jjcv on 2010-05-22
I agree, procmail is one of the best options for filtering email and doing something with it.   I have used it for years along with various types of spam catching software to deal with spam.  (currently I filter all my email via gmail which does a great filtering job).

Normally I use amavis and spamassasin (comes with amavis these days I think).    You can configure amavis to deal with spam from your ASA or get to to insert a header into the email with a spam score.   You can also configure it to delete email above a certain spam score and pass on other email to your mail server from where you can get the procmail server (which can be configured to receive email and pass it on you your mailbox) to deliver it to specific folder, users or programs depending on what the spam score is.

It is really worth getting to know procmail.   

Amavis comes with a pretty good default install but is pretty easy to customise.

Not sure what LAMP installed these days but am planning on setting up a 10.04 lamp server myself next week so I guess I will find out more.

---

### Post by HermanAB on 2010-05-22
Hmm, actually, your problem is that you are only getting 100,000 spams per month.  If you were getting a million spams per day like me, then the handful of false positives will cease to be a concern.

In a system with very high spam volume, it is impossible to review the spam.  So since I get so much of it, I spend zero time looking at it or fretting about it.  

In a business environment, if someone sends an email and gets no response, then they will eventually phone and 'I think my spam or virus filter chucked it away' is always an acceptable response - nobody has ever castigated me about it.

So, I simply use Citadel mail server, which has built in hooks for Real Time Black Lists, Spam Assassin and ClamAV and I sleep well at night with zero worries about what gets bounced.

---

### Post by BoneKracker on 2010-05-22
Since modern mail clients also have mail filtering / spam processing capabilities, I think it's better to eliminate at the server messages above a given threshold (and possibly based on additional heuristics of your own implemented outside the spam engine but inside something like procmail) and then pass on the rest (flagged as possible spam) to the end-user to make a decision on.

In an imperfect world, based on their decision, their client's filtering engine learns to handle these.  In a perfect world, your server-side engine learns based on end-user decisions (but I'm not yet sure how to do that other than by using webmail).

---


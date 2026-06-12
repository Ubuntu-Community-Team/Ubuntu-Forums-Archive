---
title: "Dropbox, Ubuntu One style client server app?"
date: 2010-08-12
forum: The Cafe
---

### Post by erpezoa on 2010-08-12
Is there any project that you know similar to Dropbox or Ubuntu One, but client server, I have tried zmanda and its not what I need, I also found a PHP based called BOB  but the project seems to be abandoned.

---

### Post by earthpigg on 2010-08-12
what, exactly, do you mean by smashing the words 'client' and 'server' together like that?

you want to run the server on computers under your own control?

like, [rsync]("http://en.wikipedia.org/wiki/Rsync")?

---

### Post by erpezoa on 2010-08-12
> **earthpigg said:**
> what, exactly, do you mean by smashing the words 'client' and 'server' together like that?

you want to run the server on computers under your own control?

like, [rsync]("http://en.wikipedia.org/wiki/Rsync")?

Yes Client and Server 
Yes under my control 
rsync -  no,  I'm looking for something with the simple functionality of Dropbox, I am currently using rsync , I'm not new to Linux.
I can't stand moronic patronizing answers such as "smashing the words 'client' and 'server' together like that?" -

---

### Post by JustinR on 2010-08-12
> **erpezoa said:**
> 
I can't stand moronic patronizing answers such as "smashing the words 'client' and 'server' together like that?" -

It most likely wasn't patronizing and yes, your oxymoron of 'client server' doesn't make sense at all.

You could try this:[http://google-opensource.blogspot.com/2010/05/manage-cloud-storage-from-command-line.html](http://google-opensource.blogspot.com/2010/05/manage-cloud-storage-from-command-line.html)

Or Cloudloop.

They both seem to offer commandline interfaces.

---

### Post by erpezoa on 2010-08-12
> **JustinR said:**
> It most likely wasn't patronizing and yes, your oxymoron of 'client server' doesn't make sense at all.

You could try this:[http://google-opensource.blogspot.com/2010/05/manage-cloud-storage-from-command-line.html](http://google-opensource.blogspot.com/2010/05/manage-cloud-storage-from-command-line.html)

Or Cloudloop.

They both seem to offer commandline interfaces.

Client-Server is a very common term, not something that doesn't make sense
[http://en.wikipedia.org/wiki/Client%E2%80%93server_model]("http://en.wikipedia.org/wiki/Client%E2%80%93server_model")

---

### Post by Simian Man on 2010-08-12
Too bad Ubuntu One is proprietary and not portable.  It could fill a real niche, but is almost useless at the moment.

---

### Post by erpezoa on 2010-08-12
> **Simian Man said:**
> Too bad Ubuntu One is proprietary and not portable.  It could fill a real niche, but is almost useless at the moment.

I have configured a couple of  rsync scripts that sync four ways every night, I have 4 machines at different locations plus a laptop that syncs every time it gets online, I have tried Dropbox and I love how simple it is, the problem is that I don't want my data outside my own environment, specially pay for storage I already own is not an option.

---

### Post by zekopeko on 2010-08-12
> **erpezoa said:**
> Is there any project that you know similar to Dropbox or Ubuntu One, but client server, I have tried zmanda and its not what I need, I also found a PHP based called BOB  but the project seems to be abandoned.

Sparkleshare?

[http://www.sparkleshare.org/](http://www.sparkleshare.org/)

---

### Post by erpezoa on 2010-08-12
> **zekopeko said:**
> Sparkleshare?

[http://www.sparkleshare.org/](http://www.sparkleshare.org/)


Thank you, it looks promising.

---

### Post by earthpigg on 2010-08-12
> **erpezoa said:**
> I can't stand moronic patronizing answers such as "smashing the words 'client' and 'server' together like that?" -

i wasn't trying to be patronizing, i honestly wasn't sure what you where trying to communicate. the term 'client server' seems redundant to me, like "RIP: Rest in Peace" written on a gravestone. aren't *all* servers, servers for clients of one form or another?

anywho, best of luck with your problem.

---

### Post by mendhak on 2010-08-12
> **erpezoa said:**
> Is there any project that you know similar to Dropbox or Ubuntu One, but client server, I have tried zmanda and its not what I need, I also found a PHP based called BOB  but the project seems to be abandoned.
Something like [Unison](http://www.cis.upenn.edu/~bcpierce/unison/)?  It works on Win and Lin.  It's very slow the first time as it seems to be building indexes but is very fast on all subsequent comparisons.

---


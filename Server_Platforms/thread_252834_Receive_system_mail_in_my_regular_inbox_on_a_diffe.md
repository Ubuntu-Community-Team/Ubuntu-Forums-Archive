---
title: "Receive system mail in my regular inbox on a different computer?"
date: 2006-09-07
forum: Server Platforms
---

### Post by kenquad on 2006-09-07
Hi all:

I have some cron-initiated backup scripts that run at various times on my Ubuntu Dapper server.  If something goes wrong I want to know about it, but I don't plan to visit this remote server room every day and grep the log files:-) So, I would like any error messages to be either emailed or instant-messaged (preferably emailed, though I can use my Skype or Google Talk account or install another IM client) to my regular Win2K workstation.  If anyone knows a fairly straightforward way to do this, I'd appreciate hearing about it.

Thanks!
Kenquad

---

### Post by jjasghar on 2006-09-07
I'd use exim or something like that, sending a cli mail with exim is pretty easy, and put it in an another cron job script and have it parse out to you.

It'll be a tad amount of work,  there are a billion howtos on exim just google it, and use the "mail" or "exim -vj" (not to sure about the -vj flag) with the data you are looking for.

---

### Post by kenquad on 2006-09-07
Thanks for the reply!:KS  How would I tell cron to send all errors to that address? And would I have to set up an outgoing mail account somewhere or would this be its own outgoing mail server?

---

### Post by jjasghar on 2006-09-07
> **kenquad said:**
>   How would I tell cron to send all errors to that address? 

I'd use a bash script with the normal grep commands that you use to parse out the data, and dump them in a file or to stdout.

> **kenquad said:**
>  And would I have to set up an outgoing mail account somewhere or would this be its own outgoing mail server?

i'd just install exim like a mentioned above, it can send out email with that data that comes from that file/stdout, you can tack the command in the bash script if you so choose. it would be it's own mail server...so exactly ;).

it'll be a little work with regex, grep, bash, and exim<enter any mta> but it'll do exactly what you are looking for....

and hell you can learn something too :-D

---


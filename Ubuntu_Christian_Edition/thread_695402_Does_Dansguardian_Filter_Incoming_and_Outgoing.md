---
title: "Does Dansguardian Filter Incoming and Outgoing?"
date: 2008-02-13
forum: Ubuntu Christian Edition
---

### Post by Teasdale on 2008-02-13
This is a long-shot, but I thought I'd ask here since people here seem more familiar with Dansguardian and may know how filters work.

We had CyberSitter in our WinXP computer and will be installing Dansguardian, probably via Ubuntu CE. Our old filter was too good at filtering our outgoing emails and blog posts by removing letters from words it thought were offensive (such as the "meth" from the word "method.") It seemed more intent and vigilant about filtering what we sent *out* into cyberspace than what came *into* our PC via the internet. 

I'm much more concerned about what comes in that what goes out of our PC. I see filters as a way to protect my kids from cyberspace; I don't think the world needs to be protected from my kids.  :confused:  How is Dansguardian about that? Is there an option to not filter our outgoing data, and only filter incoming? Or does the nature of filters make that somehow impossible?

---

### Post by milesje on 2008-02-13
I do not use Dansguardian myself but here are some of the features listed on its website.  I hope this helps.

Can block adverts by the use of an advert URL block list. 
Can filter text and HTML pages for obscene (sexual, racial, violent, etc) content. 
Uses an advanced phrase weighting system to reduce over or under blocking. 
Can filter sites using the PICS labeling system. 
Can filter according to MIME type and file extension. 
Can filter according to URLs including Regular Expression URLs. 
URL filtering is compatible with squidGuard black lists. 
The URL filtering is able to filter https requests. 
Can work in a 'whitelist' mode where all sites except those listed are blocked. 
Can block all IP based URLs. 
Is able to block sites when users try using the IP address of the site instead. 
Produces a log in a very human readable format. 
Optionally produces a log in CSV format for easy import into databases etc. 
Is able to log the username using either Ident or basic proxy authentication. 
It has the ability to switch off filtering for specified sites, parts of sites, browser IPs and usernames. 
Can block specified source IPs and usernames. 
Can block or limit web uploading (e.g. attachments in Hotmail). 
Has the ability to work in a stealth mode where it logs sites that would have been blocked, but does not block them. This allows you to monitor your users without them knowing. 
Uses a very intelligent algorithm to match phrases in web pages mixed in with HTML code and white space.

---

### Post by Teasdale on 2008-02-14
I'll bet the answer to my question is right there in that list - if I could only recognize it. If I understood the process or terminology, I could probably figure out why/how filters zealously block out-going data and determine if Dansguardian does that. But my internet searches are no help.

---

### Post by jonathonblake on 2008-02-17
> **Teasdale said:**
> I'll bet the answer to my question is right there in that list - if I could only recognize it.

I turned DansGuardian off, so I don'tknow what it does/how ti does.

However,after reading their website, it looks like it does not check outgoing email.

The simplest way to determine if it does not do what you want, would be to run the Live CD with it installed,and configure the email client to send email. Then see what gets thru,and what does not get thru. [This will be painfully slow on a system with less than 1 GB RAM.]

>  I could probably figure out why/how filters zealously block out-going data and determine if Dansguardian does that.

Most content filters are "feel good"solutions.   One way they achieve that, is by paying more attention to what goes out, than what comes in.  Compounding that corporations --- which is their target market --- are more interested in preventing data from going out, than in data coming in.

xan

jonathon

---

### Post by Teasdale on 2008-02-19
> **jonathonblake said:**
> 
Most content filters are "feel good"solutions.   One way they achieve that, is by paying more attention to what goes out, than what comes in.  Compounding that corporations --- which is their target market --- are more interested in preventing data from going out, than in data coming in.

Very interesting - and the first time I've anyone offer even a possible reason why filters are more careful about what goes out than what comes in.

Since dansguardian isn't marketed to corporations, maybe it's less focused on what goes out.

The Live CD might be a great option - our outgoing consists of blogging and webmail, and the Live CD should be able to test both of those.

---

### Post by Mithrilhall on 2008-02-19
It's been a while since I tried out  Dansguardian but I was impressed. It blocked pages well. I wasn't aware that it could be used to filter outgoing emails and attachments.

I would look at another product to handle your email requirements.

---


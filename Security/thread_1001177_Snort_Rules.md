---
title: "Snort Rules"
date: 2008-12-03
forum: Security
---

### Post by Drezard on 2008-12-03
Ive set up snort and it works like a charm except Im getting a lot of detections that are like this in BASE:

> 
#3-(1-4) 	 [snort] (http_inspect) NON-RFC DEFINED CHAR 
#5-(1-6) 	 [snort] (http_inspect) NON-RFC DEFINED CHAR 
...


Now I know there is an easy way to turn this off (by commenting out the line in the snort rules) but how do I find this line?!?

Ive tried
> 
grep rfc /etc/snort/rules/*
grep non-rfc /etc/snort/rules/*
grep defined\ char /etc/snort/rules/*


But these either turn up too few, or too many results. What should I be looking for?

Daniel

---

### Post by bodhi.zazen on 2008-12-03
There can almost never be too few ...

Is there a rule number you can search on or any additional information in the output ?

---

### Post by brandon88tube on 2008-12-03
My question is how the heck do you even use Snort? Reading from their site has left my brain hurting.

---

### Post by bodhi.zazen on 2008-12-04
> **brandon88tube said:**
> My question is how the heck do you even use Snort? Reading from their site has left my brain hurting.

LOL, I understand

Take a look at the "Intrusion Detection" sticky.

---

### Post by Drezard on 2008-12-04
Thanks, I see no rule links in the extra info part of this detection.

Also, by too few i mean 0 (zero) :P

---

### Post by Sarmacid on 2008-12-04
I found 2 rules

```
grep http_inspect /etc/snort/rules/*
/etc/snort/rules/deleted.rules:# taken care of by http_inspect now
/etc/snort/rules/web-attacks.rules:# http_inspect takes care of decoding for us, that should really look like

```
I would suggest against commenting the rules, instead use suppression, since oinkmaster will uncomment the rules when it updates them. Suppression can be done in /etc/snort/threshold.conf.

---

### Post by Kinstonian on 2008-12-04
I believe those alerts are being generated from the http_inspect pre-processor, not a rule.  It's probably not something you want to disable, but I would think you could provide some options to http_inspect in the snort.conf to stop it from generating so many alerts.


***Edit***

After a little googling, I'd backup my snort.conf and look for a line similar to:

non_rfc_char { 0x00 } \

defined in your http_inspect section.  If you do find that line, try deleting it, then stop and restart snort.  I don't know if that's the best way, or even if it will work, but it may be worth a try.

You may also have "profile all" specified, which could of enabled everything.  [Here](http://www.snort.org/docs/snort_manual/node95.html) are some examples of http_inspect settings.

---

### Post by bodhi.zazen on 2008-12-04
try grep on http_inspect

---

### Post by stmurray on 2008-12-04
You should also check that you have the HTTP_SERVERS set correctly in snort.conf.   If you have web servers on your network they should be listed here.  That way, the http rules will only be alerted on those servers (Of course, if you are worried or curious about internal users attacking external web servers, you need to set HTTP_SERVERS to "any".)

---

### Post by brandon88tube on 2008-12-04
> **bodhi.zazen said:**
> LOL, I understand

Take a look at the "Intrusion Detection" sticky.

Well, I checked it and I read that I should use AirSnort because I have wireless, but then I went to their page and it said that it was way outdated.

---


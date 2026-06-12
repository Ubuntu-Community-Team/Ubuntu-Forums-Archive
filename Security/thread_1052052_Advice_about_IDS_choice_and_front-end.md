---
title: "Advice about IDS choice and front-end"
date: 2009-01-27
forum: Security
---

### Post by anirvana on 2009-01-27
Dear All,
        I am looking to install an IDS on my Ubuntu 8.10 machine. Snort is an obvious option and there are awesome tutorials all over the place.

before I go my merry way installing and using Snort, if I could get some advice regarding if Snort is what I am looking for, would be great.

What am I looking for: An IDS which is popularly used (like Snort) and if any intrusion detection is done I want a pop up like thing or something instant to tell me "hey something is wrong".. I don't want to have to query a db by myself. Is there a front-end available which can do this?

I know some of you may think..why can't he just write  script. I can, but just looking for something a bit pretty :-)

Thanks again folks,
-A

---

### Post by The Tronyx on 2009-01-27
I don't know of anything that will give pop-ups.  You might be able to use the Firefox Nagios plugin to alert about snort but that is mostly speculation.  Additionally you could get e-mails about snort alerts so those suggestions might be the best things to look into.

EDIT:
I decided to fire up the old google machine and came across this, [http://seclists.org/focus-ids/2003/Jun/0061.html](http://seclists.org/focus-ids/2003/Jun/0061.html).  The interesting part is "Does anyone have an opinion on Nagios? They say it can use snort and it has it's own IDS functions to detect certain traffic."  So based on that, you can either somehow hook Snort into Nagios or use Nagios as a standalone IDS.

---

### Post by anirvana on 2009-01-27
thank you 2point0.. :)

---


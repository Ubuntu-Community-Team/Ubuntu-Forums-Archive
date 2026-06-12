---
title: "[SOLVED] moblocker"
date: 2008-06-27
forum: Security
---

### Post by daggerx on 2008-06-27
i know its on and i know its updatde but its not blocking anything, im using azareus and my nat is ok, please advise and thanks

ubuntu rules...im gonna convert everybody to it thats comes 5 feet from me...

---

### Post by MaddMatt on 2008-07-12
Are you running Firestarter or another firewall in addition? It's possible that none of the offending traffic is actually reaching moblock. Do you have any network logs that suggest otherwise? Is it being loaded at boot? Check out your /etc/crond.daily/ directory to see if it's in there. Check out your logs to see if it has errors starting up. There could be a lot of reasons. 

I'm glad you're psyched on Ubuntu too! 


PS. Next time try a more descriptive title like "Moblocker isn't blocking anything" rather than just "Moblocker" That will give people a better idea as to what you're writing about, and therefore cause more people to read it.

Cheers, 
-M

---

### Post by daggerx on 2008-07-13
I was able to get it to work.

Cheers

---

### Post by mikey01 on 2008-07-18
how did you get it to work?  moblock doesn't seem to be blocking anything for me either.  i'm looking at the log with 'tail -f /var/log/moblock' while using Transmission.

---

### Post by daggerx on 2008-07-18
I went [here]("https://help.ubuntu.com/community/MoBlock") and the first part of the faqs on that page solved my problems.

instead of what they have there:

```
WHITE_IP_IN="192.168.0.0/24"
WHITE_IP_OUT="192.168.0.0/24"
```

I had to put:

```
WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"
```

Also, sometime last night, moblock had an update - not sure what the update was but updates are good in this world. Hope that helps.

---

### Post by jre on 2008-07-18
> **mikey01 said:**
> how did you get it to work?  moblock doesn't seem to be blocking anything for me either.  i'm looking at the log with 'tail -f /var/log/moblock' while using Transmission.

Please post "moblock-control status" and "moblock-control test". Also the logfiles in /var/log/ might help.

---


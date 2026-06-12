---
title: "How to watch logs for attacks?"
date: 2010-03-11
forum: Security
---

### Post by dogdo on 2010-03-11
Ive often read that the first place to look for break ins is to read the logs. In ubuntu 9.10 there is the 'log file viewer' under the administration menu but i find most of the data there really confusing. Is there a program i can use in the repositories that sends a pop up on the screen when something potentially malicious is trying to get access to the local pc/bypass sudo/bypass the ip tables firewall?

---

### Post by uRock on 2010-03-11
I found this book to be helpful for that stuff. [https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=978-0-7357-1265-2&x=0&y=0](https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=978-0-7357-1265-2&x=0&y=0)

---

### Post by km0r3 on 2010-03-11
I use [logwatch]("http://www.google.com.py/url?sa=t&source=web&ct=res&cd=1&ved=0CAYQFjAA&url=http%3A%2F%2Fwww.logwatch.org%2F&ei=MF-ZS8DCBIL68Aaev-nGCg&usg=AFQjCNGCVqEQ2Rmc8Sjpg8lOY3l14E_uDA&sig2=KPrB2ajvpowfB1bW9nccGw") for being notified about meaningful occurrences in logs I specify per mail.

If you want to watch logs live you could do something like:

```
tail -f [filename]
```

If you want something more custom you could try `tenshi`, which AFAIK is in the Ubuntu repository, so
```
sudo apt-get install tenshi
```
will do the job.

Tenshi watches logs and notifies you about regular-expression matched results.

Have fun. :)

---

### Post by OpSecShellshock on 2010-03-11
Generally speaking, unless you're getting paid to watch logs, it's not a good idea to do it. It'll just make you anxious over what are mostly, if not entirely, false positives and failures. Under a default configuration (nothing listening for connections from the open web) all incoming traffic is denied unless it's in response to something you initiated on your end. As long as you don't have anything set up to allow remote access you should be OK.

The risk of web exploits is higher for most users than that of network based intrusions, but those come from the inside out (meaning you've requested a page that runs a script and the script might be malicious and could potentially do some damage). The other major risk is that you install something that you expect to do one thing but that also contains exploit code. In both of those cases, nothing is likely to show up in the logs because as far as the computer can tell, it's the behavior you've asked for.

---

### Post by bodhi.zazen on 2010-03-11
> **dogdo said:**
> Ive often read that the first place to look for break ins is to read the logs. In ubuntu 9.10 there is the 'log file viewer' under the administration menu but i find most of the data there really confusing. Is there a program i can use in the repositories that sends a pop up on the screen when something potentially malicious is trying to get access to the local pc/bypass sudo/bypass the ip tables firewall?

The most important thing you can do is familiarize yourself with the logs so you know what is "normal"

If you want some kind of HIDS, see the sticky at the top of these forums and install OSSEC or similar.

A popup with every anomaly in the logs would become overwhelming in short order and inactivated.

This is in fact one potential strategy of crackers, generate so many "false positives" that a sys admin inactivates the HIDS. Crude but effective.

---


---
title: "Blocking a website with google chrome"
date: 2010-02-11
forum: Security
---

### Post by eruheru on 2010-02-11
Hi all,
there has been a recent trend at my school of "meat spinning" laptops. (if you don't already know what this is investigate at your own risk... it is not pretty). I already take the precaution of keeping my computer password protected when not in use, but I would like the added security of blocking meatspin.com. I was able to block it in firefox by adding it to the host file, however I was unsuccessful with google chrome. I was able to block other sites such as apple.com on chrome. Is there anything else I can try? 
these are the lines I tried.

127.0.0.1 meatspin.com
127.0.1.1 meatspin.com
0.0.0.0 meatspin.com

Thanks!

---

### Post by Satoru-san on 2010-02-11
Perhaps google chrome doesnt use your computers nameserver and hosts file for things, instead it may use google dns.


EDIT: yes it does what is called prefetching dns. Here is how to turn it off.

[http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=96788](http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=96788)

---

### Post by eruheru on 2010-02-12
thanks, your fix worked!

---

### Post by Jekshadow on 2010-02-13
Why do you need to add 3 different entries to block one website? Why not just:
```
127.0.0.1     meatspin.com www.meatspin.com
```

---

### Post by eruheru on 2010-02-13
I didn't try all three at the same time, I was just showing the variations that I thought would work but didn't.

---


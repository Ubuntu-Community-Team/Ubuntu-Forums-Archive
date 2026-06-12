---
title: "rkhunter suspect file"
date: 2011-12-17
forum: Security
---

### Post by scholzilla on 2011-12-17
i took the advice to run rkhunter on my machine, but am way out of my league interpreting the output. Yes, I looked at the FAQ, but don't understand much of it. I had a couple of warnings which seem to be normal (according to posts at bugs.debian.org), but then I also have this:


```
[18:32:50] File properties checks...
[18:32:50] Files checked: 133
[18:32:50] Suspect files: 1
```

Could someone please help me understand how to proceed? Thanks.

---

### Post by Dangertux on 2011-12-17
> **scholzilla said:**
> i took the advice to run rkhunter on my machine, but am way out of my league interpreting the output. Yes, I looked at the FAQ, but don't understand much of it. I had a couple of warnings which seem to be normal (according to posts at bugs.debian.org), but then I also have this:


```
[18:32:50] File properties checks...
[18:32:50] Files checked: 133
[18:32:50] Suspect files: 1
```Could someone please help me understand how to proceed? Thanks.

Check /var/log/rkhunter.log

See what it says the suspect file is let us know. Thanks

---

### Post by scholzilla on 2011-12-18
thanks for the reply. It doesn't list the name of the suspect file as far as I can tell. If there is a way to get at this info, I don't know how. This may be academic at this point, as I decided to reinstall 10.04 as I didn't really like 11. But it would be nice to know the answer in case I run into this again. Thanks.

---

### Post by Dangertux on 2011-12-18
In the file rkhunter.log which is stored in /var/log it gives more verbose output. It should have listed the file it found as suspect. Obviously if you reinstalled though that is gone now. 

Hope this helps

---

### Post by scholzilla on 2011-12-18
thanks, but I did check the log and, though you are correct that there is a lot more output, there was no further information on the suspect file. Strange, but I guess don't worry about it.

---

### Post by Dangertux on 2011-12-18
> **scholzilla said:**
> thanks, but I did check the log and, though you are correct that there is a lot more output, there was no further information on the suspect file. Strange, but I guess don't worry about it.

That's weird that it would say there is a suspect file and not say what it was... I've never seen that behavior before :-/

---


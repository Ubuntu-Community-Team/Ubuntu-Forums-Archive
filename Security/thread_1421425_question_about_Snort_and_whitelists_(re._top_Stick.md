---
title: "question about Snort and whitelists (re. top Sticky)"
date: 2010-03-04
forum: Security
---

### Post by jacksmash on 2010-03-04
Hey,

I have a question about Snort.

I've been successfully running Snort for over a week now. Regarding the top Sticky in this forum, I'm using the provided script to run Snort. In the script, there is a whitelist variable where I add my ISP's DNS servers, because I am constantly getting false alarms about them.

```
WHITELIST='A.B.C.D A.B.C.E'
```

Where A.B.C.D and A.B.C.E. are the DNS servers. However, even after restarting Snort with this script I'm still getting DNS spoof alerts with the IP addresses of these servers as the host.

Am I missing something?

---

### Post by jacksmash on 2010-03-04
Ignore that. I typed in the wrong IP address :S

---

### Post by Richiegs on 2010-03-08
I just installed Snort through Synaptic Package Manager & restart. How come I can't find Snort under Application? Is it true that I can only run Snort in the terminal?

---

### Post by jacksmash on 2010-03-08
> **Richiegs said:**
> I just installed Snort through Synaptic Package Manager & restart. How come I can't find Snort under Application? Is it true that I can only run Snort in the terminal?

Hey,

Follow this tutorial and it will get you going:

[http://ubuntuforums.org/showthread.php?t=919472]("http://ubuntuforums.org/showthread.php?t=919472")


Cheers.

---


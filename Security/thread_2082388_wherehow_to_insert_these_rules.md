---
title: "where/how to insert these rules"
date: 2012-11-09
forum: Security
---

### Post by Soul-Sing on 2012-11-09
where/how to insert these rules in an existing iptables script?: 
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

- A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*google.com&#8221; &#8211;j DROP
- A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*google.inc.&#8221; &#8211;j DROP
- A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*facebook.com&#8221; &#8211;j DROP
- A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*akamai.net&#8221; &#8211;j DROP

main/work string: iptables &#8211;A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*blocked.com&#8221; &#8211;j DROP

---

### Post by Doug S on 2012-11-09
If you don't provide a larger context (i.e. your existing rule set), your question is difficult to answer.
Also, be aware that use of the iptables string module can be somewhat CPU intensive. (Although I haven't used it for maybe about a decade (back then, one had to re-compile the kernel to use it)).
It looks as though you are trying to use a wild card in your string match rules. I don't know for sure, but I don't think it works that way.

---

### Post by Soul-Sing on 2012-11-09
> **Doug S said:**
> If you don't provide a larger context (i.e. your existing rule set), your question is difficult to answer.
Also, be aware that use of the iptables string module can be somewhat CPU intensive. (Although I haven't used it for maybe about a decade (back then, one had to re-compile the kernel to use it)).
It looks as though you are trying to use a wild card in your string match rules. I don't know for sure, but I don't think it works that way.

Hi,
I have made an other iptables script, I found the insert rules to difficult for now. It does work for now. I'll keep a look at the logs, and how more "empty" they are, the better. :)

---

### Post by Doug S on 2012-11-11
Glad you got it sorted out. If you would be kind enough to report back, I would be very interested to know how the string rules are working for you in your application. I realize it might be several days before you know for sure.

---


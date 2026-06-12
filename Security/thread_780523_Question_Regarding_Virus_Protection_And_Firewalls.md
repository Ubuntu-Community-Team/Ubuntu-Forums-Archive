---
title: "Question Regarding Virus Protection And Firewalls"
date: 2008-05-03
forum: Security
---

### Post by Aleki on 2008-05-03
I'm rather new to Linux, in fact Ubuntu is my first OS other than Windows. What all do I need to make sure my new PC is secure? I have no clue as to what I need to keep this OS stable.

Any help?

---

### Post by p_quarles on 2008-05-03
Please read the "Ubuntu Security" sticky thread at the top of this forum. If you any (more specific) questions after that, please ask here.

---

### Post by cpkoch on 2008-06-29
OK .. What is a sticky thread?  Are there any answers to the question that can be understood just by using plain language phrases like "yes" or "no"?
 I looked all over for  a sticky thread and am at a loss.

---

### Post by brian_p on 2008-06-29
> **cpkoch said:**
> OK .. What is a sticky thread?  Are there any answers to the question that can be understood just by using plain language phrases like "yes" or "no"?

Yes. Maybe.

> I looked all over for  a sticky thread and am at a loss.

Post #2.

---

### Post by hyper_ch on 2008-06-29
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

and no, you generally don't need antivirus or twinker with any firewall.

---

### Post by kevdog on 2008-06-29
I think a blanket statement stating you don't need a firewall is a little misleading.  What role do you want your computer to play?  If you are setting it up as a router that shares connections with mixed windows and linux boxes, then I would say use of iptables is definitely a plus.  If you are using your box simply as a desktop replacement, then a firewall(iptables) is probably less important.

---

### Post by hyper_ch on 2008-06-30
that's why I said "generally" ;)

---

### Post by aysiu on 2008-06-30
Yes, please explain a bit more what you'll be using Ubuntu for.

Will it be a server of some kind (web server, file server, mail server)?

---

### Post by kevdog on 2008-06-30
Generally we would be in agreement.  Hopefully the OP will provide clarification.

---

### Post by wbutchart on 2008-06-30
I wasnt sure about firewalls so i installed firestarted im surprised as its only been on 20 mins and has already blocked 9 attempts and 4 of those it highlighted as serious.  Doesnt that show there is a need for firewalls on ubuntu? esp as a may use it to shop online.

---

### Post by Barrucadu on 2008-06-30
No, because there are no services running by default that the outside world can connect to. Those 9 attempts will just be people scanning random computers for vulnerabilities.
You only need a firewall if running some form of server.

---

### Post by hyper_ch on 2008-06-30
and even if you are running services you must ask yourself do you want them to be accessible by everyone (e.g. you normally want a webserver to be accessible by everything) and if that's the case, you don't need firewall eitehr... however you could for example blcok access for certain countries or stuff...

---

### Post by shad0w_walker on 2008-06-30
To my knowledge firestarter is a front end to IPtables, which is installed and running on Ubuntu and pretty much every Linux distro by default. You are now just able to see when it blocks the attempts, it's always been doing it, just quietly in the background.

---

### Post by kevdog on 2008-06-30
iptables by default is running in the background, but is configured without any sort of rules -- so hence its like its not running since its not filtering or forwarding any traffic.

---

### Post by Thomas00 on 2008-12-29
"We can download AVG free and it working very well on virus removal. I know one more free anti virus software which is also best for virus attack [www.search-and-destroy.com](www.search-and-destroy.com) it has proved it's work efficiency try it and enjoy.

Thank You."

---


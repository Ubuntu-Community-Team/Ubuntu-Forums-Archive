---
title: "New Russian threat"
date: 2016-02-16
forum: Security
---

### Post by Lloydb39 on 2016-02-16
What about Fysbis? Should I worry, with Ubuntu 14.04 on a homemade system?

---

### Post by Habitual on 2016-02-16
No.  See 3rd paragraph of [http://news.softpedia.com/news/fysbis-the-linux-backdoor-used-by-russian-hackers-500367.shtml](http://news.softpedia.com/news/fysbis-the-linux-backdoor-used-by-russian-hackers-500367.shtml)

---

### Post by sabina2 on 2016-02-16
Just wondering why we didn't see any patch if they know what it does ? Don't they know how we can get infected ?

Moreover, does it work and remain invisible with minimum security features working, such as AppArmor, Rkhunter, or such things ?

---

### Post by QDR06VV9 on 2016-02-16
I Do not know how valid these are but have a look How To Detect Fysbis
[https://www.rfxn.com/projects/linux-malware-detect/](https://www.rfxn.com/projects/linux-malware-detect/)

---

### Post by sabina2 on 2016-02-16
Thanks !

---

### Post by bashiergui on 2016-02-16
> **Lloydb39 said:**
> What about Fysbis? Should I worry, with Ubuntu 14.04 on a homemade system?
Not unless you work for a defense contractor or Eastern European government.
[http://researchcenter.paloaltonetworks.com/2016/02/a-look-into-fysbis-sofacys-linux-backdoor/](http://researchcenter.paloaltonetworks.com/2016/02/a-look-into-fysbis-sofacys-linux-backdoor/)

---

### Post by bashiergui on 2016-02-16
> **sabina2 said:**
> Just wondering why we didn't see any patch if they know what it does ? Don't they know how we can get infected ?

Moreover, does it work and remain invisible with minimum security features working, such as AppArmor, Rkhunter, or such things ?They didn't say how the keyloggers were delivered or installed. If they tricked users into executing them, you can't patch against that.

Install software from the Ubuntu repository and you'll be fine. Install software from random sources on the internet you're taking your chances. As is always the case.

---

### Post by matt_symes on 2016-02-16
Hi

> **sabina2 said:**
> Moreover, does it work and remain invisible with minimum security features working, such as AppArmor, Rkhunter, or such things ?

Minimum security features ?

The weak link in the chain is usually PEBKAC.

Kind regards

---

### Post by Lloydb39 on 2016-02-19
[https://blogs.gnome.org/mcatanzaro/2016/02/01/on-webkit-security-updates/](https://blogs.gnome.org/mcatanzaro/2016/02/01/on-webkit-security-updates/)

---

### Post by buzzingrobot on 2016-02-19
> **bashiergui said:**
> They didn't say how the keyloggers were delivered or installed. If they tricked users into executing them, you can't patch against that.


Indeed.  The *au courant *way to deliver malware is to persuade users to install it:  Phishing email attacks,  infected web ads, etc.  

I see many anti-malware tools sold into the Windows market claim to prevent all that, but malware distributors find workarounds. 

Run a good ad blocker and think before opening emails. (If I used Windows, I would use a mail client that allowed me to display only the subject line of messages, so the full message would load only if I specifically wanted that to happen. A good IMAP client should be able to do this.)

---


---
title: "DNS spoofing"
date: 2011-09-08
forum: Security
---

### Post by bholzer on 2011-09-08
I'm playing around with DNS spoofing using ettercap. I am testing with a windows 7 machine. 

The redirection works perfectly, however, the URL changes to reflect the website that is actually displaying. What can I do to keep this from happening?

---

### Post by Dangertux on 2011-09-08
This isn't something that is really supported here. I would suggest consulting the ettercap documentation.

---

### Post by bholzer on 2011-09-08
What exactly isn't supported? Security testing?

---

### Post by lisati on 2011-09-08
> **bholzer said:**
> What exactly isn't supported? Security testing?

It wasn't immediately clear from your first post that you were doing security testing. If this is what you are really doing, we might consider leaving this thread open.

---

### Post by bholzer on 2011-09-08
Ah, my apologies for not clarifying. I installed ettercap to test my network and see which machines/protocols are vulnerable to MITM attacks. I've had slow connections and odd behavior lately, so I was trying to see if maybe this was the issue. 

During the testing, I noticed that my computers are redirecting during cache poisoning, but the URL is changing correctly. Of course this is a good thing for me, as this means nobody is phishing, but I was just curious as to why, and now I'm a man on a mission!

---

### Post by Dangertux on 2011-09-08
To be perfectly honest, it still doesn't fit within the constraints of security auditing.

You know the system is vulnerable because the redirection works and the DNS poison was successful. Obfuscating the actual host address is pointless other than to confuse a potential victim.

I stand by my point that this is not something supported, and suggest learning more about DNS and how ettercap works.

So I will leave you with a question, if this is a legitimate 'audit' of your own systems, what advantage do you gain in preventing/mitigating/remediating this type of attack by hiding the host name? What information can that give you in terms of protection? Answer that and you will see exactly why I responded as I did.

---

### Post by bholzer on 2011-09-08
> **Dangertux said:**
> To be perfectly honest, it still doesn't fit within the constraints of security auditing.

You know the system is vulnerable because the redirection works and the DNS poison was successful. Obfuscating the actual host address is pointless other than to confuse a potential victim.

I stand by my point that this is not something supported, and suggest learning more about DNS and how ettercap works.

Understandable, thanks anyway!

---

### Post by Dangertux on 2011-09-08
I'm not trying to be a meanie or condescending a lot of people ask questions like this and not many of them often are up front with the reasons they are doing it.

I will tell you this, everything you want to know about this topic can be found in documentation relating to DNS servers and how they operate as well as the ettercap documentation.

I will give you a hint, it has something to do with TTL

---

### Post by haqking on 2011-09-09
> **Dangertux said:**
> To be perfectly honest, it still doesn't fit within the constraints of security auditing.

You know the system is vulnerable because the redirection works and the DNS poison was successful. Obfuscating the actual host address is pointless other than to confuse a potential victim.

I stand by my point that this is not something supported, and suggest learning more about DNS and how ettercap works.

So I will leave you with a question, if this is a legitimate 'audit' of your own systems, what advantage do you gain in preventing/mitigating/remediating this type of attack by hiding the host name? What information can that give you in terms of protection? Answer that and you will see exactly why I responded as I did.

> **Dangertux said:**
> I'm not trying to be a meanie or condescending a lot of people ask questions like this and not many of them often are up front with the reasons they are doing it.

I will tell you this, everything you want to know about this topic can be found in documentation relating to DNS servers and how they operate as well as the ettercap documentation.

I will give you a hint, it has something to do with TTL


+ 1 said it all really.

Very hard to respond to these types of questions, though testing is something alot of us do and need help on from time to time, it generally isnt supported here, and everything you need to know lies within DNS itself as mentioned.

Good luck or try over at the ettercap forum at [http://www.governmentsecurity.org/](http://www.governmentsecurity.org/) ettercap is a little out of date now, last realease something like 2006 or 2007 maybe ? but still valid i guess.  Last time i used it was for my CEH exam, but then that is full of old skool ;-)

---

### Post by bholzer on 2011-09-09
> **Dangertux said:**
> I'm not trying to be a meanie or condescending a lot of people ask questions like this and not many of them often are up front with the reasons they are doing it.

I will tell you this, everything you want to know about this topic can be found in documentation relating to DNS servers and how they operate as well as the ettercap documentation.

I will give you a hint, it has something to do with TTL

No offense taken, I understand where you guys are coming from, but I appreciate the hint!

> **haqking said:**
> + 1 said it all really.

Very hard to respond to these types of questions, though testing is something alot of us do and need help on from time to time, it generally isnt supported here, and everything you need to know lies within DNS itself as mentioned.

Good luck or try over at the ettercap forum at [http://www.governmentsecurity.org/](http://www.governmentsecurity.org/) ettercap is a little out of date now, last realease something like 2006 or 2007 maybe ? but still valid i guess.  Last time i used it was for my CEH exam, but then that is full of old skool ;-)

Thanks for the info, much appreciated.

---


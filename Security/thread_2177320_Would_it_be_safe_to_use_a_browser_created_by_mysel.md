---
title: "Would it be safe to use a browser created by myself to surf the net?"
date: 2013-09-28
forum: Security
---

### Post by Wiking on 2013-09-28
I really want to try to develop my own browser using some w3 libs but am wondering what kind of risks I might run into regarding malware and javascript infections things of that sort if I use it to surf the net. 

I'm going to go ahead and try to build one but would like to know what kind of risks I might into and what precautions I should take. Perhaps just running it on a virtual machine until I get a better grasp of the security aspect of it.

---

### Post by unspawn on 2013-09-28
> **Wiking said:**
>  what kind of risks I might run into regarding malware and javascript infections things of that sort
While virtualization does allow you to isolate processes it does not prohibit downloading code and subsequent client side execution of it. Given there's no code to audit and given the (with all due respect) vague definition of "malware" this IMHO shouldn't have started out as a security forum question but one for a programming forum in terms of determining programming proficiency and adherence to safe programming rules, discussing core browser features and security features like the kind of sandboxing Chrome provides etc, etc. But like I said that's just IMHO.

---

### Post by Lars Noodén on 2013-09-28
Virtual machines add absolutely zero to security.  There is a lot written on that already so you can find material if you need.  

What you can do on your machine would be to tighten down what the browser has access to.  In Ubuntu that can be done with [apparmor](https://wiki.ubuntu.com/AppArmor).  That can be a bit fiddly and it will take more than a few tries to get it right.

---

### Post by Wiking on 2013-09-28
yes, perhaps I might be getting ahead of myself a bit. In the meantime I'll start playing around with apparmor.

---

### Post by Nil_Pointer on 2013-09-29
If you write a complete browser by yourself without using any engines, it'd be very safe as long as you don't disclose code. It's called "security through obscurity". Despite such browser will certainly contain vulnerabilities, nobody will have source or even binaries, so they will have no way of learning about their existence. And of course, nobody will even bother to hack a browser that is used by one person, unless they're after you. So, this is really secure and paranoid way (meaning don't do that unless you have spies on your trail).

However, even widely-used browsers can be quite safe.

1. Linux platform is just more secure (it's secure by design and anyway, most of exploits and malware are Windows-targeted).
2. Properly configured apparmor can prevent exploited browser from causing damage to the system.
3. Disable Java-applets (I can't remember last time when I needed them. If I need them for some site, I'd enable them temporarily, because most of time they just introduce security risks (we all love Java's 0-day exploits)).
4. Disable Flash content from loading automatically by enabling click-to-play in browser (You'd cut a lot of annoying ads and security risks. This will break some sites, but you can add those to whitelist).
5. If you're absolutely paranoid, you can disable JavaScript (though it's needed for majority of sites and should be much safer than Java and Flash).

---


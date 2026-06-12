---
title: "Linux safe from poisened Google  web searchs"
date: 2007-11-29
forum: The Cafe
---

### Post by sdowney717 on 2007-11-29
[http://news.bbc.co.uk/1/hi/technology/7118452.stm](http://news.bbc.co.uk/1/hi/technology/7118452.stm)

apparently malicious sites are getting good at what they do.
Linux, I assume is completely immune from this attack.

---

### Post by rfruth on 2007-11-29
hmm, is this similar to poisoning  the DNS ?

---

### Post by Sef on 2007-11-29
From the article mentioned above:

> Websites loaded on these domains were booby-trapped with malicious software that looked for vulnerabilities in copies of Microsoft's Internet Explorer used to browse them.

If they were attacking Firefox, then GNU/Linux might be vulnerable.

---

### Post by c_plus_plus on 2007-11-29
But in windows internet explorer is a deeply integrated part of the system allowing a vulnerability in IE to yield a hole into Windows. How would a vulnerability in Firefox present a similar danger to Linux, or for that mater Firefox on Windows?

---

### Post by sdowney717 on 2007-11-29
I get updates to fix security breaches in Ubuntu programs. If hackers wished to design malicious code for Linux, it looks like they can try. I have read though that Linux is by nature more secure. Something about programs not being able to run with out permission. 
Can malicious code execute on a linux box unknown to the user or would a user have to actually knowingly star up such a program?
If linux becomes more popular, we might just see an upsurge in malicious attempts against linux.

What do you suppose could be done against a linux box?

---

### Post by p_quarles on 2007-11-29
> **sdowney717 said:**
> I get updates to fix security breaches in Ubuntu programs. If hackers wished to design malicious code for Linux, it looks like they can try. I have read though that Linux is by nature more secure. Something about programs not being able to run with out permission. 
Can malicious code execute on a linux box unknown to the user or would a user have to actually knowingly star up such a program?
If linux becomes more popular, we might just see an upsurge in malicious attempts against linux.

What do you suppose could be done against a linux box?
Well, since most people run their web browser as their normal user, and since the normal user can execute code within their userspace without root privileges, a browser exploit could potentially do a lot to a Linux user. 

The privilege separation guarantees that the exploit wouldn't be able to install software in the executable path, rootkit the system, or alter your iptables rules. That rules out some of the most damaging attacks, but there are a lot of other things that could done as well.

Basically, be careful about what sites you allow to run client-side scripts on your system. 

The bottom line is that usability and security are always somewhat at odds. If the system allows you to a lot of things with minimal effort (and that's basically what a web browser is designed to do), then the potential for security holes is always present.

---

### Post by bruce89 on 2007-11-29
Gecko is a holey thing, the sooner it is got rid of, the better.

"Hackers" don't target GNU/Linux for 2 reasons:
[LIST=1]
[*]Few experienced users use it.
[*]They probably use it, so they don't want to harm their own.
[*]Because of the nature of Free Software, anyone can find and fix holes easily.
[/LIST]

---

### Post by sdowney717 on 2007-11-29
yes, I always thought some of the malicious hackers are MS haters.

I have read how some want to exploit the MS OS simply to show everyone how they can and how bad security wise MS OS are. 

But these folks, Russian Business Network - a hi-tech criminal gang, not many I think have ever heard of them,  sounds pretty serious.
How about that a cyber war continually raging, working secretly with their activities  hidden away from most internet users

---

### Post by p_quarles on 2007-11-29
> **bruce89 said:**
> Gecko is a holey thing, the sooner it is got rid of, the better.

Because of the nature of Free Software, anyone can find and fix holes easily.

Just out of curiosity, how would you reconcile those two statements? Gecko is, after all, open source.

In any case, the vast majority of exploits don't even target html. If a browser is set to allow scripting, or has any media plugins, it's a potential target for exploits. The problem is in the power of the browser, and while design flaws lead some to be better than others, it really is a matter of this:
1) Developers build a higher fence
2) Black hats get a bigger ladder
3) Repeat. 

And like I said, I do think that Linux is much more secure against these things at the OS level, but everything I've been reading suggests that the userspace web browser is a problem without an easy fix.

---


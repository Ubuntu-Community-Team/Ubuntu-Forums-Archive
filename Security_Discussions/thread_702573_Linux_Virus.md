---
title: "Linux Virus"
date: 2008-02-20
forum: Security Discussions
---

### Post by rlange on 2008-02-20
New users  could use some help to check their systems for this age old linux virus that keeps coming back.  Is Ubuntu at risk?

Read more here:


[http://www.sophos.com/security/blog/2008/02/1062.html](http://www.sophos.com/security/blog/2008/02/1062.html)

---

### Post by p_quarles on 2008-02-20
Moved to Security Discussions. The question posed might get a more informed answer here.

In any case, I'm skeptical. This is a commercial anti-virus company, and they don't really go into detail about how these infected honeypots were set up. As far as I knew, the kernel was patched against this virus long ago. So, while I don't want to dismiss this report out of hand, I do suspect that something is being marketed here.

---

### Post by spiderbatdad on 2008-02-20
Doesn't look very practical, as Ubuntu runs anti-virus software behind the scenes. You would need to disable your anti-virus software to assist them in their research.

---

### Post by rlange on 2008-02-20
But the removal tool they provide is free. ??  Just thought I would throw this out there as the link was sent to me today from a large IT dept. I am at work now and won't be at my ubuntu box until tonight.

---

### Post by tehet on 2008-02-20
> &#8220;Your server was not booting because it had been infected with the RST.b Virus. This infection was caused by a root compromise. It appears the hacker gained access to your server by using the &#8221;news&#8221; user, and then elevated his/her privileges to root using a brute force password hack, or via a local kernel exploit.&#8221;
[http://www.shandyking.com/2006/04/20/linux-exploit-linuxrstb-my-server-was-just-hacked/](http://www.shandyking.com/2006/04/20/linux-exploit-linuxrstb-my-server-was-just-hacked/)
So I'd say the virus isn't a big deal. Bad passwords on unpatched systems are.

---

### Post by p_quarles on 2008-02-20
> **rlange said:**
> But the removal tool they provide is free. ??  Just thought I would throw this out there as the link was sent to me today from a large IT dept.
Which hardly means they're doing it out of the goodness of their hearts. They are a security software company: they wouldn't be doing this without some kind of profit motive in mind. Acrobat Reader is free of charge as well, and has been a key component in Adobe's profit model. 

Again, I'm skeptical. I'm happy to see some solid evidence that this virus is a threat to a patched machine with a sane security policy. I'll be surprised, but I'll believe what the evidence shows.

---

### Post by rlange on 2008-02-20
> **p_quarles said:**
> Which hardly means they're doing it out of the goodness of their hearts. They are a security software company: they wouldn't be doing this without some kind of profit motive in mind. Acrobat Reader is free of charge as well, and has been a key component in Adobe's profit model. 

Again, I'm skeptical. I'm happy to see some solid evidence that this virus is a threat to a patched machine with a sane security policy. I'll be surprised, but I'll believe what the evidence shows.


This could be but it would not be the first time a AV company put out a free removal tool.

---

### Post by p_quarles on 2008-02-20
> **rlange said:**
> This could be but it would not be the first time a AV company put out a free removal tool.
That's kind of my point. Releasing a free product is a common practice for commercial software companies. That doesn't mean it's charity.

---

### Post by rlange on 2008-02-20
I just wanted to pass it along so anyone with more experience with Ubuntu than I could comment as to the need to run this tool or just not worry about it.
          My system has been solid for a couple years now running Ubuntu and have not had ANY issues so I really don't need to mess with my system. This just had me somewhat concerned.

---

### Post by umattu on 2008-02-20
> **spiderbatdad said:**
> Doesn't look very practical, as Ubuntu runs anti-virus software behind the scenes. You would need to disable your anti-virus software to assist them in their research.

Really, I was totaly unaware of this, could you point me in the direction of some info in regards to this?

---

### Post by rlange on 2008-02-20
> **umattu said:**
> Really, I was totaly unaware of this, could you point me in the direction of some info in regards to this?

I really did not know this either.

---

### Post by p_quarles on 2008-02-20
> **umattu said:**
> Really, I was totaly unaware of this, could you point me in the direction of some info in regards to this?
It doesn't run anti-virus software per se. Rather, the underlying design of the system is such that self-replicating viruses aren't a threat. In the few past cases where viruses were shown to penetrate the system, security patches were able to close the holes. 

Basically, Linux's defense against Windows-style malware is its design. This does *not* mean that it's immune to any threats, but it does mean that the kind of exploits which have plagued Windows are much less likely to target Linux. (think: privilege separation and transparent process management).

---

### Post by fatality_uk on 2008-02-20
I agree with p_quarles who, as always, hit the nail on the head. It's the underlying OS architecture that means linux is much more secure than Windows. One additional point I have made before. If you use your Linux laptop on a Windows network, for instance at work, be sure that files you get and pass on are scanned. A virus might not effect your machine, but Linux wont magically remove an infected file so that virus can still effect the other Windows PC's on your network.

EDIT: Just read the EULA from that site

> THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED

That is basically saying, we are giving you this software, feel warm and fuzzy that you ran a scan, but if your PC is infected and we don't pick that fact up, **TOUGH!!!**

---

### Post by OrangeCrate on 2008-02-20
> **rlange said:**
> 
...Is Ubuntu at risk?...


A recent discussion on Linux and viruses is here:

[http://ubuntuforums.org/showthread.php?t=684224](http://ubuntuforums.org/showthread.php?t=684224)

Don't worry about viruses on Linux. AFAIK, all Linux viruses are theoretical, there are none in the wild.

---

### Post by rlange on 2008-02-20
So no Ubuntu users should not worry about this threat? It is a ruse by the AV company?  That is the general belief  here? This virus is not real?

here is what another av company says

[http://www.symantec.com/security_response/writeup.jsp?docid=2004-052312-2729-99](http://www.symantec.com/security_response/writeup.jsp?docid=2004-052312-2729-99)

And another 
[http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=ELF_RST.B](http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=ELF_RST.B)

And  howtoforge info

[http://www.howtoforge.com/sophos-linux-rst-b-backdoor-detection-tool-debian-etch](http://www.howtoforge.com/sophos-linux-rst-b-backdoor-detection-tool-debian-etch)

Not too sure this is a ruse.

---

### Post by tehet on 2008-02-20
> **rlange said:**
> Not too sure this is a ruse.
This virus does not exploit anything on its own so I doubt there was ever any patch against this virus, as opposed to what was claimed earlier in this thread. It is a backdoor that tries to copy itself to executables in /bin. A backdoor makes it easier for evil hackers to access an already compromised system.

In order to get the virus loaded onto the system one may e-mail the administrator of given system and ask if he/she would be so kind as to run the virus as root. Should the admin refuse, the evil hacker will need the following:
- break into an account on the system through ssh. This will likely require a password that is in a dictionary and therefore a bad password.
- use a known exploit that allows for privilege escalation, such as the recent splice local root exploit, and then run the code as root for it to work properly. This will likely require an unpatched system or operation in a very narrow time frame(i.e. before a patch comes out).

So when the evil hacker is about to run the virus, the system is already compromised thanks to poor security practices.

---

### Post by tubezninja on 2008-02-20
> **rlange said:**
> So no Ubuntu users should not worry about this threat? It is a ruse by the AV company?  That is the general belief  here? This virus is not real?

The virus is real, but to an up-to-date system running a current, linux kernel, it's not a huge threat, nor are other known linux viruses out there.  Your linux machine can't get this, or any other known virus, by just sitting and running.  A user (or hacker targeting a linux box with easy to guess usernames and passwords) has to do some very deliberate things to make this happen.

The key terms here are current, and patched.  As with any OS, security vulnerabilities do get discovered from time to time.  The people behind ubuntu happen to be very proactive in writing security updates to patch discovered problems quickly.  But it still remains the responsibility of the user to apply the patches as they come out ([it's not hard to do at all]("http://ubuntuforums.org/showthread.php?t=654237")).

Are there infected linux boxes out there?  Oh yes.  But they are running old kernels because the people using them aren't mindful of what they need to do, or employ extremely weak, extremely guessable usernames and passwords (i.e. guest/guest or something equally dumb).  I caught a box at a nearby university with an old linux distro doing a good old fashioned dictionary attack on my servers.  It didn't get in of course, and I sent off an e-mail to their IT department letting them know of the problem.  They took it off the network in short order, hopefully educated the user on what s/he needed to do.

Anyway, back to this detection tool.  Should you run it?  If it'll make you feel safer, go ahead.  But then again, you have to ask yourself: if you trust Sophos enough to run their code without another thought, that's very telling.   The risk, in my opinion, isn't in linux.  It starts with the person at the keyboard.

[To put your mind at ease, the detection tool appears safe.  I scanned the prepackaged executable for viruses, and for grins I ran the tool myself without ill effects.  And no, none of my machines were infected... big surprise.]

I'm not sure Sophos is scaremongering in this case more than it is fishing to see what it can find out there.

---

### Post by rlange on 2008-02-20
Well that seems to ease my mind as I have always kept my machine patched. Thanks for all the replies.

---

### Post by HermanAB on 2008-02-22
Here is a good explanation:
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---


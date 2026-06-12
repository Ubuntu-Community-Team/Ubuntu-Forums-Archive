---
title: "Worrying output from chkrootkit"
date: 2014-03-21
forum: Security
---

### Post by kjetil-fleten on 2014-03-21
When searching for rootkits with chkrootkit, I get this output in one of the last lines:
! root         1313 tty7   /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none

What is this, and what should  I do ?

---

### Post by ant2ne on 2014-03-21
Google.

(Or just search the forums)
[http://ubuntuforums.org/showthread.php?t=1980749](http://ubuntuforums.org/showthread.php?t=1980749)

---

### Post by Habitual on 2014-03-23
Does Ubuntu maintain the version in their repos?
The last apparent release-date is **Thu Jul 30 2009**.
If not, I'd not use chkrootkit and go for rkhunter, personally.

---

### Post by james114 on 2014-03-24
This is the system graphics server. 
It converts the layout of desktop applications into low-level drawing operations on your graphics card.

---

### Post by unspawn on 2014-03-24
> **james114 said:**
> This is the system graphics server. 
It converts the layout of desktop applications into low-level drawing operations on your graphics card. 
No, that's completely besides the point. This is about a known issue in 'chkutmp': a process being attached to a tty but not having any audit record yet (process waiting for a user login to occur).

---

### Post by HermanAB on 2014-03-25
Howdy,

Chkrootkit and others are mostly useless.  I haven't seen a rootkit on a machine in more than 20 years.

---

### Post by ant2ne on 2014-03-25
^^ I agree

---

### Post by unspawn on 2014-03-25
> **HermanAB said:**
> I haven't seen a rootkit on a machine in more than 20 years.
With all due respect this isn't (or shouldn't be) about *you* or what you *perceive* but what others should generally speaking do, like adhere to best practices and such.

---

### Post by ant2ne on 2014-03-26
Whether or not running chkrootkit would be a 'best practice' would be a matter of opinion.

---

### Post by kjetil-fleten on 2014-03-26
> **unspawn said:**
> No, that's completely besides the point. This is about a known issue in 'chkutmp': a process being attached to a tty but not having any audit record yet (process waiting for a user login to occur).

That sounds like a threat to me ?
I found another forum thread that suggests it could be my datacenter running a "stealth login" on tty7 so that if I put in a ticket they do not have to ask you for your password. This can be done with the openvt command ([http://www.webhostingtalk.com/showthread.php?t=566816](http://www.webhostingtalk.com/showthread.php?t=566816))

I tried to kill the process, but it immediately popped up again with a new PID.
Is there any other ways I can get rid of this ?

---

### Post by unspawn on 2014-03-27
> **kjetil-fleten said:**
> That sounds like a threat to me ?
No, not really.


> **kjetil-fleten said:**
> I found another forum thread that suggests it could be my datacenter running a "stealth login" on tty7 so that if I put in a ticket they do not have to ask you for your password. This can be done with the openvt command ([http://www.webhostingtalk.com/showthread.php?t=566816](http://www.webhostingtalk.com/showthread.php?t=566816))
That's an *interpretation* of it's *use*. Legitimacy of the process itself should first and foremost come from verifying system integrity and (changes in) configuration.


> **kjetil-fleten said:**
> I tried to kill the process, but it immediately popped up again with a new PID.
Is there any other ways I can get rid of this ?
Don't run X(11|org) on headless servers else I'm afraid you'll have to live with the message.

---


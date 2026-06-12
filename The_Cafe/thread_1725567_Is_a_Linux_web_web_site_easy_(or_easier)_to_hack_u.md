---
title: "Is a Linux web web site easy (or easier) to hack using Linux?"
date: 2011-04-09
forum: The Cafe
---

### Post by Learning Linux 2011 on 2011-04-09
I was responding to a thread earlier saying that the web site that allows students to apply for financial aid requires either Windows or Macintosh, and won't work with Linux.  Yet the irony is that the web site itself is run using a Linux web server.

It got me thinking, are they maybe afraid of getting hacked by Linux users?  If you use Linux, it it easy (or easier) to hack a Linux-based web site?


Similarly, I heard that the French government recently switched from Windows to Linux to save money, yet I recently read that they had some massive denial-of-service attack, which seems unfortunate and probably made them re-think their decision to switch.  Was that coincidence, or is that a potential problem with Linux web servers?

---

### Post by wojox on 2011-04-09
Doesn't really matter what OS you use. It's all in how it's configured and secured.

---

### Post by SeijiSensei on 2011-04-09
FAFSA doesn't "support" Linux because they don't want to maintain a support staff to handle calls about an operating system that will be used at most by a couple percent of the site's users.  It's a pragmatic decision, not a technical one.  

I do wish they'd just say, "you're on your own," rather than block Linux users entirely, but there may be Federal regulations involved that make that approach legally untenable.

---

### Post by rosencrantz on 2011-04-10
You can probably circumvent linux page blocks with the User Agent Switcher plug-in for Firefox.

I don't think the DoS attack is Linux-related (more likely anti-gloablisation protesters). 
A DoS attack buries a web server in traffic, independent of the OS running on it (actually, Apache/Unix(Linux) is pretty much standard on web servers) and it doesn't exploit security holes.
I suppose the French government switched to Linux on its office machines, which shouldn't run web servers.

However, the German foreign office switched partially to Linux and then back again to Windows because of compatibility issues.

---

### Post by supergirlkara on 2011-04-10
It will always depend on how up to date you are with security updates. There is always a way....until it is fixed in which case it's time to get the update. This is true with all operating systems.

---

### Post by ssam on 2011-04-10
remember that lots of linux people use the work 'hacking' to mean programming rather than breaking into things. so 'kernel hackers' or 'linux hackers' are the people who write linux.

---

### Post by HermanAB on 2011-04-10
Naah, you can run Cygwin on Windows and then you have access to all the usual Linux utilities like ngrep, tcpdump and whatnot.

However, you still need to know what you are doing no matter what system you use and there is no substitute for that.

---

### Post by themarker0 on 2011-04-10
No. Its not the applications, its the hacker himself. There are some hacker that i'm sure if you gave a brand new OS with just basic CLI they could do the same amount as damage with Windows seven or linux.

---

### Post by stmiller on 2011-04-10
> **Learning Linux 2011 said:**
> 

It got me thinking, are they maybe afraid of getting hacked by Linux users? 

Meh. Most people don't even know what Linux is. But I wish they would rather let you enter their site with a disclaimer: 'our help desk can only assist you with Mac or Windows'.

That is a better way of doing it.

---

### Post by WinterMadness on 2011-04-10
DOS attacks are networking related, not really OS related.

If someone pings you they ping you, that works on windows, linux, solaris, bsd, macosx.

Also, getting a DOS attack is not the same thing as being "hacked"

---

### Post by undecim on 2011-04-10
Any OS can hack any site. It doesn't matter which OS the client or the server is running.

Though I will say that hacking requires doing non-standard things, and Linux is easier to bend to your will. So I would say that hacking is easier done on Linux than on e.g. Windows. However, it can still be done with Windows, it just takes more work (in most cases)

Though blocking Linux probably wasn't a security thing. It was probably just the result of stupidity. Anyone with the ability to hack your site can do so while using, or masquerading as (e.g. with User Agent Switcher) another OS.

---

### Post by Rasa1111 on 2011-04-10
I think, in general..
Anything is "easier to hack" with Linux. lol

---

### Post by MasterNetra on 2011-04-11
> **wojox said:**
> doesn't really matter what os you use. It's all in how it's configured and secured.

+1

---


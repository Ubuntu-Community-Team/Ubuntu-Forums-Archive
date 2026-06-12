---
title: "Royal Navy Website Hacked, Passwords Release"
date: 2010-11-08
forum: The Cafe
---

### Post by Johnsie on 2010-11-08
Source: [http://freebc.co.uk/index.php?WorldNews=true&readworldnews=true&storyID=128](http://freebc.co.uk/index.php?WorldNews=true&readworldnews=true&storyID=128)

A Red Hat Linux server which hosted the Royal Navy website has been hacked. The site is currently down because so much information was released and spread across the Internet. The hackers released the contents of some of the database tables and some of the logins.

[http://www.royalnavy.mod.uk/](http://www.royalnavy.mod.uk/)


Quite embarassing for the UK military,

---

### Post by fatality_uk on 2010-11-08
This isn't a mission critical or operational web server/system.
This is the MOD Navy "web shop" nothing more.
Had they posted GCHQ logins or access to any SIS site then that would have been a hack.
Slightly embarrassing yes. A security risk, no.

---

### Post by Oxwivi on 2010-11-08
If the website is only that, the thread title is quite misleading. But still, a Linux system was hacked, and a Red Hat at that. This just might be serious for Linux at large.

---

### Post by _outlawed_ on 2010-11-08
> **Oxwivi said:**
> If the website is only that, the thread title is quite misleading. But still, a Linux system was hacked, and a Red Hat at that. This just might be serious for Linux at large.

Linux isn't 100% against invasion, it just makes it extremely harder for someone to get in.

---

### Post by jennybrew on 2010-11-08
> **_outlawed_ said:**
> Linux isn't 100% against invasion, it just makes it extremely harder for someone to get in.

Im no expert but I can tell you that where I work two *nix servers have been compromised in the last few months. Neither occasion was disastrous but it is very worrying that someone is finding it quite easy to gatecrash our party 
The techies dont say much to the likes of me but they have all put lots of hours in penetration testing recently.
No system is penetration proof me thinks

---

### Post by Dustin2128 on 2010-11-08
in my opinion, OpenBSD is what you want to run for security.

---

### Post by koenn on 2010-11-08
it was an sql injection attack, 
so the problem was in the design and implementation of the website or the framework it was built on. Maybe blame the webserver or the database too.

What operating system it runs on wouldn't have made a difference.

---

### Post by MasterNetra on 2010-11-08
Correction it was cracked, the individuals were crackers NOT hackers. (Hackers != Crackers) media and people still under the false assumption hackers break into systems... Granted it doesn't help crackers falsely take the title either.

---

### Post by Goldfissh on 2010-11-08
> **MasterNetra said:**
> Correction it was cracked, the individuals were crackers NOT hackers. (Hackers != Crackers) media and people still under the false assumption hackers break into systems... Granted it doesn't help crackers falsely take the title either.

This is true, and the god damn media still use incorrect names to refer to the bad guys, giving White Hats a bad name :(

---

### Post by radar920 on 2010-11-08
> **MasterNetra said:**
> Correction it was cracked, the individuals were crackers NOT hackers. (Hackers != Crackers) media and people still under the false assumption hackers break into systems... Granted it doesn't help crackers falsely take the title either.

crakers = good, i like ritz

---

### Post by Old_Grey_Wolf on 2010-11-08
> **koenn said:**
> it was an sql injection attack, 
so the problem was in the design and implementation of the website or the framework it was built on. Maybe blame the webserver or the database too.

What operating system it runs on wouldn't have made a difference.

+1

If the database had been properly patched, and the "best practices" followed, it wouldn't have happened. SQL injection has been known about for a long time.

---

### Post by Johnsie on 2010-11-09
Well, this could probably have happened no matter what OS was being used. Chances are the weak link was the code in the website. It's very easy to write something in PHP or whatever that is not secure.

When coding websites it's always important to write it in such a way that sql injections can be limited.


The site is still down a day later. This shows the seriousness of the incident. It makes me wonder how secure the rest of the UK military systems are.

---

### Post by koenn on 2010-11-09
> **Johnsie said:**
> This shows the seriousness of the incident. It makes me wonder how secure the rest of the UK military systems are.

it was just a website, hosted by some hosting provider from Texas. This has no bearing on the security of the actual military systems.
fatality_uk also pointed this out yesterday.

---

### Post by Evil-Ernie on 2010-11-09
Every system can be cracked given enough time and effort, its a shame its a Linux system and when the media get hold of a story facts seem to fly out the window :rolleyes:

---

### Post by Johnsie on 2010-11-09
> This has no bearing on the security of the actual military systems.

No, but it does suggest they are contracting bad programmers to do at least one of their main IT projects.

---

### Post by samjh on 2010-11-09
> **Oxwivi said:**
> If the website is only that, the thread title is quite misleading. But still, a Linux system was hacked, and a Red Hat at that. This just might be serious for Linux at large.

Not to those who know what they're doing.  ANY computer system, Linux or otherwise, is hackable.  Also, this was an application-level intrusion, so the operating system had very little to do with it.

---

### Post by Bodsda on 2010-11-09
> **masternetra said:**
> correction it was cracked, the individuals were crackers not hackers. (hackers != crackers) media and people still under the false assumption hackers break into systems... Granted it doesn't help crackers falsely take the title either.
 
+1

---

### Post by Oxwivi on 2010-11-09
> **samjh said:**
> Not to those who know what they're doing.  ANY computer system, Linux or otherwise, is hackable.  Also, this was an application-level intrusion, so the operating system had very little to do with it.
I meant the reputation, they specifically mentioned Red Hat. Those who don't know what they're doing, i.e. the general population, they're going to think negatively about Linux.

---

### Post by MisterGaribaldi on 2010-11-09
Maybe they can fix all the spelling mistakes while they're in there. Color instead of colour, and so forth. :P

---

### Post by Oxwivi on 2010-11-09
> **MisterGaribaldi said:**
> Maybe they can fix all the spelling mistakes while they're in there. Color instead of colour, and so forth. :P
That, sir, is British English.

---


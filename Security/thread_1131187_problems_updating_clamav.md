---
title: "problems updating clamav"
date: 2009-04-20
forum: Security
---

### Post by marticc on 2009-04-20
Hello,

yet again i am here asking for help. everytime I want to update my Clam AV, I run sudo freshclam, and I get this message:

ClamAV update process started at Mon Apr 20 21:37:56 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cld is up to date (version: 9261, sigs: 43961, f-level: 42, builder: neo)

I have tried to update my version but I have not been able to do it (I tried using apt-get and synaptic). Besides I have tried everything said on the Clam website,  but I failed to fix this problem. So the question is: How can i update to version 0.95.

Thanks for your help.

---

### Post by groovete on 2009-04-20
Hi!

Really good advice from the clamav -team: "Don't panic!" ;)

There is no newer version than 0.94.2 in the repository. So you can't update via synaptic. Never mind, the database is up to date. 
[http://www.howtoforge.de/forum/archive/index.php/t-1705.html]("http://www.howtoforge.de/forum/archive/index.php/t-1705.html")
(Sorry, I only detected a thread regarding this issue in a german board)
As an alternative you could install clamav from source I think:
[https://wiki.clamav.net/Main/InstallFromSource]("https://wiki.clamav.net/Main/InstallFromSource")

---

### Post by marticc on 2009-04-26
Hi, thanks for your answer. My German is even worse than my English, I am afraid. Maybe when I upgrade my ubuntu from 8.10 to 9.04 I will have my Clam updated. Otherwise I will try installing from the source.

---


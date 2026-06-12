---
title: "spamassassin - import bayes tokens ??"
date: 2009-08-30
forum: Server Platforms
---

### Post by cbear on 2009-08-30
I have a database of "learned" spam and ham in one of my user databases in /home/tom/.spamassassin/.bayes_toks.   I now run a system wide SA as root and I am building the knowledge dbase for root now - which can take a long time.  

Q:  Is there a way I can import the knowledge from "tom" to "root"?  

I looked at the command line options for sa-learn and could not find anything.  Basically, I want roots spam/ham dbase to benefit from the accumulated knowledge that "tom" already has.

thanks in advance !

---

### Post by venol on 2011-04-26
maybe someone can help us?

---

### Post by nsnidanko on 2011-04-27
You can do sa-learn --backup > /tmp/tom_bayes.db and than import it to root using the following command sa-learn --restore /tmp/tom_bayes.db I am not sure if you can combine both databases, try asking on SA mailing list.
 
Regards,
Naz

---


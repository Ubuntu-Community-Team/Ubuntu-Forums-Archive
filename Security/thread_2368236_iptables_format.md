---
title: "iptables format"
date: 2017-08-08
forum: Security
---

### Post by mwoosley on 2017-08-08
Hello everyone.  I'm tackling my system one block at a time and I'm now working on trying to setup my iptables solution to secure my system.

I have browsed many sites and have picked up on a lot of material.  My problem is exactly how to proceed with adding the rules.  For example, on one site, (I cannot find it again :()  I saw that one particular rule needed to be at the end of the table.  I think it was something about 'drop'ing packets and it needed to be at the end, because if it were in the middle of all the different rules, we would be defeating the purpose of the 'other' rules (or whatever ;))  So, with that being said, are there some general rules to follow when formatting our iptables?  Certainly what I mentioned previously about having certain rules come before others makes good sense to me, but I don't know where to put them (the rules).  

Any help and/or documentation would be great. 

Thank you in advance.

Best,
Mike

---

### Post by Doug S on 2017-08-08
iptables does involve a considerable learning curve. Myself, I think it is well worth the effort.

I do not know which resources you have already found, but I have always found [this]("bodhizazen.com/Tutorials/iptables") one to be good. (although it seems to be down at the moment. I was just there on July 20th.)

I'll pm you with a link to my iptables rule set (as a text file) on my web site.

---


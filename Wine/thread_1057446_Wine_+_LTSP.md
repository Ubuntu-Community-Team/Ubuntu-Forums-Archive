---
title: "Wine + LTSP"
date: 2009-02-01
forum: Wine
---

### Post by djsephiroth on 2009-02-01
**The current situation:**
I am the IT Director for a local private school system. We have two campuses: one for elementary students, and another for middle and high school students. The school is relatively new and does not have a ton of resources that we could really use (like a computer lab at the latter campus), though we do have a great network infrastructure and are farther ahead technologically than other local schools in a lot of areas (e.g., all of our phones are Cisco IP phones, we have campus-wide wireless). All of our teachers use a program called Renweb to do everything from attendance to lunch to grades, etc. It saves a ton of money and effort, and they have become accustomed to it even faster than I'd imagined. 

Our computer lab at the high/mid campus consists of a cabinet of Dell P4/512MB/80GB laptops that students can check out like books when needed. However, this is very subpar, and we know it. Administration wants to see a proper 20-desk computer lab next year. I want to do something even better...

**My goal: **   
I want to build a lab using thin clients. I've already got a test setup using one client, one server, and a cheap Dell switch. The server runs Ubuntu 8.10 desktop i386. After some digging and tweaking, I've got it all working properly. I'm going to demo what I've got to my superiors this week and show them how blazingly fast everything runs on the PII-based fat-client-cum-thin-client, plus all of the cool free apps we can use.

Problem 1: administration is adamant that we teach our students how to use Word, as well as any other MS Office apps they may need for the real world. OpenOffice is on the student and teacher machines throughout our organization, and no one likes it (mostly because it isn't Office). We have to be able to run Word, if not the whole Office Pro suite, on these machines.

Problem 2: some of the younger students use a web-based skill assessment app that has to use Quicktime, Flash, Shockwave, and Adobe Reader. The only one that appears to be an issue is Shockwave (no Linux version of which I know).

**Possible Solution:**
Wine! Never used it before, but it seems promising. Renweb is Platinum status, and most of the Office suite is Silver or better. 

**So, the question is:** how do I get Wine set up in my thin client lab so that Shockwave, Word, etc. will work? What issues should I expect? Has anyone even done anything like this before?

Thanks,

- Sephi

---


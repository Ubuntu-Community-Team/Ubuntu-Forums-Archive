---
title: "Virtual Server vs Dedicated Server?"
date: 2007-10-26
forum: The Cafe
---

### Post by RAV TUX on 2007-10-26
Virtual Server vs Dedicated Server?

I just talked to my host provider that says [CafeLinux.org]("http://cafelinux.org/home/") is grown beyond the shared server hosting capacity.

He is going to get back to me with quote for a Virtual Host. I guess it is a server host in VMware environment. I am not too up on all the logistics yet.

My thought is to simply buy a server and pay the monthly fees for a dedicated server.

Perhaps start a hosting business. 

I am not sure which step to take, what is everyones experience in this...

Any ideas?

---

### Post by awalsh on 2007-10-26
I've been in both situations, Ive had a dedicated and a vps then combined it into one more powerful dedicated. Personally I find VPS good if you want a lot of control over your machine but you are not putting a lot of strain on it. Dedicated is good for if your putting a lot of strain on the machine or you want a custom kernel or something like that. An extremely handy feature of VPS is that you can often reinstall it with great ease and usually without having to contact a support agent (which could cost you money).

From my experience VPS sometimes are better supported, eg with a VPS you are likely to get managed support. Where as with dedicated you are probably out on your own. Personally I would say get a decent VPS, it will likely be sufficient because shared machines do not usually give you a lot of "horsepower" in my opinion. But then again it all depends on your provider....

---

### Post by racoq on 2007-10-26
My experience is that, systems hosted though virtual machines are poor in their performance. A guy that i know that worked for sybase, was asked one time to host a web page via apache using vmware. The performance was so poor because that particular site had heavy loading that they had to give up the idea.

My advise is.. DON'T trust on reliability on those kind of systems, virtual machines were not natively conceived for that..

---

### Post by awalsh on 2007-10-26
Ive never used vmware, always been on Virtuozzo (or however you spell it). What kind of loads are you getting at the moment?

---

### Post by RAV TUX on 2007-10-26
> **awalsh said:**
> Ive never used vmware, always been on Virtuozzo (or however you spell it). What kind of loads are you getting at the moment?
I honestly don't know....a friend of mine host the website for me on a shared server and my Website uses the most bandwidth of all the other websites.

How do I check?

---

### Post by awalsh on 2007-10-26
Well bandwidth may or may not be the issue. It could be just server load which could be caused by a script taking up lots of memory (mailing list sending out emails to thousands of people for example), an unoptimised forum is another good one. You can usually check your bandwidth usage in a control panel, usually this is Cpanel for most shared hosts.

I personally would want to know in what way I was exceeding capacity, bandwidth should not really be much of an issue (should just be a case of buying more), I would bet that your using too much memory/cpu. Which in itself could be fixed by optimising any scripts, databases etc

Does the host not have like a "semi-dedicated" package? (thats what my host calls it), where they have fewer people on a machine but give you more resources because it costs more than a shared. Basically being the same as shared but with fewer users on it.

---

### Post by RAV TUX on 2007-10-26
> **awalsh said:**
> Well bandwidth may or may not be the issue. It could be just server load which could be caused by a script taking up lots of memory (mailing list sending out emails to thousands of people for example), an unoptimised forum is another good one. You can usually check your bandwidth usage in a control panel, usually this is Cpanel for most shared hosts.

I personally would want to know in what way I was exceeding capacity, bandwidth should not really be much of an issue (should just be a case of buying more), I would bet that your using too much memory/cpu. Which in itself could be fixed by optimising any scripts, databases etc

Does the host not have like a "semi-dedicated" package? (thats what my host calls it), where they have fewer people on a machine but give you more resources because it costs more than a shared. Basically being the same as shared but with fewer users on it.

I have unlimited bandwidth with my host.

so I guess that isn't the issue?

I have to find out more information.

---


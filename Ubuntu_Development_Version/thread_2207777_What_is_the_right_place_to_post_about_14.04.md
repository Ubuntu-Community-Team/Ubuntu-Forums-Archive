---
title: "What is the right place to post about 14.04 ?"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by ubucatz on 2014-02-25
Hi, 

where to post about 14.04 observations? I have found a couple of problems and annoyances using 14.04 alpha and since these are not changing for some weeks now I feel like I should draw some attention to them to the people in charge. The bugtracker does not allow me to report a problem, I am redirected to a very long page with instructions which do not work for me - I would prefer to just post my bug report to a form to support the 14.04 release to be a real good one. There are just a few things that are killing this upcoming release and I would like to be sure that I did at least write to some place about them before the actual release date. 
Thanks,
Ubucatz

---

### Post by Elfy on 2014-02-25
*Thread moved to **Ubuntu +1**.*

> The bugtracker does not allow me to report a problem, I am redirected to a very long page with instructions which do not work for meNot sure what you mean here.

The best way to report a bug is using apport

```
ubuntu-bug *packagename*
```

That way the report includes all the information it needs.

---

### Post by ubucatz on 2014-02-25
I do not want to use this method on my computer, as there is produced a very large file and I can not dedicate time to check if there is any private data that I do not want to appear in a public bug report. 

Also there is no information regarding private data on any obvious place and I am not informed about what kind of private data is send while I am using this tool, so I choose not to use it. 

ubuntu-bug should be much more transparent about what kind of data is send, also it should be more easy to decide what kind of data one would like to send. 

BTW, this annoyance is part of my observations, bug-reporting should be much better controllable by users. 

Thanks for your attention,
Ubucatz

---

### Post by 23dornot23d on 2014-02-25
Your post now seems to be in the correct place to report the bugs ..........

What are they ........ ?

Someone can at least check to see if they have previously been reported - if you post to say what they are.

---

### Post by grahammechanical on 2014-02-25
I do not agree with you about privacy. I have used the development branch for years and when there is a crash in some part of the system and I am invited to send a bug report I am always reminded that some of the log files may contain private information and I am always given the option of cancelling the report. The system has never reported crashes and sent log files without my approval.

If you cannot tolerate annoyances then do not run the development branch. If you are worried about private details being part of the log files included in the bug report then do not report the bug. It is as simple as that.

You say you want to improve the 14.04 release. Yet, you do not want to spend the time. That is a contradictory position. You also reject the method that has been set up to give the most information about bugs in the most efficient way to the developers.

If you are really worried about bug reports , then join the bug squad and see for yourself how bug reports are handled and what information is passed over.

---

### Post by cariboo on 2014-02-25
The bug reporting utility is fairly smart, when  it is about to send any private data to the bug tracker, it will notify you before doing so, and what file it is located in.

---

### Post by kansasnoob on 2014-02-25
> **cariboo907 said:**
> The bug reporting utility is fairly smart, when  it is about to send any private data to the bug tracker, it will notify you before doing so, and what file it is located in.

+1!

It always gives the option of including private info or not :D

---

### Post by ubucatz on 2014-02-26
Hi, do not want to discuss meta, but you are interpreting me wrong and not reading my post precisely:

> **grahammechanical said:**
> I do not agree with you about privacy. I have used the development branch for years and when there is a crash in some part of the system and I am invited to send a bug report I am always reminded that some of the log files may contain private information and I am always given the option of cancelling the report. The system has never reported crashes and sent log files without my approval. 

I did not say anything contradicting this. However, I still can not find any obvious place that it telling me which kind of private information exactly is sent. "Private Information" is an extremely broad description and can be anything. 

I did never say that the bug reporting tool sends data without asking.

> **grahammechanical said:**
> 
If you cannot tolerate annoyances then do not run the development branch. If you are worried about private details being part of the log files included in the bug report then do not report the bug. It is as simple as that.


I did decide to not report that bug via the bug reporting tool - thank you very much for your suggestions, they helped me very much in the decision process. I did, however, report the bug via a simple form that allows me to post the relevant information. 

I did not wrote anything about my tolerance level for annoyances, please stay on topic and do not mis-interpret things into posts. 

> **grahammechanical said:**
> 
You say you want to improve the 14.04 release. Yet, you do not want to spend the time. That is a contradictory position. 


This is wrong, please do not mis-interpret my postings and stay precise!

I did say that I do not want to inspect the generated file for private data - rather I would like to spend time on testing. 

Please add more precision to your information parsing process, or please ask for more details if things are not clear, but do not interpret stuff into posts that just happens to be an mis-interpretation.

---

### Post by cariboo on 2014-02-26
Part of testing while running a development version, is tracking down and reporting bugs.This means going through the files that apport creates when creating a bug report.

That being said, Trusty development has been pretty boring, with no major problems, except those of our own making.

---


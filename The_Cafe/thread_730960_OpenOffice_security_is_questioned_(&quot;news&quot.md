---
title: "OpenOffice security is questioned (&quot;news&quot; now outdated)"
date: 2008-03-21
forum: The Cafe
---

### Post by The Fire Fly on 2008-03-21
Security experts have discovered vulnerabilities in OpenOffice.org that could allow attackers to remotely execute code on Linux, Windows or Apple Mac-based computers. 

OpenOffice version 2.0.4 and earlier versions are vulnerable to maliciously crafted TIFF files, which can be delivered in an e-mail attachment, published on a Web site or shared using peer-to-peer software. The next version of OpenOffice (version 2.3) arrived on September 17 and is not affected by the flaw. 

The vulnerability was discovered by researchers at iDefense, who claim that the OpenOffice TIFF parsing code is flawed. 

"When parsing the TIFF directory entries for certain tags, the parser uses untrusted values from the file to calculate the amount of memory to allocate. By providing specially crafted values, an integer overflow occurs in this calculation. This results in the allocation of a buffer of insufficient size, which in turn leads to a heap overflow," the iDefense team reported last Friday. 

TrustDefender co-founder Andreas Baumhof said: "This vulnerability allows someone to execute malicious code on your computer. It's an OpenOffice bug so it doesn't matter what type of operating system you run; it allows you to run malicious software with the same rights as the user who runs OpenOffice."

"At this stage, it's only confirmed on Linux," Baumhof said. "But typically it would affect all operating systems. The only difference with Linux and Windows is that home users typically run Windows as the administrator." 

In June, OpenOffice users were warned about a worm called "Badbunny" that was spreading in the wild through multiple operating systems, including Mac OS, Windows and Linux. 

At the time, Symantec posted an advisory that said: "A new worm is being distributed within malicious OpenOffice documents. The worm can infect Windows, Linux and Mac OS X systems. Be cautious when handling OpenOffice files from unknown sources".

---

### Post by bruce89 on 2008-03-21
> **The Fire Fly said:**
> OpenOffice version 2.0.4 and earlier versions are vulnerable to maliciously crafted TIFF files, which can be delivered in an e-mail attachment, published on a Web site or shared using peer-to-peer software. The next version of OpenOffice (version 2.3) arrived on September 17 and is not affected by the flaw. 

In other words, this is ancient history.

---

### Post by GeneralZod on 2008-03-21
> **bruce89 said:**
> In other words, this is ancient history.

Yep - this seems to be the article the OP is referencing:

[http://www.news.com/OpenOffice-bug-hits-multiple-operating-systems/2100-1002_3-6209919.html](http://www.news.com/OpenOffice-bug-hits-multiple-operating-systems/2100-1002_3-6209919.html)

OP: I don't want to sound like a jerk, but if you post a news article, could you please at least post a link so we can see the source article for ourselves? Also, since this dates from 27th September of last year, it doesn't really qualify as "news", *per se* ;).

---

### Post by The Fire Fly on 2008-03-21
A report on the security of OpenOffice has caused a stir in the open-source community by highlighting six security "issues" around the open-source office suite. 

OpenOffice has said only one actual bug was discovered, and that flaw has been fixed already. But the research, by the French Ministry of Defense, also points out that many security flaws have already been discovered in Microsoft Office applications, claiming that these are "easily transportable to OpenOffice." 

According to the report, titled "In-depth analysis of the viral threats with OpenOffice.org documents," this means that the "general security of OpenOffice is insufficient," Infoworld reported. 

The report goes on to counter claims from the open-source community that OpenOffice is inherently more secure than Microsoft's Office products. "The viral hazard attached to OpenOffice.org is at least as high as that for the Microsoft Office suite, and even higher when considering some... aspects," the researchers wrote.

"This suite is up to now still vulnerable to many potential malware attacks," they added. 

The paper was first submitted for publication in April and revised in June. It was accepted in July, when some of the details of the report began to leak out, and then published Aug. 1 in the Paris-based Journal of Computer Virology. 

The paper describes four examples of how malicious code can attack OpenOffice and release hazards. The weaknesses are focused around issues such as the use of Zip files, and in particular the use of macro programming procedures and templates.

---

### Post by bruce89 on 2008-03-21
I'm afraid copying and pasting old technology news is not only annoying, but infringes copyright.

---

### Post by michaelzap on 2008-03-21
> **bruce89 said:**
> I'm afraid copying and pasting old technology news is not only annoying, but infringes copyright.

What are you talking about?!?

---

### Post by bruce89 on 2008-03-21
> **michaelzap said:**
> What are you talking about?!?

Look at the OP's past threads. They are a lot of copy and pasted tech news articles.

---

### Post by twisted_steel on 2008-03-21
> **michaelzap said:**
> What are you talking about?!?

Does this article from 2006 look familar?
[http://www.news.com/OpenOffice-security-is-questioned/2100-1002_3-6105176.html](http://www.news.com/OpenOffice-security-is-questioned/2100-1002_3-6105176.html)

---

### Post by O3. on 2008-03-21
> **bruce89 said:**
> I'm afraid copying and pasting old technology news is not only annoying, but ***infringes copyright***.lol

---

### Post by michaelzap on 2008-03-21
> **bruce89 said:**
> Look at the OP's past threads. They are a lot of copy and pasted tech news articles.

I found another when I did a search, and it was pasted without a source. This one is paraphrased with quotes, however, so that's why your comment seemed out of the blue to me. Maybe I'm just sensitive to the appearance of allegations of "copyright infringement" being used to stifle debate.

---

### Post by O3. on 2008-03-21
> **twisted_steel said:**
> Does this article from 2006 look familar?
[http://www.news.com/OpenOffice-security-is-questioned/2100-1002_3-6105176.html](http://www.news.com/OpenOffice-security-is-questioned/2100-1002_3-6105176.html)
yea, its the same one.

---

### Post by twisted_steel on 2008-03-21
> **O3. said:**
> yea, its the same one.

Ouch, missed a spot :)

```
~/Desktop$ diff TheFireFly news.com
13a14,15
> 
> Last Tuesday, Microsoft announced it had fixed a number of bugs including one in PowerPoint.
```

---

### Post by aysiu on 2008-03-21
I'm closing this thread. The issue is old. Unless someone can post a recent news item or credible source indicating the vulnerabilities still exist.

In the meantime, [OpenOffice's website](http://www.openoffice.org/security/cves/CVE-2007-2834.html) has this to say: >  Manipulated TIFF files can lead to heap overflows and arbitrary code execution

    * Synopsis: Manipulated TIFF files can lead to heap overflows and arbitrary code execution
    * State: Resolved

1. Impact

A security vulnerability with the way OpenOffice.org processes TIFF documents may allow arbitrary command execution on the system with the privileges of the user running OpenOffice.org.

We acknowledge, with thanks, an anonymous researcher working with the iDefense VCP.
2. Affected releases

All versions prior to OpenOffice.org 2.3
3. Symptoms

There are no predictable symptoms that would indicate this issue has occurred
4. Relief/Workaround

There is no workaround. See "Resolution" below.
5. Resolution

This issue is addressed in the following releases:

OpenOffice.org 2.3 

---


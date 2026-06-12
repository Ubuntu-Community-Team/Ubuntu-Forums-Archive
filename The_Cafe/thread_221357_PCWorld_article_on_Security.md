---
title: "PCWorld article on Security"
date: 2006-07-23
forum: The Cafe
---

### Post by kagashe on 2006-07-23
Hi,

I am very much concerned after reading [this article]("http://msn.pcworld.com/reviews/article/0,aid,126083,pg,1,00.asp") on PCWorld.com
[The 10 Biggest Security Risks You Don't Know About]("http://msn.pcworld.com/reviews/article/0,aid,126083,pg,1,00.asp")

The [last page]("http://msn.pcworld.com/reviews/article/0,aid,126083,pg,11,00.asp") of the article says:
[URL="http://msn.pcworld.com/reviews/article/0,aid,126083,pg,11,00.asp"]No Safe Haven: Threats Plague All Platforms
[/URL]

Quoting from the page:
> Linux has a case of worms, too; the number of malicious programs targeting that OS doubled between 2004 and 2005. Rootkits, the looming threat for Windows PCs, actually trace back to attacks meant to take surreptitious control of the administrative "root" user on Unix OSes. Also, while being able to run your own personal Web server is part of the open-source draw, doing so can allow crooks to hijack your site or take control of your PC.

The latest twist is cross-platform malware: single programs that can assault two or more types of systems.

A proof-of-concept virus that attacks both Windows and Linux appeared in April. The virus, created by antivirus firm Kaspersky, contains no payload and does no damage. Known variously as Virus.Linux.Bi.a and also Virus.Win32.Bi.a, it infects just a single type of Linux file format (ELF) and a single type of Windows file format (PE). And it's based on old Linux elements that aren't part of newer systems. Still, **it was enough of a wake-up call to prompt Linux creator Linus Torvalds to write a fix.**

kagashe

---

### Post by Iandefor on 2006-07-23
> 
I am very much concerned after reading [this article]("http://msn.pcworld.com/reviews/article/0,aid,126083,pg,1,00.asp") on PCWorld.com Why? It says that Linus got a fix out. No system is absolutely secure, nor even all that secure.

---

### Post by slimdog360 on 2006-07-23
It was a good read, nice find.

---

### Post by grte on 2006-07-23
Yes, the bolded portion is the most important part of that excerpt, but not because of the line PCWorld is trying to push.

As has been said, no system is totally secure.  What matters is that fixes are released for discovered exploits, which was done.

---

### Post by fluffington on 2006-07-23
I was under the impression that Linux systems were immune to  Virus.Linux.Bi.a because of a flaw in GCC, and that it was the patch referred to in the article that allowed the virus to run.

(here's [the NewsForge story](http://software.newsforge.com/article.pl?sid=06/04/18/1941251))

---

### Post by FredB on 2006-07-23
By the way, unix are less sensitive to viruses than Windows. And before they are linux only viruses as bad as we can see on Windows, Vista will be dead :p

---

### Post by kagashe on 2006-07-23
> **Iandefor said:**
> Why? It says that Linus got a fix out. No system is absolutely secure, nor even all that secure.I am concerned for Windows & MAC users LOL

> the bolded portion is the most important part of that excerpt

I did it here. It is not "bold" on the PCWorld article.

By the way I have made a PDF document (courtsy CupsPDF How-to on this forum) of the article and putting it up for download on [rapidshare.de]("http://rapidshare.de/files/26701364/PCWorld_com_-_The_10_Biggest_Security_Risks_You_Don_t_Know_About.pdf.html")

kagashe

---

### Post by Iandefor on 2006-07-23
> **kagashe said:**
> I am concerned for Windows & MAC users LOL lol! Well, that's another thing!

---

### Post by G Morgan on 2006-07-23
Old news this. As was correctly pointed out the virus didn't work on Linux kernels at the time because of a flaw in their design. Linus actually patched the kernel so the virus would work because he was confident the problem would be dealt with elsewhere and he was right for the greater part.

The virus itself is wrote in assembler so its questionable whether it will be able to do anything of relevance. It would take a stack of work to make a useful exploit in assembler and even then it would only be able to exploit specific processes which may or maynot be present on one machine to the next.

Then theres the very fact that 99% of Linux software comes via the repositories so isn't going to have a virus in it.

Really then a big fuss over nothing, an interesting thing but not really something to panic over yet.

---

### Post by Carrots171 on 2006-07-23
No OS is immune to viruses. Some operating systems have a stronger "immune system" than others, though.

---


---
title: "does clamav suck?"
date: 2008-06-19
forum: Security
---

### Post by waggingwabbit on 2008-06-19
i just scanned a few tutorial vids and pdf files i downloaded overnight. and on 3 of 8 of the things i downloaded clam says its a virus and the reason is "files number limit exceeded". i looked that up on google and changed the conf file to not limit files or whatever and it still does that, even when i scan just 1 of the pdf files. 

it also lists the names of the files scanned wrong. not all 8 of the files in the clam window are the names of the files i have. one of them is repeated 3 times, 2 of them counted as viruses and 1 of them is clean.

so then i tried checking the log that was saved. and it listed the infected files like this: "/home/stink/Desktop/untitled fold..." very helpful and informative....

should i just ignore everything clam says?

---

### Post by hyper_ch on 2008-06-19
I don't use AV....

---

### Post by waggingwabbit on 2008-06-19
> **hyper_ch said:**
> I don't use AV....

yes i know, i was just in the other thread where you said you encrypt your stuff =]

someone else answer me?

---

### Post by attari on 2008-06-19
> **waggingwabbit said:**
> i just scanned a few tutorial vids and pdf files i downloaded overnight. and on 3 of 8 of the things i downloaded clam says its a virus and the reason is "files number limit exceeded". i looked that up on google and changed the conf file to not limit files or whatever and it still does that, even when i scan just 1 of the pdf files. 

it also lists the names of the files scanned wrong. not all 8 of the files in the clam window are the names of the files i have. one of them is repeated 3 times, 2 of them counted as viruses and 1 of them is clean.

so then i tried checking the log that was saved. and it listed the infected files like this: "/home/stink/Desktop/untitled fold..." very helpful and informative....

should i just ignore everything clam says?


Yes and no. Yes because you really dont need AV in Ubuntu, so forget what ever its saying.

No, because you might be security paranoid like me! Moreover its better to scan as you may be sharing stuff with Windoze users.

However get Avast Antivirus. You can even configure it to scan single files from right click context menu. Get it (and other useful apps) from here:

[http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications]("http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications")

---

### Post by waggingwabbit on 2008-06-19
have yet to fully check out that sight, but from first glance it looks really useful. thanks! i do share with windows users. =]

---

### Post by Chayak on 2008-06-20
ClamAV ranks pretty low on the ranks of detection engines.  It's open source which is good but the flaw in that is they don't have a paid team constantly updating the definitions so you don't see newer malware being recognized.

[www.virustotal.com]("www.virustotal.com")
it has a multiscan engine that goes through a lot of commercial AV engines and gives you a report.

---

### Post by lisati on 2008-06-20
AV on Ubuntu is mainly a courtesy thing that only really matters when you're likely to be interacting with Windows users - some ISPs and email providers (including Yahoo) have a "Thou shalt not pass on malware"-type clause in their terms of service.

 My personal favourite is AVG, which comes in both Linux-friendly and Windows versions.

---

### Post by AmonSacha on 2008-06-21
I wouldn't say it sucks *nessesarily*. Every has covered the main reasons for using AV in ubuntu/*nix: for sharing with windows folks.

I would also through in a second vote for AVG if you need to use it:
[http://free.grisoft.com/ww.4040](http://free.grisoft.com/ww.4040) 

That url is the official site and should be easy to get up in running.

---

### Post by Oldsoldier2003 on 2008-06-21
> **AmonSacha said:**
> I wouldn't say it sucks *nessesarily*. Every has covered the main reasons for using AV in ubuntu/*nix: for sharing with windows folks.

I would also through in a second vote for AVG if you need to use it:
[http://free.grisoft.com/ww.4040](http://free.grisoft.com/ww.4040) 

That url is the official site and should be easy to get up in running.

I tend to agree when you recommend AVG over ClamAV. Every time I have tried ClamAV in the past it has been a disappointing and annoying experience. Luckily AV is not an overwhelming concern for my uses, but in some cases AV is a must and Clam falls short of optimal...

---


---
title: "&quot;Invisible&quot; Rootkit in the Wild"
date: 2006-07-18
forum: The Cafe
---

### Post by ubuntu27 on 2006-07-18
[http://www.theinquirer.net/default.aspx?article=33065](http://www.theinquirer.net/default.aspx?article=33065)

"SECURITY EXPERTS" have found a really nasty rootkit which is next to near impossible to detect and remove.

Dubbed Backdoor.Rustock.A by Symantec and Mailbot.AZ by F-Secure, the code cannot be spotted by most current rootkit detectors.

Symantec claims that it is the first of the next generation of rootkits.

It uses a mixture of old techniques and new ideas to make it "totally invisible on a compromised computer when installed". Apparently it even worked well on a beta version of Windows Vista the Symantec crowd were playing with.

The rootkit probably came from the coding hot houses of Russia and a variant called Backdoor.Rustock.B has also been spotted.

F-Secure claims that its BlackLight rootkit scanner, Build 2.2.1041, can detect the new rootkit.

However it said that it was darn hard to come up with effective detection code because the new rootkit does not have a process.

The rootkit runs inside the driver and in kernel threads and controls kernel functions via special IRP functions.

It even scans for loaded rootkit scanners, then changes its tactics to avoid detection. [More here]("http://www.cio.com/blog_view.html?CID=23011").


[http://www.theinquirer.net/default.aspx?article=33065](http://www.theinquirer.net/default.aspx?article=33065)

---

### Post by Kilz on 2006-07-18
What are the odds of a Ubuntu user becoming infected?

---

### Post by aysiu on 2006-07-18
> **Kilz said:**
> What are the odds of a Ubuntu user becoming infected?
This Wikipedia entry seems to indicate it's a problem for all operating system types:
[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

---

### Post by jpkotta on 2006-07-18
> **aysiu said:**
> This Wikipedia entry seems to indicate it's a problem for all operating system types:
[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

All OSes are vulnerable to rootkits in general, but only Windows is vulnerable to this one.

---

### Post by prizrak on 2006-07-18
> **jpkotta said:**
> All OSes are vulnerable to rootkits in general, but only Windows is vulnerable to this one.

That's why there is SELinux and the like they make it damn hard for a rootkit to get installed :)

---


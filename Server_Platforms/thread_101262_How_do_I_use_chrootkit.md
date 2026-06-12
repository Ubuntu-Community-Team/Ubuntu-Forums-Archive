---
title: "How do I use chrootkit?"
date: 2005-12-09
forum: Server Platforms
---

### Post by linbetwin on 2005-12-09
I installed chrootkit from the repositories because I want to scan my Windows partition for rootkits.

But issuing "chrootkit" in the terminal returns "command not found".

How can I run this program? Does it do a good job at checking for rootkits on a Windows partition? Other suggestions?

Thanks in advance!

---

### Post by anono on 2005-12-09
> 
But issuing "chrootkit" in the terminal returns "command not found".
maybe you installed ch**k**rootkit and you're giving the wrong command?

---

### Post by Spudgun on 2005-12-10
I believe chkrootkit only scans Linux partitions for Linux rootkits.

---

### Post by towsonu2003 on 2005-12-10
if you're dual booting, u can run this under windows for windows rootkit s... [http://www.sysinternals.com/Utilities/RootkitRevealer.html](http://www.sysinternals.com/Utilities/RootkitRevealer.html)

---

### Post by linbetwin on 2005-12-10
>  maybe you installed ch**k**rootkit and you're giving the wrong command?
Yes it was chkrootkit. Thanks, anono.

> I believe chkrootkit only scans Linux partitions for Linux rootkits.
Yeah, and I only needed it for Windows.

---

### Post by linbetwin on 2005-12-10
[quote=towsonu2003]if you're dual booting, u can run this under windows for windows rootkit s... [http://www.sysinternals.com/Utilities/RootkitRevealer.html]("http://www.sysinternals.com/Utilities/RootkitRevealer.html")[/quote]

Thanks. I used Black Light and didn't find anything.

---

### Post by phillipchandler on 2007-11-06
I also installed chrootkit. The command you need to run this, is "sudo chkrootkit" in terminal to run scan.

---

### Post by phillipchandler on 2007-11-06
Another one you may want to install is rkhunter. Then issue the following command "sudo rkhunter -c" in terminal to run scan.

---

### Post by steve.horsley on 2007-11-07
I don't know how you found this thread, but it ended 23 months ago.

---


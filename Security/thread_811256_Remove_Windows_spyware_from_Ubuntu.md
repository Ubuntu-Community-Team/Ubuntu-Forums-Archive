---
title: "Remove Windows spyware from Ubuntu"
date: 2008-05-29
forum: Security
---

### Post by Eliseo on 2008-05-29
Hi, I got some nasty spyware in my Windows partition and it's the kind of stuff that just won't go away even with Spybot and that kind of programs, somehow the spyware won't allow the system to delete the offending DLLs.

So it occurred to me that might be some antispyware program for Linux that can analyze a Windows partition and delete the files easily.

Is there such a program? :confused:

---

### Post by fbnaia on 2008-05-29
Hi Eliseo, i am not really familiar with any antispyware for linux that would remove from a windows partition, what you could try there would be start windows in safe mode and try scanning with your windows antispyware tools in safe mode.

I do tech support for a living (sort of living :)), and what i usually do is mount the windows partition in ubuntu and scan it with avira antivir, linux version [**here**]("http://www.free-av.com/en/download/download_servers.php") AND after that you could try scanning again from within safe mode with your regular tools AND scan from within a normal windows boot also just in case.

But sometimes you just have to remove the malware / virus by hand, if you know wich files are the ones that spybot just cant remove. Also try [**sysinternals suite**]("http://technet.microsoft.com/en-us/sysinternals/0e18b180-9b7a-4c49-8120-c47c5a693683.aspx") from within windows to help with this tasks...

good luck...

---

### Post by hyper_ch on 2008-05-29
can't you generate a list of the offending files? If so, you can then mount the windows partition with ntfs-3g as read/write and just run through the list and remove those files.

---

### Post by Seisen on 2008-05-29
> **Eliseo said:**
> Hi, I got some nasty spyware in my Windows partition and it's the kind of stuff that just won't go away even with Spybot and that kind of programs, somehow the spyware won't allow the system to delete the offending DLLs.

So it occurred to me that might be some antispyware program for Linux that can analyze a Windows partition and delete the files easily.

Is there such a program? :confused:

Try using spybot or whatever program it is in safe-mode that should take care of everything.

---

### Post by Zafrusteria on 2008-05-29
not tried it but this may work for you. Boot into Ubuntu and using Wine install a copy of your Windwos antispyware. then run in on the  mounted Windows partition. 
You never know :-)

---

### Post by razta on 2008-05-31
Search google for "UBCD", great tool for removing viruses/malware with out booting from HDD.

---


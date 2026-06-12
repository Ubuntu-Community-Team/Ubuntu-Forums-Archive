---
title: "Virus in java detected by avast in my home dir"
date: 2006-03-14
forum: Server Platforms
---

### Post by JoWilly on 2006-03-14
Hi,

I have installed the free Avast for linux (converted the rpm to deb with alien, works perfectly):
[http://avast.com/eng/avast-for-linux-workstation.html]("http://avast.com/eng/avast-for-linux-workstation.html")

and after updating the virus database I have started a scan on my home dir.

Avast has reported 3 infected files with the VBS:Malware, in java classes in my .java dir.

I have sun jre 1.5 installed and the only java app I am using is azureus.

This is a little scary, especially as my ".java" dir got infected without me doing anything...

---

### Post by kaamos on 2006-03-15
1) false positives?

2) assuming there really is a virus, if VBS stands for visual basic script it won't be doing anything in a linux enviroment. ;)

---

### Post by JoWilly on 2006-03-15
[QUOTE=kaamos]1) false positives?

2) assuming there really is a virus, if VBS stands for visual basic script it won't be doing anything in a linux enviroment. ;)[/QUOTE]

Are you so sure ? Also, there are many versions of the VBS virus, many are reported to reside and infect EXE and COM files. If it is visual basic script, as you say, does it reside in exe and com files ? Does a script reside in exe files ? I'm not so sure this is a visual basic script, I hope you can prove me otherwise.

The question is how has this infected my java classes ? Will this touch java "script" ?

Furthermore, if this is a windows virus (?), in this same home dir I have ".wine", ".cxoffice" and ".transgamming" directories. Can this virus propagate to these directories ? Crossover office is used to start MS office (especially MS project which has no equivalent in Linux, but also word etc...), can my files be harmed ?

---

### Post by 146lily on 2006-03-18
I have had virus like attacks on frostwire, derived from limewire. Types of problem are the program switching off by itself and the gui not forming correctly. I think java is a weak spot, novell has just issued a java security update for suse 10????

Nice find, Avast is a good windows antivirus program, 'they' will attack using easy established window methods if they can, including attacking wine.

---

### Post by Vadi on 2007-11-19
I don't think the virus will be able to do much...

Read this article ([click]("http://www.linux.com/articles/42031")) on why I think why :/

---

### Post by ukripper on 2007-11-19
JVM runs in its own environment affecting linux kernel won't apply in this case using java virus.

---


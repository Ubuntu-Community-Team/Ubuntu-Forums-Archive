---
title: "Info: VMWare Workstation 6.5/Ubuntu 9.04"
date: 2009-04-28
forum: Virtualisation
---

### Post by Faolan on 2009-04-28
If you get a lot of modinfo errors like this:

modinfo: could not find module vmmon
modinfo: could not find module vmnet
etc

When trying to start VMware Workstation on Ubuntu 9.04 then move (or delete) all the precompiled binaries from this directory to another location:

/usr/lib/vmware/modules/binary

Once you've moved the files fire up VMware once more and it should start compiling the libraries for you.

I was forced to do this with Ubuntu 9.04 today and is now running fine.

Hope this helps someone!

---

### Post by rundlc on 2009-04-29
Huge help!  Thanks!

---

### Post by NDLunchbox on 2009-04-29
I upgraded from 8.10 to 9.04 and Workstation stopped working.  Someone else had a thread about manually recompiling all the modules... scared me.  I did what you suggested... still need to do some more testing (including networking and other functionality), but everything seems A-OK so far!  Thanks!

---

### Post by Faolan on 2009-04-30
> **NDLunchbox said:**
>  Someone else had a thread about manually recompiling all the modules... scared me.

I prefer to go the easy route instead of faffing around compiling if possible, it was a old trick I found a wee while back.

Glad it's helped people.

---

### Post by Skrekkur on 2009-05-07
Works like a charm. Compiling the modules took under 2 minutes. 

Thank you!

---

### Post by bweis on 2009-05-10
> **Faolan said:**
> If you get a lot of modinfo errors like this:

modinfo: could not find module vmmon
modinfo: could not find module vmnet
etc

When trying to start VMware Workstation on Ubuntu 9.04 then move (or delete) all the precompiled binaries from this directory to another location:

/usr/lib/vmware/modules/binary

Once you've moved the files fire up VMware once more and it should start compiling the libraries for you.

I was forced to do this with Ubuntu 9.04 today and is now running fine.

Hope this helps someone!

Thanks for this but will need step by step instructions.  Assume you are dealing with sokmeone who learnt to read this morning

bw

---

### Post by brendan.lefoll on 2009-05-13
Under workstation 6.5.2 build-156735 64bit this is not needed. The install worked perfectly.

---

### Post by mostafa.bazzaz on 2009-05-15
Worked for VMware Workstation 6.5.1 build-126130.
thanks :D

---

### Post by wwynn on 2009-05-16
Please delete.

---

### Post by ROY.G.BIV on 2009-08-12
```
$ gksudo bash ./VMware-Workstation-6.5.2-156735.i386.bundle
```

**./VMware-Workstation-6.5.2-156735.i386.bundle: line 1: syntax error near unexpected token `<'./VMware-Workstation-6.5.2-156735.i386.bundle: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'**

```
$ sudo sh VMware-Workstation-6.5.2-156735.i386.bundle
```
[B]
VMware-Workstation-6.5.2-156735.i386.bundle: 1: Syntax error: redirection unexpected[/B]


:confused::confused:

---


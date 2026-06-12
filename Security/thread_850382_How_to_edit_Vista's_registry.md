---
title: "How to edit Vista's registry?"
date: 2008-07-05
forum: Security
---

### Post by azzamite on 2008-07-05
Hi there, I dual boot with vista and just got a virus calles eksplorasi or something like that and I need to edit Vista's registry to prevent it from trying to start... I already deleted it but vista won't start until the thig is deleted from the registry...

Is there a program that allow me to open the registry and edit it?


PD: clamav didn't fix the problem.

---

### Post by hyper_ch on 2008-07-05
I'd ask in a VISTA forum

---

### Post by azzamite on 2008-07-05
Never mind, I just noticed that avscan only did half of the job, it detected the virus but didn't "move it" as I told it to :mad:, so I deleted it manually.

Anyway, I know ubuntu is got apps for almos anything; doesn't it has an app to hack or edit win's registry?

> **hyper_ch said:**
> I'd ask in a VISTA forum

I asked here because vista didn't want to start and I was cleaning from ubuntu, otherwise I whould have asked in a vista forum. :)

---

### Post by hyper_ch on 2008-07-05
you ask in a Linux Forum on how to edit the Windows registry? hmmm...

---

### Post by arsenic23 on 2008-07-05
> **hyper_ch said:**
> you ask in a Linux Forum on how to edit the Windows registry? hmmm...

He's asking if there is a way to edit Vista's regestry from linux.
You may... may, and do this at your own risk kind of may, be able to load the registry into wine's regedit.  You'll find it as %%windows/system32/config

Just a guess though.  May break your windows install and/or wine.

---

### Post by spike_strip on 2008-07-05
> **arsenic23 said:**
> He's asking if there is a way to edit Vista's regestry from linux.
Well this sure was not clear, in the original post. I felt the same way as hyper_ch ... it appeared quite obvious he was asking a VISTA question.

---

### Post by hyper_ch on 2008-07-05
how do you edit the VISTA registry from windows CLI? It's a windows question, not a linux one...

---

### Post by arsenic23 on 2008-07-05
[COLOR="DarkRed"]"""[/COLOR]
[INDENT][COLOR="Gray"]Hi there, [COLOR="Black"]**I dual boot**[/COLOR] with vista and just got a virus calles eksplorasi or something like that and I need to edit Vista's registry to prevent it from trying to start... I already deleted it but [COLOR="#000000"]**vista won't start**[/COLOR] until the thig is deleted from the registry...

Is there a program that allow me to open the registry and edit it?


PD: [COLOR="#000000"]**clamav**[/COLOR] didn't fix the problem.[/COLOR][/INDENT]
[COLOR="#8b0000"]"""[/COLOR]

I thought it was fairly obvious that he was asking how to edit the windows registry while booted in his linux OS.  This is as much a question for this forum as any other.


edit:
----------
Oh, by the way, you open wine's regedit with the following (asuming you have wine installed):
```
wine regedit
```

---

### Post by RATM_Owns on 2008-07-05
Well, if you do find some way, go to this key in the registry:
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
and delete it.

---

### Post by mayer213 on 2009-03-18
Dude you are just giving a more damage in your system by getting in the registry. Just do the simple way by using anti virus. I have site here that give a very good information about Viruses and what is the good way to prevent them or remove them from you're system. The site is [http://www.systemsecurityinstitute.org](http://www.systemsecurityinstitute.org) sign up for their free weekly newsletter for any updates of the latest system threats or viruses. They also include review about latest gadgets as well.

---

### Post by WatchingThePain on 2009-03-18
Hmm..when I looked at registry in wine alot of it seems to be missing.
Also adding keys doesn't really work.
Manually removing viruses from registry is pointless.
You delete one bit and another is created.

---

### Post by bodhi.zazen on 2009-03-18
I am going to close this thread as it seems to be getting off topic.

In general you should edit the windows registry form windows and if you haev malware, search the web for the removal process.

If needed, boot a windows rescue disk, such as BART [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Although I have not done this mind you.

Linux should be used as a last resort and is likely to cause problems.

---


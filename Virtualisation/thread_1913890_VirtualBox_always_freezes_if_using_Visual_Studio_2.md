---
title: "VirtualBox always freezes if using Visual Studio 2010 Designer (adding control)"
date: 2012-01-23
forum: Virtualisation
---

### Post by EyesKiller on 2012-01-23
Hi,
VirtualBox is *always* freezes as soon as I want add a control into form by drag'n'drop. The mouse turns to circle (which means system is busy). But this circle is not circling and it doesn't matters where I move mouse. Guest is not reacting anymore and the only way is just turn off guest. :(

I'm using following versions:
- Host: Kubuntu 11.10 64-bit
- Guest: Windows 7 Professional SP1 64-bit
- Visual Studio Professional 2010
- VirtualBox 4.1.2 (Ubuntu Version)

> 00:03:12.820 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:13.821 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:14.824 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:15.820 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:16.820 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:17.820 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false
00:03:18.820 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_TRY_AGAIN)}, preserve=false

What should I do so it works? Or maybe an alternative way to add controls into form? Funny thing is:
Moving/modifying aroud already added controls is no problem. #-o

cu Floh

---

### Post by EyesKiller on 2012-01-23
Ok, I tried that: [https://forums.virtualbox.org/viewtopic.php?f=6&t=39193#p176328](https://forums.virtualbox.org/viewtopic.php?f=6&t=39193#p176328)

But still it freezes, but the error log, as posted above, disappeared. *sigh*

UPDATE:
I looked in log again, but there is no further log entry after freeze. Any idea how to increase log level?

cu Floh

---


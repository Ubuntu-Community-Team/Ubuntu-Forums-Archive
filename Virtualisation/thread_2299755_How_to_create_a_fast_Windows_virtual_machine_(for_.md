---
title: "How to create a fast Windows virtual machine (for Outlook emails and Evernote)"
date: 2015-10-21
forum: Virtualisation
---

### Post by sberla54 on 2015-10-21
Hello everybody,
I'm struggling to create a Windows virtual machine that is fast enough for daily work.

I need to keep that always running with just a couple of software, mostly Microsoft Outlook 2010 and Evernote.
So far, i've made some tests and a couple of reinstallations from scratch but everything is still laggy and slow. Adding a note from Outlook to Evernote could take 5 minutes, to make a search in Evernote causes it to freeze and Outlook takes a life to start and to download some hundreds of new emails.

I'm using Ubuntu Gnome 14.04.3 LTS (64 Bit) with Virtual Box 5.0, Windows 7 Professional (64 Bit), Microsoft Office 2010 on a Intel i5-3210M dual core 2.5 Ghz with 8 Gb of RAM and a 500 Gb IDE hard disk.

On VirtualBox, i've reserved to Windows 2 Gb of RAM, a virtual hard drive of 50 Gb (that is always mostly full), i've set that it can use 2 processors with 90% of execution cap (and PAE/NX), i've enabled hardware virtualization (VT-x/AMD-v and nested pagination).

Do you have any suggestions?
Should i try to use Windows 10 instead of Windows 7? I don't want to fall back to Windows XP.
Should i try one of those "lite" ISOs you can find on the net? I don't want trouble with drivers, devices and printers.
Or maybe there are some relevant changes i can make to Virtual Box settings? So far, they doesn't seem to have very much impact on performances.

Thank you in advance!

---

### Post by howefield on 2015-10-21
Can you put the VM on a separate disk to the host system ?

A "mostly full" Windows VM sounds like it needs more space and lastly have you tried running with 1 processor allocated to the guest ?

---

### Post by sberla54 on 2015-10-21
> [COLOR=#000000]Can you put the VM on a separate disk to the host system ?[/COLOR]

Sadly, i can't. It's a laptop with a single drive.
I've bought an SDD drive and i was planning to install it as my main hard disk but i thin i would reinstall Ubuntu and Windows on that same drive. It's seems better for performances, to me. Do you suggest to separate them?

> A "mostly full" Windows VM sounds like it needs more space
You're right.
I've always only 2 or 4 Gb of free space.
I was thinking about installing a new VM with 100 Gb reserved but wanted to hear your tips first, to be sure i'm making it right this time.

> have you tried running with 1 processor allocated to the guest ?

Yes, it doesn't change much.

---

### Post by Bucky Ball on 2015-10-21
> **sberla54 said:**
> 
I've always only 2 or 4 Gb of free space.


That might just explain it. Windows doesn't like that little headroom and needs about 10Gb to be at least reasonably happy in my experience. :)

---

### Post by sberla54 on 2015-10-21
> **Bucky Ball said:**
> That might just explain it. Windows doesn't like that little headroom and needs about 10Gb to be at least reasonably happy in my experience. :)

Because of is massive, horrible, paging file? :)
Thank you for the suggestion!

In your opinion, are there any Virtual Box settings in particular that could be useful? Or i just forget about them?

---

### Post by TheFu on 2015-10-21
> **sberla54 said:**
> In your opinion, are there any Virtual Box settings in particular that could be useful? Or i just forget about them?

[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)
Should be able to get 90% of native performance for non-GPU stuff. This assumes the hostOS isn't busy.

Did you install the Guest Additions?

I'd guess that giving more than 1 virtualCPU could be the issue. 2G of RAM seems like a bunch - I only give Windows 1.5G at most.  The goal is to share resources between all the running OSes, programs, threads, disk and network I/O.

Double check that the VM video RAM is 128MB and that 2D/3D accel is enabled.

---

### Post by sberla54 on 2015-10-22
> **TheFu said:**
> 
I'd guess that giving more than 1 virtualCPU could be the issue. 
Double check that the VM video RAM is 128MB and that 2D/3D accel is enabled.


Video memory was 50 Mb and 3D accel was disabled. I fixed them.
I also switched to 1 single CPU.

It's a couple of hours that i'm trying this new configuration and i have to say that it seems more reactive, even if it's still too laggy for a satisfying daily use.

Thank you!

> **TheFu said:**
> [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)


That link doesn't work, i receive "connection timed out". Is there any mirror? If not, i will read the Google Cache version.

> **TheFu said:**
> 
Did you install the Guest Additions?


Yes, of course!

> **TheFu said:**
> 
2G of RAM seems like a bunch - I only give Windows 1.5G at most. The goal is to share resources between all the running OSes, programs, threads, disk and network I/O.


Right now my VM with only Outlook and Evernote running, is using 1.3 Gb of RAM. That's why i assign 2 Gb to the VM.

One question: which version of Windows do you usually use, guys?
Has anyone tried Windows 10? Seems pretty fast on old hardware, according to reviews, maybe it's fast also on virtual hardware...

---

### Post by TheFu on 2015-10-22
Can't run win10 due to my privacy concerns. Never intend to run it.
Use win7 with all the win10-added-patches blocked.

Definitely look for the cached version - or the wayback machine should have a version. Pay attention to the disk setup.

---

### Post by sberla54 on 2015-10-23
> **TheFu said:**
> Can't run win10 due to my privacy concerns. Never intend to run it.


You're right, i didn't considered this before but it's relevant, mostly because it's the computer i use at work. It's better to stick to Windows 7...

> **TheFu said:**
> 
Definitely look for the cached version - or the wayback machine should have a version. Pay attention to the disk setup.


I'm sorry, i didn't understand this last sentence. What do you mean?

---

### Post by TheFu on 2015-10-23
Read the link however you need to do so - cached version or using the "wayback machine."  When you are reading it, pay attention to the disk setup information.

---

### Post by sberla54 on 2015-10-23
Ok, now i've understood. Thanks.

---

### Post by PhilGil on 2015-10-23
I've disabled all visual effects in my Win 7 VM. It looks like Windows 95 but it runs fine for day-to-day use. Because of that, I've never bothered to turn on 3D acceleration in VirtualBox since it isn't necessary.

---

### Post by sberla54 on 2015-10-23
> **PhilGil said:**
> I've disabled all visual effects in my Win 7 VM. It looks like Windows 95 but it runs fine for day-to-day use. Because of that, I've never bothered to turn on 3D acceleration in VirtualBox since it isn't necessary.

Well, i do that too. Who cares about how it looks? :)

---


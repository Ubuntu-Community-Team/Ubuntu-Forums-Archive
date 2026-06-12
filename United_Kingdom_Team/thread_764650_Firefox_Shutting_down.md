---
title: "Firefox Shutting down"
date: 2008-04-24
forum: United Kingdom Team
---

### Post by popsad on 2008-04-24
Am running Hardy Heron i get this with Firefox which shuts down for no reason at all.

No error messages or anything just shuts down

Has anyone else had the same problems

:confused:

---

### Post by BorisK on 2008-04-24
I've got exactly same problem. Firefox 3 just randomly closes itself. Sometimes my computer randomly shuts down. I don't know why. This is a serious issue. Your comp can't just shut down ! What if I was working in OO.o and comp crashed, all my data would be lost ! Fortunately, I don't do anything important on this comp, but it's still very annoying.

EDIT : Perhaps my comp shutdown is caused by BIOS settings ?
But why does the text, too fast to read, and the Ubuntu splash screen appear then ?

---

### Post by Jammy4041 on 2008-06-24
Hmmm, I've been noticing this one too, when I started using the Hardy Heron Beta back in March (ish) I noticed that Firefox was shutting itself down, the system would freeze and crash. But when I did a clean install of "The Heron", (stable version this time)everything worked fine for me.

Anoter thing LTS releases generally only become stable after the x.x.1 release- try now I think it has been released (via Update Manager)

---

### Post by NilsE on 2008-06-24
Not sure about the Ubuntu shutdowns but the Firefox closing is more than likely related to Flash

So, do the following and see what happens

Remove flashplugin-nonfree

Install flashplugin-nonfree

This should reinstall it without libflashsupport which is reported to be causing the close when viewing flash.

You could probably just remove libflashsupport in Synaptic and get the same results.

---

### Post by Joe of loath on 2008-06-25
I'm having the same problems. the firefox issue is rare, but sometimes the computer will freeze 5 or 6 times an evening!

---

### Post by freesitebuilder on 2008-06-25
I did have problems, but it was a couple of extensions that were causing it - easy to find as each timne it was either one I'd just installed, or one I'd just updated. You could try disabling all extension to see if that cures it, and if so it's a case on enabling one at a time to find the culprit. :(

---

### Post by Eviljim on 2008-08-11
> **BorisK said:**
> I've got exactly same problem. Firefox 3 just randomly closes itself. Sometimes my computer randomly shuts down. I don't know why. This is a serious issue. Your comp can't just shut down ! What if I was working in OO.o and comp crashed, all my data would be lost ! Fortunately, I don't do anything important on this comp, but it's still very annoying.

EDIT : Perhaps my comp shutdown is caused by BIOS settings ?
But why does the text, too fast to read, and the Ubuntu splash screen appear then ?

Some things to check.

1. Have you cleaned the inside of the PC recently? Sometimes excess dust causes the fans inside the PC to become blocked, and therefore overheat (inc CPU). If this happens the PC will switch off to protect itself.

2. Does the PC just reboot instantly, without warning (not running a shutdown script, but the same result as if you pushed the reset button)? My PC did this whilst running Vista (which wasnt the problem). I traced this back to a faulty PSU.

3. Faulty RAM modules may also be the cause of the problem, although Im not sure whether you would see the PC shutdown, but rather "Hang", unable to do anything.

---

### Post by Joe of loath on 2008-08-24
if you have a foxconn motherboard that can do it too. I gather you read the thread on the main forums?

---


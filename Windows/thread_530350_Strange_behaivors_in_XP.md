---
title: "Strange behaivors in XP"
date: 2007-08-20
forum: Windows
---

### Post by nvteighen on 2007-08-20
Please, could some explain me if someone knows what could be causing these problems:

1. Firefox crashing repeatedly and corruption of its Session Backup leading to a chkdsk. (this concerns me a lot)
2. Norton's LiveUpdate working weirdly: it reports in Application Log (right-click My Computer --> Administrate) supposedly missing DLL.
3. Windows Internet Explorer (aka IE 7) crashing repeatedly, curiosly with the same error code as when Firefox does.

I get exactly these same problems in two different computers, one running XP Professional, the other XP Media Center.

I suspect that it may be related to last weekend's Windows Updates, so if someone experiences the same, it wouldn't be so grave. But if not, could it be that those computers have been compromised?

---

### Post by raijinsetsu on 2007-08-20
Windows Update = Bug Central.
My suggestion would be to use System Restore and go back a week or two.
I just recently dropped windows completely, but before I did, I only installed updates that pertained to my hardware, or some bug I knew about. Most of those updates should only be installed on computers on a public network(ie. not behind a firewall).

---

### Post by nvteighen on 2007-08-20
Hmm... so you think it just a buggy update? It could be logical, but if so, more people should have the same symptoms, but I couldn't find anything in internet.

I'll wait a bit and see if someone here experiments the same.

---

### Post by raijinsetsu on 2007-08-20
Here at the office, a guy in an adjoining cubicle got the same updates we all did. He's also working with all the same software and hardware. For no particular reason, after the last update, his computer would no longer boot. After testing everything, the hardware was found to be 100% fine, and they had to reinstall windows. This time, it took the updates fine, and he has a working computer again.

Windows doesn't have a stable update system. It's commonly known that you shouldn't install updates unless you need them. They usually create more problems than they solve.

My suggestion would be: never go to Windows Update. Even when they have updates for your hardware, it's usually crap. I know these things from experience.

---

### Post by dca on 2007-08-20
> **raijinsetsu said:**
> My suggestion would be: never go to Windows Update. Even when they have updates for your hardware, it's usually crap. I know these things from experience.

Be careful w/ that...  If you bother to have MS play support for you that is the first question out of their mouths referencing Windows XP or Server 2003...  "Well, did you apply all updates?"
 
I don't care if it's something as idiotic as the PC has been on for three weeks w/o a shutdown and filled w/ stuff rattling around in memory.
 
I've had issue(s) w/ Firefox & IE in relation to google toolbar on 2000SP4 & XP machines.  Depending on websites accessed, they crash the browser w/ that annoying 'would you like to restart the browser' message.

---

### Post by nvteighen on 2007-08-20
I don't do it for my own computer (I almost only use Ubuntu... :)). I had a funny episode of a security update breaking my sound card driver and having to download a patch from Microsoft to solve it.

I'm going to see if my father has got any problem in his Vista-box; I understand these last weekend updates were there for him too.

---

### Post by nvteighen on 2007-08-20
> **dca said:**
> I've had issue(s) w/ Firefox & IE in relation to google toolbar on 2000SP4 & XP machines.  Depending on websites accessed, they crash the browser w/ that annoying 'would you like to restart the browser' message.

Well, now that you talk about Google, Google Desktop has stopped working too because it misses a DLL.

After having your Firefox issues, was there afterwards any data corruption that forced chkdsk at reboot? (specifically, FF's session restoring files) Was it related with a memory missaddressing to 0x000000?

---

### Post by raijinsetsu on 2007-08-20
Isn't it funny how Windows errors look disturbingly like virus activity... hmm... *ponders*

---

### Post by dca on 2007-08-20
> **nvteighen said:**
> Well, now that you talk about Google, Google Desktop has stopped working too because it misses a DLL.

After having your Firefox issues, was there afterwards any data corruption that forced chkdsk at reboot? (specifically, FF's session restoring files) Was it related with a memory missaddressing to 0x000000?

Don't remember, the recourse was to uninstall google toolbar and all other googles  from add/remove software utility and set firefox to use MSN as search utility...

---

### Post by nvteighen on 2007-08-20
> **dca said:**
> Don't remember, the recourse was to uninstall google toolbar and all other googles  from add/remove software utility and set firefox to use MSN as search utility...

Well, that doesn't work for Google Desktop: it cannot even be uninstalled because Uninstaller needs that missing dll...

---

### Post by raijinsetsu on 2007-08-20
Do you have any AntiVirus, Anti-SpyWare, or ad blocking software installed?

---

### Post by Steve1961 on 2007-08-20
> **nvteighen said:**
> Please, could some explain me if someone knows what could be causing these problems:

1. Firefox crashing repeatedly and corruption of its Session Backup leading to a chkdsk. (this concerns me a lot)
2. Norton's LiveUpdate working weirdly: it reports in Application Log (right-click My Computer --> Administrate) supposedly missing DLL.
3. Windows Internet Explorer (aka IE 7) crashing repeatedly, curiosly with the same error code as when Firefox does.

I get exactly these same problems in two different computers, one running XP Professional, the other XP Media Center.

I suspect that it may be related to last weekend's Windows Updates, so if someone experiences the same, it wouldn't be so grave. But if not, could it be that those computers have been compromised?

Make sure you sweep for spyware and viruses before you do anything else.  If you have an XP disc also try running;

sfc /scannow

Given the problems that norton can cause I'd also uninstall that and replace it with another firewall and antivirus solution.

---

### Post by dca on 2007-08-20
> **nvteighen said:**
> Well, that doesn't work for Google Desktop: it cannot even be uninstalled because Uninstaller needs that missing dll...

Last time I did it on a PC at work it referenced the .dll file when uninstalling...  Said missing .dll, application possibly already uninstalled would you like to remove it from add/remove list.  Answered yes and proceeded to remove all google directories from program files directory...

---

### Post by K.Mandla on 2007-08-21
> **raijinsetsu said:**
> My suggestion would be: never go to Windows Update. Even when they have updates for your hardware, it's usually crap. I know these things from experience.
To be honest, I would make the same recommendation. I get far more pleas from friends needing help after a Windows update than anything else.

---

### Post by DeusEx on 2007-08-21
best way to fix this windows problem:

```

cd /media/windowspartition
rm -Rf *

```

[edit] with a: ;) [/edit]

---

### Post by nvteighen on 2007-08-21
Strangely, now everything **seems** to work fine... Not sure; as I said, those computers are not mine, but of my parents, so I'm don't know everything that's going on them. For example, I don't remember well what finally happened with Google Desktop. Also, for the same reason, I just can't quit Norton nor suddenly install Ubuntu (that's the solution I found for my PC ;)).

Actually, I just wanted to know if someone experienced the same. As it seems not, then the problem is local to these two computers...

---

### Post by Depressed Man on 2007-08-21
> **K.Mandla said:**
> To be honest, I would make the same recommendation. I get far more pleas from friends needing help after a Windows update than anything else.

I agree. Or at least check the patch updates (and wait for other people to install it and report problems). A while back there were some XP patches that broke (well not broke but they changed enough of the OS that HP Network Printing wouldn't work with their software anymore). So I just told my family to hold off updating for a few weeks.

---


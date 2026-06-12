---
title: "Rosetta Stone won't start lessons"
date: 2011-03-14
forum: Wine
---

### Post by peterson2k4 on 2011-03-14
I am trying to learn Spanish for my job.  I downloaded Rosetta Stone and the language pack. They are both installed and I can even set up the lessons, username etc but as soon as I hit "start" I get the attached image.  Once I get that it doesn't do anything.

Thank you for your help

---

### Post by cwwilson721 on 2011-03-14
Which version of wine?
Which version of Rosetta Stone?
Did you check the wine AppsDB?

---

### Post by peterson2k4 on 2011-03-14
Rosetta Version 3.4.7
Wine 1.2

I checked the WineHQ AppDB but no one is having the same problem.

I found someone else was having the same problem.  they said a reinstall did it for them.  I reinstalled both wine and Rosetta but that didn't work.

---

### Post by peterson2k4 on 2011-03-14
Apparently the issue is with Wine 1.2.  Using Wine 1.3 works like a charm.

To install wine 1.3 add "ppa:ubuntu-wine/ppa" (without quotes) into you repository list, download wine 1.3 and enjoy!

---

### Post by XsheepX on 2011-03-15
It runs flawlessly in VirtualBox, but has had a few random crash errors in Wine, from my experience.

---

### Post by cwwilson721 on 2011-03-15
> **XsheepX said:**
> It runs flawlessly in [COLOR="Red"]VirtualBox[/COLOR], but has had a few random crash errors in Wine, from my experience.

Of COURSE it will run in VirtualBox. Or 99% of emulators, because it is ACTUAL WINDOWS. You may as well have said:

It works perfectly in Windows

Of course it runs perfectly in Windows. It's a Windows app. Let's see what you REALLY said.

wine is NOT an emulator. It is a set of hooks for windows apps to run in Linux, using the hardware. An emulator makes a "virtual machine", which makes Windows think it's running it's own hardware. Plus, since an emulator runs actual Windows, it has many advantages that wine does not, nor ever could, because it uses its own (closed source) code. Thus, using any 'vm' software, you are, in reality, running Windows. Or whatever OS. With all of it's code, in full. However, it runs slower than wine due to the fact that a VM has to 'translate' all hardware calls in Windows to an appropriate response in the host OS. wine does not have that 'translation'. It just passes them along to the actual hardware.

If you think I'm joking, try it for yourself. Install wine, then install a VM, then install Windows in the VM - any flavor you wish. We'll wait for you....Ok..1 hour later, you're done. OK..Now install whatever program you wish. I'll use World Of Warcraft as an example. I'll just copy/paste to make it faster to install (who has the time to download 16+ GB of data twice anyway?). Now, run WoW in wine. Then in the VM. See what I mean?
For those of us who dual-boot, try WoW in the 'pure' windows, then wine, then VM. That REALLY shows what wine does for you, as compared to a VM.

Considering the amount of software that wine actually runs, and quite well, I am very happy, and amazed, at wine. For an open source project, it does VERY well at 'faking' the closed source hooks that windows employs. Kudos to the wine-dev team for that.

So, to sum up, [COLOR="Blue"][SIZE="3"]W[/SIZE][/COLOR]ine [COLOR="blue"][SIZE="3"]I[/SIZE][/COLOR]s [COLOR="blue"][SIZE="3"]N[/SIZE][/COLOR]ot an [COLOR="blue"][SIZE="3"]E[/SIZE][/COLOR]mulator, VirtualBox *is* an emulator, and your response has NOTHING to do with the OP's question.

---


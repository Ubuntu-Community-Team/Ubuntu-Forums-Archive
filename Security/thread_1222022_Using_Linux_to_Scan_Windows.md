---
title: "Using Linux to Scan Windows"
date: 2009-07-24
forum: Security
---

### Post by ClydeBaneheart on 2009-07-24
I'm looking for an anti virus program that has a GUI (I personally have nothing against teaching terminal, but the higher ups think it's too risky), the ability to target the Windows Partition, and an option for quick scanning.

The point of this is to be placed on USB persistent Ubuntu flash drives to get heavily infected computers to boot to a stage where we can perform the cleanup from inside of Windows. This is, of course, only a request for a virus scanner. If there are other tools available for sorting out troublesome Windows boxes, I'd appreciate the info.

So far, I've used ClamAV (Terminal based, and GUI hasn't worked as I'd hoped) and avast! for Linux (best candidate so far, except for the fact that being a college, we need to buy licenses).

Disclaimer: No, I am not asking about an anti virus to scan Linux for viruses. I'm asking about an anti virus for Linux to scan a Windows partition for viruses.

Thank you for all of your help.

---

### Post by philcamlin on 2009-07-24
i think you can with avg :D

---

### Post by ClydeBaneheart on 2009-07-24
> **philcamlin said:**
> i think you can with avg :D
After looking at the license agreement (ugh... there's a reason I skip these), the Free edition carries the same caveats as avast!. You and I can use it to our hearts content, but when I want to use it in my offce, boom! You gotta buy it now!

I kinda understand why; they don't want to enable someone to make money using their software without getting a slice of the pie. The service me and my co workers provide is paid for in the student's tuition, so they can essentially get their computers fixed for free while enrolled. It's a good deal, but regarless of it being 'free,' we're still corporate.:(

---

### Post by fiver22 on 2009-07-24
Don't know if you've come across this but it might help:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by HermanAB on 2009-07-25
Howdy,

Things like AVG and ClamAV can run on Linux, but Spybot S&D and Hijackthis can't and those are even more important.

So I use BartPE, which is a WinXP Live CD that one can configure oneself with all the tools one needs.  It can also be installed on a USB stick, though I haven't tried:  [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I can't survive in my job without Bart's!

---

### Post by jprophet420 on 2009-07-25
> **ClydeBaneheart said:**
> I'm looking for an anti virus program that has a GUI (I personally have nothing against teaching terminal, but the higher ups think it's too risky), the ability to target the Windows Partition, and an option for quick scanning.

The point of this is to be placed on USB persistent Ubuntu flash drives to get heavily infected computers to boot to a stage where we can perform the cleanup from inside of Windows. This is, of course, only a request for a virus scanner. If there are other tools available for sorting out troublesome Windows boxes, I'd appreciate the info.

So far, I've used ClamAV (Terminal based, and GUI hasn't worked as I'd hoped) and avast! for Linux (best candidate so far, except for the fact that being a college, we need to buy licenses).

Disclaimer: No, I am not asking about an anti virus to scan Linux for viruses. I'm asking about an anti virus for Linux to scan a Windows partition for viruses.

Thank you for all of your help.

If you're using AV for commercial purposes you need to pay for it if thats what the eula dictates.

---

### Post by The Cog on 2009-07-27
clamav is the only truly freeware AV I know of. 

It may be worth trying to rustle up a script that can find, mount and scan all the FAT and NTFS partitions it can find. You may even be able to tuck that into a launcher (run in terminal) so there's just a GUI icon to click. 

Out of interest, what do they think is "dangerous" about the terminal?

---

### Post by Sir Jasper on 2009-07-27
Hi,

A-squared, Windows version for example, I'm almost sure has a substantial discount structure for educational establishments - other developers probably also offer such  discounts.

Personally, I would prefer an active guard (on execution or on access) run from within Windows. However, if you use Wine, for example, you could use 'buntu clamwin as well.

Dr.Web has both a pre-download free scanner and a free on demand scanner but I don't know about any restrictions on commercial use.

My regards

---


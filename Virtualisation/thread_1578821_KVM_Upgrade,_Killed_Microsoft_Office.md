---
title: "KVM Upgrade, Killed Microsoft Office"
date: 2010-09-21
forum: Virtualisation
---

### Post by gunksta on 2010-09-21
Note to moderators -- before you toss this out of this forum, read the entire post. I do think this is an appropriate post for this forum.

Note to all freedom loving persons reading this -- I don't consider this to be a bug. I upgraded to 10.10 and Microsoft Office decided that my virtual hardware had changed and turned itself off. Yet again, MS cripple-ware proves to be incapable of meeting the demands of the modern operating landscape. Unfortunately, it is software I need for work.

I recently upgraded an important laptop from 10.04 to 10.10. The upgrade was nearly flawless and with a little tweaking, everything looks terrific.

The only problem is with KVM. Actually, it works just fine. I have several different virtual systems and they all appear to be running in tip-top shape. I have a Fedora 14 nightly that works fine and a minix installation that works fine. I can even start my Windows XP VM.

But, when I started MS Office it informed me that my hardware has changed and as such, I must re-authenticate my copy of MS Office. Unfortunately, I am on the road this week and I don't have easy access to these codes. For the time being Office has powered down and is in Read-Only mode. Lovely. (I want to note that the Windows VM AND Office are both 100% legal.)

This raises several questions for me

[LIST=1]
[*]Who is the idiot at MS that decided to cut off my access to the software that I have licensed from MS? (No, I don't really expect anyone here to know the answer, but if you have the guy's address I would appreciate a PM.)
[*]What changed in the virtual hardware makeup that would have triggered this? Note -- This is why I posted this here. Yes, I'm asking about 10.10, but I have a bad feeling that this may be normal when updating KVM although my Googling came up empty handed. If this happens EVERY time I upgrade KVM, my Office license won't last long.
[*]Can I expect a problem like this every time I upgrade to a newer release? I should again note that the OSS software survived the transition without any affect and even Windows continues to "work", it is only MS Office that has decided to put itself into lock-down mode.
[*]How can I prevent this from happening during future upgrades? This is semi-important system but I chose to upgrade here to feel out the release. If the same thing happens to my virtualized servers running SQL Server 2000 and 2005, this could be a real problem. A problem I would prefer to avoid.
[/LIST]

Again, while I am asking the question because of something that happened during an upgrade to 10.10, I feel that this is relevant because I want to learn more about how KVM handles upgrades in a more general sense than merely looking at the 10.10 upgrade.

---

### Post by manzdagratiano on 2010-09-21
To answer some of your questions:

Your access to MS Office was cut off because I would not expect any different from Microsoft, who would not let you run the software you purchased the way you want; and, to name the guy you want, try Steve Ballmer?

I have absolutely no idea why this happened due to a software upgrade, since kvm is supposed to emulate your hardware originally anyway - provided virtualization support is enabled in the bios. However, instead of imploring you to not use office and switch to openoffice, or even to try installing office under Wine, I would implore you instead to install a dual boot with Winblows - and avoid future grief. You need not wipe Ubuntu to do this - just create a new 20G partition and install XP on there, and then you can reinstall your grub through the liveCD, which is easier than it may be expected to be. Otherwise, if the monarchical winblows, whose time is long past and which should retire already instead of hindering all progress, does not get a space truly of its own, would usually end up giving you pangs of pain from time to time.

I would myself never again install Winblows, but, I myself faced a similar requirement for MS Office on my fiancée's laptop - on which Lucid was running peacefully, and I tried and tried and tried - with first a VM, which was horribly slow as it is a netbook, and then with Wine, where Powerpoint would not run because it says it was not installed for the current user, so that I had to finally resort to put Winblows there.

---

### Post by gunksta on 2010-09-21
I am hoping somewhere here knows something about the update process for KVM so I can learn how to protect myself form this in the future. I assume that the virtual hardware changed in some manner, but I'm not sure what that is.

---

### Post by TheFu on 2010-09-22
> **gunksta said:**
> I am hoping somewhere here knows something about the update process for KVM so I can learn how to protect myself form this in the future. I assume that the virtual hardware changed in some manner, but I'm not sure what that is.

You didn't say which version of MS-Office it was. The different versions need all sorts of different settings to work under WINE (or a commercial WINE solution for $30).

I can only suggest that you restore your old system from that backup, then see which specific hardware KVM was emulating.  Next, perform the upgrade again and see which different hardware KVM is emulating now.  Manually set the items that are different in the new KVM startup - perhaps it is just the MAC address on a NIC (probably not)? I suspect the newer KVM version emulates faster drives and NICs by default than the older version.

In the meantime, you can probably download and install a 90 day trial of MS-Office on the machine.  I don't know if that will work or not, but it could be worth a try.

I place all software license keys into KeePassX - along with all my different web and systems passwords. Those keys are really just a copy/pasted txt file inside KeePassX, since putting them in individually is simply too much effort. Just a though.

---


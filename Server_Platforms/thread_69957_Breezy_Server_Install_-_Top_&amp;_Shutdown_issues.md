---
title: "Breezy Server Install - Top &amp; Shutdown issues"
date: 2005-09-28
forum: Server Platforms
---

### Post by d1337 on 2005-09-28
I'll try to be brief.  I have an IBM M Pro Dual PIII box that I have had Hoary installed on for several months...used the default install with desktop, then slimmed it down with runlevel changes.  I installed VHCS and got it running, but decided to remove as it's overkill for what I want/need and it seemed to eat alot of RAM, of which I have 1G.  Since I didn't have this box doing much yet, I decided to scrap my install and play with Breezy.

I clean installed Breezy using server, uncommented the repos, added kernel 2.6.12-9-686-smp, and loaded a few lightweight packages for a minimal desktop (IceWM, dillo, xterm to name a few), but I don't think my problem lies within these packages.

Initially, when I boot the box and leave it at a terminal, a top shows that I'm only using about 50mb of Ram.  However, after an apt-get update and an apt-get upgrade, top shows that I am using over 250mb of ram.  There are only 42 tasks running, so I can see them all in a top (ssh'd in from another box with x), and nothing is using more than 0.5 in the MEM% column.  I know that updates/upgrades are cached locally, but will my Ram ever free up without a shutdown.

Speaking of shutdowns, even if I boot the box and never get into xdm/wdm, if I throw a shutdown -h -r now at it, it hangs up at restarting system (or rebooting system...can't recall verbage).  It appears as it has halted everything and the keyboard is unresponsive (no numlock/capslock, no ctrl+alt+f*).  From there, the only way to bring it down is with the power button...and of course that's the only way to bring it back up.  I like to be able to call it to reboot remotely if I'm toying with it from work or from a friends house...but it won't come back up.  Is there another package I need that perhaps I don't have or isn't ready yet?  Potentially a bug?

I wasn't certain if I should post this on Breezy dev or here at Serevr Talk, decided here since it is more server specific...and I'd imagine that there'll be more to come from Breezy Server after release.

Thanks, in advance, for any help/insight,
d1337

---

### Post by Jussi Kukkonen on 2005-09-29
> ...will my Ram ever free up without a shutdown.
Yes. As soon as you need it. If you want to know how much memory is used check the *-/+ buffers/cache* -column in the output of *free*.

The shutdown problem sounds like your machine doesn't have *acpi* switched on (or supported)... If the machine is from this decade it should be able to do acpi. Check the bios settings. I'm not sure, but even *apm* (the predecessor of acpi) might suffice...

---

### Post by d1337 on 2005-09-29
> Yes. As soon as you need it. If you want to know how much memory is used check the -/+ buffers/cache -column in the output of free.
Thanks...I learn something new everyday.  Perhaps I should've asked that question in absolute beginner talk.
Shutdown worked proper when I had Hoary installed, so I'm assuming that the machine will support one of the two.  I'll check this evening to see if I have changed something in bios or have passed a switch on to the kernel unknowingly.  Ideally, I'm able to stop/start most services through /etc/init anyway, but I have a few configuration files to untar from backup still, and remote reboot is sometimes handy.  Otherwise, Breezy is still in development so I'll keep an eye on it or check the devel forum for any insight/bugs/other folks having the issue.
Thanks for your reply,
d1337

---

### Post by SilentCacophony on 2005-09-30
As for the shutdown problem, I noticed mine did that after a server install. With some digging around, I found that there seemed to be no installed app for it, and installing the acpid or apmd package was needed. There seem to be several packages for such functionality, but those are the ones I tried, and I think either will work.

---


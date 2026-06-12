---
title: "Xubuntu 15.10 Bugs"
date: 2015-06-18
forum: Ubuntu Development Version
---

### Post by jasonbyrne-att on 2015-06-18
New here and sorry if I'm posting in the wrong area. I have the following bugs in Xubuntu 15.10 and am wondering if and when there are fixes and when/what they may be:

Pandora breaks Flash in Chrome, but only shortly after initial log on to Pandora. It won't happen the rest of the day and I don't recall it happeneing after system reboot, only first system start of the day and first log on to Pandora.

Drag and drop within Thunar crashes Thunar

Starting yesterday my sound crashes intermittently system wide and I have to reboot. This bug I could really live without. This makes me want to ask the question of the possibility of downgrading to 15.04 without having 15.04 installed before 15.10. This is assuming these same bugs aren't present in 15.04 ?

Please Help

---

### Post by dino99 on 2015-06-18
having bugs with an early dev version is expected; and should not be used by users not able to find the issue's cause by glancing to the logs and then debug it before filling a report. Downgrading to 15.04 is not doable, forget about it.

---

### Post by jasonbyrne-att on 2015-06-18
> **dino99 said:**
> having bugs with an early dev version is expected; and should not be used by users not able to find the issue's cause by glancing to the logs and then debug it before filling a report. Downgrading to 15.04 is not doable, forget about it.

Thanks for your response. Can you suggest a tutorial or documentation outlining what logs to look at and how to debug ? Although I've become quite adept at clean installs of Xubuntu, it's something I will do for a new user but for myself, I think it's time to go outside my comfort zone and learn more. I'm not a virtual-boxer or dual-booter, I'm a straight heavy user so I guess it's time to do some reading. For future reference, where would I file a report ? Please advise.

---

### Post by VMC on 2015-06-18
Does the apport-bug dialog come up when Thunar crashes?

Examine '/var/log/syslog, kern.log, dmesg' for starters. Also, anything in '/var/crash' ?

---

### Post by grahammechanical on 2015-06-18
When using the development version, which at the moment is for 15.10, I would advise also having a stable/released version such as 14.04 to use as a fall back OS should the development version become unusable. I keep all my data on a separate partition so that if I need to reinstall then I do not lose data and I can work from any installation I happen to have on the hard disk at that moment.

I have found the development version to be very stable and I use it every day for my daily work but if I want to experiment I put in another install of the development version and I mess around with that. I never need to think about downgrading to 15.04 because I can dual boot into 15.04 whenever I want and also to 14.04. I recommend having a similar set up.

As for reporting bugs, this link will explain it.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Good hunting

P.S. Keep in mind that on this section (Ubuntu Development Version) we use the development version, we discuss the development version and that includes bugs but that does not mean we know the answers. At least I usually do not. Things often get fixed over time through daily updates.

---

### Post by enricobe on 2015-06-18
Drag and Drop works fine for me. Xubuntu 15.10

---

### Post by jasonbyrne-att on 2015-06-18
> **VMC said:**
> Does the apport-bug dialog come up when Thunar crashes?

Examine '/var/log/syslog, kern.log, dmesg' for starters. Also, anything in '/var/crash' ?

Yes dialog comes up and I click send report when Thunar crashes. I forgot to mention Thunar crashes when I have multiple files highlighted and drag then drop them. Crash happens right after the drop, with one of the files looking like it remained in the original folder but after restarting Thunar I can see that everything I dragged did end up in the folder I dropped them in.

/var/log/syslog and /var/kern.log are pretty lengthy, not sure what I'm looking for /var/dmesg has one line "(Nothing has been logged yet.)" 

/var crash has these 3 lines:

/var/crash/_usr_bin_thunar.1000.crash
/var/crash/_usr_bin_thunar.1000.upload
/var/crash/_usr_bin_thunar.1000.uploaded

---

### Post by jasonbyrne-att on 2015-06-18
> **enricobe said:**
> Drag and Drop works fine for me. Xubuntu 15.10

I forgot to mention Thunar crashes when I have multiple files  highlighted and drag then drop them. Crash happens right after the drop,  with one of the files looking like it remained in the original folder  but after restarting Thunar I can see that everything I dragged did end  up in the folder I dropped them in.

---

### Post by jasonbyrne-att on 2015-06-18
> **grahammechanical said:**
> When using the development version, which at the moment is for 15.10, I would advise also having a stable/released version such as 14.04 to use as a fall back OS should the development version become unusable. I keep all my data on a separate partition so that if I need to reinstall then I do not lose data and I can work from any installation I happen to have on the hard disk at that moment.

I have found the development version to be very stable and I use it every day for my daily work but if I want to experiment I put in another install of the development version and I mess around with that. I never need to think about downgrading to 15.04 because I can dual boot into 15.04 whenever I want and also to 14.04. I recommend having a similar set up.

As for reporting bugs, this link will explain it.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Good hunting

P.S. Keep in mind that on this section (Ubuntu Development Version) we use the development version, we discuss the development version and that includes bugs but that does not mean we know the answers. At least I usually do not. Things often get fixed over time through daily updates.

I use Dropbox for all my backing up and file syncing, so no problem there. I'm going to hang in there with 15.10. I explained to my wife earlier that with any Linux distro community, team etc. if they say they're working on it and it will eventually be fixed through an update and it will happen before the next major release which you would normally have to pay money for. I'm obviously referring to micro$oft. We have one machine still running windows and it's days are numbered. I feel I've been burned badly by microsoft. Sorry to go off topic but the point is I can sit tight for awhile with Xubuntu, which I always go back to if I go on a hopping spree, and the update fix will come or a fix will be posted somewhere and I generally don't have to wait 3 years, pay $$$ for it and still have to roll the dice, and maybe wait again. 

Thanks for the bug report link.

---

### Post by VMC on 2015-06-19
> **jasonbyrne-att said:**
> I forgot to mention Thunar crashes when I have multiple files  highlighted and drag then drop them. Crash happens right after the drop,  with one of the files looking like it remained in the original folder  but after restarting Thunar I can see that everything I dragged did end  up in the folder I dropped them in.

Where and how do you drop them? Since Thunar doesn't have multiple panes, do you drop them to the left onto some partition or other store?

edit: see here:
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1063140](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1063140)

---

### Post by enricobe on 2015-06-20
The normal drag and drop of multiple files (from a folder to another in the same partition) works fine for me

---

### Post by jasonbyrne-att on 2015-07-09
Any other ideas on sound crashing ? It's still happening as well as Thunar crashes. I've debugged to the best of my ability, used apport and filed bug reports here: 

[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4)

Would it matter if I have a UEFI machine but am using legacy boot instead of EFI ? 

Please help

---

### Post by ventrical on 2015-07-09
> **jasonbyrne-att said:**
> 

Would it matter if I have a UEFI machine but am using legacy boot instead of EFI ? 

Please help

No, not to my knowledge.

---

### Post by fidelis2 on 2015-09-21
> **jasonbyrne-att said:**
> I forgot to mention Thunar crashes when I have multiple files  highlighted and drag then drop them. Crash happens right after the drop,  with one of the files looking like it remained in the original folder  but after restarting Thunar I can see that everything I dragged did end  up in the folder I dropped them in.

I can confirm this bug in Thunar 1.6.10 which user jasonbyrne is experiencing.  I've got two independently installed Xubuntu 15.10 PCs showing the exact same Thunar bugs, so I can pretty much exclude wrong configuration of one single installation. This bug is a show-stopper for 15.10 because it renders Thunar unusable. There's more bugs in Thunar and I'll outline them here.

1) Moving multiple files from one folder to another one many times crashes Thunar without an error message: Thunar just disappears. It's exactly like Jasonbyrne explained.

2) If you open the trash-can in Thunar and want to restore a non-empty deleted file/folder from there, Thunar complains:
 Die Datei »Xy« konnte nicht wiederhergestellt werden.
 Der Herkunftsort von »Xy« konnte nicht ermittelt werden.
(Roughly translated to English:
 The File »Xy« couldn't be restored.
 The source place of »Xy« couldn't be found.
)

3) For linked folders pointing to other devices (i.e. a folder in your home linked to, for example, /media/user/mountxy ): when you delete a file in the root of the linked folder in your home, Thunar complains:
 Datei konnte nicht in den Papierkorb verschoben werden.
 Ungültiger Link über Gerätegrenzen hinweg.
(Roughly translated to English:
 File couldn't be moved to the trash-can.
 Invalid link accross device boundaries.
)
Deleting the file without the trash-option (i.e. delete "forever") works however.
Also deleting files with the trash-option in the sub-folders of the linked folder, works.

I would be happy to help, but I'm no C/C++ programmer.

---

### Post by sudodus on 2015-09-21
@ fidelis2

You can help by reporting it as a bug to Launchpad [https://launchpad.net/](https://launchpad.net/). That is the way to tell the developers that you have found a bug :-)

Please ask here if you need more help to report a bug!

---

### Post by fidelis2 on 2015-09-21
Sudodus, thanks for the reply. I searched for "Thunar" via your link and found a list of bug entries. Now to see the newer ones I clicked on "(sort by) number", so I got the newst ones on top.

The original author here (Jason Byrne) has already reported the crashing Thunar bug in July 2015 :
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1472050](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1472050)

However no comments or assignments have been made since then. Can I just "re-vive" his bug report?


P.S. For my mentioned bug 2) I also saw a bug-report there. For my bug 3) I didn't, so I'm trying to open a new bug report.

---

### Post by sudodus on 2015-09-21
Both of us can mark 'affects me too'. You can also add a comment. I think all these actions will add to the 'bug heat'.

---

### Post by fidelis2 on 2015-09-21
Thanks, I just did that, too.

---

### Post by mdn2 on 2015-11-01
> **jasonbyrne-att said:**
> I forgot to mention Thunar crashes when I have multiple files  highlighted and drag then drop them. Crash happens right after the drop,  with one of the files looking like it remained in the original folder  but after restarting Thunar I can see that everything I dragged did end  up in the folder I dropped them in.

Exactly the same thing here. Glad it's reported. Thinking of switching to Nautilus or PCMan until it's fixed.

---

### Post by fidelis2 on 2015-11-02
> **mdn2 said:**
> Exactly the same thing here. Glad it's reported. Thinking of switching to Nautilus or PCMan until it's fixed.

Please consider to vote for this very nasty bug, which has been reported here by the thread's creator:
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1472050](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1472050)

Unfortunately this nasty bug which crashes Thunar regularly, didn't get much attention so far, and its "importantance" is still listed as "undecided". So I don't think we will see a fix soon. :-(

The strange thing is, some people like the thread's creator, you and I see the bug every day multiple times even on various Xubuntu 15.10 machines, whilst other people don't seem to see the crashes...

---

### Post by sudodus on 2015-11-02
Or they 'vote with their feet' - walk away and use another file browser.

Let us hope it will be fixed, now that we have started to develop and test the next long time support version, 16.04 LTS :-)

---

### Post by howefield on 2015-11-02
15.10 thread closed.

---


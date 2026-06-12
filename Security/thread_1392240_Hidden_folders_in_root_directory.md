---
title: "Hidden folders in root directory"
date: 2010-01-27
forum: Security
---

### Post by todak on 2010-01-27
What, if any, significance is there to the following message shown in the rkhunter.log? ```
[21:11:58]   Checking for hidden files and directories       [ Warning ]
[21:11:58] Warning: Hidden directory found: /etc/.java
[21:11:58] Warning: Hidden directory found: /dev/.udev
[21:11:58] Warning: Hidden directory found: /dev/.initramfs
``` What need would there be for hidden directories to exist in /?

---

### Post by adam814 on 2010-01-27
I can't confirm it's normal, but I can confirm I have each and every one of those directories on mine.

---

### Post by adam814 on 2010-01-27
Ok, I ran rkhunter myself.  It seems pretty paranoid, it marked several files that had been updated through the repos as possible trojans.  I was satisfied with verifying that the files from the upgrade were still present in the apt cache, so I ran it with --propupd to get past those warnings.

I then re-ran it.  It made it through all the checks without any obvious warnings only to warn me at the end that I'm possibly infected with the Xzibit rootkit based on the fact that the string hdparm appears in my /etc/init.d/bootlogd script.  Under the section where it actually checks for the Xzibit rootkit all entries read not found.

I'd always used chkrootkit before and I think I'll stick with it.  It doesn't claim I'm infected because a shell script contains recognizable strings.

---

### Post by todak on 2010-01-27
I didn't find that the files in the directories were at all malicious, just that rkhunter throws a fit because they are hidden. I will mark the thread a "Solved" seeing as those directories are hidden by default. I just thought it odd that there would be any hidden directories at all in /.

---


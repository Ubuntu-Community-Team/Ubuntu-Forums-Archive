---
title: "All HDD space used up within hours"
date: 2013-04-10
forum: Ubuntu Development Version
---

### Post by man_bash on 2013-04-10
Hi everybody!

Just installed 13.04-x64 on my desktop, and within about 6 hours or so I couldn't launch System Monitor. Then I ran gnome-system-monitor from terminal, and the error msg said ```
failed to commit changes to dconf: GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dfile_2derror_2dquark.Code12: Failed to write file '/home/user/.config/dconf/user.9JL9UW': fwrite() failed: No space left on device
terminate called after throwing an instance of 'Glib::FileError'
```

Lo and behold, there was no space left on the 105 GB or so partition!

The only piece of software I installed so far, other than the few updates, was Steam for linux. Is that the culprit? I didn't even install a single game on Steam yet...

Any ideas? "Format C:/" necessary /jk?

---

### Post by cariboo on 2013-04-10
Check your log files in /var/log

---

### Post by grahammechanical on 2013-04-10
What utility are you using that tells you the Hard disk is full? In 13.04 there is now a much improved Disk Usage Analyser. We can click on a partition, let it scan for a few seconds and then use the Back button ( < ) and see a sliding bar graphic comparing the partition size with the amount used.

Regards.

---

### Post by kostkon on 2013-04-10
It would be helpful if you could paste the output of df -h and the sizes of your log files, e.g.
```
ls -la /var/log
```

---

### Post by VinDSL on 2013-04-10
My 'money' is on a corrupt /tmp folder...  :)

---

### Post by rrnbtter on 2013-04-11
Greetings,

> **kostkon said:**
> It would be helpful if you could paste the output of **df -h** and the sizes of your log files, e.g.


That turns out to be a very handy bash command. I'm putting that one in my utilities script. Thanks!

---


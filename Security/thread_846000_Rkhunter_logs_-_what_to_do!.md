---
title: "Rkhunter logs - what to do?!"
date: 2008-07-01
forum: Security
---

### Post by primky on 2008-07-01
So when I run rkhunter it shows me some warnings:
> 
Warning: The syslog daemon is not running.
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-3078549387: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /etc/.jvm.swp: Vim swap file, version 7.1


And also some warnings of this type:
> 
Warning: The file properties have changed:
         File: /usr/bin/file
         Current hash: 3f1c272113fdffe393a60c212bd6762086e0c32d
         Stored hash : e65457a0c5662f7d67516734e90d62548d6e7767


So what can I do now about these warnings? Should I delete hidden directories? What about file that has been changed?

Help!

---

### Post by bryncoles on 2008-07-01
just come across these two threads

[http://ubuntuforums.org/showthread.php?t=785332](http://ubuntuforums.org/showthread.php?t=785332)
[http://ubuntuforums.org/showthread.php?t=844605](http://ubuntuforums.org/showthread.php?t=844605)

which might help furnish some understanding.... but i hope someone who actually knows something about rkhunter comes along soon, because im very interested in this question too!

---

### Post by brian_p on 2008-07-01
> **primky said:**
> So what can I do now about these warnings? Should I delete hidden directories?

No. They are legitimate directories and files. The only one that looks a candidate for deletion is vm.swp. It's either a leftover from something you have been editing or are in the process of editing with vim.

> What about file that has been changed?

No file has changed. rkhunter may think it has but that is probably because you have not set up the program correctly. Read the documentation carefully. The propupd seems to be one option to look out for.

---

### Post by primky on 2008-07-01
Thanks to both of you! :)

---


---
title: "hidden processes found - should i worry?"
date: 2008-05-16
forum: Security
---

### Post by iamnotthemessiah on 2008-05-16
i was running rkhunter with unhide as a cronjob overnight and it found a bunch of hidden processes. is that normal or should i worry?

the output i got in my system mailbox was:
Warning: Hidden processes found:  23564
26580
27588
27592
27596
27600
27604
28612
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-3494257518: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

---

### Post by HermanAB on 2008-05-16
Run 'ps -e' and see what they are, then plug them into Google to learn about them.

Cheers,

Herman

---

### Post by iamnotthemessiah on 2008-05-16
well i ran the rootkit hunter thing again and got
Warning: Hidden processes found:  15096
17207
17211
17215
17219
17223
17227
17231

ps -e did not show those processes

---

### Post by HalPomeranz on 2008-05-17
If the processes are truly hidden, then yes it's probably something you should worry about.  But it's possible that you've got a false positive situation.

When rkhunter tells you that there are hidden processes, try to cd to the /proc/<pid> directory for the process (where <pid> is one of the process ID numbers output by rkhunter).  If you can't cd into the directory, then the process isn't really hidden, it was just in the middle of exiting when the rkhunter check ran and rkhunter was confused and you probably have nothing to worry about.

If you do manage to cd into the /proc/<pid> directory, then it's likely you have a problem.  Interesting things to do once you're in the /proc/<pid> directory include:

1) "cat cmdline" should give you the name the process is running under

2) "sudo cat environ | perl -pe 's/\000/\n/g'" gets you the environment variable settings for the process

3) "sudo ls -l fd" shows you what files the process currently has open

4) "sudo ls -l cwd" shows you the current working directory of the process (which could be interesting if the process was started by the attacker from their rootkit installation directory)

There's plenty of other cool stuff you can do with the various bits of information under /proc, but the above should be enough to help you figure out what the process(es) are doing and how much trouble you're in.

---

### Post by Meson on 2008-05-18
Very interesting stuff Hal, thanks.

---

### Post by iamnotthemessiah on 2008-05-18
thanks HalPomeranz that was very helpful
it seems i cant cd into any of the processes rkhunter is reporting so thats good news i guess. however every time i run rkhunter it reports about 7-10 hidden procs and if i run rkhunter again 2 minutes later theres another 7-10 hidden procs reported but different ports from 2 mins before

---

### Post by HalPomeranz on 2008-05-18
> **iamnotthemessiah said:**
> it seems i cant cd into any of the processes rkhunter is reporting so thats good news i guess. however every time i run rkhunter it reports about 7-10 hidden procs and if i run rkhunter again 2 minutes later theres another 7-10 hidden procs reported but different ports from 2 mins before

Sounds like you've got a process running that's spawning lots of short-lived children.  Are you running something like a web server or mail server on the machine where you're running rkhunter?

---

### Post by iamnotthemessiah on 2008-05-18
no, im not really running anything except the usual stuff like torrent client, firefox, pidgin etc
i do have that exim thing installed tho in order to get system mail

thanks for your help

---


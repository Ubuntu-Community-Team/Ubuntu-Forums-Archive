---
title: "mdadm ckeckarray"
date: 2010-10-14
forum: Server Platforms
---

### Post by hyuk48 on 2010-10-14
hello 

I'm the user operating ubuntu 9.10 server.
I made configuration with software mirroring(raid1).
when I checked cron, I found the mdadm in cron.d dir.

 57 0 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --all --quiet

checkarray is supposed to be run on the first sunday of every month.

so I just want to know

        1. what does checkarray do exactly?

        2. does it make a stress to system?

        3. Is there any problem if I get rid of the script from cron?

thanks for reading in spite of poor english.

---

### Post by hyuk48 on 2010-10-14
please help me~~

---

### Post by dtfinch on 2010-10-14
/usr/share/mdadm/checkarray is a shell script, so you can open it in a text editor to see what it does.

For each md array, it writes "check" to /sys/block/$array/md/sync_action (where $array is the array name, like md0), telling md to check the array for consistency.

(Researching this for the first time) "check" first resets /sys/block/$array/md/mismatch_cnt to zero, then scans the entire array to find mismatched blocks (which can happen in a power loss or crash while writing) and increments mismatch_cnt for each mismatched block. It does not correct them though. All that lengthy check seems to do is determine whether you need to repair the array, which can be done by writing "repair" instead of "check" to /sys/block/$array/md/sync_action.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=405919](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=405919)

---

### Post by hyuk48 on 2010-10-14
thanks for Ur reply. :)

---

### Post by hyuk48 on 2010-11-22
If there are mismatch_cnt values, does it mean " the raid was broken"?
then when should I repair the disk?

---


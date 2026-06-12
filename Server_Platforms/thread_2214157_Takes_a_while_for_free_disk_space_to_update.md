---
title: "Takes a while for free disk space to update"
date: 2014-03-30
forum: Server Platforms
---

### Post by markmckee6011 on 2014-03-30
I noticed that it takes a while for the free disk space to update after deleting files.

I share a 20GB drive using NFS.
/dev/sdc1 on /media/20GB type ext3

df -h /media/20GB
/dev/sdc1              17G   15G  180M  95% /media/20GB

Then I delete some stuff.
df -h /media/20GB
/dev/sdc1              17G   15G  180M  95% /media/20GB

And after a few minutes:
df -h /media/20GB
/dev/sdc1              17G   15G  866M  95% /media/20GB

df -h is ran on the server to try and eliminate any NFS issues.

I appreciate any help/advice.

---

### Post by thnewguy on 2014-03-30
My guess is that the act of deleting files or checking storage space is out of sync. Maybe one action or the other is being buffered. If you look at the manual page for the "df" command you will notice there is an option called "sync". Running df with the --sync flag causes the host system to perform a file system sync prior to displaying disk usage information. Try that and see if the information df outputs is up to date.

---


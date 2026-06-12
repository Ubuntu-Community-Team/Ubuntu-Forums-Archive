---
title: "local ubuntu mirror; apt-mirror -&gt; rsync"
date: 2011-01-26
forum: Server Platforms
---

### Post by surfer on 2011-01-26
i have a local repository for our internal network. up to now i used apt-mirror to download the packages.

but as i do not know how to delete the packages that are no longer used (e.g. the ones from jaunty and intrepid), i would like to mirror the repository with rsync (as described [here]("https://help.ubuntu.com/community/Rsyncmirror")).

the thing is this: i do have (most of) the files that i would download with rsync. is there a way to tell rsync just to change the user/permissions/acces times and not download the file again if the size matches?

---

### Post by amra.sonntag on 2011-01-26
As far as i understand the idea behind rsync - it shouldn't reload the whole file anyway. It is supposed to check filesize and timestamps and after that with some adv. mechanics only writes and probably downloads the parts needed to match the files.

From the rsync man page:
" It is famous  for  its
       delta-transfer  algorithm,  which  reduces the amount of data sent over
       the network by sending only the differences between  the  source  files
       and  the  existing  files in the destination."

---


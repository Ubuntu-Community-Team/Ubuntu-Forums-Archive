---
title: "Postix Question"
date: 2006-11-28
forum: Server Platforms
---

### Post by murraymints on 2006-11-28
Hi,

I'm trying to configure postfix to pipe emails to a custom script I have made but it just seems to be ignoring any entries I add to the /etc/postfix/master.cf.

I've added the following to the bottom of my master.cf

```

log    unix  -   n   n   -   -   pipe
    flags=Rq user=maillog argv=/usr/bin/log.sh -f ${sender} -- ${recipient}

```

and I have created the user maillog and made it the owner of the log.sh file and any other files/folders the scipt accesses.

The script works perfectly if I su as user maillog and pipe a test email into the log.sh script.

I used sudo postfix reload after updating the master.cf to update my changes.

Anyone have any idea what I'm missing? Any help would be greatly appreciated.

---

### Post by murraymints on 2006-11-29
hi, I'm still stuck on this. Is there anything else I need to other than add a line to the master.cf and run postfix reload to get postfix to pipe mail to a script? If anyone has any info I'd really appreciate it , itwould be great if I could solve this.

---


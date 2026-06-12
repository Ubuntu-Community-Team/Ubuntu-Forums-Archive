---
title: "DST Bug or Patch Bug?"
date: 2011-01-03
forum: Server Platforms
---

### Post by bunklung on 2011-01-03
I use Ubuntu server mainly as an offsite backup. I use WinSCP from my desktop to transfer files to my Ubuntu server.

I have maybe about 1.3TB of files and backups on this machine. I used LVM to create one large 3TB volume.

Since most of my backups are already in place. I use WinSCPs "New or Updates File(s) only" option.

I have been using it successfully for a long time. It's great where I don't have to worry about what file is new, it just gets replaced or stays. Saves me bandwidth and time since unnecessary transfers don't occur.

However, I started to notice this month everything was being retransmitted. Well, almost everything... This made no sense to me since the files had not change and were not modifed. On closer inspection, my file modified dates were off by 1 hour as such:

The entire month of 2009, Oct AND:

3/13/2010 dates prior are ok, BUT 3/16/2010 dates forward are off by 1 hour 
11/7/2010 dates forward are ok, BUT dates prior to 11/6 are off by 1 hour.

Looks like 2nd Sunday of March and the 1st Sunday of November? Meaning, DST.

This was not an issue during the summer. DST changed a while ago. Was there an update or patch pushed out that would modify all these times from 1 hour?

Linux xxxxxxx 2.6.32-26-server #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 x86_64 GNU/Linux

---

### Post by bunklung on 2011-01-03
Hmm, I think I found it:
[http://www.codeproject.com/KB/datetime/dstbugs.aspx](http://www.codeproject.com/KB/datetime/dstbugs.aspx)

---

### Post by bunklung on 2011-01-03
[http://winscp.net/eng/docs/task_synchronize_full#synchronization_mode](http://winscp.net/eng/docs/task_synchronize_full#synchronization_mode)

---


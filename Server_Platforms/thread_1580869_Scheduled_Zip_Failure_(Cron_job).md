---
title: "Scheduled Zip Failure (Cron job)"
date: 2010-09-24
forum: Server Platforms
---

### Post by roystreet on 2010-09-24
Hello,
...I am trying to have a regularly scheduled "zip" job done, but it keeps partially zipping the files & then stops.  For instance, I use something similar to this:
```
zip -r /partition2/folder1backup-`date +%m%d%y`.zip /partition1/folder1
```

If I run this in the terminal, it works.  If I run it in webmin as a scheduled command, it works.  But when I make it a scheduled cron job, it starts, but then after a while it stops never completing the job.  It seems to have worked when folder1 would be maybe 20mb it did it sucessfully.  If folder1 was 120mb, it will get all the way to around 90mb & then stop.  You can see the temporary file, you can see its increasing in size...Then it stops, the file never having an extension, etc.
...Any thoughts on this?  Why it would work as a one time job, but when it's a cron job?

NOTE: If you are wondering what ```
`date +%m%d%y`
``` does, it simply appends the date.  Once again, this will work from the command line, etc.

I'm confused :confused:
Thanks for your help,
~roystreet

---

### Post by anglican on 2010-09-24
> **roystreet said:**
> Hello,
...I am trying to have a regularly scheduled "zip" job done, but it keeps partially zipping the files & then stops.  For instance, I use something similar to this:
```
zip -r /partition2/folder1backup-`date +%m%d%y`.zip /partition1/folder1
```If I run this in the terminal, it works.  If I run it in webmin as a scheduled command, it works.  But when I make it a scheduled cron job, it starts, but then after a while it stops never completing the job.  It seems to have worked when folder1 would be maybe 20mb it did it sucessfully.  If folder1 was 120mb, it will get all the way to around 90mb & then stop.  You can see the temporary file, you can see its increasing in size...Then it stops, the file never having an extension, etc.
...Any thoughts on this?  Why it would work as a one time job, but when it's a cron job?

I'm confused :confused:
Thanks for your help,
~roystreetIf you're running the command without the -q option then you should get output mailed to you from it - a list of files and what zip did with them. Where does it stop and why?

H

---

### Post by roystreet on 2010-09-24
Hi, I don't have an email server setup currently, so I haven't messed with that very much.  I haven't had time to dive into that, to know what I'm doing.
I will note that this has happened for more than one folder.  I've had one that was roughly around the numbers I mentioned earlier, but I've also had one that was a couple hundred mb in size.  It gets pretty far into it...Then it just stops.  So, it's not even one specific folder.
.
Is there a time limit on how this process is allowed to run?
Thanks,
~roystreet

---

### Post by CharlesA on 2010-09-24
What you can do is throw it into a script and tell cron to run that script.

Also, might try redirecting the output to a file with > /path/to/some/file 2>&1

So you can check for errors.

---


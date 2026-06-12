---
title: "Webmin - File System Backup Error"
date: 2012-06-05
forum: Server Platforms
---

### Post by maverickaddicted on 2012-06-05
Hello Everyone,

I am trying to take backup of my files on server using Webmin Filesystem backup, but I am getting this error message -

```

tar: Removing leading `/' from member names
tar: /home/serveradmin/backup/designers: Cannot open: Is a directory
tar: Error is not recoverable: exiting now

```

backup is a backup directory with 777 permission. How can I take backup using Webmin filesystem backup module?

---

### Post by rubylaser on 2012-06-05
By default, tar removes the leading / on filepaths.  For example /home/rubylaser would end up with the member name of home/rubylaser. If the leading / wasn't removed, tar would end up taring to the same location as the original.  Also, does the directory you're trying to backup contain a space anywhere in the filepath?

You have a couple of options:
1. Add the -P option (--absolute-names) to your tar command so that it will archive relative to the root path.
2. cd to / first, then run your tar command.

Sorry, I don't use Webmin, so I'm not sure what options Webmin filesystem backup gives you.  At least you know what's causing the problem now :)

---

### Post by maverickaddicted on 2012-06-06
> **rubylaser said:**
> By default, tar removes the leading / on filepaths.  For example /home/rubylaser would end up with the member name of home/rubylaser. If the leading / wasn't removed, tar would end up taring to the same location as the original.  Also, does the directory you're trying to backup contain a space anywhere in the filepath?

You have a couple of options:
1. Add the -P option (--absolute-names) to your tar command so that it will archive relative to the root path.
2. cd to / first, then run your tar command.

Sorry, I don't use Webmin, so I'm not sure what options Webmin filesystem backup gives you.  At least you know what's causing the problem now :)

Thanks for the response. That's what I am thinking about, how can I take the backup using webmin module, or is there any way to manually modify that webmin backup module.

---

### Post by rubylaser on 2012-06-06
From looking at screenshots on Google, it looks like it supports an extra command line parameters option that you could use to add the -P option.

[IMG]http://www.webmin.com/screenshots/chapterfs/figure2.gif[/IMG]

---

### Post by maverickaddicted on 2012-06-06
> **rubylaser said:**
> From looking at screenshots on Google, it looks like it supports an extra command line parameters option that you could use to add the -P option.

[IMG]http://www.webmin.com/screenshots/chapterfs/figure2.gif[/IMG]

Thanks for pointing that, I almost overlooked that part. I will surely try it tomorrow.

---

### Post by maverickaddicted on 2012-06-07
Thanks rubylaser, that done the trick.

---

### Post by rubylaser on 2012-06-07
Great, I'm glad to hear it :)  Please mark the thread as solved with the thread tools at the top of the page.

---


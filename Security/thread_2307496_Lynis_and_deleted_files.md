---
title: "Lynis and deleted files"
date: 2015-12-25
forum: Security
---

### Post by james188 on 2015-12-25
Good day,

I just ran a Lynis scan and I got the following results: 

[02:00:21] Performing test ID LOGG-2190 (Checking deleted files in file table)
[02:00:21] Test: checking deleted files but are still in use
[02:00:21] Result: found one or more files which are deleted, but still in use
[02:00:21] Found deleted file: /tmp/mu7Xe843
[02:00:21] Found deleted file: /tmp/tmpfVCoMGl
[02:00:21] Found deleted file: /var/log/upstart/systemd-logind.log.1
[02:00:21] Suggestion: Check what deleted files are still in use and why. [LOGG-2190]

Why would a file still be used after deletion? And how can I find out what program created these files? And is this something to be worried about?

Any help would be greatly appreciated!

Thank you, 
James

---

### Post by The Cog on 2015-12-25
If the files are still in use then the command lsof will be able to list them. e.g.:
```
lsof | grep -e COMMAND -e '\(deleted\)'
```

It is fairly common to open a file and then delete it. It means the file is private to that application, and auto-deletes when the application exits. It's a normal way to use temporary files. I've got around 970 of them open on my system right now.

---

### Post by james188 on 2015-12-25
> **The Cog said:**
> If the files are still in use then the command lsof will be able to list them. e.g.:
```
lsof | grep -e COMMAND -e '\(deleted\)'
```

It is fairly common to open a file and then delete it. It means the file is private to that application, and auto-deletes when the application exits. It's a normal way to use temporary files. I've got around 970 of them open on my system right now.

When I run the command I get:

57133 /var/log/upstart/systemd-logind.log.1 (deleted)

Thank you,
James

---

### Post by The Cog on 2015-12-25
You are welcome.
Chromium-browser opens hundreds of them. Without chromium-browser running I see just 3 log files right now.

You can mark the thread solved using the pull-down **Thread Tools** menu near the top of the page.

---


---
title: "auditing a folder"
date: 2012-09-04
forum: Server Platforms
---

### Post by JAZ1976 on 2012-09-04
I've been looking for a solution to a problem my boss handed me this morning. We have an old BBx system running on our Ubuntu 12.04 server. This system is made up of multiple program files. I need a way to monitor the programs folder to see what files were created/deleted/modified, when it happened and by who. I've looked at auditd, but that seems to be for file level tracking. I also looks at inotify, but haven't found any good examples. Can someone point me in the right direction? Would either of these programs work or is there something better that I can use?

---

### Post by gordintoronto on 2012-09-04
Do you mean, the Business BASIC interpreter?

What is the folder name?

File creation and modification dates can be provided by the Nautilus file manager. It can also tell you the file's owner.

If I delete a file, that fact might be logged, but the log entry will be removed eventually.

---

### Post by JAZ1976 on 2012-09-05
I'm not looking for the owner of the file, I'm looking for who modified the file and when it was modified. Yes, BBx is a Business BASIC interpreter. The files are located in /users/bbx/programs. I get alot of the info I need with ls -lt, but that doesn't give me who modified the file. An this is a server with no desktop installed.

---

### Post by gordintoronto on 2012-09-05
ls can give you when a file was modified.

I hardly use ls, because there is almost no reason to run a system with no GUI. However, that philosophical discussion doesn't solve your problem.

You might try: ls -lt --author
I honestly don't know if that is the solution, but it might be.

On my system, only the owner can modify a file. However, different permissions can be set.

---


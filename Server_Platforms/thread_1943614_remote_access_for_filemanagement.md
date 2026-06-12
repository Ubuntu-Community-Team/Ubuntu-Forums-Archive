---
title: "remote access for filemanagement"
date: 2012-03-19
forum: Server Platforms
---

### Post by doas777 on 2012-03-19
hello all,
I have a desktop server(10.04), with a dump directory, that I must periodically root through and file away the contents. the files will be moved to other locations on the server, or to my nas. I connect from a windows terminal.

I've used NX for years to remote in, and cut/paste the files from one server location to another. unfortunately lately NX has caused my server to stop responding on a weekly basis or so (it won't allow new network connections, or respond to pings, but existing sessions continue to work...?)

anyway, I've since tried VNC and winscp, but both are too clunky for the scale of work I'm doing. I've tried just moving from share to share, but then the files get passed to the windows host, and then written back to the new location, which is on the same partition as the source.

so I'm looking for a good windows-compatible utility for moving files around (in groups or individually), Any ideas?

---

### Post by darkod on 2012-03-20
Is doing it at the command line out of the question?

You could enable SSH access to your server, use Putty in windows for SSH, and just move the files directly with mv to the destination which will be mounted first (temporary or permanently).

I use SSH and mv to move from my NAS server to another NAS network hard disk. The data never passes through the computer you are doing it from.

---

### Post by rubylaser on 2012-03-20
> **darkod said:**
> Is doing it at the command line out of the question?

+1. There must be some logic to moving these items, so it should be scriptable.  I'd hate to have to do mundane task like sorting all the time.  Why don't you provide some more info and maybe this whole process can be scripted.

---

### Post by bubylou on 2012-03-20
Definitely use ssh for this. If this is a reoccurring then it can easily be scripted and run periodically with cron.

---

### Post by doas777 on 2012-03-21
well, unfortunately it is a complex and random set of tasks. the contents vary wildly and many things go in unpredectible locations. really not a cli friendly task. the dump is used by several users, and I have to file the contents, generally based on my knowledge of the likes and dislikes of those around me. one of IBMs super-AIs might be able to do it after intense interviews and some serious code-fu, but no simple AI could do it. let alone one of my pathetic bash scripts.

I also have to try to be efficient in how I group files for copy to the nas as the files may be 12+ GB (I often have batches in excess of 100Gb), and that takes a while. batches of files may have wildly differant names (and often require human renaming). if not appropriately timed, a task that takes an hour's attention and 4+ hours unattended copying, turns into an all-week job. 

in fact, the reason I don't like winscp is that its just too clunky. folders take at least half a second to react to changes, click selection is not really smooth, and you can't open multiple destination windows (or tabs as i prefer when I'm nx'ed into the server) so no drag-n-drop, etc. I need something very smooth and fast to click through. I wish VNC behaved better as well. nothing should be laggy on a gigabit net. unacceptable. 

I'm getting the impression I may have exhausted the possibilities on my own, so if you have any ideas let me know. I should probably focus on trying to fix freeNX.

Thanks!

---

### Post by volkswagner on 2012-03-22
Two things come to mind.

1.  Use SFTP with your favorite FTP client such as filezilla.

2.  Run a live linux via Quemo, or in a virtual machine allowing ssh-sftp through nautilus.

---


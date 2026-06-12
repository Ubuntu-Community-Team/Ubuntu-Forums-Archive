---
title: "rdiff-backup keeps backing up /home/[root]"
date: 2007-06-30
forum: Server Platforms
---

### Post by BroadArrow on 2007-06-30
I'm using rdiff-backup to back up my server and so far it seems fairly reliable except that it keeps backing up the home folder of the superuser in entirety, whether or not the files have changed.

It doesn't do this for other folders I'm backing up (including other users' /home folders) so it must think the files have changed for some reason when they haven't.

Has anyone else encountered this problem and/or found a fix for it?

---

### Post by MJN on 2007-06-30
I don't use rdiff-backup myself but do use rsync which can be set (logging verbosity) to output the reasons why a particular file is being backed up e.g. change in size, time, name etc. Is there a similar facility in rdiff-backup that could give you an indication of what might be causing the behaviour?

Mathew

P.S. Incidentally, your title suggests you've got root's home folder in /home/root/ - are you sure? Root's home is usually /root/ (not that I suspect this has anything to do with it)

---

### Post by BroadArrow on 2007-07-01
> **MJN said:**
> I don't use rdiff-backup myself but do use rsync which can be set (logging verbosity) to output the reasons why a particular file is being backed up e.g. change in size, time, name etc. Is there a similar facility in rdiff-backup that could give you an indication of what might be causing the behaviour?

Mathew

P.S. Incidentally, your title suggests you've got root's home folder in /home/root/ - are you sure? Root's home is usually /root/ (not that I suspect this has anything to do with it)

Thanks for your reply. 

It does have a verbosity setting (which I currently have set to 4 as the default setting -- 3 I think -- didn't even list which files it was backing up) which it probably passes on to rsync.

Which setting would I have to go up to get the reasons for backing up a file and how specific does it get? I don't want to max it out and get a 2 gig email with a whole lot of info I don't need!

The home folder is actually the root's but the superuser created during Ubuntu installation I was just inserting [root] for illustrative purposes. Sorry, I should have been clearer!

---

### Post by MJN on 2007-07-01
I'm afraid as I don't use rdiff-backup I couldn't say. A single -v with rsync is sufficient to explain on a per file basis what's changed.

Mathew

---


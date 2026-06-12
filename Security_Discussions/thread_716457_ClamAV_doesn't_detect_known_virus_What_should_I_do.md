---
title: "ClamAV doesn't detect known virus? What should I do?"
date: 2008-03-05
forum: Security Discussions
---

### Post by h6w on 2008-03-05
What should I do if I have a file that I know to be a virus (because AVG detects and removes it), but clamav comes back with "OK"?

The setup is an Ubuntu 7.10 server running Samba.  One of the windows machines spread it all over the server.  I'd really like to clean it up but when I do a "clamscan" on one of the files it comes back with "OK".

I've tried freshclam, and that says everything is up to date, running version 0.91.2.

Cheers,
h6w

---

### Post by h6w on 2008-03-06
To answer my own question, it appears that version 0.91.2, even with the latest signatures, can't detect some viruses, particularly Worm.Sohanad-155

To fix this, ScottK suggested I install the backported 0.92.1 from clamav-ppa, which worked.

To do this, I added the following lines to my /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/ubuntu-clamav/ubuntu gutsy main
deb-src http://ppa.launchpad.net/ubuntu-clamav/ubuntu gutsy main

```

Then do:
```
sudo apt-get install avscan clamav clamav-daemon clamav-freshclam
```

Note: As of 2008-03-06, apt-get upgrade won't work as it keeps most of the packages back.

Now you should have a backported version of 0.92.1 with support for all the latest viruses. :-)

---

### Post by kitterma on 2008-04-23
I'm working on getting those into the official backports archives, but it takes a fair amount of testing first.

---

### Post by Chayak on 2008-04-24
ClamAV isn't a good scanner.  It misses a lot of known stuff.  I've seen a lot of files that none of the AV systems pick up.
try submitting the file to [http://www.virustotal.com]("http://www.virustotal.com")

---

### Post by netlogic on 2008-04-25
I'm sorry to hijack this thread, but what is happening to this forum? It seems like I can't create a **new thread** anywhere in the forum. It started ever since Hardy was released. Anyone having a similar experience? Are they doing this, because they are short of a bandwidth?

Thanks

---

### Post by netlogic on 2008-04-30
Anyone getting this error when they are trying to post a new thread? What gives? I noticed this is happening to all the older forum members now. Should we take our consulting business to Redhat and give them the money?

===================================================================
You are browsing the ARCHIVE section at Ubuntu Forums. You are able to reply/post to threads that are ALREADY created, however you cannot create NEW threads in the archive.
===================================================================

---


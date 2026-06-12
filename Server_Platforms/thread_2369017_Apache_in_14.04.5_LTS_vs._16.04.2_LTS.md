---
title: "Apache in 14.04.5 LTS vs. 16.04.2 LTS"
date: 2017-08-17
forum: Server Platforms
---

### Post by George_R._Kasica on 2017-08-17
Hello, we're currently running several 14.04.5 LTS Servers here with the packaged Apache server that loads and maintains via the apt get:
Existing 14.04.5 LTS Server
centsgpsgaa01:~# apache2 -version 
Server version: Apache/2.4.7 (Ubuntu)
Server built:   May  9 2017 16:14:10

We are getting hit by a vulnerability in Nessus scans here and wondering if there is any way short of going to 16.04.2 LTS and its Apache to upgrade since its a total new deployment and reload of the servers here - not a small task. Unless someone has a better suggestion.....

16.04.2 LTS Server
#apt -a list apache2
Listing... Done
apache2/xenial-updates,xenial-security 2.4.18-2ubuntu3.4 amd64
apache2/xenial 2.4.18-2ubuntu3 amd64

Thank yiou,

George Kasica

---

### Post by deadflowr on 2017-08-17
10.04 is unsupported.
And thus susceptible to vulnerabilities. 
Do you mean 16.04?

---

### Post by George_R._Kasica on 2017-08-17
YEs I'm sorry my poor typing 16.04.2 LTS. Edited above as well.

---

### Post by deadflowr on 2017-08-17
I've edited the thread title, since 10.04 is irrelevant here.

And [I]Moved the thread to Server Platforms.
[/I]

---

### Post by George_R._Kasica on 2017-08-17
Sorry Missed that one. Thank you.

---

### Post by LHammonds on 2017-08-18
I believe the best way to maintain servers is to document how you install, configure and deploy them so you can repeat the exact same roll-out on a newer OS.  (thus the links in my sig and all the tutorials on my forums)

I recently upgraded all my 12.04 servers to 16.04 and only have a couple 14.04 servers that I plan to move up to 16.04.  But in each and every case, I build a new server and configure it to work the exact same way as the old server and verify that I can migrate the data/apps.  Once documented, I then migrate the data/services to the new server and swap the IP.

I never do an in-place upgrade of a major OS version.  That only works somewhat OK if you don't have any applications on it and you wait for the 1st SP. hehehe.

I know it can be complicated and scary especially if you don't know what all is going on (many hands in the pot).  But far better to figure it out and document the process so it won't be scary the next time it is needed.

LHammonds

---

### Post by George_R._Kasica on 2017-08-18
Found a PPA to load 24.27 easily and solve our issues. Closing.

---


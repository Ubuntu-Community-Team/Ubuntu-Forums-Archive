---
title: "Update Manager says 8 updates ready but only 4 show"
date: 2008-06-21
forum: Security
---

### Post by Udibuntu on 2008-06-21
Hi,

Update Manager promoted me a notice on updates, saying 8 updates are ready for download.

Only 4 downloads are visible in the update pane, each 24K in size (something to do with kernel this and that...).

Total download size is 43MB...I'm no math wizard but I can tell something sure ain't kosher here...

Now, I tried to uncheck them and download, and I got a message saying this download is from an unverified source...

What do you think?

---

### Post by Oldsoldier2003 on 2008-06-21
> **Udibuntu said:**
> Hi,

Update Manager promoted me a notice on updates, saying 8 updates are ready for download.

Only 4 downloads are visible in the update pane, each 24K in size (something to do with kernel this and that...).

Total download size is 43MB...I'm no math wizard but I can tell something sure ain't kosher here...

Now, I tried to uncheck them and download, and I got a message saying this download is from an unverified source...

What do you think?

check your software sources and temporarily disable any third party repositories, then do 
```
sudo apt-get update
```
and see what happens.

---

### Post by Udibuntu on 2008-06-21
> **Oldsoldier2003 said:**
> check your software sources and temporarily disable any third party repositories, then do 
```
sudo apt-get update
```
and see what happens.

Thanks, but now 5 are said to be available and only 3 show, 24K each. Total size is 30 MB...

---


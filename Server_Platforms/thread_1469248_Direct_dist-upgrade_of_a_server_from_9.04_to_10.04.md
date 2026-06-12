---
title: "Direct dist-upgrade of a server from 9.04 to 10.04 LTS possible?"
date: 2010-05-02
forum: Server Platforms
---

### Post by habrys on 2010-05-02
So is it possible? I've got a sweet little ubuntu 9.04 server with a few TB of disk storage all in RAID5, LVM, encrypted with lots of movies and music there. I was planning to dist-upgrade it to 10.04 (skipped 9.10 as everything worked then and still works very well, but now when LTS got released I figured it would be a good moment to upgrade at last).

I was going to replace "jaunty" with "lucid" in sources.list and then simply run:
```
sudo apt-get dist-upgrade
```

But I've read somewhere, that a direct upgrade should be only done from previous release (9.10) or previous LTS release (8.04). I really don't wanna install from scratch again. I have also no possibility to backup nearly 4TB of data somewhere else. The data is cleanly separated from system on another device (RAID5 matrix of 5x1TB disks; the system itself resides on a physically separated 250 GB disk).

So what are your recommendations? I don't wanna start the upgrade now and have to tell my wife, that she cannot watch movies or listen to the music anymore - until I repair the server. It could be fatal :D

---

### Post by Ryan Dwyer on 2010-05-02
I would wait until 10.04.1 is out before upgrading a server. Although this is an LTS and is supposed to be stable, there's no harm in waiting a bit.

As you said, upgrading directly from 9.04 to 10.04 is not supported. You will need to upgrade to 9.10 then 10.04, or just do a fresh install of 10.04. You said your data is separate so you shouldn't need to back it up.

And for a server I believe the correct procedure is to run do-release-upgrade.

---

### Post by habrys on 2010-05-02
> **Ryan Dwyer said:**
> I would wait until 10.04.1 is out before upgrading a server. Although this is an LTS and is supposed to be stable, there's no harm in waiting a bit.

Yes, good idea. 10.04.1 it is then.

> **Ryan Dwyer said:**
> 
As you said, upgrading directly from 9.04 to 10.04 is not supported. You will need to upgrade to 9.10 then 10.04, or just do a fresh install of 10.04. You said your data is separate so you shouldn't need to back it up.

And for a server I believe the correct procedure is to run do-release-upgrade.

Do I understand it correctly - when I run do-release-upgrade once, it'll upgrade from 9.04 to 9.10 and then, after second run from 9.10 to 10.04?

---

### Post by Ryan Dwyer on 2010-05-02
Yes, that's right. I imagine it would make it clear which version you're upgrading to anyway.

---


---
title: "No disks detected on Megaraid"
date: 2009-02-25
forum: Server Platforms
---

### Post by alkisx on 2009-02-25
I installed an LSI megaraid 8208 raid controller, and configured it through its bios as a raid 10 with 4 active disks and 1 spare.

The problem is when it comes to install ubuntu server, it says it cannot detect any disk drive, and provide me with some drivers to choose for it. I tried everything that starts with "megaraid" on the list and it still says no disk drive detected.

any help?

---

### Post by alkisx on 2009-02-25
It seems the right driver to use is "megasr" which is not available on the ubuntu installation.

Anyone nows where can I find the megasr driver?

---

### Post by alkisx on 2009-02-25
No one knows where to find megasr??????

---

### Post by Flyingjester on 2009-02-25
[http://www.gossamer-threads.com/lists/linux/kernel/925695](http://www.gossamer-threads.com/lists/linux/kernel/925695) take a look at this link, seems to be the best thing i can do to help you with it. and calm down.. bumps are normally 24 hour things.

[http://tjw.org/ubuntu-megasr/](http://tjw.org/ubuntu-megasr/) also i found this link in another post on this website.

---

### Post by wirelessmonkey on 2009-02-25
Well, their driver download page is here: [http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/megaraid_sas_8208xlp/index.html?locale=EN&remote=1]("http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/megaraid_sas_8208xlp/index.html?locale=EN&remote=1")

But it also looks like they only support RedHat and SuSE linux, though you may want to give it a try anyway...

---

### Post by alkisx on 2009-02-25
Thank you for your answer.

It is that for almost 2 weeks I am trying to have a working raid.

Tried dmraid with no luck

With soft raid, the installations of ubuntu (every possible 64 bit edition) as also debian, wouldn't let me partition my raid (no one knew anything on so many posts I made through misc forums, and no answer also).

Getting this card, I was hoping to have real raid, but seems I am not so lucky again. That was for my hurry. It is a bit difficult to calm down. I am sorry for this:)

--------------------------------

TO THE SUBJECT:

your first link:
In my model at least, there is no open_source directory, so I cannot compile anything.

About your 2nd link. I've fount it also, but it is for an old kernel, and no upgrades possible.

Also found this: [http://mentors.debian.net/debian/pool/non-free/m/megasr/](http://mentors.debian.net/debian/pool/non-free/m/megasr/)

is for debian, but it may works. I will try burning it into a cd, and use it for during install with a second terminal to insmod (after a make I suppose).

If you have any news meanwhile, let me know. thanks:)

---

### Post by cainwong on 2010-08-08
You may give a try at:
[http://ubuntuforums.org/showpost.php?p=9690768&postcount=7](http://ubuntuforums.org/showpost.php?p=9690768&postcount=7)

---


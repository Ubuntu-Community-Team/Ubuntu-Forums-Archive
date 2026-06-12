---
title: "How do I cap storage limit for a particular folder, and use PHP to meter that?"
date: 2009-05-17
forum: Server Platforms
---

### Post by avahi on 2009-05-17
I am giving a few people space on my server, but I want to cap them at 10gb each.

They each have DAV access to a folder in /web/sites, and I wanted to cap the folders limit to 10gb each. How would I go about doing that?

I also want to write a quick PHP page that will be inside the folder that tells them how much space they have left, how much they are using, etc. How would I do that?

Thanks

---

### Post by cariboo on 2009-05-17
Use quotas, have a look at this [howto]("http://www.debianadmin.com/implement-and-manage-disk-quotas-in-linux.html"), it is for debian, but it should work for you.

---

### Post by 3L33T on 2009-05-17
Cariboo:  Thanks for posting this link.  I actually have not givent this feature much thought until my filesystems began to exceed %60 threshold I setup.

---


---
title: "Ubuntu Software Centre secure?"
date: 2011-01-02
forum: Security
---

### Post by roton on 2011-01-02
Does Ubuntu Software Centre use any kind of hash checking when you install apps? I recently came back to Ubuntu and have been installing lots of apps. However, they have not all been from my home connection.
Since the repo's don't use https how easy would a mitm attack be? If there is no hash checking what's to stop someone sitting at a hotspot or on a work network with a dir full of "modified" popular apps?

Has anyone already tried this? Or am I just being paranoid?

Thanks for any replies.

---

### Post by rookcifer on 2011-01-02
The repos each have their own GPG signing key that you must import before downloading anything.  Once you import the key, then each package you download is checked to make sure it was signed with that key.  This ensures the integrity of the packages.

---

### Post by roton on 2011-01-02
> **rookcifer said:**
> The repos each have their own GPG signing key that you must import before downloading anything.  Once you import the key, then each package you download is checked to make sure it was signed with that key.  This ensures the integrity of the packages.

Excellent, thanks! I now feel more secure in my Ubuntu use :p

---


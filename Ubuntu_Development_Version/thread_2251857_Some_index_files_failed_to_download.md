---
title: "Some index files failed to download"
date: 2014-11-07
forum: Ubuntu Development Version
---

### Post by Chanath on 2014-11-07
> W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. 

Should I do something about this, such as unticking the source line, or just wait?

---

### Post by Elfy on 2014-11-07
extras usually takes a while to turn up, I disable that

---

### Post by Chanath on 2014-11-07
> **Elfy said:**
> extras usually takes a while to turn up, I disable that

Thanks!

---

### Post by zika on 2014-11-07
> **Elfy said:**
> extras usually takes a while to turn up, I disable thatBeg to differ: Use &#8222;old&#8220; repos until new are open because there are some important packages (at least for some of us) that are getting upgrades frequently. ;)

---

### Post by Elfy on 2014-11-07
horses for courses - I tend to test what we seed by default here - nothing in there we need :)

with some exceptions ;)

---

### Post by zika on 2014-11-07
> **Elfy said:**
> I tend to test what we seed by default hereOn the other hand, I can not (honestly) test something I can not use 24/7... ;)
I do not have 2^x disks and time for that... ;)

---

### Post by Cavsfan on 2014-11-08
I put Utopic in extras there for a while then decided I didn't want to mix anything in with Vivid like Elfy and commented it out.

I've noticed extras are the last to be added. So, I'll just wait. Every once in a while I'll check  [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) click on dists to see if it's been added yet.
When it is I uncomment it out.

My
 [IMG]http://www.tammystwocents.com/wp-content/uploads/2013/09/two-cents3-150x150.jpg[/IMG] :p

---


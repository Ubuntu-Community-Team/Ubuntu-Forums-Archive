---
title: "installing only one or two universe-based packages"
date: 2005-11-07
forum: Server Platforms
---

### Post by OneSeventeen on 2005-11-07
I'm going to install php-db, the PEAR::DB module, and I know I can manually do it, or use apt-get to do it.

The downside is apt-get requries me to add universe repositories, whereas manually does not, but manually does not allow me to easily upgrade in the future.

I do not want to install the latest and greatest universe packages, I want all but a few PEAR modules to be default/fully supported, and just a few to be universe/not fully supported.

Does this make sense?  I just remember that on my desktop I wound up installing all sorts of unsupported software because I added all the unsupported repositories, and I don't want that to happen on my main machine.  

So I guess my question is:
**Can I flag 2 or 3 packages as acceptable to download from universe, but leave everything else out?**

---

### Post by 23meg on 2005-11-07
You can add universe/multiverse, install what you want, and then remove them. You won't be getting any updates (except security ones; just leave security updates turned on) until the next release anyway.

---

### Post by OneSeventeen on 2005-11-08
Oh, I don't know why I thought the software would be updated between releases, but that would make sense to wait until the next release to work out any kinks.

I guess what I'm worried about is adding the universe package then having it update my main software to whatever the universe has, but I just ran through the package list and everything I saw used a different name for each package, such as mysql-server and mysql-server-4.1

Anyway I see what you are saying and I agree.  I just wanted to put it in my own words so when I search for this again I'll remember why I did things this way. :p

Thanks!

---


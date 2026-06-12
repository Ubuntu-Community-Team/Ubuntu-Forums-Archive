---
title: "Why is there a different folder for extra sources?"
date: 2010-05-01
forum: The Cafe
---

### Post by donniezazen on 2010-05-01
Hi,

Some of the sources go to source.list other go to sources.list.d. Why so? I am trying to make a source.list so if i reinstall the system i can easily get all repositories at one place. Is it OK to have just one source list with all the repositories or should i keep them in different files and in sources.list.d folder?

Thanks,

***********************
I tried Google but couldn't come up with the exact answer. Please pardon me if there is a similar thread.
*************************

---

### Post by swoll1980 on 2010-05-01
Apt doesn't care whether the sources come from sources.list
or files in sources.list.d

---

### Post by juancarlospaco on 2010-05-01
Because its better to add/remove a file than add/remove a specific line of a large text file.

*i.e. some .deb can install a source cleanly and remove it cleanly*

---


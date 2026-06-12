---
title: "-u switch in tar"
date: 2009-08-29
forum: Server Platforms
---

### Post by e24ohm on 2009-08-29
Folks:
I am having a difficult time with the "-u" switch for "tar". I want to only append files that have changes in a directory, not re-tar every file in the directory.

I know the -u switch is used for this, but how do I use this switch? When I use "-cvfu" I get another archive labeled "u", so I am not sure what is going on, and I'm not sure what I am doing wrong.

---

### Post by DaithiF on 2009-08-29
the problem is that the 'f' parameter needs to be followed by the name of the archive you are creating.  just reorder your parameters to put 'f' last.

---

### Post by e24ohm on 2009-09-01
> **DaithiF said:**
> the problem is that the 'f' parameter needs to be followed by the name of the archive you are creating.  just reorder your parameters to put 'f' last.hey thanks for the help. I ended up having to use the following command.

"tar -vuf", which updated the tar archive with only the modified and added content.

thanks mate...

---


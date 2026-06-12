---
title: "Advice from someone with Apt-Mirror experience??"
date: 2014-10-27
forum: Repositories &amp; Backports
---

### Post by DVD-R on 2014-10-27
Hello,
I've setup Apt-Mirror for the first time and have it running as we speak.
As I'm doing this for the first time, I wanted to limit the amount of files that I download.
So when I setup the configuration file mirror.list, I removed "restricted", "universe" and "multiverse" in the source list string and left "main" only.

When Apt-Mirror setup the index files it identified 37 GIG as the download size.
I figured this might be about right for just the "main" repositories.

But as I'm watching it download, I'm noticing that it has setup other folders like "multiverse" and is loading files into it as well.

I'm wondering if this is normal behavior for Apt-Mirror?
Does anyone who has used Apt-Mirror some, know if this is normal?
Sincere thanks
dw :-]

---

### Post by DVD-R on 2014-10-29
Well it took 4 fool days to do it, but it only pulled the "MAIN" repository.
Case closed :-]

---


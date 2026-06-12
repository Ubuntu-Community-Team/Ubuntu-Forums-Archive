---
title: "Hash sum mismatch at end of latest update"
date: 2014-01-18
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2014-01-18
FTR: Using 3.13.0-4-generic, 64bit minimal install with xfce4. At the end of the latest update I get this:

```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.aarnet.edu.au_pub_ubuntu_archive_dists_trusty_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.aarnet.edu.au_pub_ubuntu_archive_dists_trusty_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.aarnet.edu.au_pub_ubuntu_archive_dists_trusty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.aarnet.edu.au_pub_ubuntu_archive_dists_trusty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by cariboo on 2014-01-18
Have you tried a different mirror?

---

### Post by Bucky Ball on 2014-01-18
Thanks, but problem gone. I was just offered another update by Software Updater, installed, ran <sudo apt-get update> in a terminal and all good. Might have been my mirror catching up. ;)

---


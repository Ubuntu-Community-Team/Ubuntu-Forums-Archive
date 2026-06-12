---
title: "apache2 - regenerate config files"
date: 2023-06-16
forum: Server Platforms
---

### Post by Kakers on 2023-06-16
Hi all, just recently come back to Ubuntu from CentOS so getting used to the differences.
Wondering if someone can help me because I've done something potentially stupid here...

I wanted to start with a fresh apache install, so I removed the apache2 packages, deleted the /etc/apache2 directory and tried reinstalling.
Problem is, the conf-available, mods-available are empty and some other default files are missing.
I've tried to reinstall again but no luck, it's only the files under /etc/apache2 as the actual modules (.so files) exist under /usr/lib.

Is there any easy want to regenerate these files that I'm missing? As they were there the first time the packages were installed but not for the reinstall.

---

### Post by Kakers on 2023-06-16
Of course I find the answer AFTER I post...
I'll list it incase anyone else needs to find the answer.

> 
sudo apt-get remove --purge apache2 apache2-utils apache2-bin
sudo apt-get install --reinstall  apache2 apache2-utils apache2-bin


---


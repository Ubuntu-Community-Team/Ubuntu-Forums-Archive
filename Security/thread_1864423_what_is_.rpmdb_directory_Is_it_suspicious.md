---
title: "what is .rpmdb directory? Is it suspicious?"
date: 2011-10-18
forum: Security
---

### Post by vahaboglu on 2011-10-18
I installed 11.10 few days ago. I am careful not to install any stuff from an unknown source. However, to day I detected a directory under the File System: /.rpmdb.
There are some files in the directory, named "Basenames", "Dirnames" etc. File Basenames at terminal prompt returned " Basenames: Berkeley DB (Btree, version 9, native byte-order)". These files can not be opened by any file manager. Okteta displayes some very few bytes inside.
I moved the directory out of the system and nothing changed. As soon as I see all the programs are working.
Do anybody know anything about this directory.

---

### Post by Coder68 on 2011-11-15
I wonder what this folder is also. I am having slow Nautilus issues and this file is in my home folder, but owned by root. 

Anyone care to shed some light on this file and who should own it?

Thank you,

C68

---

### Post by kalkems on 2011-11-20
If I'm not mistaken it seems as if both alien and rpm are installed as standard in 11.10.
/ernie

---

### Post by Hackie2 on 2012-03-12
> **kalkems said:**
> If I'm not mistaken it seems as if both alien and rpm are installed as standard in 11.10.
/ernie

rpm depends on alien which depends on lsb-base which is Ubuntu default. I wasn't able to check if lsb (the standard) really enforces rpm, but it is possible.

Anyway: I can live with an installed rpm package, but I don't think that a  /.rpmdb directory is conformable to any standard (especially not to lsb), it should go into /var/lib/rpm which even exists but is empty

---

### Post by Oedipe on 2012-07-25
Hi,

Same here, since yesterday, without doing anything special... I really don'like that hided /.rpmdb directory at the top of my system, full rooted. Never saw such thing on a Linux system ! Never ! I'm very suspicious about that.

---

### Post by Rytron on 2012-10-19
I also have a .rpmdb directory. It is owned by root. Can I safely delete it?

---

### Post by Ms. Daisy on 2012-10-20
This explains what it is:

[http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/](http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/)

So if you don't use the redhat package manager then you can remove it.

---

### Post by Rytron on 2012-10-21
> **Ms. Daisy said:**
> This explains what it is:

[http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/](http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/)

So if you don't use the redhat package manager then you can remove it.

Cheers Ms. Daisy.

---

### Post by Hackie2 on 2012-10-21
> **Ms. Daisy said:**
> This explains what it is:

[http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/](http://useranswer.com/answer/unknown-folder-on-system-root-rpmdb/)

But it doesn't explain why it's /.rpmdb instead of /var/lib/rpm.

Btw: on an ubuntu system, you usually find out the owner of a directory or file by using dpkg -S /.rpmdb which is not the case for this directory.

---

### Post by Rytron on 2012-10-21
> **Hackie2 said:**
> But it doesn't explain why it's /.rpmdb instead of /var/lib/rpm.

Btw: on an ubuntu system, you usually find out the owner of a directory or file by using dpkg -S /.rpmdb which is not the case for this directory.

Are you sure **dpkg -S** is correct?

---

### Post by Hackie2 on 2012-10-22
> **Rytron said:**
> Are you sure **dpkg -S** is correct?
Try this:

dpkg -S /var/lib/vim/
vim-common: /var/lib/vim

It doesn't always work; the directory or a contained file has to be listed in /var/lib/dpkg/info/<package>.list. But it is a good indicator that one of the named packages is responsible for it and also will clean it if not used anymore.

---


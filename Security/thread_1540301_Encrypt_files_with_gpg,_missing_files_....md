---
title: "Encrypt files with gpg, missing files ..."
date: 2010-07-27
forum: Security
---

### Post by joseba on 2010-07-27
Hi, I have this system to backup my data:

/home/user/documents     <-- My Documents to backup

/home/user/backup        <-- Here Documents to encrypt to rsync to a remote server

1.- Sync:

*$ rsync -avu /home/user/documents /home/user/backup*

2.- Encrypt and delete original files to the 3.- step:

*find /home/user/backup/* ! -iname '.gpg' -type f -exec gpg -e --batch --yes --recipient "My key User" '{}' \; -exec rm -f '{}' \;*

to encrypt all my dir documents (with subdirs)

The problem is:

*$ find /home/user/documents/ | wc -l*
2952

*$ find /home/user/backup/ | wc -l*
2930

2952 - 2930 = 22 missing files on the backuped files

I know, empty files dont be encrypted but:

*$ find /home/user/documents/ -empty | wc -l*
6

And /home/user/documents dont have any *.gpg file


Any idea about this?

Thx
Juanjo A.

---

### Post by oldos2er on 2010-07-27
Are you sure the directory isn't called /home/user/Documents ?

---

### Post by joseba on 2010-07-28
Sorry, the problem was the step 1-

The firs rsync not run propoerly, and this cause the missing files to the next steps.

Thx
Juanjo A.

---


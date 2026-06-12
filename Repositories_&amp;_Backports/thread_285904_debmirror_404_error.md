---
title: "debmirror 404 error"
date: 2006-10-27
forum: Repositories &amp; Backports
---

### Post by hogman23 on 2006-10-27
I am getting errors trying to download my mirror, here is the command and the output I am getting.  There are obviously two seperate problems here, one with the keys and one with the 404 errors.  What is going on?????


#/usr/bin/debmirror --verbose --ignore-small-errors --getcontents  --host us.archive.ubuntu.com --method http --root=ubuntu --dist dapper,dapper-backports,dapper-updates --section main,restricted,universe,multiverse  --ignore-missing-release /mirrors/ubuntu | /usr/bin/logger -t debmirror 2>&1

gpg: Signature made Wed 31 May 2006 02:02:10 PM CDT using DSA key ID 437D05B5
gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
gpg: Signature made Tue 17 Oct 2006 09:22:35 PM CDT using DSA key ID 437D05B5
gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
gpg: Signature made Tue 24 Oct 2006 07:31:03 AM CDT using DSA key ID 437D05B5
gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
dists/dapper-backports/Contents-i386.gz failed 404 Not Found
dists/dapper-updates/Contents-i386.gz failed 404 Not Found

---

### Post by bb002 on 2006-12-07
Your 404 errors are because you are using "us.archive.ubuntu.com" drop the us and use "archive.ubuntu.com". In hoary I could use the us mirror just fine. but I've had to use the plain archive.ubuntu.com for breezy and dapper.


> gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg: There is no indication that the signature belongs to the owner.
I dunno what to do about that, I've got the same problem. It is really annoying. Hopefully reviving this thread we'll get some help ;)


[edit]
Oops....missed the slash to terminate my quote tag...

---

### Post by bb002 on 2006-12-08
GOT IT!!!

First off open a terminal window.
Run this to import the key: ```
gpg --keyserver subkeys.pgp.net --recv 437D05B5
```
This next part probably isn't the recommended method but it works.
```
gpg --edit-key 437D05B5
```
Now you will be at a prompt. Type "trust" and press enter.
A list of numbers with words next to them are printed. pick "5 = I trust ultimately" and press enter. You will be asked if you are sure you want to ultimately trust this key. type "y" and press enter. To complete the process, type "quit" and press enter. Choosing 1-4 will not prompt you to change but the gpg warning will persist.

PS: Seems not all man pages are evil....:mrgreen:

---

### Post by carlxs99 on 2008-07-30
worked, thanks!

---


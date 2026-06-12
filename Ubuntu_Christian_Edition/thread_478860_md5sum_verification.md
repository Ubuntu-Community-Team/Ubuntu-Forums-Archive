---
title: "md5sum verification"
date: 2007-06-19
forum: Ubuntu Christian Edition
---

### Post by bumpkin on 2007-06-19
I just received an CD of Ununtu Christian Edition V3.2 and while checking the MD5sums it gave some errors. 

I went to the download page and looked at the hash for version 3.2 and see 

a06b429d21ffaf85aa7c7a8ccfd350ef  Ubuntu_7.04_i386_Christian_Edition_v3_2.iso

Yet on my cd I have a file of about 50 to 100 md5sum hashes (I believe that is what they are called) none are for the iso image. 

How can I use the Ubuntu_7.04_i386_Christian_Edition_v3_2.iso from the website to verify the CD?ubuntu christian edition

UPDATE:

Found the answer on the web.  For those interested. Here is how. The following command will generate an md5sum for the entire CD and write it to the file cdrom.md5. I compared it to the on on the Ubuntu CE website  and they match. Hope this is useful for someone else. 

$ md5sum /dev/cdrom > /tmp/cdrom.md5

---

### Post by Drakkor on 2007-06-19
I saw the iso image of the virgin mary on a ham sandwich ;)
uh,oh, flames coming,lol

---


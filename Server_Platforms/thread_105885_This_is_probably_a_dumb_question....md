---
title: "This is probably a dumb question..."
date: 2005-12-19
forum: Server Platforms
---

### Post by mattskr on 2005-12-19
Ok, got my SSH, FTP, Samba all up and running, now I am in the process of copying my files from my desktop and my two laptops to my new Ubuntu server. I am using SFTP on WS_FTP Pro 8.0 to do this. Now, when everything is copied over, I check the properties on both sides to make sure everything matches, and it never does. Same amount of files but the total file size is always a little bit off. Well not wanting to delete the original stuff until I figure this out but after looking through the directories and comparing side-by-side I figured out it's .txt files and .htm/.html files that are always a little bit less in size on the ext3 filesystem. Upon opening the files they seem to be the same. so my question is this: Is this normal? And what causes it to do this?

---

### Post by LordHunter317 on 2005-12-19
You're probably comparing the size on disk (i.e., number of blocks it occupies), not the size of the actual file.

---

### Post by mattskr on 2005-12-19
No, it's the size of the file. I believe it might have to do with the way that it's sent over. You know the binary, auto, and text modes of most file transfer software. When I force everything to transfer as binary I do not have different file sizes, but what difference does it make? should I not force binary or does it matter?

---

### Post by noigeaR on 2005-12-19
comparing sha1 or md5 sums for the files would be a bit more reliable to see if they are the same than simply comparing the size.

(use the sha1sum or md5sum command from a terminal)

---

### Post by LordHunter317 on 2005-12-19
Oh, the difference you're seeing is due to the newlines being different on different platforms.

---

### Post by mattskr on 2005-12-19
How would I do an md5 hash in windows? or even better...how do I do an md5sum of an entire directory in Ubuntu? I don't want to get an md5 for all 40000 of my files!

---

### Post by noigeaR on 2005-12-19
md5sum of an entire directory in ubuntu works like this
```
md5sum * > checksums
```
this writes the checksums for all files in the current directory into a newly created textfile with the name checksums. to check the copied files against the checksum list use the following command
```
md5sum -c checksums
```
there's a md5sum version for windows which probably works the same way as the linux version. you can download it from one of the links at the bottom of this page [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

---


---
title: "Will a type of compression do what I'm asking?"
date: 2012-03-26
forum: Ubuntu One (CLOSED)
---

### Post by irishetalon007 on 2012-03-26
I'm using box.com with an account that is limited to 100 MB files on the cloud.

I have the box.com drive mounted in my Ubuntu OS.

I compressed my files into a RAR archive split into 100 MB files. I uploaded them and that worked fine. However, when I try to query the archive to get its file list, I watch the resource monitor and it downloads the equivalent size of the entire collective archive before it will display the file list.

What I'd like to be able to do is query the archive for its file list with as little bandwidth as possible, and hopefully download individual files from the archive without necessitating the download of the entire collective archive, only downloading about the exact amount of data that I'm trying to extract from the archive.

Is this possible??

Also, this is far less important, but it would be nice to be able to add files to that archive and have it automatically end and begin another part of the archive when each part reaches 100 MB in-place in the mounted web drive. This way I can upload (potentially large) files into the existing archive, and have all my files in a single archive directory.

(I know this doesn't have to do with Ubuntu One, but cloud storage is cloud storage, right?)

---

### Post by LewisTM on 2012-03-27
AFAIK to query a RAR file list you have to read through the entire archive or archive set. Even worse, to uncompress a single file you have to uncompress the lot. This is because all files are fused into one big 'blob' that then gets compressed as a single entity, leading to better compression ratio at the expense of practicality.
RAR is best used for single 'Extract all' operations. Adding and extracting single files can be a pain, especially over a slow cloud connection. 
Zip might work better, the file list is typically located in the last file split, which ends with .zip

Cheers!

---

### Post by irishetalon007 on 2012-03-27
Thanks for the info on zip files!

However, the Archive manager in Ubuntu cannot split zip files into multiple parts. Is there a way to do this, or another kind of compression that will behave in this manner?

---

### Post by LewisTM on 2012-03-27
[Peazip]("http://www.peazip.org/download-linux-gtk2-deb.html") will do the job for you.
Ubuntu's archive manager (file-roller) can read and extract those archive sets.

---


---
title: "7zip or Rar for ubuntu"
date: 2009-02-20
forum: Server Platforms
---

### Post by misheck on 2009-02-20
I have movie files on my Ubuntu server 64bit which are zipped. I have tried installing 7zip from the applications and add/remove but I cannot find it when I look for an application to open my files. Is there any alternative I can use to open zipped files.

The files I need to open are Divx or some sort of d.. video files and I am also looking for software for ubuntu that I can use to burn the files directly to DVD so they can play in my dvd player or a ps3 at least.

---

### Post by fuzzyk.k on 2009-02-20
try xarchiver and install unrar from the repos

---

### Post by howefield on 2009-02-20
Add the medibuntu repository to your sources.list

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then in the terminal, type the following command to add the ability to file-roller to deal with these file types.

```
sudo apt-get install lzma unrar rar p7zip p7zip-full p7zip-rar
```

You might find that you already have some of the above installed.

Double clicking your file will load it up in file-roller, or if you have a multi part set of rar files, right click and extract.

DeVeDe is very good for converting video to DVD format.

---

### Post by misheck on 2009-02-20
Thanks you, I will try that out.

---


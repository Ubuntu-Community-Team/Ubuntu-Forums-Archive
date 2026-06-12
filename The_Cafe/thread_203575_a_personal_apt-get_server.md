---
title: "a personal apt-get server?"
date: 2006-06-25
forum: The Cafe
---

### Post by freemanen on 2006-06-25
If you want to set up a apt-get server. What do you need to do. Is there any howto for what?

---

### Post by rai4shu2 on 2006-06-25
Here's a page that shows you how to build a local repo:

[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

---

### Post by freemanen on 2006-06-28
I get this error after following the guide. That could i be missing?
Misslyckades att hämta [http://193.10.194.16/binary/Packages.gz](http://193.10.194.16/binary/Packages.gz)  404 Not Found
Misslyckades att hämta [http://193.10.194.16/source/Sources.gz](http://193.10.194.16/source/Sources.gz)  404 Not Found

---

### Post by professor_chaos on 2006-06-28
If your trying to create a repo server, then you need to generate a Packages.gz file using the last command listed below. Google Debian Package Building for more info.

#create deb
dpkg-deb --build "directoryyouwanttobuild"

#update Package.gz
sudo dpkg-scanpackages ./ yourdebfile.deb | gzip -9c > Packages.gz

---

### Post by freemanen on 2006-06-28
sudo sh scan.sh
sudo dpkg-scanpackages ./ lmms_0.1.2-1_i386.deb | gzip -9c > Packages.gz
 ** Packages in archive but missing from override file: **
  lmms

 Wrote 1 entries to output Packages file.


I can't understand what this means?

---

### Post by professor_chaos on 2006-06-28
The result of that should be a Packages.gz file. Upload that file with the lmms deb file to your server. Then sudo apt-get update, sudo apt-get install lmms_0.1.2-1_i386.deb

The package file should contain the index to all of the deb files you have on your repo. So make sure you generate it using all of the debs you plan to upload to one directory. If lmms is the only package, then your ok.

---


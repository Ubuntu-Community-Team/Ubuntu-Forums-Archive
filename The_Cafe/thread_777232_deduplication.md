---
title: "deduplication"
date: 2008-05-01
forum: The Cafe
---

### Post by Daveski on 2008-05-01
There seems to be a lot of noise made about 'de-duplication' technology especially for backups / storage. This means that duplicate files (or files which share large areas of duplicated data) are only stored once, and the duplicates are essentially linked to the original block of data. Saves space and time - nice.

I am SURE that there must be an open-source project out there which I can use to take advantage of this technology in my archives. I have some large directory structures where there are many copies of the same (or similar) bits of data stored in different subdirectories. Tar / Compress works to a degree, but if I could essentially dedupe the stream while the Tar was being created I think I could save quite a lot of space.

Does anyone know of such a project or application?

Thanks.

---

### Post by saulgoode on 2008-05-01
[www.ext3cow.com/]("http://www.ext3cow.com/")

---

### Post by Daveski on 2008-05-01
Wow - that is jolly interesting.

However, this might solve some of the problems of backup and archiving, but my immediate requirement is to take data which is out of my control, and store copies for potential use some time in the future. I need to minimise the space required as the whole structure being archived borders on massive. I notice that many of the data files are duplicated, or have only tiny modifications. Compressing the Tar does help, but I think deduplicating this data before compressing what is left should help me keep the storeage requirements under control. 

Any ideas?

Thanks

---

### Post by nihilist514 on 2009-04-29
this one looks promising

[http://gotitsolutions.org/2007/01/15/open-source-backup-and-data-de-duplication-virtual-appliance-2.html](http://gotitsolutions.org/2007/01/15/open-source-backup-and-data-de-duplication-virtual-appliance-2.html)

can be downloaded here
[http://backuppc.sourceforge.net/index.html](http://backuppc.sourceforge.net/index.html)

---

### Post by Daveski on 2009-11-03
Quick note to anyone interested: I have been playing with lessfs, and this might be exactly the sort of thing I need. I certainly think this is an interesting project:

[http://www.lessfs.com](http://www.lessfs.com)

---

### Post by schauerlich on 2009-11-03
There's ZFS, too.

---

### Post by Bubbel on 2010-01-18
**Update:** I Created a new forum thread here: [http://ubuntuforums.org/showthread.php?p=8721344]("http://ubuntuforums.org/showthread.php?p=8721344")
That one will stay current. Please put all comments there.

Hi,

I am now busy installing LessFS. Here are my steps. (ran from a Terminal Window)
[LIST]
Get the prerequisites: ```
sudo apt-get install build-essential libselinux1-dev libsepol1-dev pkg-config 
```
[/LIST][LIST]
Get Fuse 2.8.1: download from [http://code.google.com/p/s3ql/downloads/list]("http://code.google.com/p/s3ql/downloads/list") the three FUSE packages
[/LIST][LIST]
Install them like this: ```
sudo dpkg -i *.deb
``` assuming the FUSE files are in the same folder as the shell is.
[/LIST][LIST]
Download & Extract LessFS: Download .tar.gz package from [http://sourceforge.net/projects/lessfs/files/]("http://sourceforge.net/projects/lessfs/files/"). Extract like ```
tar xzf *.tar.gz
```
[/LIST][LIST]
cd into lessfs folder and run ```
./configure
``` This gives a lot of text. Check for errors.
[/LIST][LIST]
Run ```
make && sudo make install
```
[/LIST]
You are done installing. Now configuring...

This is just quick-and-dirty install. Now I'm getting into configuring...

---


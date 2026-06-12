---
title: "gtkpod (ver. 0.99.0)"
date: 2005-12-13
forum: Requests
---

### Post by dexae on 2005-12-13
**About this version**
gtkpod ([http://www.gtkpod.org]("http://www.gtkpod.org")) is a platform independent GUI for Apple's iPod using GTK2. It allows you to import your existing iTunes database, to add songs, podcasts, video and cover art and to edit ID3 tags. gtkpod also features international charset support for ID3 tags, detects when adding already existing songs, and more.

The main new features are podcast, video and cover art support, type-ahead search functionality, better handling of compilation CDs. An 'Edit Details' dialog now allows easy editing of all track data including cover art.

New scripts are available to sync contacts from a Palm, ldif addressbooks, and notes from KNotes.

Many bugs have been fixed as well. Have a look at the changelog ([http://www.gtkpod.org/news.html)]("http://www.gtkpod.org/news.html%29").

---

### Post by 23meg on 2005-12-13
It's a major update, lots of bugfixes but it hasn't hit Dapper yet.

---

### Post by samir85 on 2005-12-13
is there already some debian package out there ?

---

### Post by dell500 on 2005-12-19
Is there a version out for Breezy?  0.94 is kinda buggy and I'm not sure how to install 0.99.2.

---

### Post by BeeRockxs on 2006-01-02
Dapper now has 0.99.2, can we please get it backported?

---

### Post by Manny C on 2006-01-03
In the absence of it being in backport, do the following:
[LIST=1]
[*]Grab the rpm [here]("http://dag.wieers.com/packages/gtkpod/").   
[*]Install alien: ```
sudo apt-get install alien
```   
[*]Convert the rpm into a *.deb: ```
sudo alien gtkpod-0.99.2-1.1.fc3.rf.i386.rpm
```   
[*]Install the generated deb package ```
sudo dpkg -i gtkpod_0.99.2-2.1_i386.deb
```   
[*]Run gtkpod. [/LIST] There you go.

---

### Post by Kevin on 2006-01-04
You also need libgpod installed for the newer gtkpod versions to run.

This can be installed using the same process from here:
[http://dag.wieers.com/packages/libgpod/]("http://dag.wieers.com/packages/libgpod/")

Also you need to make sure you have libmp4v2-0 installed.

---

### Post by livewyer on 2006-01-04
There's a package available now.  As root: apt-get install gtkpod.  

However, it's not quite working for me.  See my post here: [http://www.ubuntuforums.org/showthread.php?t=111416&highlight=gtkpod](http://www.ubuntuforums.org/showthread.php?t=111416&highlight=gtkpod)

---

### Post by Manny C on 2006-01-09
Yes, you alse need to install libgpod.

---

### Post by bestiarosa on 2006-05-01
> New scripts are available to sync contacts from a Palm, ldif addressbooks, and notes from KNotes.

Where do I find those scripts?

---


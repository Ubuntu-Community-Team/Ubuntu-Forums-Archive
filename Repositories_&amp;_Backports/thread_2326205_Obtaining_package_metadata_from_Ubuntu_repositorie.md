---
title: "Obtaining package metadata from Ubuntu repositories"
date: 2016-05-29
forum: Repositories &amp; Backports
---

### Post by petersfreeman2 on 2016-05-29
I have written a bash script that allows me to install deb packages from the Ubuntu repositories for a large number users whom I support.  I have set up a database with fields that store the attributes of a package and which user requires this package (along with other control fields).  The important fields are package name; description; and various user names.  A typical (simplified) CSV type record would be:

Field Names:Area,Category,Sub-Category,License,Package,Description,fred,tom,harry,susan,sandi
Record Data:Applications,Games,Arcade Games,Open Source,chromium-bsu,Space Aliens Arcade Game,y,y,y,n,n

I have been building this database by hand and it is tedious.  What I would like is some way to obtain the metadata that must be stored in the repositories.  I want to know the categories and sub categories that show in the Ubuntu Software Centre, the friendly name of the package, the package name (it used to be in the old Software Centre but is missing in the new 16.04 Software Centre) and the description.  For example, I want to extract from the repositories this information for a typical package:

Category: Audio
Sub-Category: Recorders
License: Open Source
Friendly Name: RecordMyDesktop
Package Name: gtk-recordmydesktop
Description: Adds an easy to use graphical icon on the GNOME toolbar to make screencasts with the video and audio capture application recordMyDesktop

I know that both Synaptic Package Manager and the Ubuntu Software Centre can extract such info and it is must be from the same source as the package description appears to be consistant

How do I do this?

Thanks!


[IMG]http://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAIAAACQd1PeAAAADElEQVR4nGP5dvoHAAWEAr7DS8p7AAAAAElFTkSuQmCC[/IMG]

---

### Post by oldfred on 2016-05-29
I know how to list some of that from installed apps.
 [http://superuser.com/questions/585304/how-to-retrieve-a-list-of-installed-packages-on-kubuntu-sorted-by-category](http://superuser.com/questions/585304/how-to-retrieve-a-list-of-installed-packages-on-kubuntu-sorted-by-category)
dpkg-query -Wf='${package}\t${Section}\t${status}\n' | grep installed | 
  gawk '{print $2"\t"$1}' | sort 
Also how to list applications you installed.
[http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages)
With compare
[https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages](https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages) 



 [http://askubuntu.com/questions/651123/how-to-generate-a-list-of-categorized-list-of-applications?noredirect=1#comment935144_651123](http://askubuntu.com/questions/651123/how-to-generate-a-list-of-categorized-list-of-applications?noredirect=1#comment935144_651123)
Application to show apps by category
sudo apt-get install alacarte

---


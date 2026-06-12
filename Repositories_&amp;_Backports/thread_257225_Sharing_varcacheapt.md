---
title: "Sharing /var/cache/apt??"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by mvdw on 2006-09-14
Hi all:

I don't want to keep downloading the same .deb files for all my machines, so can I safely share /var/cache/apt between machines? Is there any extra metadata in there that will break things if I try this? Alternatively, is there a better way, short of creating a full-blown mirror - I don't have the bandwidth for that!

Cheers,
mvdw

---

### Post by grimmson on 2006-09-14
In Fedora I just burnt a disk of the dir. copied files the the other computer, yum "varified" the copies by going on line and installed them very quickly. Might try it and cancle if quick and dirty doesn't work.

---

### Post by Matchless on 2006-09-15
I have beeen doing this for a long time. I copy all my .deb files in the cache to a folder called Repos and then just create a new Packages.gz. You can put this on a cd and let synaptic see the CD or you can create a file repository and use synaptic, adept, apt-get etc to read from this in the sources.list (  cd to your folder and run dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz)

---

### Post by bonjun on 2006-09-16
this is what i do when upgrading, i download the ISO then
> sudo mount -t iso9660 ubuntu-6.06.1-alternate-i386.iso /cdrom -o loop
sudo apt-cdrom -m add
sudo apt-get update

but i have not done this, maybe you could try....
> make an ISO of all file/packages, then mount the iso in /cdrom then apt-cdrom -m add and update

wish you luck, i'll also try this...


---
edited: i found these things in wiki

[https://help.ubuntu.com/community/LocalAptGetRepository]("https://help.ubuntu.com/community/LocalAptGetRepository")

[https://help.ubuntu.com/community/LocalAptGetRepositoriesTrivial]("https://help.ubuntu.com/community/LocalAptGetRepositoriesTrivial")

---


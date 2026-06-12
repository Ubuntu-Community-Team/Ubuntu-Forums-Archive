---
title: "problems using my own repository"
date: 2006-10-20
forum: Repositories &amp; Backports
---

### Post by rpm13 on 2006-10-20
I recently setup dapper on my desktop.
I want to install the same stuff (more or less) on my laptop and perhaps a few other machines.
I thought it would be more sensible to  make the files in /var/cache/apt/archives/ into my own little repository rather than waste all that time and bandwidth doing the same downloads.

So followed the instructions in [https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto) to make my own cd.

But now I get the following error (both in synaptic and in apt-get)

[FONT="Fixedsys"]Failed to fetch cdrom:[Ubuntu-updates 2006-10-18]/dists/dapper/Release Unable to find expected entry main/binary-i386/Packages in Meta-index file (malformed Release file?)
[/FONT]
However if I do look at dists/dapper/Release there is at line 9:
[FONT="Courier New"]MD5Sum:
 9ec41984f9b0bc23386f6ff170630fb2  145406 main/binary-i386/Packages.gz[/FONT]

Is the .gz the problem? How do I solve it?

---

### Post by mcneely.mike on 2006-10-26
The one problem i can see is where it says something like below:

apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/dapper/main/binary-i386/Packages.gz

at the end of apt-ftp...../main/ \
     there is the back-slash   \
   this is meant to mean that the next line starting with 
      "| gzip..." is not really a new line but a continuation of the same line but it wouldn't fit on the one line in the author's typing.

In other words, just omit the "\" and just keep typing:

apt-ftparchive packages pool/main/ | gzip -9c > dists...etc

all as one command and one line.

you can also omit any of the references to gpg and it will work but without the gpg key protection (it is after all a local cdrom and should be trustable.

hope this helps.

---

### Post by rpm13 on 2006-10-27
Thanks.
Actually I did just that (typed without the \ and the newline)
and not what exactly as is suggested.
Anyhow...
What seems to work is that the directory main/binary-1386/ should contain all three -- Packages, Packages.gz and Packages.bz2.

God alone knows why!  But thats what it seems to want! I wish someone who knew apt better would explain why?!

Thanks anyway

---


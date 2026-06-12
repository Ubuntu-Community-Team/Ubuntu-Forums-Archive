---
title: "repositories are back...but"
date: 2005-09-25
forum: Repositories &amp; Backports
---

### Post by jamesford on 2005-09-25
they are back

but with my experience from windows, when something like this happens it could be bad news, like a hijacking.

would be nice with some kind of official confirmation on qwhat happened and that they can safely be used now

im just a bit paranoid

---

### Post by Muhammad on 2005-09-25
Did you edit the sources.list? Because they're still not working for me. :(

---

### Post by jamesford on 2005-09-25
no i didnt edit anything, they suddenly just worked again, all of them as far as i can tell. but im talking breezy though

---

### Post by Muhammad on 2005-09-25
I'm using breezy too, but they're still not working... :(

---

### Post by jamesford on 2005-09-25
thats odd....

my sources.list:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb http://no.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://no.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
## Backports hoary
#deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
```

---


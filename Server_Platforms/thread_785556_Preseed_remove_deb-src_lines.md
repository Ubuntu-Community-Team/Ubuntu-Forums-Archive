---
title: "Preseed remove deb-src lines"
date: 2008-05-07
forum: Server Platforms
---

### Post by code0 on 2008-05-07
For some reason, I can't seem to figure out how to prevent the installer from adding deb-src lines to sources.list. I'm running a local mirror of all packages except for the source debs, and don't mirror package sources.

I tried it in the style listed in the preseed examples for local repositories, but I can't seem to get it to work for the "standard" repositories.

Here is my preseed file:
```

d-i	mirror/country				string enter information manually
d-i	mirror/http/hostname			string galactica
d-i	mirror/http/directory			string /ubuntu 
d-i	mirror/suite				string hardy
d-i	mirror/http/proxy			string

d-i	clock-setup/utc				boolean true

d-i	time/zone				string US/Central

d-i	apt-setup/local0/repository		string http://galactica/myrepo infosvc all
d-i	debian-installer/allow_unauthenticated	string true

d-i	apt-setup/restricted			boolean true
d-i	apt-setup/universe			boolean true
d-i	apt-setup/multiverse			boolean true

d-i	apt-setup/main/source			boolean false
d-i	apt-setup/restricted/source		boolean false
d-i	apt-setup/universe/source		boolean false
d-i	apt-setup/multiverse/source		boolean false

d-i	passwd/root-login			boolean true
d-i	passwd/make-user			boolean false
d-i	grub-installer/only_debian		boolean true
d-i	pkgsel/include				string openssh-server build-essential
d-i	finish-install/reboot_in_progress	note
d-i	cdrom-detect/eject			boolean false

ssh	ssh/new_config				boolean true
ssh	ssh/protocol2_only			boolean true
ssh	ssh/run_sshd				boolean true

```

---

### Post by songshu on 2008-05-07
just a wild guess,

but did you try this?
d-i apt-setup/local0/source boolean true

edit, that would be false offcourse ;)

d-i apt-setup/local0/source boolean false

---

### Post by code0 on 2008-05-07
I don't think so. The "local0" is the same name you use when adding a local repo (which works and does NOT add the deb-src). I'm looking at preventing the installer from adding deb-src entries for the main, universe, multiverse, and restricted repos.

---

### Post by songshu on 2008-05-07
maybe a different approach would also work in your case

i'm using a custom preseed files as well with the ubuntu and medibuntu + a local mirror for a few packages and did not notice the issue untill i saw your post


i use apt-cacher and reprepro, when i've set up reprepro i noticed it had set up a source archive as well altough i do not use it.

i guess your problem is that apt is trying to hit repo's that are not there

ugly solution
create an empty source archive on your mirror?

---

### Post by koenn on 2008-05-07
> **code0 said:**
> For some reason, I can't seem to figure out how to prevent the installer from adding deb-src lines to sources.list. 
I don't know of any preseed option that would do that - I assume it's hard-coded in the installer, possibly to easily satisfy the (GPL) requirement that a distributor must provide (means of access to) source code for distributed binaries. 

A workaround could be to run a "late command" from your preseed, with something that removes deb-src lines. Maybe
```
sed -i ^deb-src/d /etc/apt/sou...
```
Im not sure whether that would have to run against /etc/... on your hard disk  or against /target/... but I'm sure you can figure that out (from a preseed howto)

---

### Post by theparadigm on 2013-02-22
This is what I use:
```
sed -i '/^deb-src/s/^/#/' /etc/apt/sources*
```

Hope someone else finds it useful.
Cheers,
D

---


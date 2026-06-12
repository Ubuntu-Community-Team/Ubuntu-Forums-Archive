---
title: "creating a local repository"
date: 2006-10-04
forum: Repositories &amp; Backports
---

### Post by ArneLovius on 2006-10-04
Hi, 

I've been trying for a few days now to create a local copy of the dapper repository to enable [COLOR="Red"]installs[/COLOR] to use this local copy rather than connecting over the internet.

I can't use a CD/DVD to do the install as the machines don't have one.

I've used debmirror with both http 

> sudo debmirror -p -v --nosource --host=us.archive.ubuntu.com --method=http --root=ubuntu --dist=dapper,dapper-updates,dapper-security --section=main,restricted  /usr/local/repos

and rsync

> sudo debmirror -nosource -m -passive -host=us.archive.ubuntu.com -root=:ubuntu/ -method=rsync -progress -dist=dapper,dapper-updates,dapper-security  -section=main,restricted /usr/local/repos

and apt-mirror

am-mirror.list =
> set base_path /usr/local/repos
set skel_path $base_path/skel
set var_path $base_path/var
set mirror_path $base_path
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main/debian-installer
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted/debian-installer

> sudo apt-mirror /etc/apt/am-mirror.list

I haven't seen any error messages about missing files when using any of the above three methods

As far as I can tell, any of the above should create a copy that I can install from, but whichever method I use to create the repository, it fails to find binutils-static-udeb_2.16.1cvs20060117-1ubuntu2.1_i386.udeb and on checking > sudo find / grep binutils-static-udeb_2.16.1cvs20060117-1ubuntu2.1_i386.udeb the file has not been downloaded.

I can however see the file on us.archive.ubuntu.com. 

I'm guessing that both debmirror and apt-mirror use the contents of various files to determine which files to download, and these files don't have the correct files listed in them.

I'd appreciate any assistance that can be provided on this before I go completely mad....

Cheers

Arne

---

### Post by brodie-bruce on 2007-04-10
i ran into the same problem. i believe the solution turns out to be making sure you have both "dapper-security" in the dists option and "main/debian-installer" in the section option. as of this post, you also need "restricted/debian-installer" in the section option. you also can't have "dapper-backports" in the dists option because it doesn't have a "restricted/debian-installer" section.

in your case, you were missing "main/debian-installer" in the debmirror tries and missing "dapper-security" in the apt-mirror try. you may have figured this out by now.

at any rate, the general issue is that it appears the installer possibly gets some updated files from the internet (if available) instead of from the mirror. there are some bugs posted on launchpad for the debian-installer package if you filter for [netboot]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/?field.searchtext=netboot&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") that mention this.

hopefully, this information might help someone as i wasted a bit of time on this.

---


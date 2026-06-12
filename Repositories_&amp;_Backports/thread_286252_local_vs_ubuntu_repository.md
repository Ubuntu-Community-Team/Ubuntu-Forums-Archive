---
title: "local vs ubuntu repository"
date: 2006-10-27
forum: Repositories &amp; Backports
---

### Post by HIV on 2006-10-27
Hello everyone,

I recently made my transition from windows, having now 2 workstations running ubuntu 6.10 at home.

To avoid any bandwidth waste, I set up a local repository with 3 folders, so my old laptop won't take forever while generating Packages.gz. 

I edited /etc/apt/sources.list and added:
deb file:/media/repository/a ./
deb file:/media/repository/b ./
deb file:/media/repository/c ./

(in case you're asking why /media/repository : It's actually a smb mount as the files reside in a windows desktop my laptop has a scarce 10gb drive)

When I try to install a package all goes well, as long as I don't have any external repositories in the /etc/apt/sources.list.

The problem is, when I add the standard ubuntu repos, apt-get/synaptic will always download and install from Ubuntu online repositories, even when the required packages exist locally.

I searched online and found some references to "pinning" but I don't know how to prioritize the repositories to fix my needs.

Any help would me more than welcome.

Thank you.

---

### Post by MrBlond83 on 2006-10-27
In Synaptic you can "Force Version" to tell it which version to install for a certain package. It will give you options to choose from, taken from the versions available on your repositories.

This however would need you to Force Version on every package you installed locally...

To my understanding, if you make apt think that the version that you have installed is newer than the version available in the official repositories, it wouldn't try to upgrade it. At least, that's how it works for me. Which means all you have to do is give your local packages version numbers that will be higher than the repository ones... So lets say you have version 1.5 installed, and the version in the official repositories is called 1.5-1ubuntu3 or something like that, just change the version of what you have to 1.5-1ubuntu99 or something.

Just pay attention to the version names in the official repositories, because I think Apt would think that "1.5-1ubuntu3" is newer than "1.5-1", for example. But this way you won't have to Force Version, and if the repositories get updates with a higher version number it will suggest the upgrade, but until then your apt will behave.

---

### Post by HIV on 2006-10-27
I don't want to "force versions". What I need is that apt-get would only download the packages that are not in my local repository.

Thanks anyway

---

### Post by az on 2006-10-27
> **HIV said:**
> I don't want to "force versions". What I need is that apt-get would only download the packages that are not in my local repository.

Thanks anyway

I think the issue is the SMB mount.  If it was mounted as NFS, for example, I think it would recognise that as local.  This is a bug in the form of a missing feature in apt, I think.

---


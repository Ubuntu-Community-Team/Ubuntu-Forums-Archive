---
title: "Can one user share a /home/oneuser directory on two computers?"
date: 2009-03-17
forum: Server Platforms
---

### Post by MountainX on 2009-03-17
On my home network I log in to two computers with the same user account. One computer is now a file server and I would like to keep my home partition on it.

I will access that home partition via NFS from computer1 and I will access it locally when on computer2 (the new file server).

What will happen if I login, as the same user, to both computers at the same time? I assume that might be bad if the same home location is used by each user account. Or would it be OK?

Would it be OK if I set it up this way but didn't login at more than one computer at the same time?

---

### Post by MountainX on 2009-03-18
bump

---

### Post by wkulecz on 2009-03-18
I'd expect problems if both systems were logged into as your home directory is filled .application_name subdirectories filled with configuration files.  I doubt any file locking for these are in the applications so corruption could result with two machines trying to update the same file.  But depending whcih apps you run, it might mostly work.


If you restrict to only being logged into one machine at a time everything should work but...

There is a new thing with 8.04 (at least new since 6.06) the .gvfs special sub-directory in your home directory which is "Gnome Virtual File System".  I've no idea if this thing would crash and burn over nfs or not.  But rsync chokes on it, I suspect nfs would too as it is a "mount point" shown in the df command output.

The simplest thing might be to back up your home directory and then just try it.

--wally.

---

### Post by MountainX on 2009-03-18
Thank you. Your advice agrees with [this post]("http://ubuntuforums.org/showpost.php?p=6712851&postcount=3"), so I think I will not go this route.

---

### Post by HermanAB on 2009-03-18
It should work provided that you ensure that the user and group IDs are the same on both machines and you only log in from one at a time.

Cheers,

Herman

---


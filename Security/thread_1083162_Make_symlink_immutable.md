---
title: "Make symlink immutable"
date: 2009-02-28
forum: Security
---

### Post by bryonak on 2009-02-28
I'd like to create symlinks in some user's folders and make them undeletable/unchangeable, just so I don't have to run around if someone deletes their symlink.
Trying "chattr +i" gives me "chattr: Operation not supported while reading flags on ..." or it changes the attribute of the target (which is how it should work when you think about it).
chmod doesn't help either.

In [this mail archive]("http://oss.sgi.com/archives/xfs/2006-08/msg00521.html"), Nathan Scott claims that it isn't possible to protect symlinks, but others make some vague points.

Still, anyone knows a good way to accomplish this?

---

### Post by bodhi.zazen on 2009-02-28
I do not know about links or why you would want to do this exactly, but you can use mount --bind

Say you want to link /data to /home/user/data

But let us use bind instead :

```
sudo mkdir /home/user/data
sudo mount --bind /data /home/user/data
```

so long as you do not put that in fstab, the user will not be able to unmount the bind

So, to make it active on boot , add this to /etc/rc.local :

```
mount --bind /data /home/user/data
```

---

### Post by jdong on 2009-03-01
Bodhi's method is probably the easiest way to create a catch-22 for users trying to remove/delete something in their directory. Remember that delete/move permissions are assigned to the parent directories, and symlinks are special entities in filesystems that typically do not have file status. If you are not happy with its granularity, I suggest looking into a dynamic FUSE filesystem proxy such as bindfs and modifying it to do what you need.

---

### Post by bryonak on 2009-03-01
```
mount --bind /data /home/user/data
```

Thanks bodhi, I think I'll use that.

I also had a look at xattr, which is a bit too tacked on for my liking.

> **bodhi.zazen said:**
> I do not know about links or why you would want to do this exactly...

I think the reason I gave in the first line of my OP is valid, isn't it?
Educating users would be another good option, but nevermind ;)


> **jdong said:**
> Remember that delete/move permissions are assigned to the parent directories, and symlinks are special entities in filesystems that typically do not have file status. If you are not happy with its granularity, I suggest looking into a dynamic FUSE filesystem proxy such as bindfs and modifying it to do what you need.

Why can't symlinks be just files whose permissions are changeable but "masked" by the target? (yeah I know, why are there still wars in the world)

Thanks for the tip, I may look into it some time. For now, bodhi's solution tops the cost/benefit list.

---

### Post by jdong on 2009-03-01
That would require symlinks to be represented as inodes instead of "fast symlink objects", amongst other design details.

---


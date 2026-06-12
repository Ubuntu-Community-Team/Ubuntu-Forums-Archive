---
title: "Re: Nautilus no longer provides SMB mount points in ~/.gvfs"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gecka on 2012-03-05
In 12.04 this .gvfs mount point seems to have been removed!

Now I can't use many of my apps with network shares. Eclipse is a good example!

Please add this bug as affecting you so it get solved before the release: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/945399](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/945399)

---

### Post by sffvba[e0rt on 2012-03-05
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by Morbius1 on 2012-03-05
Same thing is happening in Xubuntu 12.04. I almost hate to post this for fear that they will think this is an acceptable work around but:

First I compared the gvfs-fuse package to 11.10 and found that there's a dependency missing: fuse-utils. So I added it. Then I added myself to the fuse group:
```
sudo gpasswd -a user-name fuse
```[COLOR=Blue]Those 2 actions did nothing. [/COLOR]

Then I found a post from 2 years ago and did the following as a regular user:
```
mkdir ~/.gvfs
```Followed by:
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```Now it works. [COLOR=Blue][COLOR=Black]It even changes permissions on the folder to the correct value.[/COLOR] You will have to run the gvfs-fuse daemon command at every reboot.[/COLOR]

I only mention the fuse-utils add and membership change because I don't know if that was integral preliminary steps or not. Try to just create the folder and run the daemon first to see if it is necessary.

---

### Post by bedbug on 2012-03-05
ln -s ~/.cache/gvfs ~/.gvfs

---

### Post by Morbius1 on 2012-03-06
Well, had I not panicked and found the hardest route instead of doing a simple "mount" command where it clearly showed the new mount point I would have saved a lot of time. I sincerely hope that moving it to .cache fixes some bug that I'm not aware of since on the surface it makes no sense placing it in cache. 

Before, the user had to know that there was a hidden directory called .gvfs in his home directory and then he had to make the leap to know that something called ".gvfs" was related to connecting to a remote share. Putting it in .cache makes it more obscure - well, it was obscure to me anyway.

The person responding to the bug report seems unaware that the mount point had changed which suggests that this is something done by our Gnome overlords instead of something that Ubuntu did because they thought it would be funny.

---

### Post by gecka on 2012-03-06
So the mount point is now ~/.cache/gvfs. Thank you. Solved.

---

### Post by CrusaderAD on 2012-03-09
> **gecka said:**
> So the mount point is now ~/.cache/gvfs. Thank you. Solved.

Worked for me, thanks for posting!

---

### Post by Roasted on 2012-03-20
In previous varions of Ubuntu, it was:

/home/user/.gvfs

In the beta of 12.04 I'm running, it's:

/home/user/.cache/gvfs

I exclude gvfs (--exclude=.gvfs) in my rsync command I run at login through Startup Applications. I'm curious if gvfs has found a new home within .cache/gvfs so I can change it come 12.04 installation day. I just wasn't sure if this was because it's beta or if it's an actual permanent change that'll filter to the final release.

Thanks guys!

---

### Post by tekstr1der on 2012-03-20
> **Roasted said:**
> In previous varions of Ubuntu, it was:

/home/user/.gvfs

In the beta of 12.04 I'm running, it's:

/home/user/.cache/gvfs

I exclude gvfs (--exclude=.gvfs) in my rsync command I run at login through Startup Applications. I'm curious if gvfs has found a new home within .cache/gvfs so I can change it come 12.04 installation day. I just wasn't sure if this was because it's beta or if it's an actual permanent change that'll filter to the final release.

Thanks guys!

This issue was discussed here recently in the thread:
[http://ubuntuforums.org/showthread.php?t=1936071&highlight=gvfs+cache](http://ubuntuforums.org/showthread.php?t=1936071&highlight=gvfs+cache)

I never was able to find any info on the decision to move the mount point.

EDIT: Apparently the ~/.gvfs mount point will return soon per comment #7 here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/945399](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/945399)

---

### Post by Roasted on 2012-03-20
> **tekstr1der said:**
> This issue was discussed here recently in the thread:
[http://ubuntuforums.org/showthread.php?t=1936071&highlight=gvfs+cache](http://ubuntuforums.org/showthread.php?t=1936071&highlight=gvfs+cache)

I never was able to find any info on the decision to move the mount point.

EDIT: Apparently the ~/.gvfs mount point will return soon per comment #7 here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/945399](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/945399)

Good find my friend. Thanks for the update! :guitar:

---

### Post by tekstr1der on 2012-03-21
You're welcome. It's fixed now:

> gvfs (1.11.5-1) experimental; urgency=low

  [ Michael Biebl ]
  * Bump Build-Depends on cdbs and debhelper for multiarch support.
  * Replace Depends on fuse-utils with fuse, as fuse-utils is now only a
    transitional package depending on fuse.

  [ Martin Pitt ]
  * debian/watch: Watch for development versions in experimental.
  * New upstream release:
    **- fuse: Keep using ~/.gvfs as fallback (LP: #945399)**
  * Drop 02_deprecated.patch: Fixed upstream.
  * debian/control.in: Bump glib build dependency as per configure.ac.
  * debian/copyright: Move to copyright format 1.0.
  * debian/control.in: Bump Standards-Vesion to 3.9.3.

---

### Post by Morbius1 on 2012-03-21
Now that we all got used to it being in a new location it appears they are going to put it where it used to be:
> [ Martin Pitt ]
  * debian/watch: Watch for development versions in experimental.
  * New upstream release:
    - [COLOR=Blue]**fuse: Keep using ~/.gvfs as fallback**[/COLOR] (LP: [#945399]("https://bugs.launchpad.net/bugs/945399"))
  * Drop 02_deprecated.patch: Fixed upstream.
  * debian/control.in: Bump glib build dependency as per configure.ac.
  * debian/copyright: Move to copyright format 1.0.
  * debian/control.in: Bump Standards-Vesion to 3.9.3.
 -- Martin Pitt <email address hidden>   Wed, 21 Mar 2012 09:24:41 +0100

---

### Post by cariboo on 2012-03-21
Merged two threads on the same topic.

---


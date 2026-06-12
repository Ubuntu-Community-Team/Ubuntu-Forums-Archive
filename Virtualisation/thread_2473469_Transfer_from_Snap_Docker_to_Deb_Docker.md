---
title: "Transfer from Snap Docker to Deb Docker"
date: 2022-04-05
forum: Virtualisation
---

### Post by databoy2k on 2022-04-05
I’m just getting started with Docker. I’m running it on Ubuntu Server 20.04. I didn’t realize that Ubuntu packaged Docker as a snap container or the various issues with Snap. Of course, I have a handful of containers that all have their data mounted in external docker volumes, since permission issues made storing their volumes in /home above my head.

So now I’m leaning towards migrating from snap. I would have expected this to be easy and to have guides everywhere, but shockingly enough there’s virtually nothing out there.

Can anyone lead me down the right path to backing up at least the external volumes, if not the containers with the volumes, in a way that is then restorable once I’ve purged the snap versions from the server and re-installed via apt?

Ideally, I’d like to backup the paths as well (e.g. “namedExtVolume:Container1/config”) so that it’s a one-line (or one line per container) restore.

Any pointers on purging the snap version and getting the apt version? Anyone else tried this migration and knows of the pitfalls or issues?

Huge thanks.

---

### Post by TheFu on 2022-04-05
Snaps and linux containers aren't virtualization. they are constraint techniques for environments. It is a common mistake.

Linux containers, like docker, allow much more local control than snaps.  Snaps provide very little to ZERO local control.
The Ubuntu version of Docker is much more flexible and called LXD.  Sadly, it is distributed as a snap and it nearly demands that the underlying storage used is ZFS.

Snaps are more like flatpaks or AppImages.  Those are the competition for snaps.
Docker's competition is LXD, lxc, runc, rtk, containerd and there must be 20 other "me too" options.  The good news is that docker has won the format war. The bad news is that docker does seem to be as secure as many/most other linux container options.  Of course, you can roll your own container with a good understanding of cnames and cgroups, but there are enough lite options to completely replace any need for docker.

This is why the migration from snap to any container-based solution doesn't really happen.  I suppose Canonical's efforts to make snap packages for their IoSh offers which only support package management via snap (*cough), might be a place to start.  I've avoided snaps whenever any other option exists.  Seems you may have learned that too this week.

As for how to access data that is attached to a snap, each snap will have a specific location where that data is stored.  You'll probably need to hunt down where it is for each snap package.  I'd guess it might be in the manifest for the snap package.  Generally, snap data will be either in the user's $HOME/snap/ directory or somewhere under /var/snap/.

I'm off doing a little reading ... 

Seems that snaps should let you place data on storage either under /mnt/ or /media/. If you want it somewhere else, outside the default location or those 2 places, then you do not want to use snaps.  BTW, not all snap packages allow access to /mnt/ or /media/. That capability is determined by the team that creates the snap package - **snap connect <name of snap>:removable-media** is the command to enable that access. Again, this has to be allowed by the snap package, otherwise, no way.

I don't see any easy way to loop over 50 snaps and backup the data as separate objects/directories. Sorry.

---

### Post by databoy2k on 2022-04-05
Thanks for the thoughts. I had searched for "docker" and found a number of posts in this subforum, so I thought this was the appropriate place to ask.

If a mod could move me to wherever a question about Docker belongs, I'd appreciate it.

I'm not sure that I need to pull the external volume out of the snap as much as I need to use Docker's own tools to pull out the data first. As I said, I had thought that external volumes in docker were kind of like a VHD; I've since been disabused of that notion, but I'm just stuck on whether it's worth my weekend to just rebuild everything that I've done to date so that my docker isn't a snap package.

Really do appreciate your review, though. I've been wondering about the purpose of yet another set of formats (snap, appimages, flatpacks... ugh)

---

### Post by TheFu on 2022-04-05
appimages don't have any constraints, but have the same issues that setup.exe files on that other OS have. No automatic way to update.

flatpaks have constraints, but those can be locally overridden. There are tools to update all the flatpaks on a system. 

snaps have mandated constraints that cannot be overridden, except in specific ways.  snaps update whenever they like. We have little to no control over when.  By default, 3 versions of a snap will be retained. It is not possible to set that to less than 2 versions.  In my use attempts, over 70-80% of snaps refuse to work.  Further, when a snap doesn't provide the amount of constraints that I like, running them inside another constraint system - I like firejail - isn't possible.

I know the least about flatpaks, though they would probably be the best technical choice for these sorts of run-anywhere desktop packages.

All of these run-anywhere solutions have some major drawbacks, especially when it comes to RAM and disk usage.  That effectively double the bloat on a system, when it wouldn't be THAT hard to accomplish the same goals via normal system packages, existing constraint systems, and a few environment variable controls - specifically the LD_LIBRARY_PATH.  

What's the point of your 'code' block. It is confusing without any context.

---

### Post by databoy2k on 2022-04-06
I set that back in the days of signatures in forums. It perfectly encapsulates a noob's experience trying to troubleshoot anything in linux and the advice that we often get.

It also reminds me every time I post to make sure that I don't commit those sins (on the off chance that I'm helping someone weaker in Ubuntu than I).

---

### Post by TheFu on 2022-04-06
```
aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots
``` seems wrong.
```
[COLOR="#FF0000"]/[/COLOR]aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots
```
would be clearer. The leading / matters!

Or use
```
~/aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots
```
if you want to point deep inside someone's $HOME.

And yes, I get that I'm not helping and my reply is making your point. ;)

---


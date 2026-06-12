---
title: "[LXD] lxc copy seems to not understand hardlinks with dir driver"
date: 2023-12-15
forum: Virtualisation
---

### Post by vilo999 on 2023-12-15
Hi,

I have a container on one host node using the dir driver, inside this container rsnapshot is being used to create backups.

I am now migrating this container to another host node, same settings.

However, I&#8217;ve verified in the new rootfs that the incremental backup gets copied over and over again (no hardlinks are copied).

Is this the expected behavior?

How about other system files, can the CT become corrupted if a hard link is expected but instead a plain old file copy is written?

EDIT: this only happens when copying from remote via https, local lxc copy preserves hardlinks.

Thank you

---

### Post by TheFu on 2023-12-15
The official backup method seems to be to create a LXC container backup is to use the **lxc export** and **lxc import** commands.

Alternatively, snaps have a backup command that can be used for all snaps or just 1.
**sudo snap save**

These do not support versioned backups, sadly.

Some reference links I found in my research:
[Https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/](Https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/)
[Https://snapcraft.io/docs/snapshots](Https://snapcraft.io/docs/snapshots)

I'm less than thrilled with these limited choices.  Instead, I decided to ignore they are containers and perform backups like they are any physical machine using the normal backup too and methods we've used with physical systems since 2010. I've posted about that at least 50 times in these forums.

Hardlinked files aren't usually something that any backup tool handles well as a source. All that I've seen effectively create new copies of the files, unless a backup happens as a blob from the file system or night level.  For me, that's useless.  I need versioned backups.

---

### Post by vilo999 on 2023-12-15
Thank you, I will try it. I would have imagined lxc copy would essentially do the same, especially when the container is forced to be stopped in order to be copied.

---

### Post by vilo999 on 2023-12-15
It works, wow. Now I have to figure out filesystem corruption level when I used lxc copy (how many hardlinked files were duplicated instead of copied) and proceed / decide from there.. thanks a bunch!

Still, isn't it a bug in lxc copy?

---

### Post by TheFu on 2023-12-15
> **vilo999 said:**
> It works, wow. Now I have to figure out filesystem corruption level when I used lxc copy (how many hardlinked files were duplicated instead of copied) and proceed / decide from there.. thanks a bunch!

Still, isn't it a bug in lxc copy?

LXD and the snap packages have been changing vastly of the years.  lxc copy never worked on the versions I had.  I couldn't wait for them to fix something and the direction they were headed wasn't one I liked. Further, I have 40% containers and 50% VMs and 5% physical machines, so haven't a single solution that works well across all of those situations was desired.  I do use a snap export/copy for our nextcloud instance, running inside lxc, but I manually "fixed" the way they were doing it to make versioned backups possible.  I posted that solution, perhaps a year ago here.

ZIP and tgz files as backups is for pre-teens.  We are adults and expect snapshots, versioning, and full enterprise support, right?  Of course, you can always leverage ZFS, if you use ZFS as the backing storage.  I'm an LVM user, so that really doesn't apply, no matter how badly the LXD team wants ZFS to be used (which is extremely high on their desired list).

With the screwing around that Canonical has done with snaps + lxd, I'm just waiting until a next major upgrade to switch to Debian which doesn't force snap-lxd/lxc onto people.  I like the technology of lxd/lxc, but my hatred of snaps cannot be overstated.  Canonical's recent change to bring LXD in-house, then the announcement a few days ago that lxd/lxc would be A-GPL licensed is more proof they want as tight control as they can keep for the system.  They need to hold on loosely, since they definitely have some brilliant people and ideas.

BTW, I don't need to be "right", I just need something that works.  Bugs only matter to me when there isn't a trivial workaround.  I was a software developer for about 15 yrs, so perhaps my view is slanted.  Every developer wants bug-free code, but that isn't realistic. There are always bugs that aren't prioritized very high based on many choices.  For a few years, I was on a bug priority team at a commercial company.  Bugs that impacted the greatest number of users, were in our long term plans, AND would make people stop using our software got the highest priority.   

As an example, snaps have a known bug since at least 2017 which make them useless for many enterprises.  I'd think Canonical would want to solve that issue, but they just push it as an "upstream" issue.  I happen to be one of the users and my clients cannot use anything from Canonical with snap packages that is meant for end users.  We have a bad workaround to use snaps (like lxd) for servers - the issue is due to mandated constraints in all snap packages.

---


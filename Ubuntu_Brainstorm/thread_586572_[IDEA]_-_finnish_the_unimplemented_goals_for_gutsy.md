---
title: "[IDEA] - finnish the unimplemented goals for gutsy in hardy"
date: 2007-10-22
forum: Ubuntu Brainstorm
---

### Post by Sonrep on 2007-10-22
I think there where lots of good goals on lauchpad that didn't made it's way to hardy. Work on these have been started, so they just need to finish the work.

Some goals that weren't implemented(as example)
[https://blueprints.launchpad.net/ubuntu/+spec/system-cleanup](https://blueprints.launchpad.net/ubuntu/+spec/system-cleanup)
[https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy](https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy)
[https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish](https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish)

---

### Post by Sonrep on 2007-10-24
not necessary?

---

### Post by hardyn on 2007-10-24
i would hope that things that didn't get finished, would in the next release.  But the examples that you have shown are not at all critial components, and are upgrades for the sake of upgrades.  As hardy is to be a LTS release, i would doubt if any extra time would be spend on changing the boot-splash system, when the current one is working.  hardy+1 maybe.

---

### Post by maynoth on 2007-10-24
hope we get xorg 7.3 and a gui to force refresh rates and resolutions this time

---

### Post by Sonrep on 2007-10-24
> **hardyn said:**
> i would hope that things that didn't get finished, would in the next release.  But the examples that you have shown are not at all critial components, and are upgrades for the sake of upgrades.  As hardy is to be a LTS release, i would doubt if any extra time would be spend on changing the boot-splash system, when the current one is working.  hardy+1 maybe.
A lot non-critical components as you said where in my opinion included in gutsy., feisty and edgy.

Well the current boot works, not good enough, but it works. The idea was however accepted for gutsy, so it's ok to move that goal to hardys goal list, that doesn't mean it's necessary to implement it in Hardy. Maybe in the future as you said.

But is system-cleanup and full-filesystem-sanity-gutsy not good enough to be implemented in Hardy?

What I'm trying to say is that we may not need a lot new ideas. There's already ideas that wasn't implemented in Gutsy. Implement those that developers and others already have spent time on. So we don't have to waste time in coming up with new ideas and writing new blueprints and new code all from the start.

---

### Post by hardyn on 2007-10-24
im not arguing that they should not be implimented, if they have been approved... but disk thing and cleanup seem trivial... and could cause problems in a release that should be stable.

kernels are not hard to manually remove... and yes it does suck if you run out of disk space, it is something that can be avoided by just keeping tabs on your machine.  It would be a shame to put some extra stuff in and have it be buggy in the stable release.

---

### Post by Sonrep on 2007-10-24
> **hardyn said:**
> im not arguing that they should not be implimented, if they have been approved... but disk thing and cleanup seem trivial... and could cause problems in a release that should be stable.

Trivial? How do you define a good feature?

A feature that automates a task that should be done(when there's no significant benefit in not doing it) manually is generally a good feature. 

> **hardyn said:**
> kernels are not hard to manually remove... and yes it does suck if you run out of disk space, it is something that can be avoided by just keeping tabs on your machine.  It would be a shame to put some extra stuff in and have it be buggy in the stable release.
For me and you it isn't but people that really want to do such tasks manually could use debian. Ubuntu is mainly aimed for those who don't want to remove the kernels manually, but also don't want to collect them.

Come on, it's about 6-8 months left to the Hardy release. Work has already been started. I also agree that more of efforts needs be done on fixing bugs. However, some people would feel that implementing these features would be like fixing two bugs.

What features that wasn't implemented in Gutsy do you want to implement in Hardy?

---

### Post by 23meg on 2007-10-24
> 20070613: old kernel removla added to the release-upgrader
20070702: current release-upgrader will do kernel cleanup + removal of automatically installed packages

Looks like parts of system-cleanup are in Gutsy already. I didn't perform an upgrade, so I'm not sure; can anyone confim?

---


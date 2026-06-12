---
title: "Why does Canonical allow third-parties to submit to the Snap Store?i"
date: 2023-11-13
forum: Ubuntu, Linux and OS Chat
---

### Post by masterrabbit on 2023-11-13
I understand..., the percentage of Linux users is extremely low, compared to macOS and Windows users and that Canonical wants the Snap Store to have actual content to tether people to it. But of all the things that would discourage me from adopting the Snap Store (and switching to Linux full-time), the number one point of hesitation would be the warning under every single application in the Snap Store, stating that the application is "potentially unsafe" because it was submitted by someone other than the developer. I'd rather have half the applications that are currently listed in the store if it meant not having a warning that I may be downloading malware.

As it stands, the Snap Store only lists a name--sometimes an individual's name, a group name, or a company name--and a checkmark. You cannot click on the name to find out more about the party who published the software to the store, cannot figure out why they are submitting third-party software, etc. Of course, there's occasionally an obscure link to Github at the very bottom in grayed-out, difficult-to-read text, and some reviews from users, but that information would be easier to consume if it was incorporated into a developer page in the store, much like the Apple App Store, Google Play Store, etc.

It just feels exceedingly unsafe as it stands, and that seems extraordinarily counterproductive to what Canonical appears to be aiming to achieve. And it's frustrating because I just read a post from 2018 where someone recommended adding 'official' tags to repository software registrants, so people understand whether software available in the apt repositories is coming from developers or third-parties. Canonical responded, "We're working on it!," indicating that this would be an upcoming feature. Of course, that was over five years ago.

If someone other than a developer is registering software, users ought to know why they are listing someone else's software--e.g., whether they're acting as the developer's agent or distributor--before its made available. Just my thoughts...

---

### Post by TheFu on 2023-11-13
For the appearance of being open.  One of the early complaints is that the snap storage could be used to track all software and now that Ubuntu has released a snap-only immutable variant of the desktop (no support for APT .deb programs) for developer pre-view (it is very, very, very, alpha code), I can only guess that Canonical wanted to allow anyone to make packages as a way to get as many packages - well-sourced or not - into the tracking.

Effectively, the snap store is like all the best and worst PPAs we've had for the last 20+ yrs.  Some are excellent and maintained by the project teams we already trust to create the software we love and some are from some 12 yr old kid in a basement trying to see what they can get away with adding to otherwise known software.

Humans will find a way to do great and terrible things for each other.

Canonical claims that anyone can setup a snap store, if they like.  Yet nobody else has.  

BTW, you can happily run normal Ubuntu without any snaps at all.

---

### Post by ian-weisser on 2023-11-13
> **masterrabbit said:**
> If someone other than a developer is registering software, users ought to know why they are listing someone else's software--e.g., whether they're acting as the developer's agent or distributor--before its made available.

You're not going to like almost any deb package in that case.
Most deb packages in both Debian and Ubuntu are community-submitted instead of developer-submitted.
And yet, those packages are safe.

It is possible to have safe, secure software that is packaged by community members whom you may not personally know.
It requires different methods of verification...but those methods exist and have been used for 20+ years.

There have been a few poisoned snaps and poisoned debs in the past.  Permissions and sandboxing limited their impact. The community usually discovered the problem quite soon after uploading, the  offending packages were removed swiftly, and the uploaders promptly  banned.

---

### Post by grahammechanical on 2023-11-13
> the number one point of hesitation would be the warning under **[COLOR=#ff0000]every  single application[/COLOR]** in the Snap Store, stating that the application is  "potentially unsafe" because it was submitted by someone other than the  developer.

That statement is not accurate. This is what I see for the Anbox snap

> Potentially unsafe Unconfined

This is what I see for the Firefox snap

> Safe Confined; Auditable Code; Software Developer is Verified 

zoom-client

> Safe Confined

The zoom-client is snap package by a Ubuntu developer.

[https://wiki.ubuntu.com/OliverGrawert](https://wiki.ubuntu.com/OliverGrawert)

Regards

---


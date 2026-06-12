---
title: "Snap Management Could be Improved"
date: 2023-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by 7-webmaster on 2023-04-22
The implementation of SNAP packaging has some mildly annoying characteristics.

It is understandable that when updating a SNAP that the application must be shut down while the new version is deployed.  This is primarily an issue with browsers because these days we tend to live on our browsers.  It is therefore as inconvenient for us to be forced to shut down our browsers as it is to be forced to postpone activities while our cars are in the shop for an oil-change.  But the way that oil-changes are performed has been changed to minimize that inconvenience.  In particular I do not understand why the SNAP update for the browser is delayed while hundreds of megabytes of the SNAP file are downloaded.  I do not understand why the mere fact that the browser is running should prevent the SNAP daemon from downloading the new SNAP and storing it in a temporary file.  This would save many seconds during snap refresh.

Another issue is the requirement for users to manually run SNAP refresh.  In particular why is SNAP refresh not run at times when the manager daemon can reasonably expect that all applications are not running, for example during a reboot?

---

### Post by TheFu on 2023-04-23
Snaps can be delayed, if you like.  I allow updates only on Saturdays, for example.  There's no way to prevent a snap update if you do not specify a specific snap version to be installed.  However, if you say "Latest/Stable" as the channel, then it will be updated automatically checked 4x daily, by default.  
[Https://snapcraft.io/docs/keeping-snaps-up-to-date](Https://snapcraft.io/docs/keeping-snaps-up-to-date)
[Https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](Https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

These capabilities are documented at snap.io.

Of all the issues with snap packages, these are the least in my mind.  The lack of local controls over which file system locations can be accessed is my main problem.  Users with HOME directories on NFS or not under /home/ can't use any snap programs, for example.  Accessing network storage that isn't mounted under /media/ is impossible too. [Https://snapcraft.io/docs/removable-media-interface](Https://snapcraft.io/docs/removable-media-interface)

 In an enterprise, running 20 types of Unix systems, nobody is interested making changes to their entire infrastructure just so that snap packages work, effectively breaking every other system and the setups they've had for 20+ yrs.

And running remote X11 applications that happen to be snaps shouldn't require an  ~/.Xauthority hack.

---

### Post by ian-weisser on 2023-04-23
> **7-webmaster said:**
> ... forced to shut down our browsers...

This seems like Classic FUD which (regrettably) distracts from the rest of what you are saying. You are not "forced" to do anything inconveniently. You have a 14-day window. Two whole weeks. You choose when to shut down your browser at your convenience to refresh the snap.



> **7-webmaster said:**
>  I  do not understand why [XYZ] should prevent the SNAP daemon from downloading the new SNAP and storing it in a  temporary file.  This would save many seconds during snap refresh.
[...]
[W]hy is SNAP refresh not run at times when the manager  daemon can reasonably expect that all applications are not running, for  example during a reboot?

Judging by the amount of developer discussion on the mailing lists and at snapcraft.io about exactly those ideas (and others) to improve the experience, the developers seem to agree with you. Feel free to jump in and help.

---

### Post by TheFu on 2023-04-23
> **ian-weisser said:**
> This seems like Classic FUD which (regrettably) distracts from the rest of what you are saying. You are not "forced" to do anything inconveniently. You have a 14-day window. Two whole weeks. You choose when to shut down your browser at your convenience to refresh the snap. 

That might be true, but when Firefox gets updated here, within about 10 minutes, it refuses to open any new tabs or refresh existing ones.  It offers to restart ... which generally works to bring back all opened tabs to the locations they were, including logins, but not all. Some websites have stronger session security and a browser restart forces restarting everything in that session.

---

### Post by ian-weisser on 2023-04-23
> **TheFu said:**
> That might be true, but when Firefox gets updated here, within about 10 minutes, it refuses to open any new tabs or refresh existing ones.

Hmmm. That one is new to me. A curious bug.

---

### Post by TheFu on 2023-04-23
> **ian-weisser said:**
> Hmmm. That one is new to me. A curious bug.

I don't think it has anything to do with snaps.  It is a firefox behavior.

I have been screwed by a nextcloud snap upgrade due to being on the "Latest/Stable" channel. It moved to v25 of nextcloud and some very important addons that we use constantly stopped working because they don't support v25.  Took me a bit to realize that I needed to be on "v24/stable" channel instead.  That happened about a month ago and seems to be working fine.  Moving between v25 and v24 of the Nextcloud (in my instance) wasn't any issue. I don't know if there were DB migrations, but they didn't remove anything from the DB, so v24 has been working.  When the addons finally do support v25, the upgrade will be to take a snapshot of that entire lxc container, change the snap channel for that specific snap, then force an refresh and go through each app to bring them up to the correct version.  We probably run about 25 NC addons.  Only 3 really matter, daily.  The others are nice to have and some have never really worked - like the search and maps and gallery addons. They did work in prior, pre-snap, versions of nextcloud. Think I was running v18 and v19 where everything worked, but the major upgrades were becoming more complex than even I cared to handle, so when it was time to retire 18.04, I moved over NC to a snap lxc on ... 22.04.2 ... it seems.  It is a standalone container, just for nextcloud.

I'm not thrilled with the backup/restore capabilities for snaps/lxd, mainly because they don't do versioning.  They effectively create a tgz file. Meh.  That's not useful except for a quick migration and if there isn't much data inside the container.  I suppose if I'd fully integrated ZFS backup methods, then I wouldn't care.  It's on the list long list of things to get to, but I suspect death will happen before I get there.

---

### Post by zebra2 on 2023-05-03
Snap is under continuous development and improvement.  This is more obvious in the latest releases or even not yet released editions of Ubuntu.  I by default use the current development version of Ubuntu/Gnome/Wayland currently 23.10 Mantic and Flatpack was installed by default in the Gnome Software app.  Now depending what is available from the software developers you can chose DEB, SNAP or FLATPACK install from Gnome Software. Today May 3rd I got a update to Core22. You may want to read the Core Docs to see the snap improvement in that alone.  I have been using Snap from its inception and have had to tolerate many problems but right now I like what I have. You have to remember that Snap is not one sided. It requires proficiency from the developers that code the software into snap/deb/flatpack format in the first place.  Improvements are two sided. I try to avoid blaming Canonical for the perceived ineptitude of the software developers. Bottom line is that Snap may be much better than you think it is. It also depends on how much you are fiddling with your platform.  It isn't uncommon for users to screw around with their system to the point that they become their own worst enemy.

---

### Post by 7-webmaster on 2023-07-11
> **ian-weisser said:**
> This seems like Classic FUD which (regrettably) distracts from the rest of what you are saying. You are not "forced" to do anything inconveniently. You have a 14-day window. Two whole weeks. You choose when to shut down your browser at your convenience to refresh the snap.


But I do not want to shut down my browser at all!  Ever.  I live in the cloud.  All of my working data is in the cloud where it can be shared, not on my own computer where I would need to back it up.

I did a search for "why do i have to shut down an app to refresh snaps" and various variations but there was no matching answer.  

This is Linux not *******.  There are no locks to prevent replacing open files.  Snap refresh could replace the actual snap files  and it would mean nothing to the running applications which already have  the inode of the old copy of the snap open even though that inode is no  longer pointed to by the named entry in the directory.  Closing and  reopening the application merely releases the old inode.  Many of us  left ******* precisely **because** of its unnecessarily slow and disruptive update process.

Back when Firefox was updated by APT the updates were downloaded and applied immediately, like all standard LINUX software.  I did not have to shut down Firefox to update it, although for some changes it was necessary to briefly shut down and restart Firefox **after** the update was applied.  But Canonical insists that to update the Firefox Snap we must close all Firefox windows, by console "killall firefox" because a normal termination closes all of the tabs individually which contain our current activities, and issue "sudo snap refresh" to **download and apply** the updated snap because the update is apparently not waiting for a notification that Firefox has shut down to start doing its work automatically, and this download and update can take a long time by computer standards, and then later we must restart Firefox **hoping** it will recover all the tabs.  I am merely requesting that the SNAP update not cause me to lose working time while it goes through its lengthy housekeeping.  Ideally give us the same level of support for updates to these applications that we had **before** Canonical fell in love with SNAPS.  Frankly because I do almost all of my work these days in the **Cloud**, that is through Firefox, this implementation wastes too much of my time.  I would rather be working than effectively masturbating while the sluggish Snap refresh does its thing.

See also:
[https://ubuntuforums.org/showthread.php?t=2486631](https://ubuntuforums.org/showthread.php?t=2486631)
[https://ubuntuforums.org/showthread.php?t=2481994](https://ubuntuforums.org/showthread.php?t=2481994)
[https://ubuntuforums.org/showthread.php?t=2470846](https://ubuntuforums.org/showthread.php?t=2470846)
[https://ubuntuforums.org/showthread.php?t=2466372](https://ubuntuforums.org/showthread.php?t=2466372) 
[https://www.reddit.com/r/linux4noobs/comments/12soa4c/why_does_canonical_force_snap_packages_onto/](https://www.reddit.com/r/linux4noobs/comments/12soa4c/why_does_canonical_force_snap_packages_onto/)

Canonical needs to make SNAPS less painful or give up on them and try some other method of packaging applications.  I have been running Ubuntu since Warty Warthog in 2004.  I have been almost exclusively on UNIX since working on a Solaris workstation starting in 1990.  Why is Canonical, in effect, **encouraging** me to switch to Mint by their clumsy implementation of Snaps?

---

### Post by ian-weisser on 2023-07-11
> **7-webmaster said:**
> Back when Firefox was updated by APT the updates were downloaded and applied immediately, like all standard LINUX software.  I did not have to shut down Firefox to update it, although for some changes it was necessary to briefly shut down and restart Firefox **after** the update was applied.

You have been misinformed.

None of your Firefox apt upgrades were available until after quitting and restarting the application. The running binary was the old binary. Same behavior for snap refreshes.

---

### Post by donald187 on 2023-07-12
Actually, it seems snap management has been improved.  I just got the "You have 13 days  to...."  notification for Firefox. But the next sentence said "Close the app to update now".  So I did and waited several seconds.  Then a banner appeared saying something like "Firefox has been refreshed.  Start to use new version."  And sure enough.  When I started Firefox it had been updated.  Very nice!  I'm on Ubuntu Jammy.

---

### Post by mikewhatever on 2023-07-12
> **7-webmaster said:**
> But I do not want to shut down my browser at all!  Ever. ...

Yeah, know how you feel exactly. I do not want to need to breath ever again, or see another snap complaint.

---


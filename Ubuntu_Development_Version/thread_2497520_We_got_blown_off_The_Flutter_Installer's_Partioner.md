---
title: "We got blown off: The Flutter Installer's Partioner"
date: 2024-05-08
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2024-05-08
Remember this back in DEV-Lunar and DEV-Mantic... and was still a problem with DEV-Noble?
RE: [https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236)

They closed it saying that they wouldn't fix it for Mantic, because Noble has a "different installer"... (ubuntu-desktop-installer vs. ubuntu-desktop-provision). A couple weeks before Nobles release, about the same time of the Noble Repo freeze... That's when they did that. Remember that Mantic (23.10) is still officially supported for a few months yet...

I remember during DEV-Noble, Canonical had a purge of the Team handling that. We talked about that here. Well in the process, they gave the name of the installer a new buzzword-- ubuntu-desktop-provision. Meaning: To provision new Desktops. As far as I can tell, the name is all that changed. 

Except, behind the scenes, if you look at the desktop file of the Noble Installer, it says /snap/bin/ubuntu-desktop-bootstrap instead of /snap/bin/ubuntu-desktop-installer. A distraction from the problem.

You all remember the dead-end journey I had filing issues at the Canonical GitHub for ubuntu-desktop-installer, and as a question at LaunchPad, on asking just what the installer was, right?

Well, as I remember back in DEV-Lunar, when Canonical made the official announcement for Lunar, that's when they announcement for moving to the Flutter installer, and choosing a newer, different partitioner. We lost a whole lot of capabilities that we had, moving to this partitioner. Of most User's concerns on the forum was that is didn't recognize pre-existing LVM2, LUKS, mdadm storage containers, and filesystems such as BTRFS & ZFS. The older partitioner could recognize those. It couldn't handle doing anyhting with ZFS, but since it recognised eveything else, you could do a somewhat non-destructive reinstall, like guiverc documented so well on AskUbuntu, that we in the know have been recommending for many users to fix their systems, or to pop into the Live system, toggle over to a console prompt or terminal session to create the LUKS, LVM, mdadm storage containers there, then toggle back to the installer to use manual partitioning in the partitioner, to create the mount points (the internal wiring), and continue wiht the installer to install the system.

I've been doing that, and recommending that to Users since 10.04 LTS for tweaked, custom installs. That was a big plus for Ubuntu. That was something that really worked. 

We. keep recommending that users install their system with a separate /home partition folder. Or at least a Home LV somewhere...) That just makes sense. Most of my installs as a Systems Admin are this way. 

We lost all that. They said they would not fix it, at least specifically for Mantic, which is still officially supported. They said it would not affect Noble. IMHO-- They didn't have any idea what they were talking about. It's still the same exact problem.

I can tell you with the facts, and references, that we have lost Users with Noble releasing and this problem not resolved. I have Sys Admins telling me that their shop will not go from 22.04 LTS to 24.04 LTS with this problem unresolved. I have old, long-time Users telling my they will be going back to Debian, where their installer still has those capabilities. Users are jumping ship

This will be a problem with DEV-Oracular, because it "IS the same". Nothing has changed because we recommend things in the DEV cycle, and file bug reports on things,  where we say something is not right and is not working... I feel like they really blew us off.

I'm not letting our Users down with this. I'm not letting this go away by not trying to get this resolved. It's just the right thing to do.

This new DEV-Cycle, I'm taking a defibrillator to this issue and restarting the process all over again: [https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236)

If you see my slipping with my momentum on that, please kick me in the behind to get me going again.

If you can recreate this, please join the bug. If you see Users complain about this, have them join the bug. I don't feel Ocular should release if we can't get this back, or at least we gave it 100% trying our best with that. I feel that our Users deserve that.

We don't have a lot of say, but their are ways we can make noise to be heard, right?

Yes, a bit passionate about this. I care about our Users, and this has been a sore spot for me in the last 3 DEV-Cycles, that has not gone anywhere (yet).

---

### Post by MAFoElffen on 2024-05-08
If you have any recommendations on anything else I can do to maybe get this looked at seriously, do not hesitate to let me know. Publicly, or in PM.

---

### Post by ajgreeny on 2024-05-10
> We. keep recommending that users install their system with a separate /home folder. That just makes sense. Most of my installs as a Systems Admin are this way.
Just to clarify your comment, did you mean separate folder or partition?

---

### Post by MAFoElffen on 2024-05-10
Oh dang. Yes, was a typo, Should have been "partition". (Edited)

Thank you.

---

### Post by TheFu on 2024-05-11
Has the autoinstall Storage documentation with lots and lots of examples been updated?

I can see where autoinstall files will be the preferred method, but only if people can figure out how to use it.  Examples of storage layouts with full explanations are needed.  The examples I've seen 
a) are trivial - all or just let the automatic settings work
b) do not specifically say which releases they work under.
c) need a clear, manual, way to provide the URL to the autoinstall file(s) on-the-fly at install time.  Perhaps on the first screen of the installer, after checking default locations (which I assume is currently done).

Mainly, just need many, many, more non-trivial examples.

---

### Post by #&amp;thj^% on 2024-05-11
> **MAFoElffen said:**
> 

Yes, a bit passionate about this. I care about our Users, and this has been a sore spot for me in the last 3 DEV-Cycles, that has not gone anywhere (yet).
I too am very passionate over this, I'm just amazed the bug has gone to just ignored.

Makes me appreciate my Arch systems all the more. (Sorry if that sounds offensive but it is what it is)

---

### Post by MAFoElffen on 2024-05-12
Kids sometimes.

Dang. It will be hard tedious work, but we will bring them along eventually. LOL

---


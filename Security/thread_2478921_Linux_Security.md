---
title: "Linux Security"
date: 2022-09-08
forum: Security
---

### Post by jacksonguitars on 2022-09-08
Dear sirs and ladies!

What tools do I need to keep Ubuntu safe and secure?

Thank you!

---

### Post by #&amp;thj^% on 2022-09-08
"**Security is a process, not a product.**" -- Bruce Schneier, encryption and security expert.

The best place to start, and that is exactly what it means, >> a start, have a good read here: [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)
There are good and bad tools for this depending on your skill level.

Minimal Basic starting tools: [https://www.fossmint.com/linux-security-tools/](https://www.fossmint.com/linux-security-tools/)
I'm on the fence on ClamAV, but that's my opinion.

you will certainly get more idea's from other reply's as well.

Here is a list that was published in 2021 with ratings if your into that stuff: [https://linuxsecurity.expert/security-tools/top-100/](https://linuxsecurity.expert/security-tools/top-100/)

---

### Post by TheFu on 2022-09-08
> **jacksonguitars said:**
> What tools do I need to keep Ubuntu safe and secure?

Nothing replaces a human brain making good choices based on the best, current, knowledge, available about the OS.

The types of things performed on the system alters the security needs greatly. There are as many different Linux systems running different things as there are computers + virtual machines + Linux containers.  All are a little or hugely different, so their default security needs are different too.  Working hard on security for things that aren't running on your system is a waste of time.  Ignoring security for things you do and run daily is also a bad idea.

So, make a list of everything you do on the computer, what is local, what is on the LAN and what happens over the internet, then research how to secure each of those things.  For most pure-end users, there isn't really much to be done beyond this: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)  If you do more things on the LAN or over the internet, the risks increase and your security stance should improve too.

And daily, automatic, versioned, backups that aren't available to the system that is backed up 99.99% of the time. Malware can attack backups if the client system has direct access to those backups.

And don't use the root account. Learn to use sudo only when necessary.  Have a "default deny" stance for everything on the system. That means, only allow specific actions that are necessary, not everything that is possible.

Did I mention having automatic, daily, versioned, backups?  That truly is the #1 security tool that I know.  With modern backup tools, keeping 90 days to 1 yr of daily backups doesn't really take much storage or time.  Learn to use a good backup tool that handles the versioning and storage efficiency well.

---

### Post by jacksonguitars on 2022-09-16
Thank you, sirs.

---

### Post by jacksonguitars on 2022-09-16
What backup tool would you recommend sir?

> **TheFu said:**
> Nothing replaces a human brain making good choices based on the best, current, knowledge, available about the OS.

The types of things performed on the system alters the security needs greatly. There are as many different Linux systems running different things as there are computers + virtual machines + Linux containers.  All are a little or hugely different, so their default security needs are different too.  Working hard on security for things that aren't running on your system is a waste of time.  Ignoring security for things you do and run daily is also a bad idea.

So, make a list of everything you do on the computer, what is local, what is on the LAN and what happens over the internet, then research how to secure each of those things.  For most pure-end users, there isn't really much to be done beyond this: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)  If you do more things on the LAN or over the internet, the risks increase and your security stance should improve too.

And daily, automatic, versioned, backups that aren't available to the system that is backed up 99.99% of the time. Malware can attack backups if the client system has direct access to those backups.

And don't use the root account. Learn to use sudo only when necessary.  Have a "default deny" stance for everything on the system. That means, only allow specific actions that are necessary, not everything that is possible.

Did I mention having automatic, daily, versioned, backups?  That truly is the #1 security tool that I know.  With modern backup tools, keeping 90 days to 1 yr of daily backups doesn't really take much storage or time.  Learn to use a good backup tool that handles the versioning and storage efficiency well.

---

### Post by #&amp;thj^% on 2022-09-16
rsync on the command line or cronnie.
Timeshift for a nicer/easier GUI look, It can use rsync as well.
TheFu will add his very nice and workable method suggestions as well, I'd expect.

---

### Post by ipv2 on 2022-09-16
> **1fallen said:**
> I'm on the fence on ClamAV, but that's my opinion.

likewise.

to keep or not to keep, that is the question.

---

### Post by #&amp;thj^% on 2022-09-16
> **ipv2 said:**
> 
to keep or not to keep, that is the question.

Solely up to the user, If it was just an email server, then I'd use it with a grain of salt. (Just too many false positive's)

---

### Post by ipv2 on 2022-09-16
> **1fallen said:**
> (Just too many false positive's)

ditto that.

am going minus clamav & clamtk on my main machine since a couple months now & i do not find anything amiss.

---

### Post by TheFu on 2022-09-16
> **1fallen said:**
> rsync on the command line or cronnie.
Timeshift for a nicer/easier GUI look, It can use rsync as well.
TheFu will add his very nice and workable method suggestions as well, I'd expect.

My backup methods have proven to be too hard for most people to implement, based on history trying to help people here.  There must be 20+ threads here where I've attempted to help.  I can remember only 1 where it was very clearly successful.  Because my rdiff-back method is too complex for many people when used in the most efficient way, it probably needs to be dumbed down to a method that I've never used 
OR
Use rsnapshot, which is based on rsync + hardlinks to handle the versioning.  There are some liabilities for all backup tools that use hardlinking for their versioning.  Seems that 95% of people here don't care about those issues ... probably because they haven't been burned like I was.  Back-In-Time is similar to rsnapshot, but with a GUI.  rsnapshot doesn't have a GUI.  Back in Time does.   I've used back-in-time myself and created a script much like rsnapshot in the 1990s.  Better to just use the already perfected rsnapshot tool.  Both of these are in the Ubuntu Repos.

Backups need to be run with elevated privileged on Unix system to retain users, groups, permissions, ACLs, and xattrs.  If all you backup is 1 user's HOME, that stuff probably isn't important.  But if you are doing a system backup or the HOME directories for more than 1 userid, it is mandatory.  You've been warned.  BTW, GUIs don't like be run with elevated privileges, so expect problems if doing that.

For people at advanced-intermediate level of skill, rdiff-backup addresses lots of problems that rsync and most other rsync-based tools don't address.  Plus rdiff-backup can "pull" backups from client systems to a backup server,  it is crazy fast compared to using rsync, and it is more efficient for storage than hardlink-based versioned backups.  But I suspect most of those things aren't understood by average users, so the subtle problems solved are missed.   Add in using volume manager snapshots (ZFS, BTRFS, and LVM only) and backups won't have corruption when taken on an active system doing work.

---

### Post by ipv2 on 2022-09-18
1. on a fresh install of jammy is apparmor good enough out of the box or does it need additional configuring to be done manually?

2. would removing apparmor & replacing it with selinux be a wise thing to do?

3. since ubuntu comes with apparmor would it mess up ubuntu if i remove apparmor?

all & any advice is welcome.

---

### Post by TheFu on 2022-09-18
> **ipv2 said:**
> 1. on a fresh install of jammy is apparmor good enough out of the box or does it need additional configuring to be done manually?
I never have.

> **ipv2 said:**
> 2. would removing apparmor & replacing it with selinux be a wise thing to do?
No.  If you want SELinux, install a distro with SELinux.

> **ipv2 said:**
> 3. since ubuntu comes with apparmor would it mess up ubuntu if i remove apparmor?
Probably.  Install a play VM and try it.  Expect the system not to work.

---

### Post by ipv2 on 2022-09-18
copy that.

am rest assured.

---


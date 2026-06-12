---
title: "How can I restore my backups on my VPS?"
date: 2019-09-22
forum: Server Platforms
---

### Post by MariosFFX on 2019-09-22
I have a VPs and I'm doing my expirements on it.
Sometimes things break and I'll have to destroy my VPs and a create a new one.

The only things I have access to is the master terminal where I can see my VPS booting up and where I can also launch grub rescue and access to the terminal after VPs has finished booting up.

Can I restore my VPs while Ubuntu runs??

By the way, I do my commands with tar and some arguments.

---

### Post by QIII on 2019-09-22
Moved to Server Platforms as a more appropriate location.

Is this VPS on a physical machine that you control, or is it hosted on a physical machine controlled by someone else?

---

### Post by MariosFFX on 2019-09-22
I don't have physical access, only a GUI where I can see everything on the screen, like how's it's booting up but I cannot plug any USB devices or load any other images.

Only what my VPS provider provides me which is some installation images like Ubuntu 16.04, 14.04, Fedora and Windows.

Well my VPs provider is outdated and is provided by my University and it's free.

---

### Post by TheFu on 2019-09-22
It depends on what the tar includes, and how the VPS boots.
Tar was designed for MB-sized backups, not GB. Best to use a better backup tool or just pay the VPS to handle it for you.

On a VPS, it should be faster to bring up a fresh VM, and restore the data, settings and the list of manually installed packages, than it would be to restore an entire OS.  Should take 15-20 minutes. Should be trivial to test, so there wouldn't be any questions about this.  Spin up another instance for an hour or two - test the restore.

Until a restore is tested and working, nothing anyone else says means anything.

---

### Post by Skaperen on 2019-09-22
what areas of your VPS did you include in the tar backup?  just /[COLOR=#0000cd][FONT=courier new]**home**[/FONT][/COLOR] and /[COLOR=#0000cd][FONT=courier new]**etc**[/FONT][/COLOR] or everything?

---

### Post by MariosFFX on 2019-09-22
Everything

---

### Post by MariosFFX on 2019-09-22
Can't I restore my VM while it's on?
Does untar work like that?

---

### Post by SeijiSensei on 2019-09-22
No, you can't restore a running VM.  What you can do is clone it, then spin up a new VM instance running the clone.

---

### Post by TheFu on 2019-09-22
> **MariosFFX said:**
> Can't I restore my VM while it's on?
Does untar work like that?

Well ... sorta.   Sometimes, I restore my backups by booting a VM off an ISO (Ubuntu-mate iso) and use it to restore files from my backup tool.  Fixing boot issues using an install-ISO is how I do it. There are a few other ways.

Really the answer is that you cannot restore a full backup to an OS partition actively in use as the OS.  Booting from alternate media is a common thing, then you can mount the old OS partitions and restore anything you like, but depending on how the boot is configured, the restored data might not boot.  Legacy boot stuff needs to have grub installed in a specific location with specific  settings.  UEFI booting is different and needs to follow the UEFI standards.

---

### Post by MariosFFX on 2019-09-27
> **TheFu said:**
> Well ... sorta.   Sometimes, I restore my backups by booting a VM off an ISO (Ubuntu-mate iso) and use it to restore files from my backup tool.  Fixing boot issues using an install-ISO is how I do it. There are a few other ways.

Really the answer is that you cannot restore a full backup to an OS partition actively in use as the OS.  Booting from alternate media is a common thing, then you can mount the old OS partitions and restore anything you like, but depending on how the boot is configured, the restored data might not boot.  Legacy boot stuff needs to have grub installed in a specific location with specific  settings.  UEFI booting is different and needs to follow the UEFI standards.


What if I am able to log in to my VPS just fine.

Let's say for example: 
I am trying out Web Control/Hosting Panels and I have messed up the configuration of a panel.
Web Panels touch and make changes to Server core files, for example DNS records on Bind9 and most of the times even if you uninstall those Web Panels, they do not restore the original settings of those files they touch.

So if I mess my DNS records while installing a web control and then uninstall it, unfortunately those settings will be not removed and if I am going to install another Web Panel, that web panel will also append its settings to those files.

What if I want to try 5 different web panels, just to find one that I really want to use.
But if I try 5 different web panels, they will cause a mess to my server files and that's why what I have been for the past days is like this:
Create VPS -> Install Ubuntu 16.04 -> Change default user, root passwods -> apt update -> apt upgrade -> apt full-upgrade -> reboot -> install web panel -> break something -> Destroy VPS

Unfortunately my provider is from my university, it's free but I also have a Static IP address, 1 Gbit line bandwidth and unfortunately it they haven't done any updates on their systems since 2012 and I cannot make VM Snapshots or Restore partitions or boot other OS, it's options are limited as hell.
Ad because it's free I don't want to change the provider because I'm still learning and I would like to learn how can I also use a Web Hosting Control Panel, Deploy Python & NodeJS Apps, Git between my machines and the server.

Long story, short:
All I want to do is a make full backup before installing a Web Hosting Panel (or any app here) and if something breaks, I want to revert my **system files **like they were before installing the Web Hosting Panel.

I'm not asking for restoring system partitions.

---

### Post by LHammonds on 2019-09-27
Are you not able to create snapshots at the host level?

If not, you might want to consider installing Ubuntu on your PC inside a VM so you can get a base install, create a snapshot, then test a particular application and then revert back to the snapshot to erase all changes made since the snapshot...then test another app, etc.

Once you have an application selected and document how to install/configure it, then do it on your VPS.

But no matter what, you need a workable backup/restore procedure for your VPS.

LHammonds

---

### Post by TheFu on 2019-09-27
YOU are responsible for any updates, not them. That applies to all VPS providers.  Never assume anyone will patch your systems.  That will just cause the provide headaches, so it is your problem, not theirs.

What did you backup?  Did you get everything in /boot, /etc, /usr, /lib, /home, /var?  If you used tar, you can selectively restore specific files.  tar can do that, but it will be slow - depending on the size of the file.

What do you mean by "system partition"?  Partitions aren't fixed.  Then can be setup anywhere.

Full backup means system files, settings, personal files, personal settings.  
2012!?  Hacked much?  There are many remote kernel hacks in the wild in 2019 and pretty much for every year prior.  You should start over at this point.  Seriously.  Start over with a fresh 18.04 install and put back the specific data.  Any settings from 2012 are next to useless. The configuration files have changed.

---


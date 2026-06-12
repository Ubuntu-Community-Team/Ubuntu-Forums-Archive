---
title: "Almost-painless Hoary to Breezy upgrade with aptitude and DVD ISO file"
date: 2005-10-27
forum: Testimonials &amp; Experiences
---

### Post by Bill Statler on 2005-10-27
This is for the 2 or 3 remaining people who haven't already upgraded from Hoary to Breezy.  :-)

I did my upgrade using aptitude and the install/live DVD ISO file.  It took a long time because I was careful to fix all broken packages reported by aptitude before proceeding, but I ended up with a bootable, working Ubuntu with only a few serious problems that needed fixing.

By the way, it's really helpful to have a second computer (with Internet connection) available during this process, so that you can Google for help!

I'm not going to detail every single step like a "HOWTO", but here is what I did:

1. Downloaded the install/live DVD file, ubuntu-5.10-dvd-i386.iso, using BitTorrent.  (Of course you will want to download the correct version for your processor.)  Checked the file using md5sums and isovfy.

2. Mounted the ISO file in the filesystem.  First I created the directory /mnt/iso.  Then I added this line to /etc/fstab:
```

/path/to/downloaded/file/ubuntu-5.10-dvd-i386.iso /mnt/iso iso9660 ro,loop,auto 0 0

```
After rebooting, the entire DVD contents could be read at /mnt/iso.

3. Checked for already-installed broken packages or other warnings using aptitude and (just to be safe) Synaptic.  Didn't find any.

4. Still using the old sources.list for the Hoary repositories (with backports commented out!), upgraded a few packages that needed it, including the kernel (linux-image-2.6.10-5-386), and rebooted afterwards.  (I wanted to be sure I had a "perfect" Hoary before the big upgrade.)

5. To try to prevent a possible conflict, removed obsolete versions 1.0.6-1ubuntu1~5.04ubp1 of firefox and firefox-gnome-support which came from the backports repositories.  (Doing this made Firefox unusable -- I think it deleted the chrome -- but I didn't bother to fix it at this point because I figured the upgrade to Breezy would take care of the problem later.  Which it did.)

6. Still using the old Hoary sources-list, verified that ubuntu-base and ubuntu-desktop didn't have any unsatisfied dependencies.

7. Created a new /etc/apt/sources.list that had only this one line uncommented:
```

deb file:/mnt/iso breezy main restricted

```

8. Rebooted AGAIN.  At this point I tried to avoid running any programs besides aptitude, just in case they might interfere in some way.  (I did need to run gedit but shut it off before starting the actual upgrade process.)  I don't know if this level of paranoia was necessary, but it seemed like a good precaution.

9. Started aptitude and did an update so that it would read the new repository (that is, the DVD ISO file).

10. Pressed "U" to mark all upgradable packages; aptitude reported that 12 packages were broken.  You might think that, at this point, the thing to do is list the broken packages and start fixing the dependencies.  DON'T.  That way lies madness, because almost everything you fix breaks something else.  Here's what worked for me:

11. Went to the section titled "Obsolete and Locally Created Packages", and looked for broken packages.  (Note that not everything in this section is *really* obsolete: aptitude puts installed packages here if it can't find them in the repositories.  So later, when you change sources.conf to include the Internet repositories, most of these packages will magically stop being "obsolete".  Nevertheless, this is a good place to start hunting for "problem" packages.)

This is a rather long job.  You will find quite a few packages in this section that are already marked for automatic removal, and in a few cases these will cause other packages to be broken.  There are also some packages you will need to remove manually in order to make things work.  A good place to start is manually removing the old OpenOffice.org Version 1 packages:
  openoffice.org
  openoffice.org-bin
  openoffice.org-l10n-en
  openoffice.org-gnomevfs
  openoffice.org-gtk-gnome
These files may be slightly different on your system, depending on your language and whether you're running GNOME or KDE.  Removing them will eliminate quite a few conflicts.

Similarly, the old version of Evolution has several packages which need to be manually removed to avoid conflicts with the new version.  I removed these:
  libebook1.2-3
  libedataserverui1.2-4

Other good candidates for removal are packages you installed from backports.  For example, I had to manually remove gimp-svg version 2.2.8-1ubuntu1~5.04ubp1 because it required the matching version of gimp (which was being upgraded to a non-backports version).

Here are a few more packages I manually removed:
  dbus-glib-1
  libhal-storage0
  libhal0
  libnautilus-burn1
  libcurl3-gssapi
  fetchmailconf
Again, this list might be different on your system, depending on what software you have installed.  Continue looking through the "Obsolete and Locally Created Packages" section until you've eliminated all the conflicts.  (After I finished this, aptitude reported only 1 broken package remaining.)

12. Pressed "b" to search for any other broken packages.  There was only one: libesd-alsa0, which conflicts with libesd0.  These two packages are used to control sound, and you can have one or the other but not both.  After some research I kept libesd-alsa0 and manually removed libesd0.  I still have sound after the upgrade, so apparently this worked.

13. Pressed "g" to see a list of the packages aptitude was about to install or remove.  Looked through this for obvious problems, but didn't find any.  At the bottom of this list are two useful sections: "Packages which are recommended by other packages" and "Packages which are suggested by other packages".  I went through these sections and chose a few packages for installation.  Then I double-checked the whole list and verified that there were still no broken packages shown.

14. Made sure no programs were running except aptitude.

15. Pressed "g" again to start installation.  During installation, the user is asked many questions, mostly about whether your existing config files should be overwritten by new versions.  Usually you can press "D" to display the differences between the old file and the new one, to help you decide.  If you do let a config file be replaced with a new version, the old one will be saved (for example, my old /etc/gdm/Init/Default was saved as Default.dpkg-old).  It's a good idea write down the changes you allow and disallow during this process, since it may help you to fix problems later.

16. After installation was finished, quit aptitude and rebooted.  This caused GNOME Session Manager to crash with a fatal "segmentation fault" error, but after that, the reboot proceeded normally.

That's it!

Well, that's not quite it, because there were still a few problems to clean up.  In my case, I had one serious problem: none of the regular users on my system were allowed to use sudo, and I couldn't log in as root.  This problem, and the solution, are discussed in this thread:
[http://www.ubuntuforums.org/showthread.php?t=77614](http://www.ubuntuforums.org/showthread.php?t=77614)

Also, right after login, I received a message warning that "Your $HOME/.dmrc file has incorrect permissions and is being ignored."  The solution to that one is in this thread:
[http://www.ubuntuforums.org/showthread.php?t=77627](http://www.ubuntuforums.org/showthread.php?t=77627)

It's also worth looking at the "Post-Upgrade" section of this Wiki article for a few more changes that ought to be made:
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

I still have a few fixes I need to do here, but at least I have a stable, running, usable system.  I'm happy with the results.  But, compared with installing Windows XP Service Pack 2, the Hoary to Breezy upgrade was really difficult.  I'm not going to complain about free software, but it would be great if this problem could be addressed before the next release, so that Ubuntu can be taken more seriously as a viable alternative to Windows.

Anyway, I hope all this is of help to someone.

---

### Post by Bill Statler on 2005-10-28
Excuse me, but who moved my post to the "Ubuntu Testimonial Archive"?

This is not a testimonial, it's help for people who are trying to upgrade.  I strongly feel it belongs in  "Ubuntu Breezy Badger 5.10 > Installation and Upgrade Help", where I originally posted it.

Put it back, please.

---

### Post by majikstreet on 2005-10-28
[QUOTE=Bill Statler]Excuse me, but who moved my post to the "Ubuntu Testimonial Archive"?

This is not a testimonial, it's help for people who are trying to upgrade.  I strongly feel it belongs in  "Ubuntu Breezy Badger 5.10 > Installation and Upgrade Help", where I originally posted it.

Put it back, please.[/QUOTE]
I would say make a seperate HOW-TO in the How-To's section/and or in the section you posted it in....

---


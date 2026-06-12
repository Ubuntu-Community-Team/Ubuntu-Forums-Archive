---
title: "Newer versions of Bibletime"
date: 2014-01-18
forum: Ubuntu Christian Edition
---

### Post by ronbu on 2014-01-18
An attempt to build Bibletime 2.10.0 on Ubuntu CE 12.04 failed due to a requirement of the qt package with the name "qt".  The latest version that can easily be run on UCE is 2.9.2 .  That is available at launchpad.net in the Saucy repository.  It does not require any updated core packages.  The bibletime-data package of the same version number must be installed, then the bibletime package.   If, an older installation of Bibletime was used, the .bibletime directory in the home folder must be deleted.  It can be deleted with Nautilus after the Ctrl-H has been pressed which allows dot directories to be displayed.  It can also be deleted from the terminal with the command:  "rm -rf ~/.bibletime".  I strongly advise not to use versions of core packages in repositories other than the repository of your version, which in Ubuntu 12.04 is "Precise", as that could break your system.

---

### Post by ronbu on 2014-01-20
I found out in devel.bibletime.info that Bibletime 2.10.0 needed extra packages in order to build.   After, i got the extra packages, I was able to build Bibletime 2.10.0 and run it successfully.  However, I had to rebuild Biblememorizer against the new version of Sword.  I was able to run and save a Bible verse.  I would also need to build Xiphos which has a new bugfix version, with the Sword 1.7.2.

---

### Post by ronbu on 2014-01-20
I was able to successfully build and install and run Xiphos 3.1.6 with Sword 1.7.2.  However, it is much easier to use already made .deb installers to install packages.

---

### Post by Saunter on 2014-06-30
I've been using Bibletime with Kubuntu for a few years now.  In May, I upgraded to Kubuntu 14.04 on both my desktop and laptop machines.  The desktop had a problem with the upgrade and I had to reinstall Kubuntu from a CD.  The laptop upgrade went well, but now I've noticed that Bibletime doesn't run any more.  It works fine on the desktop machine, but when I open it on the laptop, I get a popup box that says it is creating the user interface, then it disappears and nothing more happens.  I tried removing and reinstalling Bibletime to no avail.  Then I removed and purged Bibletime using apt-get and reinstalled to no avail.  It still just has the one-second popup and dies.  Any ideas?

---

### Post by ronbu on 2015-04-29
This response is over nine months after Saunter's post.   I used to have Kubuntu 14.04 on a USB hard drive.  Bibletime worked fine for me on it.  Perhaps a firewall could have blocked Saunter's use of it on his laptop in 2014.   If, you want to run BIbletime on a 'Buntu version 14.04 to 15.04 it is best to enable Unit 193's Crosswire PPA.  You do this by adding ppa:unit193/crosswire to your system's Software Sources and then updating and installing BIbletime.  This will allow the latest version to be run.  I was able to successfully build Bibletime 2.10.1 (the latest version at this time) on Ubuntu Christian Edition 12.04.  I first built Sword 1.7.4, and installed it after deleting the older version of Sword that ships with UCE 12.04.  Then, I added the Cmake backport for Ubuntu 12.04 by adding ppa:kalakris/cmake to my Software Sources and updated and installed cmake.  Then I built Bibletime 2.10.1.  if, you rebuild Sword, then you'll also have to rebuild any other software which is a dependant of Sword, if you want to use it.  This includes Xiphos, which I successfully built the latest version (4.0.2) on UCE 12.04.  This also includes Biblememorizer which hasn't been updated since 2009.

---

### Post by Saunter on 2015-04-29
ronbu, I reinstalled 14.04 from CD and that fixed the problem.  Bibletime works now.

---

### Post by ronbu on 2015-04-29
Saunter, it's good that Bibletime works well for you!

---


---
title: "Re-install Advice needed"
date: 2011-11-10
forum: Ubuntu Studio
---

### Post by PcMojo on 2011-11-10
Hey all!  I was wondering if I could get some advice from those of you who have had to do the dreaded “re-install”.  I am currently working on a problem in another thread and the least aggravating answer might be to do a re-install. While most of the *buntu versions are pretty straightforward with the initial install process, I’ve had difficulty in the past doing re-installs. In particular, I want to manually install onto a specific partition, as opposed to the installer automatically trying to create a new one. Anyone know how to do this? 
  Also, I am currently running a multi-boot XP and Ubuntu Studio. I also like to test other distros from time to time. Sometimes the last installed distro will have its Grub file “take over”. Then I can’t blow away the test distro without having Grub issues. Is there any way to “write protect” the Ubuntu Studio Grub files or keep other distros from making their Grub primary?
  Thanks for any help you can offer!

---

### Post by 1clue on 2011-11-10
Sorry I can't really help on some of this.  I've been using the server install and put my own xorg stuff on separately, so EVERYTHING is 'manual'.

If you're staying inside of a version (11.10 to 11.10 for example) then you can save your entire HOME directory.  Otherwise just export your email contacts, firefox bookmarks and anything else, then archive your entire home directory.  Copy over files one at a time, don't bother with settings files because they're often not compatible and/or won't run an upgrade script if you manually install the old settings.

My main reason for posting:
If you just want to try out a distro, then use VMware or Xen or similar.  It lets you do anything you want without worrying about trashing your system.  It also lets you simultaneously run more than one operating system.  This includes Windows, Linux, whatever.

---

### Post by PcMojo on 2011-11-10
It's funny you should mention that, I've been thinking of that for a while and just downloaded Vmware and VirtualBox.  Thanks!

---

### Post by sgx on 2011-11-10
Hi, pclinuxos has a great installer, that covers the features
you mention, but most installers have an advanced option, at the 
beginning, that allow choosing partitions, and where to place the mbr. The easiest way is to get a couple of external drives and usbsticks for testing. And separate /home partitions saves lots of needless reconfigurations.

here is a gparted tutorial page

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

and

[http://www.gnu.org/s/parted/manual/parted.html](http://www.gnu.org/s/parted/manual/parted.html)

is a manual page for the underlying parted app. 


I like having several wildly different linux versions to keep me on my toes. Ubuntu Mint, Bodhi E17, Macpup, pclinuxos, and Puppy Studio.

---

### Post by PcMojo on 2011-11-13
Great Links! I wish I would have had them a year ago! Your list of Distros is very similar to what I have tried or plan on trying. I plan on having a multiboot with multiple Linux distros. What I really want is the ability to directly boot into more memory intensive installs such as Ubuntu Studio, but for other needs use virtual technology. So now I am on a mission to find a distro with the smallest footprint that can act as a virtual host. I don't know if Puppy can handle being a virtual host. I'll probably end up with a distro meant for older hardware with E17 or Lxde front end. I'm going to post another thread soon to see what other people's experiences have been trying to find a good virtual host distro.

---


---
title: "Conflict Exists between v4.3 &amp; 5.0 - How &amp; Why to Upgrade?"
date: 2016-02-23
forum: Virtualisation
---

### Post by Rick St. George on 2016-02-23
Originally sent this message via Email;

> 
 Have currently VBox v4.3 installed on Ubuntu v14.04
 Downloaded VBox v5.014-105127-ubuntu-trusty

 Using GDebi Pkg Installer v0.9.5.3 I get a message in the window
 Status: ERROR Conflicts with the installed pkg 'virtualbox-4.3'

 Any suggestions? I thought I would upgrade before Exporting from
 my Desktop to my Laptop. Thanks for any advice and your time!


Received this Reply;

> 
From: Software Development Director, VirtualBox ORACLE Deutschland B.V.

To get help with such problems please go to our forum.

Regarding your problem: The conflict between the VirtualBox 4.3
package and the VirtualBox 5.0 package is intended. If you use
a package manager like aptitude it will suggest you to remove the
4.3 package before installing the 5.0 package and this is the
correct way to resolve this conflict. No harm will be done to your
virtual machines when you uninstall the VirtualBox 4.3 package.

  
I have 4.3 running perfectly with lots of data for Trading, including Trading Software that I can't afford to lose!

Question: How do I upgrade without losing all my Data and installed Software? And Do I really need to Upgrade?

I understand uninstalling 4.3 and installing 5.0. But reading other posts ... they've lost all data and files in previous VM. Logically thinking, I could Export the VM, and after installing v5.0 - IMPORT the previous VM. However, I am unsure if v5.0 will import from an earlier version as the above message proves there is a "conflict" by design, but yet also states - "No harm will be done" !?!?!  Confused !!! If it ain't broke - Don't fix it. 

Do I really need to upgrade?


Thanks!
Rick

---

### Post by Rick St. George on 2016-03-10
Moreover, Ubuntu v16.04 will be out in April. Will wait till then ... So, wouldn't it be best to upgrade the Distro before VB? 
Curiously Logic,
Thanks!
Rick

---

### Post by QIII on 2016-03-10
So long as you don't destroy the virtual disk (which simply uninstalling should not do), the you should be able to uninstall the old, install the new and create new macines using the same virtual disks.

When you uninstall, don't use "purge" if your virtual disks are in your /home directory in the default vbox directory or you will lose them along with your vbox directory.  Your machines should also be preserved if you do not use purge.

As a precaution, you could make backups of the disks in a safe location for good measure.

It's the preservation of the virtual disk that is the key.

---

### Post by Rick St. George on 2016-03-10
Is there a better choice for Backup? I see under;

1. FILE / IMPORT APPLIANCE; and EXPORT APPLIANCE.
2. Also under FILE / VIRTUAL MEDIA MANAGER, under HARD DRIVERS tab - I can COPY the existing VDI.
3. Or I can copy the Folder under /home/Virtual Box VMs/ to another partition.

Just curious if it matters which one is better, or all the same. But also, should I wait until I UPGRADE UbuntuStudio to v16.04 ???

Thanks!
Rick

---

### Post by deadflowr on 2016-03-11
3 is simplest.
But there is no need as remove or purge does not remove files from home.

---

### Post by QIII on 2016-03-11
> **deadflowr said:**
> But there is no need as remove or purge does not remove files from home.

Right you are, of course.  I will blame this on a past-50 brain fart and pretend I didn't write that...

---

### Post by MAFoElffen on 2016-03-11
You two are sort of both right.

Based on the feedback from Oracle-- The reason to remove the program VirtualBox version 4.3 before installing 5.0.x... The new package does not check for an installed instance of VirtualBox. It does not upgrade, does not remove a previous install, it only installs new.

So being mixed version on the same machine using the same API calls... It would make sense that there would be conflicts. 

An 'apt-get remove' on that would leave the VM's, and only remove the program itself.

---

### Post by Rick St. George on 2016-03-11
> **MAFoElffen said:**
> An 'apt-get remove' on that would leave the VM's, and only remove the program itself.

So, would be OK (you think) to Upgrade VirtualBox before Upgrading UbuntuStudio to v16.04 in April?
If so, would be the Terminal Command be? 

```
 sudo apt-get remove virtualbox 
```

Thanks!
Rick

---

### Post by MAFoElffen on 2016-03-12
Well... I'm running (Oracle) VirtualBox 5.0.x on one of my Machines now. Other here are running Ubuntu's packaged VirtualBox 5.0.16(?), which was released into the repo's last week. That version of VirtualBox is stable.

I've been running Ubuntu 16.04 for the past 5 plus months... but testing Ubuntu Dev versions for over 4 years, there is always a transition period of about a week, after they put the pieces back together for the release. where they have to fine tune it for the myriad of unknown factors that wasn't uncovered during testing.

The LTS release is now about a month away... But it is a really good release, well worth the upgrade from 14.04. I (personally) wait about a week or so after the initial release before jumping in with my main (non-test) machines. I've already upgraded some of my servers. (there is little left in the final of those).

But then again, I'm used to having to fix dev version issues...

---

### Post by Rick St. George on 2016-03-13
Great Thanks! And for anyone else interested, here is the info on HOW TO DO IT...
[http://ubuntuhandbook.org/index.php/2015/07/install-virtualbox-5-0-ubuntu-15-04-14-04-12-04/](http://ubuntuhandbook.org/index.php/2015/07/install-virtualbox-5-0-ubuntu-15-04-14-04-12-04/)

Case Closed !

---


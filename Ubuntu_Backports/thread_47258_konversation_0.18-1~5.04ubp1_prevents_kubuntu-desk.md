---
title: "konversation 0.18-1~5.04ubp1 prevents kubuntu-desktop from being installed"
date: 2005-07-07
forum: Ubuntu Backports
---

### Post by jcohen on 2005-07-07
Backport's konversation package is broken as it depends on kdelibs4 3.4.1. It should depend on kdelibs4 3.4.0. Because of this incorrect dependency, users can not install kubuntu-desktop and are being told to install KDE 3.4.1 on their Hoary systems to fix the problem. This is completely unecessary and is potentially dangerous as it may make upgrades to Breezy more difficult. Please either remove konversation from backports or fix this dependency issue. 

TO INSTALL KDE WITH BACKPORTS ENABLED FOLLOW THESE INSTRUCTIONS:

1) sudo apt-get install konversation=0.16-1ubuntu1
2) sudo apt-get install kubuntu-desktop

If you feel more comfortable with the synaptic graphical installer follow these instructions: 

Bring up synaptic and search for konversation. Highlight the konversation package and then select Package > Force Version from the menu and select 0.16-1ubuntu1 (hoary). After that, hit apply to install. Once that's complete you can install kubuntu-desktop or the kde meta-pacakge.

---

### Post by Seth on 2005-07-07
[QUOTE=jcohen]Backport's konversation package is broken as it depends on kdelibs4 3.4.1. It should depend on kdelibs4 3.4.0. Because of this incorrect dependency, users can not install kubuntu-desktop and are being told to install KDE 3.4.1 on their Hoary systems to fix the problem. This is completely unecessary and is potentially dangerous as it may make upgrades to Breezy more difficult. Please either remove konversation from backports or fix this dependency issue. 

TO INSTALL KDE WITH BACKPORTS ENABLED FOLLOW THESE INSTRUCTIONS:

1) sudo apt-get install konversation=0.16-1ubuntu1
2) sudo apt-get install kubuntu-desktop

If you feel more comfortable with the synaptic graphical installer follow these instructions: 

Bring up synaptic and search for konversation. Highlight the konversation package and then select Package > Force Version from the menu and select 0.16-1ubuntu1 (hoary). After that, hit apply to install. Once that's complete you can install kubuntu-desktop or the kde meta-pacakge.[/QUOTE]
 Mez packaged Konversation with deps on 3.4.1 so users would upgrade. There is nothing wrong with upgrading to KDE 3.4.1 and you should do it to have the newest bugfixes and patches. There are Kubuntuized debs available for KDE 3.4.1 at [http://kubuntu.org](http://kubuntu.org)

---

### Post by jcohen on 2005-07-07
That is absolutely incorrect. 

A) I don't see why the package couldn't be built against KDE 3.4.0 kdelibs4. I bet it wasn't because it was simply rebuilt with breezy source and the dependencies were never altered. This is why packages should be built on a fresh hoary install. It was probably built on a system with KDE 3.4.1 installed from the Kubuntu sources.

B) If it is really necessary to require KDE 3.4.1 to run konversation, users should be WARNED BEFORE HAND on the website that they need kubuntu sources for KDE 3.4.1 to use backports! Otherwise, you're leaving a user's system broken. 

Oh, and what exactly is so compelling about konversation 0.18 to require KDE 3.4.1. Here's the changelog - [http://konversation.kde.org/](http://konversation.kde.org/)

---

### Post by Seth on 2005-07-07
[QUOTE=jcohen]That is absolutely incorrect. 

A) I don't see why the package couldn't be built against KDE 3.4.0 kdelibs4. I bet it wasn't because it was simply rebuilt with breezy source and the dependencies were never altered. This is why packages should be built on a fresh hoary install. It was probably built on a system with KDE 3.4.1 installed from the Kubuntu sources.

B) If it is really necessary to require KDE 3.4.1 to run konversation, users should be WARNED BEFORE HAND on the website that they need kubuntu sources for KDE 3.4.1 to use backports! Otherwise, you're leaving a user's system broken. 

Oh, and what exactly is so compelling about konversation 0.18 to require KDE 3.4.1. Here's the changelog - [http://konversation.kde.org/](http://konversation.kde.org/)[/QUOTE]
 I don't believe there is anything preventing Konversation from being built against 3.4.0, but nor is there a reason not to be running KDE 3.4.1. Any user who is using backports obviously wants the latest packages... why not KDE 3.4.1 as well?

In addition, Konversation with deps on 3.4.1 doesn't break your system or anything else. It just will not install.

---

### Post by jcohen on 2005-07-08
I don't care that much that konversation won't install. What bothers me is that by making konversation depend on KDE 3.4.1 you're preventing many hoary users from installing KDE because both kubuntu-desktop and the meta package kde requires konversation and konversation can't be installed without, a) forcing the hoary version (shouldn't be necessary) or b) installing KDE 3.4.1. As I said in my last post, if you want to require users to install KDE 3.4.1 to use your packages- that's fine, but you have to TELL THEM FIRST. Otherwise, they're just going to wonder what's going on when they can't install KDE! 

Also, there's no reason to force users to install KDE 3.4.1. If they want to install KDE 3.4.1, that's fine, but why require them to do so to install one package? If you required kdelibs4 3.4.0 or higher, any user with 3.4.0 or 3.4.1 could install the package. Despite what you may think, many users use Backports not simply to have the latest version of all packages but to in particular have the latest version of desktop applications or to get packages which are missing from hoary. Installing KDE is a large alteration to the system and it requires installing over a 100 new packages including many libraries. Backports is now an official project and one of the guidelines is that libraries shouldn't be backported. All backported packages are supposed to work with a base hoary system with hoary libraries. You have ignored that rule for no good reason that I can see.

---

### Post by Mez on 2005-07-08
Actually it wasnt for no good reason.

I built a few things in a pbuild witht eh latest version of kubuntu... not realising that I'd copied them across to the pbuild ;)

Since then I've rebuilt other things to work back with hoary base... this must be one I've missed, therefore, I'm recompiling now as we speak, and it'll be uploaded and mirrored out as soon as humanly possible

I apologise for the problems this may have caused, it was a system-level error for me, and i thought I'd fixed everything.

I'll increase the version number on this just so I can be sure that the changes get pushed out to everyone.

---

### Post by jcohen on 2005-07-08
I appreciate the quick response. I support the Backports project for the work they have done to provide Ubuntu users which packages unavailable in Hoary (especially from hoary-extras) but I think as Backports transitions to an official project more work will have to be done to ensure quality control. This package should not have left the staging area with this dependency issue preventing the install of KDE. There have also been numerous posts on the forums about this issue which is why I'm puzzled that it took this long for the issue to be resolved.

---

### Post by Mez on 2005-07-08
I've only seen errors with other packages, whcih is why I sorted this ASAP

When we move to official status, the sbuild will automatically run against a clean hoary chroot.

---


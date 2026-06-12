---
title: "LMMS: Outdated package needs some bug fixes."
date: 2012-11-27
forum: Ubuntu Application Development
---

### Post by TREESofRIGHTEOUSNESS on 2012-11-27
First, I will relay my story, and then ask the question:
I am a Ubuntu user, and I am active in reporting bugs, some beta testing, etc.  I've started reading the Debian packing documentation and it is immense.  I am particularly interested in music making/recording programs and have grown very fond of LMMS.  A few release cycles ago, the program stopped showing up in the USC under the Audio/Video section, and it also fails to show up in the dash and other menus because it has no lmms.desktop file.  This has been reported in launchpad, and there is no active maintainer for the project.  So I began digging around and e-mailing everyone I could, and suddenly I was made the package maintainer by the person who it was defaulted to previously.
So....

I need HELP.  I simply wanted the bugs to be fixed, and now here I am in charge of fixing them, and I don't know where to go from here.  Links are helpful.  People that I can e-mail are helpful.  Anything to get me going in the right direction will greatly help.

---

### Post by cariboo on 2012-11-30
You'd probably be better off asking for help on IRC, #ubuntu-devel, or on the ubuntu-devel mailing list, as developers generally don't frequent the forums. This sub-forum is for people that are developing new applications specifically for Ubuntu.

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-30
> **cariboo907 said:**
> You'd probably be better off asking for help on IRC, #ubuntu-devel, or on the ubuntu-devel mailing list, as developers generally don't frequent the forums. This sub-forum is for people that are developing new applications specifically for Ubuntu.

For sure.  They have definetly been much more helpful.

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-30
But just for posterities sake, I will record some valuable info I found out from the #ubuntu-devel irc channel...  I'll just use lmms for the examples
The Ubuntu software-center looks at the lmms.desktop contained in the binary.  If the package is in a ppa, this comes from an untrusted source and wont work, though the description will appear nicely.  
Secondly
/usr/share/app-install/desktop/ should contain a file for that program like lmms:lmms.desktop
If this isn't the case (which neither desktop file install for lmms)
you need to release a good one in the upcoming release.
Patching it is probably hard (I will find out I suppose)
One must go about adding it to "app-install-data-ubuntu"
I am going to leave this question open, so I can post the full solution here when it is solved.

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-11
Ok, the real issue with lmms was in the debian folder.
The lmms.install file was missing the line
```
usr/share/applications*
```
which tells the installer to install the desktop file there.
This ALSO will tell the software-center about the program, and list it in the appropriate category, etc...

---

### Post by TREESofRIGHTEOUSNESS on 2013-03-19
"This ALSO will tell the software-center about the program, and list it in the appropriate category, etc..." is apparently not true, however a *new* version is now in Raring Ringtail!!

---


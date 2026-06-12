---
title: "Idea: Wubi should let user select the ISO file or CD drive to be used for install"
date: 2009-12-26
forum: The Cafe
---

### Post by csh on 2009-12-26
[[IMG]http://brainstorm.ubuntu.com/idea/22824/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22824/)

_Rationale_
This is not about the bug in Wubi, but suggestion for feature in Wubi.

This feature suggestion was somewhat related to bug #488319 I reported at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488319](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488319) . I know that Wubi automatically select the ISO file to be used for Ubuntu installation. Even if Wubi run from Ubuntu CD, but it will still search for ISO image file of Ubuntu or its derivative distro.

About the bug I reported in the link above, Wubi run from the Ubuntu CD, but it use the xubuntu iso file located in my hard drive.

So, for Wubi downloaded from the internet, why not having an option to let the user browse and choose the correct ISO image file for installation?

And, for the Wubi bundled with Ubuntu CD, why not disable the ISO file search function and directly use the CD? 

_Solution #1: Having an option let the user browse and choose the correct ISO file._

For the Wubi installer file that can be downloaded from Wubi website, the following features should be implemented.

1. User will be able to browse and select the correct ISO image file for Ubuntu and its derivative distro (Kubuntu, Xubuntu, Edubuntu, etc).

2. If Wubi installer is run inside the folder same with the ISO image file, the ISO file will be automatically selected, BUT USER WILL BE ABLE TO CHOOSE ANOTHER ISO IMAGE FILE IF THEY WISH TO DO IT.

3. Wubi will verify whether the user selected ISO image file is a correct ISO image file for the chosen Ubuntu derivative distro.

For the Wubi bundled with the Desktop CD, the function for searching the ISO file should be disabled to prevent searching for ISO file in internal or external hard drive, and directly use the CD.

---

### Post by Psumi on 2009-12-26
I like solution 2 better to be honest.

---

### Post by csh on 2009-12-30
> **Psumi said:**
> I like solution 2 better to be honest.

To be honest, solution 2 will cause the following problems:
1. Users who requested free cd have to download the ISO file instead of using the received free CD.
2. Some users may delete the downloaded ISO file after burn to CD, to save disk space. In this case, they have to re-download the ISO file again.

This will be hassle.

---

### Post by Psumi on 2009-12-30
> **csh said:**
> To be honest, solution 2 will cause the following problems:
1. Users who requested free cd have to download the ISO file instead of using the received free CD.
2. Some users may delete the downloaded ISO file after burn to CD, to save disk space. In this case, they have to re-download the ISO file again.

This will be hassle.

It's still a better idea than removing GIMP from the liveCD.

---


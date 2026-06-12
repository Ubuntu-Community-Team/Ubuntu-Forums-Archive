---
title: "Installing Windows after Ubuntu &quot;Setup was unable to create a new system partition&quot;"
date: 2015-07-09
forum: Windows
---

### Post by eMshsWE on 2015-07-09
Hello, I have a Hp Pavillion dm4 laptop running Ubuntu 14.04 and now want to install Windows 7 64 bit and make the laprop dual booted. I burnt the Windows installation iso  file onto a pen drive and booted from it. It runs till the dialog box "where do you want to install Windows", It shows the following partitions on my Hard Drive. 

I am also attaching a screenshot of output of GParted from my Ubuntu. It shows 50.5 GB as unknwon file system, and thus I would like to install Windows 7 on to this partition.

I guess in the windows 7 installation setup, it shows 50.5 GB as System partition and that is the same partition that is pointed to by Gparted.

However, when I click on "Next" when trying to install  Windows it says

**Setup was unable to create a new partition or locate an existing system partition. See the Setup log files for more information.**

I have no idea why this error is being thrown. Could someone please help me out?

---

### Post by yancek on 2015-07-09
I have no idea why you are getting that message.  You might try using GParted to format whichever partition you want to install windows to as ntfs before beginning the install.  I don't see why that would be necessary but I haven't used windows for some time.  If you do this, make sure you get the correct partition.

---

### Post by thomas52 on 2015-07-11
you should first install windows 7 by formatting total hard drive and then install ubuntu, this will help u to cleanly install ubuntu and windows as well, ubuntu will automatically recognise that there is already installed os on ur drive and u can install ubuntu by selecting this option 


:- i**nstall ubuntu alongside windows **

good luck buddy

---


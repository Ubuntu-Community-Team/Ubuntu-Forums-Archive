---
title: "Virus Scanner antivirus engine update"
date: 2009-08-05
forum: Security
---

### Post by hihihi100 on 2009-08-05
Hi there:

Yes, I know Linux is virtually virus-free, but I still transfer files from a windows based laptop to a Ubuntu based one.

I've been updating the virus scanner, but I dont know how to update the "Antivirus Engine". Can any of u give me any tip? GUI version and virus definitions are updated.

Cheers

---

### Post by cariboo on 2009-08-06
If you transfer files from Windows to Linux, you have nothing to worry about, as Windows executables will not work on Linux. You can update to the lastes version of clamav [here]("http://launchpad.net/~ubuntu-clamav/+archive/ppa") you will have to use the version for Karmic Koala.

---

### Post by l951b951 on 2009-08-07
> **cariboo907 said:**
> If you transfer files from Windows to Linux, you have nothing to worry about, as Windows executables will not work on Linux. You can update to the lastes version of clamav [here]("http://launchpad.net/~ubuntu-clamav/+archive/ppa") you will have to use the version for Karmic Koala.

Is there any risk to using the older engine found in the Repositories?

---

### Post by cariboo on 2009-08-07
Considering you are only scanning for windows viruses, unless the new version has a feature you desperately need, I would stay with what you've got. Just make sure to keep the definitions up-to-date.

---

### Post by oktapod on 2009-10-21
[http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)

---

### Post by nmyrick on 2010-08-24
Here is the download link for the latest ClamAV Antivirus Engine as of 8/24/2010 (version 0.96.2), but I have yet to figure out how to install it. Can anyone help with this?  It just downloads as an archive package.

[http://sourceforge.net/projects/clamav/files/clamav/0.96.2/clamav-0.96.2.tar.gz/download](http://sourceforge.net/projects/clamav/files/clamav/0.96.2/clamav-0.96.2.tar.gz/download)

Neil

---

### Post by cariboo on 2010-08-24
If the file is a tar.gz file, just double click the file name and let file-roller extract to the location of your choosing, then check the readme or install instructions for what to do next.

---

### Post by nmyrick on 2010-08-25
Yes I know, but that's the million dollar question.  The files in the Tarball would have to replace the files for version 0.96.1, so where do I extract it to?

All the readme file contains are change logs from the previous versions, and the website that it directs me to for upgrade instructions [http://wiki.clamav.net/Main/UpgradeInstructions](http://wiki.clamav.net/Main/UpgradeInstructions) is also less than helpful.

---

### Post by nmyrick on 2010-08-25
There are some more detailed instructions now that I look at [http://wiki.clamav.net/bin/view/Main/InstallFromSource](http://wiki.clamav.net/bin/view/Main/InstallFromSource) , but I'll have to try it on another day.  Thanks for your help, cariboo907.

---


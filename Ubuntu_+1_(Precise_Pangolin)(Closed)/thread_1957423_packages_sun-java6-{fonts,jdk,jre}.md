---
title: "packages sun-java6-{fonts,jdk,jre}"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-12
The packages sun-java6-{fonts,jdk,jre} were in the partner repository in previous versions of Ubuntu we were running. The plan is to upgrade to 12.04 LTS and I'm testing things on Beta2 right now.  But these packages are not found even on the partner repository.

Is there a preferred alternative?  Is there another repository for them?  Any other ideas?

---

### Post by roelforg on 2012-04-12
One word: Open-JDK
They're gone because they're closed source and some licences conflicted.

---

### Post by cariboo on 2012-04-12
The Oracle version of java will no longer be available for download from the repositories, see this wiki article:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition)

---

### Post by na5h on 2012-04-12
As roelforg stated, Open JDK can be found in the Software Center. Oracle Java (former Sun Java) is still available, but it must be downloaded and installed manually from Oracle's website.

---

### Post by craig10x on 2012-04-12
Rather then having to manually compile it from oracle (which is a pain in the backside...lol), if you like to have the licensed version, see this link from the linux mint forums...

With 4 simple terminal commands (just copy/paste and enter each command 1 at a time...waiting for the terminal to do it's thing for each one you enter) and you'll have it in just a few minutes...

This is a pre-packaged deb file that automatically installs the latest version...
the post also shows a command you can use to update the version, should a newer one come out and you want to grab it...

[http://forums.linuxmint.com/viewtopic.php?f=42&t=93052](http://forums.linuxmint.com/viewtopic.php?f=42&t=93052)

I have in installed on my ubuntu 12.04 and it works great!
Hope that helps...

---

### Post by williammanda on 2012-04-12
Go here an install jdk version 7...simple:

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by sammiev on 2012-04-12
[Java-6-31]("http://sites.google.com/site/easylinuxtipsproject/java") can be found here if you do not like to use any PPA. :)

---

### Post by Skaperen on 2012-04-13
Do you know which ones work correctly with the Android emulator?  Previously the sun-java6 was used because the others would not work.

---


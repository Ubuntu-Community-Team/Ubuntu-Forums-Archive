---
title: "Security/ExecutableBit"
date: 2010-06-04
forum: Security
---

### Post by boarder428 on 2010-06-04
Just upgraded to 10.04 LTS and am having problems opening programs with wine that I was able to open before.  Get the following error...
```

The file '/home/corey/Dropbox/KeePass.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```
tried the "read executable bit" link but has no resolve posted.
[https://wiki.ubuntu.com/Security/ExecutableBit]("https://wiki.ubuntu.com/Security/ExecutableBit")
Corey

---

### Post by madverb on 2010-06-04
```
chmod uga+x /home/corey/Dropbox/KeePass.exe
```

---

### Post by FuturePilot on 2010-06-05
There is also a native Linux version of KeePass called KeePassX which is in the repos. Any particular reason you're running the Windows version in Wine?

---

### Post by bodhi.zazen on 2010-06-05
> **futurepilot said:**
> there is also a native linux version of keepass called keepassx which is in the repos. Any particular reason you're running the windows version in wine?

+1

---

### Post by boarder428 on 2010-06-05
> **FuturePilot said:**
> There is also a native Linux version of KeePass called KeePassX which is in the repos. Any particular reason you're running the Windows version in Wine?

I also use windows and need the ability to open this file on both os's
What's the deal with the security/executable bit thing, is this new and do I have to run the chmod command on any executable I try to open with wine?

---

### Post by FuturePilot on 2010-06-06
> **boarder428 said:**
> I also use windows and need the ability to open this file on both os's
What's the deal with the security/executable bit thing, is this new and do I have to run the chmod command on any executable I try to open with wine?

There are no compatibility issues between the Windows version and the Linux version. Both can read and write to the same file. They are essentially the same program.

---

### Post by boarder428 on 2010-06-06
> **FuturePilot said:**
> There are no compatibility issues between the Windows version and the Linux version. Both can read and write to the same file. They are essentially the same program.

Thanks for the info!  I was not aware of that, i'll have to give it a try.

---

### Post by boarder428 on 2010-07-08
thanks for the tip on keepassx although I could'nt find it in synaptic a google search helped me find it. [https://launchpad.net/~keepassx/+archive/ppa]("https://launchpad.net/~keepassx/+archive/ppa")I did seem to have some issues adding the repo in Lucid,the command just seemed to hang.  I did find this build and it installed great. [https://launchpad.net/ubuntu/+source/keepassx/0.4.3-1/+build/1554244]("https://launchpad.net/ubuntu/+source/keepassx/0.4.3-1/+build/1554244")  I need to learn how to compile source, are there any links availible for beginners?

---

### Post by bodhi.zazen on 2010-07-08
> **boarder428 said:**
> thanks for the tip on keepassx although I could'nt find it in synaptic a google search helped me find it. [https://launchpad.net/~keepassx/+archive/ppa]("https://launchpad.net/%7Ekeepassx/+archive/ppa")I did seem to have some issues adding the repo in Lucid,the command just seemed to hang.  I did find this build and it installed great. [https://launchpad.net/ubuntu/+source/keepassx/0.4.3-1/+build/1554244](https://launchpad.net/ubuntu/+source/keepassx/0.4.3-1/+build/1554244)  I need to learn how to compile source, are there any links availible for beginners?

keepassx is in the repos

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=KeePassX](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=KeePassX)

To compile software see:

[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

Most of the problems compiling applications are due to missing dependencies.

---


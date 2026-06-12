---
title: "Trusty 14.04 missing ia32-libs-multiarch:i386"
date: 2013-10-24
forum: Ubuntu Development Version
---

### Post by sparker256 on 2013-10-24
I do not see ia32-libs-multiarch:i386 in Ubuntu Software Center or Synaptic Package Manager.

Is this because extra is not online yet or some other reason?

Thanks Bill

---

### Post by mc4man on 2013-10-25
It was removed in 13.10

---

### Post by sparker256 on 2013-10-25
> **mc4man said:**
> It was removed in 13.10
I wonder then in my Ubuntu 13.10 install how I show it installed in Software Package Manager and Synaptic Package Manager. 

Bill

---

### Post by sparker256 on 2013-10-25
With this being a LTS version and if ia32-libs-multiarch:i386 is no longer available then I cannot run X-Plane 10 32bit on a 64bit system.

I had thought that the reason for multiarch was so you could run 32bit apps on 64bit systems but with this info that does not seem to be true.

Bill

---

### Post by Mateusz Stachowski on 2013-10-26
The multiarch packages are still available but ia32-libs is not. That package pulled many 32-bit libs on a otherwise 64-bit system and was a huge hack. 

In Ubuntu 13.10 and onward you supposed to install 32-bit libraries for the programs that aren't part of repositories using :i386 [packages]("http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package"). If X-Plane doesn't depend on ia32-libs then you can make it to work on 13.10. I already installed AdobeAIR on Saucy using the .bin installer and that doesn't need ia32-libs but the packages for AIR have that as dependency and are unusable. 

You can find out what :i386 packages you need to install with ldd.

```
ldd '/home/mateusz/Pobrane/X-Plane 10 Demo Installer Linux'
```

The path looks that way because I simply drag and dropped the binary in Terminal (it's the easiest way). On my install all the dependencies are already satisfied and the installer starts without any problems.

---

### Post by erkiha on 2013-10-28
Essentially the same thing applies to Teamviewer and Citrix receiver, solution can be found in this thread: [Link]("http://ubuntuforums.org/showthread.php?t=2166020")

---

### Post by Marlon_Molina on 2014-05-06
You should try this.. I am on 14.04 LTS version and it worked for me when I was trying to Ziplalign a ROM. 

[http://ubuntuforums.org/showthread.php?t=2182653](http://ubuntuforums.org/showthread.php?t=2182653)

---

### Post by cariboo on 2014-05-06
14.04 has been released, please continue this in General Help. Thread closed

---


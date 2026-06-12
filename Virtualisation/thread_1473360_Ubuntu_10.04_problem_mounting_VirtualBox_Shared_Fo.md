---
title: "Ubuntu 10.04: problem mounting VirtualBox Shared Folders at startup"
date: 2010-05-05
forum: Virtualisation
---

### Post by lmarmisa on 2010-05-05
I have installed Ubuntu 10.04 as a virtual machine of VirtualBox in a XP Pro host system. Then, I have installed the VB Guest Additions and I have defined one shared folder named "**share**" that is mapped in **/media/share**. I have added this line to the **/etc/fstab** file for an automatic mounting:

 **share /media/share vboxsf defaults 0 0**

I have repeated this installation procedure with previous Ubuntu releases and it worked fine.

But something is different with 10.04. I get a (silly) message at start-up telling "**An error occurred while mounting /media/share. Press S to skip mounting or M for manual recovery**". Then, if I press S, the start-up sequence continues normally and the folder is mounted automatically as expected.

The problem is not very important, but the start-up sequence is not automatic now: I have to press the S key at every start-up. :mad:

I suppose that the stupid message is originated by some start-up shell script file, but I am not able to locate this file.

I would appreciate any help for fixing this problem.

Thanks in advance.

Best regards,

Luis

---

### Post by k00lman on 2010-05-05
Exactly the same problem, but reading this:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9225175](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9225175)
helped me solve it.

---

### Post by lmarmisa on 2010-05-05
Thanks a lot for your information, k00lman. This workaround is very useful.

Best regards,

Luis

---


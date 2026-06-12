---
title: "grub2 can't see hd1 from inside VirtualBox"
date: 2012-05-18
forum: Virtualisation
---

### Post by mikeydeeeee on 2012-05-18
Hey gang, trying to get a copy of Windows XP (installed on the first partition of my second hard disk) to run within VirtualBox.  The method (from [here]("http://ubuntuforums.org/showthread.php?t=769883") and [here]("http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/")) involves creating a bootable iso of my grub2 configuration and loading the environment through that.

After several attempts to boot XP, I eventually realized it was failing because grub2 can't see my second hard disk, and therefore any attempt to reference it or any of it's filesystems fail.  This probably isn't the only problem, but it's obviously one I'll have to solve before I get there.

So anyway, if anybody out there has solved this or similar problems, I'd be thrilled to hear from you.  My machine is a Dell 5100 running Ocelot 64 bit, Vbox version 4.1.14 from the Sun site, although I got the same error from the regular dist version (4.1.2  I think).  If anybody wants more info (like the grub.cfg or the actual error messages) I'll be glad to post it, but I was hoping someone might have a quick answer.

Thanks,
MikeD

---

### Post by wilee-nilee on 2012-05-18
So if I get this correct you have XP there and want to boot it with grub, if you don't have a actual OS installed with grub you can just load the windows bootloader if you havs XP cd. Grub can be setup to run without a os though. To use grub by itself to boot XP is the long way to go there is actually a bootloader called lilo that would do the boot.

The best way for us to see, at least me anyway to see, what you have would be to boot a live ubuntu cd in that virtual set up and download this link extract it to your desktop and run the command. This generates a results.txt, then copy and paste all the text from that to a reply. When you do this open the reply click on the # in the panel of the reply to generate code tags a then paste the text between them.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by mikeydeeeee on 2012-05-18
This is a repost of an article originally posted to the 'General Help'  forum:

Hey gang, trying to get a copy of Windows XP (installed on the first  partition of my second hard disk) to run within VirtualBox.  The method  (from [here]("http://ubuntuforums.org/showthread.php?t=769883") and [here]("http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/")) involves creating a bootable iso of my grub2 configuration and loading the environment through that.

After several attempts to boot XP, I eventually realized it was failing  because grub2 can't see my second hard disk, and therefore any attempt  to reference it or any of it's filesystems fail.  This probably isn't  the only problem, but it's obviously one I'll have to solve before I get  there.

So anyway, if anybody out there has solved this or similar problems, I'd  be thrilled to hear from you.  My machine is a Dell 5100 running Ocelot  64 bit, Vbox version 4.1.14 from the Sun site, although I got the same  error from the regular dist version (4.1.2  I think).  If anybody wants  more info (like the grub.cfg or the actual error messages) I'll be glad  to post it, but I was hoping someone might have a quick answer.

Thanks,
MikeD

---

### Post by mikeydeeeee on 2012-05-18
Thanks for the reply, but XP boots fine from grub2 normally, it's only when using VirtualBox from inside a running version of Kubuntu that I have the problem I described.

I have reposted the question to the Virtualization Forum [here]("http://ubuntuforums.org/showthread.php?p=11948757#post11948757").  Please direct any followups there.

---

### Post by cariboo on 2012-05-18
Please don't create multiple threads on the same subject, I have merged your two threads.

---


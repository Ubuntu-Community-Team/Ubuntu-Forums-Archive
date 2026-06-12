---
title: "Virtualization"
date: 2006-10-13
forum: Ubuntu Christian Edition
---

### Post by rcdeacon on 2006-10-13
I need to use ONE windows program. I routinely use Logos Bible Study Software which will run only on xp. I know that CE has vmplayer but you cannot create with it. How can I create the necessary xp files to be read with vmplayer? I do have a legitmate xp disk although I will have to get the code to authenticate since I have exceeded the allowable number of installs, but I do have it. Can anyone lead me in the right direction? Thanks.

---

### Post by mysticrider92 on 2006-10-13
Have you tried the wine software ([www.winehq.com)?](www.winehq.com)?) It is hard to get some things to work on it, but it allows you to run Windows programs on a Linux PC.

From what I saw on their web site, it looks like you will probably have to use this or xp, but I don't know for sure.

---

### Post by NetworkGuy on 2006-10-13
rcdeacon,

I came across this web page which tell you how to create a Windows XP virtual machine using VMPlayer.  YOu need to use a program called QEmu that should be available within the repositories to create the  .vmdk file.

[http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)

Be aware that the 2GB they make the .vmdk file may be too small for your needs.  I recommend at least 6GB minimum for a Windows XP virtual machine.

---

### Post by mysticrider92 on 2006-10-13
Oh.. I didn't realize that VMPlayer is used for vitual machines. I guess either one should work then, as long as you have a powerful enough computer to support both os's.

---

### Post by rcdeacon on 2006-10-13
Thanks for this valuable information. I will try to work on it later. God bless.

---

### Post by UberKnight on 2006-10-29
rcdeacon, any success?

I also use Logos Libronix Bible study software on Win2K, however, I'd love to get it working on ubuntu.  Were you able to get this working via wine?  Or did you have to use a virtual machine setup?  Did you get it working at all?

---

### Post by jinx099 on 2006-10-29
I'm surprised this wasn't mentioned before.  You should download vmware SERVER to create VMs.  It's very easy to use and fairly easy to install.  It is free from [www.vmware.com](www.vmware.com)

---

### Post by danoyoto on 2007-01-25
any updates?  I am playing around with the new release of Ubuntu CE (6.10) and am holding back because of Libronix!

---

### Post by mhancoc7 on 2007-01-26
> **danoyoto said:**
> any updates?  I am playing around with the new release of Ubuntu CE (6.10) and am holding back because of Libronix!

I use vmware server in Ubuntu CE and it works quite well. Check this thread.

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+windows+xp](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+windows+xp)

God Bless, Jereme

---

### Post by pay on 2007-01-26
There also this method for running windows programs [http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html](http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html)

---

### Post by mhancoc7 on 2007-01-26
> **pay said:**
> There also this method for running windows programs [http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html](http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html)

Now that looks awesome!! I will trying this very soon.

Thanks, Jereme

---


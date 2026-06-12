---
title: "How do I share a folder?"
date: 2008-04-06
forum: Virtualisation
---

### Post by luisjorge on 2008-04-06
Hi everyone! I just installed windows vista home premium in virtualbox, in ubuntu 8.04 beta, and everything works fine, but I can't get the shared folders to work. How should I do it? I'm trying to share just one folder in my home. Any help would be greatly appreciated!

Thanks in advance!

Luis Jorge

---

### Post by myusername on 2008-04-07
google is your friend

---

### Post by Rinzwind on 2008-04-07
It's not that hard!

[http://ubuntuforums.org/showthread.php?t=519890](http://ubuntuforums.org/showthread.php?t=519890)
> 
First you'll want to install the guest additions on your virtual machine. If you are running your machine in a window, click on Devices/Install Guest Additions to do that.

After you've got Guest Additions installed you'll notice there is a bunch of icons near the bottom right of the host window for your virtual machine. One of them looks like a folder. If you right click this folder and hit open it will show you a list of folders that are accessible to your virtual machine - since this is your first time there probably wont be anything there - just click the add folder icon the right of the list and navigate to a folder you want to share.

After you've added a folder that you want to be accessible in your virtual machine, you need to map a drive to that folder within your Windows vm. You can do this easily at a command prompt by entering the following and substituting the necessary values:

```
net use x: \\vboxsvr\share
```

where x: is the drive you want to map the folder to in your vm and \share is the folder you want to get to.

Have fun!

:) 

myusername: that's not the way to answer on these forums.

---


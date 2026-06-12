---
title: "Shrink and make ISO"
date: 2016-04-22
forum: Virtualisation
---

### Post by FerryGnu on 2016-04-22
Hi, I have Ubuntu 14.4-LTS running in VMWare Player under win8.1, with a dynamic-size max of 120gb and it is currently showing a size of 19.7gb. All good - kinda.

I read about removing old Kernels and it freed up 3/4 of the 19.7gb. 

I tried the Compact and Defrag of VMWare but not surprisingly they did nothing but waste time while I watched. I posted on the VMWare forum, but also not surprisingly, it is being ignored. 

So, Plan-B is to make an ISO of the Ubuntu installation and hopefully that process will shrink the unused space. Then I can reinstall it as a new VMachine in Player.

I would like to shrink the thing as it is currently taking half an hour to back up that 19.7gb, 3/4 of which is blank space within Ubuntu. I did some searching and can't find anything useful newer than ver12 and around 2012. I am hoping someone can point me at something simple (not Clonezilla, it is way too slow) that will make an ISO.

Thanks

---

### Post by MAFoElffen on 2016-04-24
From your VM, Please post the results of 
```

sudo df -h

```
Next information needed is to ask what format the VM's virtual disk image is? (If you do not know, please post the image filename, with it's extension.)

I read your post as that your are trying to get rid of some of the unused space in your virtual disk image, and skrink the size of the image file... Correct?

---


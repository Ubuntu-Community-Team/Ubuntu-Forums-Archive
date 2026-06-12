---
title: "Ubuntu Resolution as VirtualBox Guest"
date: 2010-07-07
forum: Virtualisation
---

### Post by ejohns2012 on 2010-07-07
Hello all,

I am having some issues with my screen size and resolution of Ubuntu when running it on VM VirtualBox on a Windows 7 machine...

The screen size of Ubuntu is only about 1/3 of my screen size and I can't set the resolution higher than 800x600...I've seen some ways to alter the parameters for maximum VirtualBox resolutions on a Linux host, but can't find any to do so on a Windows host...

Thanks in advance for any suggestions/solutions!

---

### Post by buddyd16 on 2010-07-07
If my memory is correct you need to install the guest additions in order to achieve a larger resolution.

Look through the available menus at the top of the virtual box window one of then should contain an entry saying something along the lines of "install guest additions". 

Click on "install guest additions" and an iso disc should be mounted in your ubuntu virtual machine.

Double click the iso to open it in nautilus then locate the appropriate install script for your install (32bit or 64bit) 

My memory is hazy on whether or not the script needs to be run as root or not

After the guest additions are installed you will need to restart the virtual machine and you should then be able to adjust the resolution. Note: you may need to adjust the amount of resources alloted to virtual machine for higher resolutions

---

### Post by slooksterpsv on 2010-07-09
Yes the scripts need to be run as root, but you just have to run them, they do the rest of the work.

Do this:
Click Devices -> install guest additions
Once you see it mount on your desktop click on Applications -> Accessories -> Terminal

Next type in (for x86 clients):
```

cd /media/[press tab][press enter]
sudo VBoxLi[press tab]-x[press tab][press enter]

```

For AMD64 clients( x86_64 or 64-bit in other words)
```

cd /media/[press tab][press enter]
sudo VBoxLi[press tab]-a[press tab][press enter]

```

---


---
title: "installing mac OS X in a virtual machine"
date: 2011-04-09
forum: Virtualisation
---

### Post by kinderen on 2011-04-09
hello everyone,
i have been trying a few things with virtual machines and i have been trying to find a way to intall mac OS X in a virtual machine. i have an official disk, but using virtualbox wont work. please help....

thanks,
Vince....

---

### Post by wardo1254 on 2011-04-09
To Install Mac OS X in Virtualbox you will need a boot disc/iso for what is called a Hackintosh [Non-Mac computers that run Mac OS X]. The one I used can be found ~snip~

Before you boot off the iso though you will have to turn off Efi under the system tab in the virtual machine configuration [or else the boot disc won't load] and under storage click on your virtual cd/dvd drive and enable "Passthrough" to allow the OS X disc to be read properly.

After the boot disc loads swap it for your Snow Leopard DVD [I assume you have Snow Leopard At Least]. Press f5 and in a few moments The Mac OS X Install DVD will be displayed. Type "-v" to boot it in text mode you you can Google any errors if something were to go wrong and then press enter to boot it.

If all goes well you should reach the language selection screen in a few minutes. Select English [or whatever language you prefer] and press the blue arrow at the bottom of the window.

Now we have to format the Virtual Hard Drive. On the top bar click Utilities --> Disk Utility. Then pick your HD and partition it with one partition under the partition tab. Make sure the format is "Mac OS Extended Journaled".

Close Disk Utility by again going in the menubar and selecting Disk Utility --> Exit Disk Utility.

Press continue, agree to the conditions, customize the install if you like and then press Install.

Once done the Virtual Machine will restart but when it does select the boot iso again but don't press f5 this time, instead just select the apple logo with the arrow keys and press enter.

This will boot the new osx install.

Follow thorugh the steps to set up your new "Mac" and have fun. ;)

---

### Post by Lankster on 2011-11-22
Your link is dead? could you update it please.. ty
> **wardo1254 said:**
> To Install Mac OS X in Virtualbox you will need a boot disc/iso for what is called a Hackintosh [Non-Mac computers that run Mac OS X]. The one I used can be found ~snip~

Before you boot off the iso though you will have to turn off Efi under the system tab in the virtual machine configuration [or else the boot disc won't load] and under storage click on your virtual cd/dvd drive and enable "Passthrough" to allow the OS X disc to be read properly.

After the boot disc loads swap it for your Snow Leopard DVD [I assume you have Snow Leopard At Least]. Press f5 and in a few moments The Mac OS X Install DVD will be displayed. Type "-v" to boot it in text mode you you can Google any errors if something were to go wrong and then press enter to boot it.

If all goes well you should reach the language selection screen in a few minutes. Select English [or whatever language you prefer] and press the blue arrow at the bottom of the window.

Now we have to format the Virtual Hard Drive. On the top bar click Utilities --> Disk Utility. Then pick your HD and partition it with one partition under the partition tab. Make sure the format is "Mac OS Extended Journaled".

Close Disk Utility by again going in the menubar and selecting Disk Utility --> Exit Disk Utility.

Press continue, agree to the conditions, customize the install if you like and then press Install.

Once done the Virtual Machine will restart but when it does select the boot iso again but don't press f5 this time, instead just select the apple logo with the arrow keys and press enter.

This will boot the new osx install.

Follow thorugh the steps to set up your new "Mac" and have fun. ;)

---

### Post by coffeecat on 2011-11-22
From the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy):

> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here.

From the Apple EULA:

> you are granted a limited non-exclusive license to install, use and run one (1) copy of the Apple Software on a single Apple-branded computer at a time. You
agree not to install, use or run the Apple Software on any non-Apple-branded computer, or to enable others to do so.

Thread closed.

---


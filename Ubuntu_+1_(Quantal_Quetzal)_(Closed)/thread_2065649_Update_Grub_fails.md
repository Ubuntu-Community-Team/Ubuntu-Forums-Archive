---
title: "Update Grub fails"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by awam66 on 2012-10-02
Hi folks, 
Have just come back from hols to find large upgrade for QQ and after it was complete update grub gives the following error. ```
sudo update-grubGRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.

```
Can't find anything that tels me how to fix it. Any ideas please.Sony vio laptop VGN-NR10E runnung QQ i386.

---

### Post by philinux on 2012-10-02
> **awam66 said:**
> Hi folks, 
Have just come back from hols to find large upgrade for QQ and after it was complete update grub gives the following error. ```
sudo update-grubGRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.

```
Can't find anything that tels me how to fix it. Any ideas please.Sony vio laptop VGN-NR10E runnung QQ i386.

Run this.

```
sudo dpkg --configure -a
```

---

### Post by dino99 on 2012-10-02
Dont worry its the builtin verbosy process till it end upgrading. You will see that each time grub is updated.
Its not an issue , just a confusing comment than Colin might silence (if someone let him know about ;) )

---

### Post by awam66 on 2012-10-02
> **philinux said:**
> Run this.

```
sudo dpkg --configure -a
```

Nope that did nothing, still the same message with update-grub

---

### Post by philinux on 2012-10-02
> **awam66 said:**
> Nope that did nothing, still the same message with update-grub

Dino seems to have got it then although I do not see that error.

---

### Post by awam66 on 2012-10-03
> **dino99 said:**
> Dont worry its the builtin verbosy process till it end upgrading. You will see that each time grub is updated.
Its not an issue , just a confusing comment than Colin might silence (if someone let him know about ;) )

Yes but I get this every time I issue update-grub and I know the new kernel 3.5.0-16 was installed in he upgrade but grub menu still shows 3.5.0.-14 only which is currently running. The grub menu is still the old style grub 1.99 so the grub 2 install does not seem to have worked properly, and yes, I have tried re-installing Grub2 from Synaptic.

---

### Post by dino99 on 2012-10-03
> **awam66 said:**
> Yes but I get this every time I issue update-grub and I know the new kernel 3.5.0-16 was installed in he upgrade but grub menu still shows 3.5.0.-14 only which is currently running. The grub menu is still the old style grub 1.99 so the grub 2 install does not seem to have worked properly, and yes, I have tried re-installing Grub2 from Synaptic.

That means that you have installed several grub, and that one is not the master one, thats all. As said on other threads (you might read them instead of whining about discussed issues proposing workaround):
- purge grub on every mbr (sudo dpkg-reconfigure grub-pc)
- logout/in
- reinstall grub-pc

That way you will only get one grub2.0 installed, so no more grub menu issue not been updated.

---

### Post by grahammechanical on 2012-10-03
May I add the results of my research into Grub 2.0?

update-grub is an x-shellscript in /usr/bin that says only this:

> #! /bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

Update-grub runs the application/x-executable called grub-mkconfig that is also in /usr/bin and that is all. Grub-mkconfig creates the grub.cfg script but it does not install Grub into the MBR. This is why update-grub in one install will not over-write what another install has put into the MBR.

The command to save Grub into MBR is grub-install, an application/x-executable in /usr/bin.

I also have a Grub menu that is controlled by my 12.04 install and I have found that update-grub in either of my 3 x 12.10 installs does not change the grub menu. But a fresh install of 12.10 in another partition will write its Grub into MBR.

There is also an x-shellscript called update-grub2 but it is only a sim-link to update-grub. Now, if update-grub2 included a command to run grub-install after grub-mkconfig then we would be getting somewhere.

Alternatively, we could try running grub-install in a terminal and see if that works. I may just do that.

source of knowledge: Grub 2 manual.

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

**Update to research**

I have just booted into one of my 12.10 installs using the Grub menu produced by my 12.04 install. After running

```
sudo update-grub
```

I also ran

```
sudo grub-install /dev/sda
```

And it saved my 12.10 generated Grub configuration into the MBR. so, I am now booting from a Grub menu controlled not by 12.04 but by a 12.10 install.

if you run this command

```
grub-install
```

You will get list of options. You will also see this:

> grub-install copies GRUB images into /boot/grub, and uses grub-setup to install grub into the boot sector


Regards.

---

### Post by awam66 on 2012-10-03
> **dino99 said:**
> That means that you have installed several grub, and that one is not the master one, thats all. As said on other threads (you might read them instead of whining about discussed issues proposing workaround):
- purge grub on every mbr (sudo dpkg-reconfigure grub-pc)
- logout/in
- reinstall grub-pc

That way you will only get one grub2.0 installed, so no more grub menu issue not been updated.

I am well aware of where Grub is installed I only have one MBR! I am not aware of whining about anything, merely trying to establish what has happened in the upgrade to Grub two. It works on my other three computers so I do know what I am doing and have read many threads. And have previously done all the above commands to no effect.

---

### Post by awam66 on 2012-10-06
I solved this by purging all the grub files and installing afresh after none of the above suggestions worked.

---


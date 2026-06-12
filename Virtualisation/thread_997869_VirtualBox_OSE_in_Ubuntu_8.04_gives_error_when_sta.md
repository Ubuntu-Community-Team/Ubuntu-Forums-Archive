---
title: "VirtualBox OSE in Ubuntu 8.04 gives error when starting XP"
date: 2008-11-30
forum: Virtualisation
---

### Post by SonOfOdin on 2008-11-30
Hi everyone

After this weeks mega updates I have found a few issues with my system.  The most concerning is that when I run Virtual Box OSE in Hardy (trying to get some use of XP) I get the following message...


"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"

How do I fix this?  Am I going to have to mess around with that damn add-on that gives me sound, USB, and CDRom etc?

Thanks for your help :)

J!

---

### Post by dutchman72 on 2008-11-30
This error message most likely pops up now after all the updates because the original kernel module no longer works wth this kernel version. Try running 'sudo apt-get install viartualbox-ose-modules-generic' from terminal to get a version that will work for all kernels.

---

### Post by SonOfOdin on 2008-11-30
Hey Dutchman

I tried your suggestion.  The latest version of the modules are installed, and running this command gives me this feedback.

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Nothing has changed with regards to the error given earlier.

So, I ran  'sudo apt-get remove virtualbox-ose-modules-generic' and then tried again.

Unfortunately, this changed nothing.  Even after reboot.

Any ideas?

---

### Post by SonOfOdin on 2008-12-02
Sorry about the blatant bump to this thread, but I have had no success in getting my XP to boot.

If I do a fresh reinstall of Virtualbox, will I have to re-install XP also, or will it be accessable to the fresh install of VBox?

I havent had the courage to try, because I cant lose the documents in the OS' files system.

Thanks

---

### Post by bodhi.zazen on 2008-12-02
You may wish to use Virtualbox from Sun rather then the OSE.

---

### Post by SonOfOdin on 2008-12-05
Actually, all I wanna do is get my XP back.  OSE was fine for my needs.

---

### Post by vince_77 on 2008-12-05
I think I got the same problem here. Kernel updated to 2.6.24-22-generic lately... the corresponding virtualbox ose module is not out yet. An simple way to work around this is to reboot with the previous kernel, it worked for me.

---

### Post by SonOfOdin on 2008-12-05
> **vince_77 said:**
> I think I got the same problem here. Kernel updated to 2.6.24-22-generic lately... the corresponding virtualbox ose module is not out yet. An simple way to work around this is to reboot with the previous kernel, it worked for me.

Thanks Vince.  How do I do this?

---

### Post by ^andrea^ on 2008-12-05
you could manually tweak 'menu.lst' file or install a software that allows you to do that easily...

One very nice could be StartUp-Manager...

Once it's installed in 'boot options' you can set the default OS/kernel prefered... set it to kernel 2.6.24.21 and restart the computer.

If you don't know is better you don't touch anything else... ;-)

---

### Post by bodhi.zazen on 2008-12-05
> **^andrea^ said:**
> you could manually tweak 'menu.lst' file or install a software that allows you to do that easily...

One very nice could be StartUp-Manager...

Once it's installed in 'boot options' you can set the default OS/kernel prefered... set it to kernel 2.6.24.21 and restart the computer.

If you don't know is better you don't touch anything else... ;-)

No you do not need to do any of that.

Each time you boot ubuntu you are presented with a list of choices of which kernel to boot (or hit the esc key during the boot process to see it).

To see a list of your currently installed kernels :

```
ls boot | grep vmlinuz
```

lower number = earlier kernel.

When updating and cleaning Ubuntu it is good to leave at least one old known good kernel.

---

### Post by vince_77 on 2008-12-06
bodhi.zazen you are right, no need for that, but it's true Starup-Manager is a convinient way to tweak some boot options, ex which Os or kernel to boot by default, so you don't have to wait in front of your screen and choose manually...

Beside that, I did try the xVM version from Sun yesterday... same problem with the ...22-generic kernel. This time vbox spit out that installing DKMS package could solve the problem... I didn't dig into this... I'll keep booting on the 21 kernel 'till the new module package is released.

---

### Post by SonOfOdin on 2008-12-06
Phew, thats so awesome.  I was almost ready to go back to the dark side.

Thanks for your help peeps.  Still having trouble with my number pad, but I can investigate it a bit further now atleast.

Is there a guide for recompiling the kernel so that I can do a clean up?

---


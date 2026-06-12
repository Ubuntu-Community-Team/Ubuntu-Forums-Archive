---
title: "Virtualbox 3.2.8 problems"
date: 2010-08-09
forum: Virtualisation
---

### Post by Stuey on 2010-08-09
Hi all,
I hope I haven't missed this being posted already - I apologise if so, but I couldn't find it :)

I decided today to update my old install of virtualbox OSE and install the new 3.2.8 version - basically to get USB support.

I thought it best to remove the old version first so I did a sudo apt-get remove virtualbox-ose, and then an autoremove in case anything else needed removing.

Then I followed the instructions on the virtualbox website to install the new version - add the software source, register the key and then install dkms and virtualbox 3.2.8 via terminal as instructed. Everything seemed to go fine.

But I cannot start it - there is no launcher on the system (I'm running 10.04 NBR) and trying to run the command "virtualbox" in terminal results in an error that "the package is not installed - install using sudo apt-get install virtualbox-ose".... this is the one I removed.

What did I miss/do wrong? Or is it simply not possible to install the newer ones on a system that had the old one installed?

Help!!!

Thanks in advance.

---

### Post by Warthaug on 2010-08-09
A couple of options:
1) rather than installing from Oracle's repsoitry, download the ubuntu .deb file fomr the oracle webpage to your computer and install using that.  This method has worked for me every time.

2) Missing icons sometimes appear if you reboot.

3) You can manually add the icon.  Right click on the applications menu, and choose edit.  A window will open where you can add/remove/move icons.  Select the folder you want, click "New", and enter the details you want.  For the "command" entry you should simply be able to add "VirtualBox" (no quotes) to make it work.

4) In old versons of ubuntu you could use the following commands to fix the applications menu.  I do not know if this still works in 10.04
```
sudo apt-get update
sudo apt-get install menu menu-xdg
update-menus
```

I'd add those are not in any specific order - pick and choose as you see best (or wait for someone more knwledgable than I to reply).

Bryan

---

### Post by Stuey on 2010-08-10
> **Warthaug said:**
> A couple of options:
1) rather than installing from Oracle's repsoitry, download the ubuntu .deb file fomr the oracle webpage to your computer and install using that. This method has worked for me every time.
 
2) Missing icons sometimes appear if you reboot.
 
3) You can manually add the icon. Right click on the applications menu, and choose edit. A window will open where you can add/remove/move icons. Select the folder you want, click "New", and enter the details you want. For the "command" entry you should simply be able to add "VirtualBox" (no quotes) to make it work.
 
4) In old versons of ubuntu you could use the following commands to fix the applications menu. I do not know if this still works in 10.04
```
sudo apt-get update
sudo apt-get install menu menu-xdg
update-menus
```
 
I'd add those are not in any specific order - pick and choose as you see best (or wait for someone more knwledgable than I to reply).
 
Bryan
 
Thanks for the reply,
I tried to install from the .deb file as mentioned - it's still the same. Tried rebooting as well, no luck. Also tried adding a manual launcher as one of the first things. It failed, and then I tried launching the command "virtualbox" from a terminal to be told "the program virtualbox is not installed, to install it run sudo apt-get install virtualbox-ose-qt".... which is the old version I removed prior to installing 3.2.8.
 
The menu fix you suggested appeared to run OK, but did not fix the problem.
 
Is there anything else I could try, I don't use it a lot - but I really could do with a working Windows VM at the moment to update my Sat Nav unit.

---

### Post by Warthaug on 2010-08-10
Sorry that didn't work.  I'm afraid we've hit the end of my capabilities - perhaps someone else will pop in to lend a hand.

Also, it may be worth re-posting this in the general help area, as there is a lot more traffic, and this missing icon issue is hardly unique to vbox.

Bryan

---


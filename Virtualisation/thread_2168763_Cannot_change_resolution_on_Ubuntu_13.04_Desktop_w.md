---
title: "Cannot change resolution on Ubuntu 13.04 Desktop with VMware tools"
date: 2013-08-19
forum: Virtualisation
---

### Post by jfeyen on 2013-08-19
Hi,

I installed a new linux guest in my VMWare Vsphere 5.1 enviroment.
This guest is an Ubuntu 13.04 Desktop.

After the installation of VMWare tools I wanted to change the resolution because now it is 800x600. I cannot change the resolution cause then the system hangs. 
Except when I change it to 1024x768 it works. If I change it into a higher resolution it also hangs if i apply the resolution. VMWare tools should normally manage the resolution.. What is wrong here?
The display is displayed as "Unknown" under the display menu in Ubuntu.

Kr,

Joeri

---

### Post by slickymaster on 2013-08-19
Have you tried rerunning VMware Tools?

Open a Terminal window and launch the VMware Tools configuration program, by running this command:```
sudo vmware-config-tools.pl
```Follow the prompts and make the necessary changes.
Close the Terminal window and restart the virtual machine.

---

### Post by jfeyen on 2013-08-19
> **slickymaster said:**
> Have you tried rerunning VMware Tools?

Open a Terminal window and launch the VMware Tools configuration program, by running this command:```
sudo vmware-config-tools.pl
```Follow the prompts and make the necessary changes.
Close the Terminal window and restart the virtual machine.

Hi, 

I already tried that. Still the same issue.
Shouldn't the VMware installer ask for the resolution? 

Kr,

Joeri

---

### Post by slickymaster on 2013-08-19
> **jfeyen said:**
> ...
I already tried that. Still the same issue.
Shouldn't the VMware installer ask for the resolution? 
Kr,
Joeri

Yes it should. When you run the command did you get any prompts from it?

Anyway, over here, [Howto install VMware tools on Ubuntu 13.04/12.10/12.04 Debian]("http://ithelpblog.com/os/linux/debian/ubuntu-debian/howto-install-vmware-tools-on-ubuntu-13-0412-1012-04-debian/"), at the end of step 4, it's said that:> To enable advanced X features (e.g., guest resolution fit, drag and drop, and file and text copy/paste), you will need to do one (or more) of the following:
1. Manually start /usr/bin/vmware-user
2. Log out and log back into your desktop session; and,
3. Restart your X session.

---

### Post by jfeyen on 2013-08-20
Hi ,

I found out that the virtual memory of my VMGuest was causing this problem.
When i set the memory to 8MB it works on the higher resolution.

Thanks for your help!

Kr,

Joeri

---

### Post by slickymaster on 2013-08-20
Glad you've got it fixed.

Please, don't forget to marked this thread as SOLVED. Follow the link in my signature if you don't know how to do it.

And be very welcome to the forums.

---


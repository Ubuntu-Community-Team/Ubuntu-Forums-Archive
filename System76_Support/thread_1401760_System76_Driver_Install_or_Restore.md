---
title: "System76 Driver: Install or Restore?"
date: 2010-02-08
forum: System76 Support
---

### Post by bvandev on 2010-02-08
Hi,

Could someone please clarify the difference between Install Drivers and Restore System on the System76 Driver interface?  

Reading the titles and pages it seems obvious what they do, but in the forums I seldom, if ever, see it recommended that the Install Driver function be used.  It's always the Restore System choice.

To me, restoring the system is a major action that will do exactly what it says, restore the system to factory defaults.  But it doesn't seem to do that.

Thanks in advance.

---

### Post by thomasaaron on 2010-02-09
In years past, the Install Drivers function would do just that, install system/os specific drivers. The Restore function would install System76's repositories in the sources.list file, install necessary configuration files like the xorg.conf, and install optional programs (gnucash, cheese, etc...), AS WELL AS install drivers.

Today, the Restore Drivers function just installs our repositories in sources.list and installs drivers... i.e. no software or configuration files are installed. You would want to use this functionality after, say, re-imaging your machine only.

For most purposes, just using the Install Drivers functionality is all you need.

In theory, as Ubuntu supports more and more hardware, the System76 Driver becomes less necessary. Hopefully one day we won't need it at all. But practically speaking, a lot of our hardware is cutting-edge, which means that we tend to be more on the forefront of hardware support in Ubuntu. So, the driver will probably be needed for quite some time.

Here is a little blurb I send out from time to time...

> The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Downloads folder.

Once it has downloaded, double-click the icon in your Downloads folder and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore functionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

Hope that helps.

---

### Post by bvandev on 2010-02-09
Perfect.  Thank you.

---


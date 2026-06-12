---
title: "vmware workstation tools installation"
date: 2014-03-03
forum: Virtualisation
---

### Post by sniper8752 on 2014-03-03
I am trying to install the tools following this tutorial: [http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/](http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/).  When I get to
[COLOR=#333333][FONT=Verdana]```
cp /cdrom/*.gz /tmp/
```[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]I get a "no such file or director[/FONT][/COLOR]y" for /cdrom/*.gz.  How can I install these?

---

### Post by varunendra on 2014-03-04
The version of Ubuntu and VMware both are ultra-ancient on that page. Which version of Ubuntu are you trying to install on? And which version of VMware?

I hope you already know that it is installed *Inside* the running Guest OS, not the Host.

So, is your target Ubuntu OS running within a VMware virtual machine? Usually, you just select **VM > Install VMware Tools..** option from the menu of a running VM's window > It automatically loads the ISO in the virtual CDrom > the cdrom automatically gets mounted and opened as soon as the guest OS detects it. You then just have to copy or extract the only file on the disk to your Desktop or anywhere you wish > open a terminal > change to the extracted directory > install with command "**sudo ./vmware-install.pl**"

---

### Post by sniper8752 on 2014-03-04
I am running 12.04 in vmware workstation.  I tried this tutorial: [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools).  Got stuck at [COLOR=#333333][FONT=UbuntuMono]apt-get install vmware-open-vm-tools-kmod-source since it could not locate it.[/FONT][/COLOR]

---

### Post by sniper8752 on 2014-03-04
I actually got them installed.  It told me to run /usr/bin/vmware-toolbox-cmd to run vmware tools, but it says that the command is missing.  and it says that I have to restart my x session.  I do not need to do this if I do not have a gui installed, right?

---

### Post by varunendra on 2014-03-04
Not familiar with Headless Ubuntu VMs, so can't say for sure, but yes, the 'toolbox' or settings box does need a gui. So you may not be able to use it without a gui unless it also provides a CLI interface (which again, I'm not aware of).

But actually I never needed to configure it from within the running VM as far as I remember (it's long since I installed Ubuntu in a VM, I only use them for live sessions now), the presets were all good for me.

---

### Post by sniper8752 on 2014-03-04
Oh- so I can't use the vmware guest tools if I don't have a gui installed?

---

### Post by varunendra on 2014-03-04
Installation is a commandline process, so that should be fine. You just can't use its 'Preferences' panel which uses a GUI.

But like I said before, I am just guessing because I don't have experience with headless of CLI-only version of Ubuntu. Besides, I never needed to use that preferences panel anyway. Things that we install VMware tools for start working automatically as soon as the installation finishes and the VM is rebooted.

Don't rely on my knowledge, the wiki page is much more informative and covers the part about installation on servers.

---

### Post by Simon_WM on 2014-03-05
VMWare Tools KB:

[h=3]Ubuntu Server with only a command line interface[/h]
[LIST=1]
[*]Go to **Virtual Machine** > **Install VMware Tools** (or **VM** > **Install VMware Tools**).

**Note**: If you are running the light version of Fusion, or a version of Workstation without VMware Tools, or VMware Player, you are prompted to download the Tools before they can be installed. Click **Download Now** to begin the download.
[*]In the Ubuntu guest, run these commands:
[LIST=1]
[*]Create a directory to mount the CD-ROM by running the command:

sudo mkdir /mnt/cdrom

When prompted for a password, enter your Ubuntu admin user password.

**Note**: For security reasons, the typed password is not displayed. You do not need to enter your password again for the next five minutes.
[*]Mount the CD-ROM by running the command:

sudo mount /dev/cdrom /mnt/cdrom ** or **sudo mount /dev/sr0 /mnt/cdrom
[*]The file name of the VMware Tools bundle varies depending on your version of the VMware product. Run this command to find the exact name:

ls /mnt/cdrom
[*]Extract the contents of the VMware Tools bundle by running the command:

tar xzvf /mnt/cdrom/VMwareTools-*x.x.x-xxxx*.tar.gz -C /tmp/

**Note**: x.x.x-xxxx is the version discovered in the previous step.
[*]Change directories into the VMware Tools distribution by running the command:

cd /tmp/vmware-tools-distrib/
[*]Install VMware Tools by running the command:

sudo ./vmware-install.pl -d

**Note**: The -d switch assumes that you want to accept the defaults. If you do not use -d, press **Return** to accept each default or supply your own answers.
[/LIST]

[*]Run this command to reboot the virtual machine after the installation completes:

sudo reboot
[/LIST]

---

### Post by sniper8752 on 2014-03-05
I do have them installed.  It looks like the shared folder option works.

---


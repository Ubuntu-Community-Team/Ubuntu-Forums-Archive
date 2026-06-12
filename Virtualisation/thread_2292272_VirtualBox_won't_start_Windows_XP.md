---
title: "VirtualBox won't start Windows XP"
date: 2015-08-26
forum: Virtualisation
---

### Post by johnaaronrose on 2015-08-26
I'm using Ubuntu Trusty. Under VirtualBox 4.3.10_Ubuntu R93012, my other OSs (e.g. Debian, openSuse) startup OK. However, Windows XP (my only Windows OS) starts up OK but then displays a window with details of NS_ERROR_FAILURE (0x80004005). Any ideas please?

---

### Post by ajgreeny on 2015-08-26
Have you checked all the settings of the XP VM in the VBox window itself?  Make sure there are no error messages at the bottom of that window?

A quick google of the error [COLOR="#FF0000"]NS_ERROR_FAILURE (0x80004005)[/COLOR] shows no obvious solution to that problem but one or two suggest making sure you are a member of the vboxusers group, or in one case just reinstalling VBox and the XP VM again solved this.

There is, by the way, a later VBox version than the 4.3.10 that you have; I am using 4.3.30, though there is also a 5.0.2 available from the VBox site's ppa which does not like my hardware and all VMs are too dark to be useful.

---

### Post by johnaaronrose on 2015-08-27
My user id is in the vboxusers group.

I tried a web search for a ppa for VirtualBox. I found [http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/](http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/) But it did not find v4.2 or 4.3.

BTW VirtualBox used to work OK for Windows XP. I haven't used it for at least 3 months so there may have been a Software Update to VirtualBox.

---

### Post by coldraven on 2015-08-27
My VBox virtual XP pro stopped working some months ago. It would boot to the desktop but hang and never show the start button. Even my back-up copies would not run. I began to think that MS had somehow installed an update that prevented it from running in a VM. I have no solution, I just stopped trying to use any MS product.
So far I have not missed anything :)

FWIW I had XP running from an OEM restore disc using VBox's "fake BIOS" utility. 
See here: [http://ubuntuforums.org/showthread.php?t=2070347&p=12293480#post12293480](http://ubuntuforums.org/showthread.php?t=2070347&p=12293480#post12293480)

---

### Post by johnaaronrose on 2015-08-27
Carried out install of VirtualBox 5.0.2 from LocutusOfBorg's ppa ([https://launchpad.net/~costamagnagianfranco/+archive/ubuntu/locutusofborg-ppa/](https://launchpad.net/~costamagnagianfranco/+archive/ubuntu/locutusofborg-ppa/)). Once I'd removed old Extension Pack & installed Extension Pack 5.0.2 from Oracle's site, Windows Xp & other guest OSs started OK.

PS this is logged on Launchpad as bug 1489279

---

### Post by ajgreeny on 2015-08-27
The VBox website itself shows you how to add its own repos to your sources.list file, which is what I have done and it seems to work fine for me.

I do not know if the version on the ppa you are using is different ijn nay way from the one I can install, but as I said, I can not use version 5 on my machine as the screen output is just too dark.
> Debian-based Linux distributions

Add the following line to your /etc/apt/sources.list:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) vivid contrib

According to your distribution, replace 'vivid' by 'utopic', 'trusty', 'raring', 'quantal', 'precise', 'lucid', 'jessie', 'wheezy', or 'squeeze'.

(Up to version 3.2 the packages were located in the non-free section. Starting with version 4.0 they are located in the contrib section.)

The Oracle public key for apt-secure can be downloaded here. You can add this key with

sudo apt-key add oracle_vbox.asc

or combine downloading and registering:

wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -

The key fingerprint is

7B0F AB3A 13B9 0743 5925  D9C9 5442 2A4B 98AB 5139
Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

(As of VirtualBox 3.2, the signing key was changed. The old Sun public key for apt-secure can be downloaded  here.)

To install VirtualBox, do

sudo apt-get update
sudo apt-get install virtualbox-5.0

Replace virtualbox-5.0 by

    virtualbox-4.3 to install VirtualBox 4.3.30
    virtualbox-4.2 to install VirtualBox 4.2.32 

Note: Ubuntu/Debian users might want to install the dkms package to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the linux kernel version changes during the next apt-get upgrade. For Debian it is available in Lenny backports and in the normal repository for Squeeze and later. The dkms package can be installed through the Synaptic Package manager or through the following command:

sudo apt-get install dkms


---

### Post by johnaaronrose on 2015-08-27
The above alternative method is useful to know. I spoke too soon about VirtualBox being OK. It's OK on my desktop as detailed above. However, I've just tried the same updates on my laptop. It installs VirtualBox 5.0.2 & its Extension Pack OK. However, starting Windows XP gives a slightly different error:
Failed to open a session for the virtual machine **WindowsXP**.
Unsupported version 56 of data unit **'PATM'** (instance #0, pass 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[/TABLE]

PS problem is now logged on virtualbox.org as ticket 14512

---

### Post by johnaaronrose on 2015-09-09
Solved:

When I reported a bug on Launchpad ([https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1489279](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1489279), I had a reply asking me to report it (as a ticket i.e. defect) on Oracle's VirtualBox site. VirtualBox ticket had reply suggesting using a special build (v5.0.3 I think). I did so. Though it got further, it gave a different error (see the VirtualBox ticket 14512 on [https://www.virtualbox.org/ticket/14512](https://www.virtualbox.org/ticket/14512)).

This morning there was an automatic download VirtualBox 5.0.4. When I started VirtualBox, it requested download of replacement Extension Pack 5.0.4. I assented and it downloaded & installed it. Afterwards I successfully started Windows XP with VirtualBox. However, it seemed to go to a previous saved version of Windows XP (e.g. it 'lost' AVG AntiVirus). I saved the machine state. I increased the Base Memory from 192MB to 1024MB and started Windows XP again. I then installed Firefox & AVG AntiVirus. Everything now seems OK.

---


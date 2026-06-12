---
title: "Running newer version of VirtualBox"
date: 2020-08-01
forum: Virtualisation
---

### Post by sniper8752 on 2020-08-01
I installed virtualbox from the ubuntu repo, had some issues with it, so I uninstalled it (sudo apt purge), then downloaded the .deb 6.1 file from VirtualBox's website, and installed.  I now get this error when I attempt to run a VM:
```
[COLOR=#000000]RTR3InitEx failed with rc=-1912 (rc=-1912)[/COLOR][COLOR=#000000]
The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

[COLOR=#0000FF]'/sbin/vboxconfig'[/COLOR]

may correct this. Make sure that you are not mixing builds of VirtualBox from different sources.

[/COLOR]
[COLOR=#000000]where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. [/COLOR]
```

I did what it says, but I get the same error.

---

### Post by SeijiSensei on 2020-08-01
Follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the Oracle VB repository to your system.  Then system updates will automatically update VirtualBox when there is a new version available.

---

### Post by sniper8752 on 2020-08-02
I still get the same error after following those instructions.

---

### Post by &amp;KyT$0P# on 2020-08-02
> **sniper8752 said:**
> I installed virtualbox from the ubuntu repo, had some issues with it, so I uninstalled it (sudo apt purge)

Could you please post the entries from [FONT=Courier New]/var/log/apt/history.log[/FONT] for both the installation and uninstallation of the repo package?

---

### Post by SeijiSensei on 2020-08-02
The version in the Oracle repository is designed to compile the required "kernel module" when it is installed.

Did you use "sudo apt install virtualbox-6.1"? That's the version in the Oracle repository. The package named simply "virtualbox" is the one in the Ubuntu repositories. It should be automatically uninstalled during the process that installs the virtualbox-6.1 package.

Just to be sure, run

```
sudo apt-get purge virtualbox
```

then run

```
sudo apt update
sudo apt install virtualbox-6.1
```

---

### Post by sniper8752 on 2020-08-03
> **SeijiSensei said:**
> The version in the Oracle repository is designed to compile the required "kernel module" when it is installed.

Did you use "sudo apt install virtualbox-6.1"? That's the version in the Oracle repository. The package named simply "virtualbox" is the one in the Ubuntu repositories. It should be automatically uninstalled during the process that installs the virtualbox-6.1 package.

Just to be sure, run

```
sudo apt-get purge virtualbox
```

then run

```
sudo apt update
sudo apt install virtualbox-6.1
```
Did all of this, and it said it is already the newest version.

---

### Post by monkeybrain20122 on 2020-08-03
Did you download and install the guest additions?

---

### Post by sniper8752 on 2020-08-03
> **monkeybrain20122 said:**
> Did you download and install the guest additions?
Yes.

---

### Post by SeijiSensei on 2020-08-03
> **sniper8752 said:**
> Did all of this, and it said it is already the newest version.

So did you run /sbin/vboxconfig as the error message read?  This compiles and installs the required kernel module. You need to run it with sudo, i.e., "sudo /sbin/vboxconfig". You shouldn't need to do this when installing from the Oracle repository, but your experience is so far removed from mine that it's worth giving it a try.

---

### Post by monkeybrain20122 on 2020-08-03
Maybe a long shot, I ran into something like that before, it turned out I have switched to a different version of gcc and forgot to switch back

so are you playing with an alternative version of gcc?

```
gcc --version
```

---

### Post by &amp;KyT$0P# on 2020-08-03
sniper8752, did you not see my post above? -

> **halogen2 said:**
> Could you please post the entries from [FONT=Courier New]/var/log/apt/history.log[/FONT] for both the installation and uninstallation of the repo package?

---

### Post by sniper8752 on 2020-08-04
Yes, and it still doesn't work. 
[FONT=monospace][COLOR=#000000]gcc (Ubuntu 9.2.1-9ubuntu2) 9.2.1 20191008[/COLOR]
[/FONT]

---

### Post by lammert-nijhof on 2020-08-05
You also have to reinstall the Virtualbox Extension Pack, that installs some additional kernel modules. The message indicates that you still have some older Virtualbox kernel modules installed. 
So:
- install the deb file, preferably by dpkg or alternatively; install gdebi; right click the deb file and select gdebi.
- double click the Virtualbox Extension Pack and install that pack downloaded from [www.virtualbox.org]("http://www.virtualbox.org").

---

### Post by CelticWarrior on 2020-08-07
> [COLOR=#000000]- install the deb file, preferably by dpkg or alternatively; install gdebi; right click the deb file and select gdebi.[/COLOR]

The default Software app can install .deb files. No need to install additional software, Gdebi or other, just double-click the file.

---

### Post by bls3427 on 2020-08-20
I ran into this as well. I **think** that I fixed it by downloading the latest extpack and then

```

sudo VBoxManage extpack install --replace Oracle_VM_VirtualBox_Extension_Pack-6.1.12.vbox-extpack 
```

Sorry can't be more definite, was overly focused on getting the system up again.

And thanks for the link, @SeiijiSensei, that is of course the correct approach. I'll swing over to that next time I'm ready to upgrade virtualbox.

---


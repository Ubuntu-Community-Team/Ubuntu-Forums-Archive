---
title: "VMWARE: Can't Load Guest on Ubuntu 20.04 LTS - &quot;Could not open /dev/vmmon&quot; Error"
date: 2021-11-12
forum: Virtualisation
---

### Post by wholockedat221b on 2021-11-12
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]([/FONT][/FONT][/FONT][/COLOR]EDITED TO ADD: Both Ubuntu and Windows guests are set to boot via BIOS and not UEFI. I tried creating a new VM using UEFI and the same issue occurred.)[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]
I am having an issue with VMWare on Linux.After trying to launch an Ubuntu or Windows Guest on a host running Ubuntu 20.04 LTS 64-BIT, I am presented with the following three errors:[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]1st: "Could not open /dev/vmmon: No such file or directory. Please make sure that the kernel module &#8216;vmmon' is loaded."[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]After clicking OK, the 2nd error: "Failed to initialize monitor device."[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]After clicking OK on the 2nd error, the 3rd error: "Unable to change virtual machine power state: Transport (VMDB) error -14: Pipe connection has been broken"[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]Host Info:AMD 64-Bit FX9800 8-core CPU, 32GB Ram, plenty HDD Space. OS: Ubuntu 20.04 LTS running latest kernel 5.11.0-40-generic. VMware Workstation Pro 16.2.1 (build 18811642). UEFI - Secure Boot Enabled. Single Boot Only - No Windows Partition.Steps I have so far taken:- Uninstalled via terminal command "sudo vmware-installer -u vmware-workstation", rebooting, then re-installing via "sudo sh VMware-Workstation-Full-16.2.1-18811642.x86_64.bundle" (Installed via CLI - did not use GUI installer). I then rebooted, > Same Issue. Both with previous VM and brand new VM.[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]- Physically at host machine, Uninstalled via terminal command "sudo vmware-installer -u vmware-workstation", rebooting, then re-installing via "sudo sh VMware-Workstation-Full-16.2.1-18811642.x86_64.bundle". I then rebooted, > Same Issue. Both with previous VM and brand new VM.[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]- Confirmed dkms is installed and all updates are installed. Installed packages linux-tools-generic-hwe-20.04, libelf-dev, linux-generic, fdutils, then uninstalled VMWare, rebooted and re-installed VMware > Same issue when launching guest VMs.[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]- tried generating SSH keys as per [/FONT][FONT=inherit]https://kb.vmware.com/s/article/2146460[/FONT][/FONT][/FONT][/COLOR][FONT=system-ui][FONT=inherit][FONT=inherit]. Rebooted. > Issue persists.[/FONT][/FONT]
[/FONT][COLOR=#050505][FONT=system-ui][FONT=inherit][FONT=inherit]
- tried running "sudo vmware-modconfig --console --install-all". Output will be located at [/FONT][FONT=inherit]https://paste-bin.xyz/12577[/FONT][/FONT][/FONT][/COLOR][FONT=system-ui][FONT=inherit][FONT=inherit] 
The last section showed:
"Starting VMware services:Virtual machine monitor failed
Virtual machine communication interface done
VM communication interface socket family done
Virtual ethernet failed
VMware Authentication Daemon done"
What else should I try? How can I fix this?[/FONT][/FONT][/FONT]

---

### Post by slickymaster on 2021-11-12
Thread moved to **Virtualisation** for a better fit

---

### Post by MAFoElffen on 2021-11-12
Seems this error is a re-occurring problem with VMware Fusion (OSX) and Player (Several branches of Linux, not just Ubuntu)... Seems they both create kernel modules that end up being broken and need to be rebuilt after a Kernel Update.

The instructions I found to correct it are basically the same with a few caveats between:
(these two you tried)
[https://kb.vmware.com/s/article/2146460]("http://kb.vmware.com/s/article/2146460")
[https://communities.vmware.com/t5/VMware-Workstation-Player/quot-Could-not-open-dev-vmmon-No-such-file-or-directory-Please/td-p/747787]("http://https://communities.vmware.com/t5/VMware-Workstation-Player/quot-Could-not-open-dev-vmmon-No-such-file-or-directory-Please/td-p/747787")

This is dated,but where most of the answers come from still:
[https://kb.vmware.com/s/article/1002411](https://kb.vmware.com/s/article/1002411)

Still dated, a bit more complete, and more relevant:
[https://stackoverflow.com/questions/49205162/install-vmware-could-not-open-dev-vmmon-no-such-file-or-directory-please-ma](https://stackoverflow.com/questions/49205162/install-vmware-could-not-open-dev-vmmon-no-such-file-or-directory-please-ma)

Both the same, relevant, and somewhat current:
[https://itectec.com/ubuntu/ubuntu-vmware-15-error-on-ubuntu-18-4-could-not-open-dev-vmmon-no-such-file-or-directory/](https://itectec.com/ubuntu/ubuntu-vmware-15-error-on-ubuntu-18-4-could-not-open-dev-vmmon-no-such-file-or-directory/)
[https://askubuntu.com/questions/1096052/vmware-15-error-on-ubuntu-18-4-could-not-open-dev-vmmon-no-such-file-or-dire](https://askubuntu.com/questions/1096052/vmware-15-error-on-ubuntu-18-4-could-not-open-dev-vmmon-no-such-file-or-dire)

---

### Post by wholockedat221b on 2021-11-14
> **MAFoElffen said:**
> 
This is dated,but where most of the answers come from still:
[https://kb.vmware.com/s/article/1002411](https://kb.vmware.com/s/article/1002411)


The "[COLOR=#C7254E][FONT=monospace]*vmware-config.pl*"[/FONT][/COLOR] command is either not installed with VMWare 16 or not present on my system.

> **MAFoElffen said:**
>  Still dated, a bit more complete, and more relevant:
[https://stackoverflow.com/questions/49205162/install-vmware-could-not-open-dev-vmmon-no-such-file-or-directory-please-ma](https://stackoverflow.com/questions/49205162/install-vmware-could-not-open-dev-vmmon-no-such-file-or-directory-please-ma)



When I perform "[FONT=var(--ff-mono)]*sudo modprobe -v vmmon*"[/FONT] this is the result:

[COLOR=#696969][FONT=Monaco]insmod /lib/modules/5.11.0-40-generic/misc/vmmon.ko [/FONT]
[FONT=Monaco]modprobe: ERROR: could not insert 'vmmon': Operation not permitted
[/FONT][/COLOR][COLOR=#00FF00][FONT=Monaco]
[/FONT][/COLOR]When I perform "*sudo modprobe -v vmnet*" this is the result:
[COLOR=#696969][FONT=Monaco]insmod /lib/modules/5.11.0-40-generic/misc/vmnet.ko [/FONT]
[FONT=Monaco]modprobe: ERROR: could not insert 'vmnet': Operation not permitted[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-11-14
Okay... Now I actually read through my install notes on Workstation 16. I didn't pay attention to them at the time... I do beta testing for vSphere and EsXi, so Workstation and Player really was not my main Focus...

Here is what I had:

For system requires, is said:
```

    &#8805;6th generation i5 or better/later
    &#8805;8 GB of RAM
    &#8805;250 GB SSD (120 GB for VM)

```

In your host machines BIOS UEFI firmware setup... Ensure your have your Virtual Support, Virtual Direct I/O, Enabled... or similar setting enabled for your BIOS. 

Next part is important... In your BIOS setting, if you have a TPM, make sure that Trust Execution is enabled. How this relates to this error... In some BIOS'es it says"
> This option specifies whether a Measured Virtual Manager Monitor (MVMM) can utilize the additional hardware capabilities of the Intel Trusted Execution Technology. The TPM has to be enabled and activated, and the Virtualization Technology and VT for Direct I/O must be enabled to use this feature.

But I found during testing, that "this" last was only a real hard requirement if I created a windows 10 that used bitlocker, or if I was trying to create a Win11 guest from the traditional installer, where it checked for the TPM being version 2.x. Even though it said this was a hard requirement for those, I got around this (for those kinds of guests) by installing packages swtpm and swtpm-tools to emulate that .

 Then for guest, if you want to create a guest where SecureBoot is enabled in the guest BIOS... then you have to generate a  new Machine Owner Key (MOK) for the host machine, with vmnet and vmmon Services. If you do not, and if you try to start a VM Guest with SecureBoot enabled in the Guest UEFI BIOS, then you will get an error saying:
> Could not open /dev/-vmmon: No such file or directory. Please make sure that the kernel module 'vmmon' is loaded.
You can check to see if those are loaded, but initially, just after a fresh install, they will not be able to yet. In the install process, it means that the MOK key that allows those to load, is not present, or is not imported into the UEFI BIOS'es trusted keys yet... These two services cannot start until that key is created and imported...

Create the key by:
```

openssl req &#8211;new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=VMware/"

```
This creates a blank MOK key called MOK.priv... Then add the vmmon service to it:
```

sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmmon)

```
That adds that vmmon service to that MOK.priv by creating a new MOK file called MOK.der...

Then add the vmnet service to the MOK.der file:
```

sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet)

```
Then you need to add it to the UEFI BIOS by importing MOK.der with mokutil. This is easier if you are root, instead of just using sudo.
```

sudo su
mokutil -import MOK -import MOK.der

```
To do this with this utility, you have to create a one-time password. It will ask you to enter a password, then again to confirm it... the same characters, to use later, (after the reboot)...

Close the terminal session, then reboot... On reboot, it will bring you to the MOK Management Screen, within your UEFI BIOS. Select "Enroll MOK". Select "Continue". Select "Yes" to enroll the key(s)...

It will prompt you for the password you just created (for this)... Enter it and press <Enter>. Select "Reboot". Ubuntu will reboot and come up...

Start Workstation 16 and try again... those services (vmmon and vmnet) should be running now.

Those are the notes I had...

But this also means that it should only get this kind of error if you are trying to create a guest that boots from UEFI, "AND" has SecureBoot Selected in the VM Guest BIOS. If the VM is Legacy, or if it is UEFI with SecureBoot off, it should not get that error. Because it wouldn't be using either of those services.

Next observation... Since it includes the Kernel Version in that key, I believe (and I could be wrong, but) it has to be regenerated every time the Kernel version number changes... Like I said, it might not be a problem. It might recognize the modules on it's own, but... If on an update of the host, if this error message comes up again, delete the old key, regen and re-import a new key.

---


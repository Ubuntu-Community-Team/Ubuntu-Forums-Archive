---
title: "issues for xubuntu in a virtual machine"
date: 2022-06-28
forum: Virtualisation
---

### Post by ubunternow on 2022-06-28
Hi. I'm not sure if it's the right place for these questions. I'm using xubuntu in a virtual machine and I have several issues. I don't know how to change the network I'm using if I want a different one from the one used by the host computer. I don't know how to reveal/receive external hard drives or pens attached to the machine. How to reciprocally exchange files with the host computer, (even though I went to General then Advanced and put 'Bidirectional' twice). And how to improve the size of the screen. I hope you can help me and guide me. Thank you very much.

---

### Post by slickymaster on 2022-06-28
Thread moved to **Virtualisation** for a better fit

---

### Post by ajgreeny on 2022-06-28
I presume from what you say that you are using VirtualBox but please let us know which version and whether or not you have installed the guest additions of the exact same version.

When I used VBox I always used the version direct from their own repositories as shown at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the ***Debian-based Linux Distributions*** section as it was more up-to-date than the version in the repos.

---

### Post by ubunternow on 2022-06-29
Thank you for the answer. It's virtual box 6.1, not sure about the exact version. Currently after a removal and reinstall I'm not able to have access to internet. I don't know where I can manage/have access to the part that deals with that.

---

### Post by ajgreeny on 2022-06-29
It looks as if you have the most recent version, but do you have the guest additions installed as they are needed for a lot of the things you seem to be missing such as fullscreen display and copy/paste between host and guest.
I always used the NAT networking so can't really help with bridged connections.

---

### Post by ubunternow on 2022-06-29
Thank you. How do I add those guest additions?

---

### Post by ajgreeny on 2022-06-29
Download the installer from [https://download.virtualbox.org/virtualbox/6.1.34/Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.34/Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack) 

Install it by double clicking it in the file manager.  That should offer to install it into the VBox manager.

I am assuming, possibly wrongly, that your host OS is Ubuntu or another Linux distro but tell us more about that as if you use Windows as the host I shall have to leave it to others to help as I no longer use any Windows OS.

Once installed by VBox boot to the VM of Xubuntu, go to the Device menu and choose ***Add Vbox guest additions CDROM*** or something similar to that; I may have the words wrong and don't use VBox any more, preferring KVM/QEMU.
Once that is inserted into a virtual CDROM you should see it in the thunar left hand pane as a disk volume.  Open that and run the ***VBoxLinux.run*** file in terminal. Once again I may have that filename wrong but it will be fairly obvious which to use when you open that virtual CD.

Give that a try and come back if you don't manage to figure this out yourself; I can always install VBox and install a Xubuntu guest to remind myself how it all fits together.

---

### Post by ubunternow on 2022-06-29
The host os is MAC OS. This is what I see. Where should I go to change the network settings? There are no wifi settings.

---

### Post by ajgreeny on 2022-06-29
Sorry; I've no idea about that never having used any Mac systems in my life.

I did at least use Windows in the past, MAC OS or any other Mac system is totally outside of my experience.

EDIT:
One idea springs to mind which is related to the VM not the host.
In the VBox manager window highlight your VM and go to Settings.  You should be able to make changes to the network, setup there and either choose NAT, the default, or bridged network which should then use your real network hardware and not the virtual hardware.

---


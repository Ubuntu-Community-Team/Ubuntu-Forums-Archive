---
title: "Looking for clues on why Subiquity is crashing near end of autoinstall"
date: 2022-03-08
forum: Server Platforms
---

### Post by kmcgregor-cow on 2022-03-08
I set up Hashicorp Packer (1.7.10) using the files from [https://github.com/vmware-samples/packer-examples-for-vsphere](https://github.com/vmware-samples/packer-examples-for-vsphere), and it mostly works. I have only been working with the part that generates a build image/template for Ubuntu Server 20.04. I have tried 20.04.3 and 20.04.4 ISO images. I can't get a complete build. Packer stops after "Waiting for SSH to become available..." and eventually times out. Looking at the console of the VM being built by Packer, I can see that subiquity runs for a while and then crashes, not always at the same place. Where should I be looking for clues for the crash cause?

I've attached three excerpts of the crash files. I can provide full versions if necessary.

[ATTACH]290130[/ATTACH]
[ATTACH]290131[/ATTACH]
[ATTACH]290132[/ATTACH]

---

### Post by MAFoElffen on 2022-03-08
Looking at that error message, that seems to be a common eror while installing in Vagrant and VirtualBox... What is your Virtual Host of the VM Guest you are installing?

---

### Post by kmcgregor-cow on 2022-03-08
It's running on VMware vSphere 6.7 as a host. I specified a VM with 2G RAM, then upped it to 4G, then 8G which didn't help. The disk is 50G. The firmware is set to 'efi-secure' and the VM version is 15. We will be upgrading to vSphere 7.x later this year but I can't wait that long to get this running.

---

### Post by MAFoElffen on 2022-03-08
Skip vSphere 7.2. I don't even think it is an option. I was on the test team, it was still released (shortly) then pulled. We said it had problems. It was bigger than they thought, and they took us more seriously. . After being pulled they resolved those. 

It should run on 4GB just fine... depending on the services, but you are not even to that point yet. I suggest even if the services are going to be less, that I pump it up to at least 4GB for the install. You can see your resource monitor that it takes most of that in an install with the Live Installer. I don't know why. The system itself takes less, depending on what you are running.

On efi-secure secureboot enabled, I have installed and tested with that and had no problems with 20.04 on... But I don't usually have that enabled, as a general practice. Ubuntu Server 20.04.x on vSphere is usaully a no-brainer, with no surprises. 

Since you said 20.04.3 and 20.04.4, I would assume that the integrity checks on the ISO's are good right? That is the usually problem when an install fails at different points on multiple tries...

EDIT: 
What system template are you using for the guest? And what does the installer logs say?

---

### Post by kmcgregor-cow on 2022-03-09
I'm using Packer to create a template for use later with Terraform. I provided the sha256 checksum with the path to the ISO for both 20.04.3 and 20.04.4 and there was no problem there. I can install either of those on vSphere 6.7 manually using efi or bios firmware and with 2 GB (maybe less). The problem crops up well after Packer fires off the autoinstall. The install gets past the part where the disk is partitioned and formatted, the OS is installed, and final packages are being installed - openssh-server, open-vm-tools... Then it gets to
start: subiquity/Install/install/postinstall/install_ansible: installing ansible
and fails with
finish: subiquity/Install/install/postinstall/install_ansible: FAIL: Command '['/snap/subiquity/3119/usr/bin/python3.8', '-m', 'curtin', '--showtrace', '-vvv', '--set', 'json:reporting={"subiquity": {"type": "journald", "identifier": "curtin_event.1923.7"}}', 'system-install', '-t', '/target', '--', 'ansible']' returned non-zero exit status 100.

...although it's not ansible every time. I wonder what exit status 100 means?

---

### Post by MAFoElffen on 2022-03-09
Exit code 100 is a generic error code that covers a whole lot of things. Usually, when dealing with systems, it has to dues with the non-availability of files/directories due to permissions, file-locks, or being missing. Can also be reported on records of a dB system. 

It's telling you that something is not there or that is is not available for some other reason... But is is not telling it can't find or access, right? Except that somehwere in an installer curtin call, thta it couldn't access 'something'.

That is why I asked you if you checked the installer logs of the target VM Guest's system. That should contain what went wrong, and where. Even if not bootible on it's own,you could mount a LiveCD image to look at the logs of the VM Guest. Right?

Or if it is still running, can you ssh into the instance?

---

### Post by jonasb-to on 2022-09-26
I'm seeing the same problem (for me it's in VMWare Fusion 12 on macOS, so no vSphere here), albeit with a different package - I'm trying to add the `ubuntu-desktop` package at the end of my server autoinstall but end up with the same subiquity error 100...

---

### Post by jonasb-to on 2022-09-26
It would seem this is a timing-issue, since once in a while it works just fine...

---


---
title: "Installing Windows 10 in VirtualBox causes Ubuntu to freeze"
date: 2018-03-19
forum: Virtualisation
---

### Post by agnister on 2018-03-19
Running Ubuntu 16.04 with VirtualBox 5.0.40. I want to use Photoshop & Lightroom so I allowed 8GB RAM and 50GB of SHD for Win10 leaving the other 8GB RAM for Ubuntu.
Established the virtual space; win10.iso on the optical drive; turned off "Auto Capture Keyboard"; set virtulization in Bios to enable; 
Went to "Start" in Virtual Manager ready to commence installing win10 and the black screen came up indicating that it commenced but then frooze. I did not get the typical windows logo.
Had to hard boot the PC. Any ideas what the problem might be?

---

### Post by SeijiSensei on 2018-03-19
Did you install from a valid Windows disk with a product key?

---

### Post by yancek on 2018-03-19
You might try some of the suggestions at the link below.  Note the site is microsoft which would be a better place to go for information on installing your microsoft windows system.

[https://answers.microsoft.com/en-us/insider/forum/insider_apps-insider_other-insiderplat_pc/cant-install-win10-in-virtualbox/65d57548-d39f-4c69-b5a6-73b4f1079825](https://answers.microsoft.com/en-us/insider/forum/insider_apps-insider_other-insiderplat_pc/cant-install-win10-in-virtualbox/65d57548-d39f-4c69-b5a6-73b4f1079825)

---

### Post by agnister on 2018-03-20
SeijiSwnsei I recently purchased a product key and downloaded the Win10.iso from the microsoft site.

---

### Post by slickymaster on 2018-03-20
Thread moved to **Virtualisation** for a better fit

---

### Post by agnister on 2018-03-22
I posted the same thread on a windows forum but have not received a reply. I still have not solved my problem.
I even downloaded the Win10 iso file from a different site in case the iso file was corrupted but got the same result as before. Ubuntu just frooze and the windows icon did not appear.

---

### Post by QIII on 2018-03-22
If you still have a copy of the downloaded .iso on your hard drive, what happens if you use it directly rather than using the optical drive?

---

### Post by agnister on 2018-03-23
QIII - I tried that and got the same outcome. Is their a limit to setting the VirtualBox. I set RAM at 8GB and SHD at 50 Gb which is well above the default because of the resources Photoshop requires.

---

### Post by Sophont on 2018-03-23
Yesterday I tested moving a Win10 VM from VMWare to qemu/kvm - using virt-manager. Using QXL for video with SPICE.

Went surprisingly smooth, even before I installed guest-agent and virtio drivers into Win10.

Perhaps give this a try?

The virt-manager ("Virtual Machine Manager") GUI  is not quite as polished as VirtualBox - but still fairly comfortable to use.

---

### Post by agnister on 2018-03-27
I still have not solved my problem. I might try WIN 7 as I know most users have had success with this OS

---

### Post by agnister on 2018-05-29
I finally got a solution to my problem with installing win10 in VirtualBox thanks to the help from Ross. He started from scratch by upgrading all libraries etc then did a fresh install of VirtualBox followed by win10 and everything fell into place. Where the problem was which the install to freeze we will never know.
Does anyone know how to make the VirtualBox of win10 full screen?

---


---
title: "Share with us your Hirsute Hippo installation/Upgrade Experience"
date: 2021-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by wildmanne39 on 2021-04-26
Hirsute Hippo was released April 22, 2021, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Hirsute Hippo.

This thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2452678](https://ubuntuforums.org/showthread.php?t=2452678)

---

### Post by TheFu on 2021-04-27
Did a fresh install into a KVM/Spice VM.  Selected minimal install + LVM.  This was the Gnome desktop.

The good:
[LIST]
[*]install worked
[*]virtio for NIC and disk controllers worked perfect.
[*]OS seems fast
[*]The installer finally used GPT partitioning!!! Thank you! Thank you! Thank you! Thank you! Thank you!
[*]A swap LV was used, not swapfile. Thank you!  However, the swap LV is undersized.
[*]Spice didn't work [s]and I've not gotten it to work.  Had to drop back to VNCserver + VMVGA drivers.[/s]
[*][s]It appears that Wayland is attempted, then fallback to X/Windows is working. There is a long delay before Wayland gives up, it [/s] Spice is working with Wayland now. Don't know what changed.
[/LIST]

The bad:
[LIST]
[*]Initially, the display resolution was set to 800x600 on a 1920x1200 monitor/VM
[*]virtio for the GPU acted funky.  The mouse click-point was off 2-4 inches both horizontal and vertical. The amount off was dynamic, not static.  **When spice started working, this self-corrected. Only 1 pointer is seen and working as expected not.**
[*]I'm hating the new bash v5.1 defaults for select/paste that highlights what is pasted and doesn't cause <enter> to be entered when the full line is part of the selection.  Efforts to fix this via the .inputrc *set enable-bracketed-paste off* have failed.
[*]I don't use Gnome, so when nautilus is run, I'm missing window manager decorations. These aren't displayed over a remote X session either.  The X/Server should control WM decorations, not the client program.
[*]Nautilus/Files insists on showing locations that don't exist.  I remove empty directories in $HOME, but Nautilus sidebar still shows them in a list. Clicking on them displays an error. I'll never have Music or Video on this system.  /tmp/ is where Downloads belong too.
[*]Edited ~/.config/user-dirs.dirs to remove unwanted XDG locations.  Somehow, Gnome decided my edits weren't good and put those back.  Bad behavior.
[*]The "root" LV tool all the storage available. However, it is oversized.
```
/dev/mapper/vgubuntu-root ext4    33G  5.7G   26G  19% /
```
[/LIST]

I'm still working through some other issues, but as Gnome isn't my flavor choice, I'll be better off switching flavors or  trying the mini-ISO install, I suspect.  

It is also highly likely that my ignorance is simply missing where the controls for things I like are located. For example, I want focus to follow the mouse, never raise a window, unless I click inside it. I don't want clicks to set focus. 25+ yrs experience with this behavior, so I'm not likely to change. Can't find the mouse focus policy in any settings.

---

### Post by Dennis N on 2021-05-01
**Ubuntu 20.10 to 21.04**
Done on 1 May 2021 
Read the [current caveats for some UEFI systems]("https://ubuntuforums.org/showthread.php?t=2461374") on upgrading to this release. 
Since my Ubuntu 20.10 has BIOS firmware, I expected it would work and it did, with no post install adjustments needed, since the gnome shell version is the same (3.38). I had to use do-release-upgrade with the -d option (development release) or else there was no upgrade offered. I'm happy to have all my applications and tweaks from the previous version still there. Hours of work saved.
```
dmn@Sydney-vm:~$ neofetch --stdout
------------- 
OS: Ubuntu 21.04 x86_64 
Host: KVM/QEMU (Standard PC (Q35 + ICH9, 2009) pc-q35-3.1) 
Kernel: 5.11.0-16-generic 
Uptime: 41 mins 
Packages: 2016 (dpkg), 35 (flatpak), 11 (snap) 
Shell: bash 5.1.4 
Resolution: 1920x1080 
DE: GNOME 3.38.4 
WM: Mutter 
WM Theme: Adwaita 
Theme: Adwaita-dark [GTK2/3] 
Icons: Tela-blue-dark [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel (Haswell, no TSX, IBRS) (2) @ 3.491GHz 
GPU: 00:01.0 Red Hat, Inc. Virtio GPU 
Memory: 780MiB / 3927MiB 

```
I also did some successful upgrades of 18.04 systems to 20.04, but that's not the subject of this thread.

---

### Post by rbmorse on 2021-05-01
> **TheFu said:**
> 
[LIST]
[*]Edited ~/.config/user-dirs.dirs to remove unwanted XDG locations.  Somehow, Gnome decided my edits weren't good and put those back.  Bad behavior.
[/LIST]

The xdg thing bit me, too.  I had to edit /etc/xdg/user-dirs.defaults to keep unwanted directories from being created in my user account.  This may be a bug as the global default shouldn't override the user's setting.

---

### Post by TheFu on 2021-05-01
> **rbmorse said:**
> The xdg thing bit me, too.  I had to edit /etc/xdg/user-dirs.defaults to keep unwanted directories from being created in my user account.  This may be a bug as the global default shouldn't override the user's setting.

Definitely a bug based on 40+ yrs of Unix - the-way-things-work.

Also, creating a new userid should create a fresh account with all the defaults. Handy for figuring out if a problem is self-created or system-wide.

---

### Post by Frogs Hair on 2021-05-03
Just switched from my upgraded test installation to a clean installation of Ubuntu Budgie without issues. I don't install proprietary drivers during the installation.


Some legacy dual boot settings not directly related to how Ubuntu functions include, having disable fast startup again from the Win 10 side so Win 10 would shut down.I used the reinstall 21.04 option and both operating systems booted properly. Local time was set in Ubuntu to make sure both operating systems display the correct time.Win 10 was set as default in grub for Windows update auto restarts.

---

### Post by Dennis N on 2021-05-12
**Upgrade of Ubuntu 20.10 UEFI to 21.04 done on May 12, 2021**

I updated my UEFI Ubuntu 20.10 system when Software Updater offered the upgrade, right after I had updated my packages today. Must be safe now, so I accepted. The upgrade process proceeded apace. At the end, it removed what it considered "obsolete" packages (9) one of which was gnome-software, which I wanted. Rather than "keep" all of them (you must keep all or none!) I allowed removal. After rebooting to desktop there was some weird behavior of the home and trash icons spontaneously jumping onto the Desktop, then disappearing. This became an endless loop of activity, which I determined was caused by a new extension "Desktop Icons NG" being installed and turned on. I turned that off and the weird behavior went away. There is another extension "Desktop Icons" retained from 20.10 but it's off. There's no option to uninstall these "Built In" extensions from the Extensions App. 

I reinstalled gnome-software, because only it can manage Flatpak. I removed Ubuntu Software which is like Gnome Software except it doesn't manage Flatpak (a non-starter).

If I was allowed another vote in the poll, it would be:  "Upgrade - Worked but had a few things to fix, nothing serious though.."

ADDED:
I forgot to mention that the updater changed my display manager from **x-org** to **wayland** without asking. I am going to let this switch go for now.

2nd ADDED:
I was experiencing a "ghost dock" when viewing the Overview screen. I attach a screenshot. I changed the display manager to "Xorg" at the login screen and the ghost disappeared.

---

### Post by codetricity on 2021-05-12
I went from 20.04 to 21.04 to take advantage of Wayland and Flutter desktop development.  I wrote about my experience in this [blog post]("https://www.codeproject.com/Tips/5300996/Configuring-Ubuntu-21-04-for-Wayland-and-Flutter-D"). 
As I have an NVIDIA GTX 950, my experience did not go smoothly.

Had to modify:

/etc/gdm3/custom.conf

and 

/usr/lib/udev/rules.d/61-gdm.rules

In addition, I had to purge my NVIDIA drivers.

After that, I can use Wayland.

However, my Flutter desktop apps are running slowly when I use complex graphics.  I'm building camera and photo management apps, so I need to work with large 360 images.

I can't seem to use Google meet with Wayland.  I'm happy to switch to Zoom if it works, but maybe it doesn't work?

Would NVIDIA driver 465.19.01 help?  

I'm not that familiar with Wayland technology and much of the vocabulary about Wayland graphics is beyond my understanding.

My primary goal is to build Flutter desktop apps on Linux.  However, I need to have meetings with something like Google Meet or Zoom.  

I'm having other problems with Wayland related to v4l2loopback and gstreamer.  However, I can live without that on Wayland and switch to X11 with X.org for those if I need to.

I also need to record my desktop, which is kind of painful the the Gnome screen recorder.  I used to use OBS with X11.

Is there another thread where I can seek help with the configuration of 21.04?  

Thanks for the help.

---

### Post by guiverc on 2021-05-12
@codetricity, start a new thread for your support questions ([https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331))

Please note however Ubuntu *fully* QA-tests upgrades from one release to the next, **or** from one LTS to the next LTS.  So from Ubuntu 20.04 the intended upgrade path was to 20.10, or to wait until *after* 22.04.1 has been released when you can upgrade to the next 22.04 LTS.  You going outside of intended upgrade paths meant you want outside what is *Quality Assurance* tested *by people on real hardware*.

My upgrade to *hirsute* was normal, but I'd have upgraded most likely Saturday 24 October 2020 or less than 48 hours from [20.10's release]("https://fridge.ubuntu.com/2020/10/22/ubuntu-20-10-groovy-gorilla-released/") so the reboot takes longer than my upgrade of packages. I left *hirsute *moving to *impish* on 24th April 2021 returning to the *development* cycle.  I thus didn't use poll sorry.

---

### Post by steve949 on 2021-05-15
So I bought a refurbished Dell XPS13 9305 i7 (Tiger Lake) from Dell Outlet for the express purpose of running Ubuntu 21.04 on a dedicated Linux machine, having previously used dual boot machines and Virtual Box VMs. I chose an outlet XPS13 9305 because it appeared to be more or less identical to the officially 'supported' 9310 model but at almost half the price of the Ubuntu XPS13 Developer Edition that Dell provide as a custom build, and I wanted to see for myself how easy/hard it would be to install from scratch.

I elected to use LVM and full disk encryption with Secure Boot enabled (*the XPS13 has a 500GB NVMe drive and a TPM2 module*).

On the whole the installation procedure was fairly painless  - the only thing that really threw me was the 'blue screen' MOK Manager key enrollment procedure (*blue screen not a good look if you're coming from Windows :o*), which I had anticipated but which doesn't appear to be mentioned anywhere in the standard installation wikis (though it is referenced in the technical documentation). The MOK Manager prompts you for a key enrollment password but it's by no means clear which password it requires. I tried entering the user password, the disk encryption passphrase and the recovery key but nothing worked.  Eventually after trawling through the forums I established that it's actually after the root password, so after starting from scratch by defining the root password in 'Try Ubuntu' mode, I was able to successfully enrol the Secure Boot key and proceed with the standard installation prompts. I think this whole procedure could be better explained in the standard installation wikis.

This set up obviously requires you to enter the disk encryption passphrase on every subsequent boot. The next step was to try to use the XPS's TPM2 module to store and retrieve the disk encryption key automatically, similar to the way Bitlocker works on Windows 10 Pro. TPM is something of a hot topic on the ISec forums, but I do think it's a useful safeguard against all but the most determined attackers, and I eventually found a workable wiki here: [https://run.tournament.org.il/ubuntu-18-04-and-tpm2-encrypted-system-disk/](https://run.tournament.org.il/ubuntu-18-04-and-tpm2-encrypted-system-disk/) and was able to successfully configure automatic key retrieval from TPM2. Again, I think it would be helpful if Canonical could publish a definitive procedure for this or  - better still - make it part of the standard installation procedure.

On the plus side;
- Wi-Fi integration was fine - no difficulty with Wi-Fi 6 via onboard AX200.
- Bluetooth integration was fine - was able to hook up a couple of AD2P headsets and AV receiver with no difficulty (had always been shaky under 18.04).
- Thunderbolt integration was fine - was able to hook up to a couple of Dell Displayport monitors via a generic Thunderbolt hub and if anything it works better than Windows 10 or MacOS Big Sur.
- Power management and lid sleep/wake functionality was fine.

On the minus side;
- I was disappointed to find that the specific variant of the Goodix  fingerprint reader on this machine is NOT currently supported on Ubuntu,  but that's another story.
- the GNOME Ubuntu Software installation app doesn't always give you an installation progress bar, or indeed any visible acknowledgement afer clicking 'Install'. I found myself clicking it twice and getting an error message signifying in very opaque terms that the installation was already in progress. I presume this is a bug in the desktop app - as I recall it worked intermittently on 18.04. I still find Snap installations a bit hit and miss, and find myself reverting to the command line apt options more often than not.

On the whole, happy with the installation procedure and very happy with the performance of the machine under 21.04, but felt the documentation could be clearer, particularly with regard to the use of disk encryption which should surely be the default option these days. Other than that, I honestly think we're ready for Primetime, ideally with a paid domestic user support offering for those who are happy to fork out for it.

---

### Post by bernard010 on 2021-05-17
It was a quicker install compared to the last LTS. I used all of the install methods that were available. Started with making a few bug reports before the final release.
I am on the QA Testing Team. The upgrade was put on hold until a bug could be fixed after the release. I was impressed with the new Ubuntu. 
Wayland being easy to locate and toggle to X11 on the login screen. Disk encryption worked excellent. Manual partitioning was easier, as replied above Gparted.
The only new problems are certain Wi-Fi NIC's being hard to configure without a workaround. I feel the entire Ubuntu did an excellent job. 
I Did not fill out the Poll - I am on the QA Team.

---

### Post by graymin on 2021-09-14
Installed:
 Tried PoP os then Debian 11 now Ubuntu 20.04 switch to it Because Shinobi recommended it to run there camera monitoring software took a bit to get it working the way I wanted. a few headaches  here and there but its up and running still a few bugs to work out with the monitors, and myself lol

  and sound in Shinobi while watching live  
 looking good having fun.
 
 
 
 
 Note: I am 61 years old and been away from Linux too long :) I would drop windows altogether but I have a lot of $$ tied up in my VR gaming :)

---

### Post by guiverc on 2021-09-14
> **bernard010 said:**
> Started with making a few bug reports before the final release. I am on the QA Testing Team.
...
 I feel the entire Ubuntu did an excellent job. 
I Did not fill out the Poll - I am on the QA Team.

Thanks for your testing & contribution @Bernard010 in QA-testing :P

(*I too didn't complete the poll; I upgraded too long ago I don't reliably remember it; and even if I did, the download & install of packages take a fraction of the time a reboot requires given the release-upgrade is usually only the change of name itself as I bump very early; in about a month I bump to a release I don't yet know the name of*..*jj*.)

---


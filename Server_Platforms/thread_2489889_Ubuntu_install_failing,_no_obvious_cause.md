---
title: "Ubuntu install failing, no obvious cause"
date: 2023-08-13
forum: Server Platforms
---

### Post by ericbrow1337 on 2023-08-13
Hi,

I'm fairly new to Linux, I picked up a decent office PC to start using as a home server and hopefully get some experience in Linux but I'm failing at the first hurdle so far.  Specs are 32gb RAM, 1TB brand new Samsung Evo SSD, Nvidia Quadro P1000, and an Intel i7-10700.
I can boot into and get through the initial installation menus process fine, but then as soon as I actually hit 'Install', the installation log says nothing (Or sometimes it'll list a few subiquiti scripts being loaded), and after about 30s if I check the help menu there's an unviewed error.

Viewing this error either causes text to flash down the screen extremely fast and just end up a terminal like screen, however the couple of times I have managed to actually see the error log there is no clear information that suggests what the issue is - and the installer just labels it as 'an unknown error occured'.

I'm not doing anything fancy with it, just a single drive/use all available space, it only seems to reserve 100gb for / so I have been upping it to the max available, however it has failed with or without this.

Things I have tried:

- Used 3 different USB devices to install - Two SSDs with a USB to SATA adapter that I have used to install Ubuntu Server before on another machine, and just to make sure a USB stick too
- Varying config setups, including LVM and non, different amounts of space for disk, and just leaving it default.
- Different Ubuntu Server image (Daily) rather than the one straight from the site
- Running through the PC's firmware settings to see if anything in there might cause issues - Disabling secureboot - I can't see RAID/AHCI settings but on one of the screens it says the drive is AHCI.
- Plugging the SSD into a Windows PC and running diskpart clean on it to uninitialise it, before trying again.

Same issue pretty much every time.  The fact that I had 0 issues installing it a few days ago on another machine makes me think it must be something to do with the computer or the drive I'm trying to install it to.

Am I missing something really obvious?

Edit:

Managed to catch this by videoing the error and going frame by frame:

[IMG]https://i.imgur.com/Ou4pkgn.jpeg[/IMG]

It says no space left on the device, this is a fresh install on an empty 1TB SSD?

---

### Post by MAFoElffen on 2023-08-14
I couldn't make out what was beig said on that screen from that photo.

And you didn't post anything from the install logs.

Which Live Installer? 22.04.3?

Boot from that same Server Live installer USB, and after you get past the first two panels (language and keyboard), then tab until you hightlight the "Help" button, the press <Enter>. <Arrow-Down> to the option that says "Enter Shell"...

Then do this:
```

wget -N -t 5 -T 10 https://github.com/Mafoelffen1/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```
Run the report and select upload to a pastebin. Please post that URL here.

I will look to see if I see anything with the hardware, that would prevent a successful  install with that ISO.

---

### Post by TheFu on 2023-08-14
Four things come to mind.
a) Update the motherboard BIOS
b) Update the SSD firmware
c) Use a non-Nvidia GPU.
d) Ensure the SATA mode for storage is AHCI, not RAID. That's in the BIOS.

I have a Samsung 970 EVO SSD. Didn't have any issues installing, but I don't have any new Intel systems. Mine are all Ryzen now.
The last time I had a Quadro GPU, was in 2015-ish.  Obviously, it was an older GPU.
[https://ubuntu.com/certified/component/723](https://ubuntu.com/certified/component/723) shows that GPU is certified for 18.04 and 20.04 Ubuntu in HP equipment. Some other links have guides for installing drivers. With nvidia, the drivers are kinda hit-or-miss.  I've had both great results and terrible outcomes with nvidia driver installs.  The last 8 months or so, nvidia driver installs have left Ubuntu systems with networking broken on some systems. Don't know why.

In theory, your system should be able to easily run any Ubuntu version from the most bloated to the lightest variant.  You might try Kubuntu, just to change up some things.
Also, you should try without secure boot enabled - as a test.  I remember reading about some issues with it recently.  Many Linux distros don't pay MSFT to get their certs into the MSFT approved secure boot credentials for motherboard BIOS. Something could have screwed up, though it is doubtful with Ubuntu/Canonical or MSFT. They are boot good at consistent processing, but humans do make mistakes.

Trying to make / larger is a bad idea.  Linux isn't Windows.  The way we layout file systems matters.  / really shouldn't need to be over 40GB for any Ubuntu system in the lifetime of that system.  Create another partition for /home and make it as large as you like, but with SSDs, I want to never actually use more than 80% of the storage to increase the lifespan of the SSD.  Adding more space to a partition and file system provided it is directly "to the right" of the current partition is pretty easy in Linux.  Just leave some space *to the right* of the 2 partitions you will create.  / and /home.

You mentioned LVM. As a beginner, that should probably be avoided for a few years, unless you have experience with Veritas FS and Veritas VM already.  If you do, then you'll be familiar with the LVM ideas already.  If not, it is adding complexity that you don't want/need at this stage when learning a new OS with all the new ideas of Linux/Unix.  I love LVM and use it almost everywhere, but it is not for beginners.

When you choose to install, be certain you check the box that says to use the entire drive.  That should make whatever pre-exists on the SSD unimportant.  It won't care if there are existing partitions, since it will wipe everything and start over.  If the SSD was previously used in a RAID setup, some extra steps are needed to wipe the RAID flags, but it is unlikely you have that.

If the install seems to work and there's a fail at the first reboot into the new OS, that means we need a _boot-info_ report.  There's a tool called **Boot-Repair** which will generate a boot-info report for experts to review.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) has details for installing and simple use.

BTW, when an installer says _no space left on device_ and it was told to wipe the disk, I have to wonder if it has been told to use the wrong disk.  NVMe storage devices have names like /dev/nvme0n1 for the entire disk and /dev/nvme0n1p1 for the first partition, nvme0n1p2 for the second partition, nvme0n1p6 for the sixth partition.  This is by the order created, not by where they are laid out on the storage. Heck, with SSDs, all storage layouts are virtual, so the idea of specific storage chips being used for a "sector" means nothing. They aren't like HDDs.   

HDD names are tied to the order of discovery at boot and the driver used to access the disk.  "sd" is for SCSI and SATA and eSATA disks.  "hd" is for IDE disks.  Many USB connected disks will use pseudo-SATA drivers, so they will be given "sd" names.
/dev/sda is the first disk discovered.
/dev/sdb is the second disk discovered.  BTW, the order of discovery can and does change between boots. The only time it can be trusted is when only 1 storage device using the same storage driver is inside the computer.  Since we need to know a specific device consistently, Linux added the concept of UUIDs for partitions. These don't change between boots, even if the disk controller changes or which SATA port connection inside the computer is used. There are some other consistent names for drives and partitions besides UUIDs, but UUIDs is what the installer will use.  Probably more than you need to know today.

Oh ... and if you are coming from MS-Windows.  Don't ever, ever, confuse *a drive* with *a partition*.  MSFT's calling a partition a "drive letter" is unfortunate and confusing.  All those "drive letters" are actually partitions in MS-Windows.  I think they are left over from the floppy drive days when no partitions were used. and A: or B: were used to access logical floppy drives.  To keep things simple in the 1980s, C: ,as a drive letter, was used even when it was a partition.

Wayland doesn't really get along with Nvidia, so choose to use X11, not Wayland for now.  X11 and Wayland are display servers.  Without one of those, there won't be a GUI, no mouse.  Both display servers are usually installed, on the login screen, there is a "gear" button for settings which let's us choose between the different display servers and DEs and WMs, but if you don't see a GUI login screen, then you can't make a selection.

After booting, have you tried to use a different tty?  <cntl><alt>-F4 should switch to a different tty (I think there are 8 or 10 of them). Only 1 TTY is connected to the display server, so all the others are text consoles.  If you get that far, there is much that can be done without any GUI.  I think F1 has the default GUI display server connected. In older Linux versions, it was F7 (for some reason).

SSDs connected USB can be troublesome.  Best not to use them.  A slow, USB2 flash drive for installation ISO would be my preference and only 1 internal SSD.  Best not to connect too many storage devices when there are issues. Limit the confusion.

---

### Post by oldfred on 2023-08-14
If primarily a server, you do not need the nVidia card if Intel chip has video.

I made a mistake when building my system in 2016. Motherboard had 2 video outputs and monitor had 2 inputs. None matched. I used a bit older video card to give compatibility. Later checking video performance data, it showed Intel chip was better than older nVidia card. I do not game, so do not need video cards anyway. Found adapter to convert output/input, so removed old nVidia card. do not plan on buying video card ever again. 

I have not had issues with external SSD and now do not plan on using any of my (many) flash drives for installs. I typically install from one drive to another using grub's loopmount, so do not have to totally erase a drive. And converted a M.2 SSD from the 2016 build to M.2 NVMe as I wanted larger drive, and NVMe have dropped a lot in price. I then put M.2 SSD into USB adapter and it was almost as fast as internal SSD, faster than internal HDD. But some with drives sold as external drives have had some issues as they are pre-formatted. 

Adapter may not be as water resistant nor shock resistant, but I do not (hopefully) need that. I see a lot of NVMe to USB3 adapters, but find that as overkill. NVMe drive only has its speed advantage over SSD when connected directly to NVMe.

---

### Post by MAFoElffen on 2023-08-14
On that I support Ubuntu Server, I'm interested in the hard facts of why an Ubuntu Server ISO is having troubles installing to "something", when it installs to most anything. 

Again, more data needed. I want to see what the error was, and on what hardware. (Specifically.)

---


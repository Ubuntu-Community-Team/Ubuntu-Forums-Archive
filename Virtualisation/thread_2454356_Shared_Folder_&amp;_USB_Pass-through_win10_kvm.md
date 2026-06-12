---
title: "Shared Folder &amp; USB Pass-through win10 kvm"
date: 2020-11-27
forum: Virtualisation
---

### Post by Quarkrad on 2020-11-27
Try as I might I cannot get either shared folder and usb pass-through in either my win10 guest kvm (or ubuntu guest).  I have followed many instructions both via virt manager and the terminal, deleted vm s to start again fresh, but find I'm still defeated.  I feel somewhat exited because indeed kvm is faster and more responsive (than vb) and I can see the end of my win10 dual boot days, but I feel frustrated not being able to achieve what appears to be achievable. A pointer to some instructions that definitely work would be most appreciated (although I suspect I'm not doing something obvious that is not given in the many web pages I have so far tried).

---

### Post by TheFu on 2020-11-27
For shared storage, just use any network method that you would use between 2 physical systems. If that is CIFS or NFS, then use those.  If you want sftp, Windows has filezilla or WinSCP.  These all work, though CIFS has the same problems that CIFS always has.

As for USB passthru ... let me check it out.
My KVM host is running 16.04.  I'll connect to a Windows host using SPICE. On Windows, the GPU drivers are QXL. Inside the VM window, there is a menu .... File View  Send Key Help .... 
I plug in a USB Flash drive, but for Windows VMs, the File --> USB Device Selection is gray.
For a 20.04 Linux VM, File --> USB Device Selection is available. I selected that, a window popped up with 2 USB devices. 
* USB Flash Memory
* CHESEN PS2 to USB Converter (i.e. a USB to PS2 keyboard + mouse)

Inside Linux, I see:
```
$ lsblk 
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sda                        962M disk             
&#9492;&#9472;sda1                     961M part vfat
```
as expected. Back in the USB Device Selection - I deselect the Flash memory and check the Windows File menu. No joy.

Let's check the USB Controller in virt-manager. Under Windows, it is emulating a USB3 controller. It is for the 20.04 VM system too. Hummmm. 

Looking at the Linux guest, I see 2 USB Redirectors setup in the VM HW list, but none are in the Windows VM HW list.  I need to add one to Windows, yes?  Add Hardware, USB Redirectory, Spice Channel.  This change requires a reboot to become effective. No problem - isn't only Windows. ;)  Shutdown (not reboot).  Then restart.  Check the File ---> USB Device Selection.  It is not gray!   Select the Flash Memory and get a warning .... "there are no free channels."  Perhaps I need 2 USB Redirectors minimal?  Let's try that.  Ok, shutdown, added another USB Redirector, started the VM, File--> USB Device selected, no warning/errors.  Could this be it?

Open MS-Exploder and there's not extra drive label.  Check out MS-Disk Manager ... the device isn't seen at all there either.  Maybe I should try a different flash drive?

Grabbed a Kingston microSD -to- USB3.1 converter; dropped in a 64G FAT32 (had to reformat from f2fs) Samsung card, plugged it into the KVM host.  Did a quick mount to ensure it was working:
```
sudo mount -o uid=tf /dev/sdb1  /mnt/1
```
de-mount it in Linux.  Tell Windows VM to redirect it and told disk manager to rescan for disks.  Disk manager isn't seeing it.  It has a MSDOS Partition table and 1 partition FAT32.  Bummer.

Let's try USB2.  Shutdown, change VM settings (USB Controller 3 --> 2), restart the VM .... 

Ok, I spent another 20 minutes screwing around with this and didn't get any farther. Disk Manager, Device Manager, I did see that some "unknown device" was listed, but couldn't install a driver to make it work and at the end, Windows claimed the existing drivers were fine.  I use virtio SCSI disk drivers from redhat in this VM - the QXL driver is from Redhat too, I think.

Just a second ago, saw a Windows popup about a new device, which I was able to click.  It said that the device wasn't working properly and that I needed to remove and re-insert it.  I did that.  The removal had the expected sound, but the re-insertion did not.

Even connected the device to an old, old, old, Win7 machine here. It worked perfectly, as expected.  Told it to format - the default was for exFAT, which I allowed. I don't use exFAT - ever, but this 1 time.  That didn't help.

Time to google some libvirt, Windows USB controller passthru help.
[https://virtuozzosupport.force.com/s/article/000017379](https://virtuozzosupport.force.com/s/article/000017379) says we have to use old versions of USB controllers.
When I look in the VM XML file, I'm seeing ich9-ehci1 as the model of USB controller show.  That link says the model nec-xhci should work. Let's try that.  Ouch. The VM refused to start.  Put it back, quick! ;)

I give up. Sorry.

Use Linux. Much easier. ;)

---

### Post by tea for one on 2020-11-28
Host:-----------[COLOR="#0000FF"]Ubuntu 20.10[/COLOR]
Guest:---------[COLOR="#0000CD"]Win10_20H2_English_x64.iso[/COLOR]
Virtualiser:----[COLOR="#0000FF"]QEMU/KVM[/COLOR]
GUI:------------[COLOR="#0000FF"]Virtual Machine Manager 2.2.1
[/COLOR]
This is my first time using QEMU/KVM and during installation of the VM software and VM GUI, I accepted the defaults.

Luckily, USB Pass Through seems to work OK

Insert USB > Virtual Machine > Redirect USB Device

It was also OK for a USB DVD RW (I managed to add some DVB drivers to Windows 10 guest)

Screenshot attached with USB Stick acceptance.

---

### Post by Quarkrad on 2020-11-28
Wow - thank you, that simple! Just tried it and yes, it is working for me.  Have you had any luck/tried a shared folder(?) - this is a biggie for me as if I could do this I can do away with my win10 dual boot.

---

### Post by TheFu on 2020-11-28
> **Quarkrad said:**
> Wow - thank you, that simple! Just tried it and yes, it is working for me.  Have you had any luck/tried a shared folder(?) - this is a biggie for me as if I could do this I can do away with my win10 dual boot.

I'm on 16.04 KVM.
```
ii  virt-manager     1:1.3.2-3ubuntu1.16.04.4
```
Cannot change that for a few months.
My Windows install has been migrated from VM-host to VM-host for about 10 yrs.  A fresh install will break it.

Happy it is working for someone.  Would be interesting to see the USB controller model specified in the VM XML.  Please.

There are serious security considerations using VM-host-sharing capabilities.  Best to use existing network protocols.  For any Vbox lurkers - this is especially important for people running virtualbox as there are number of problems with the sharing under that hypervisor.

---

### Post by tea for one on 2020-11-28
> **TheFu said:**
>   Would be interesting to see the USB controller model specified in the VM XML.  Please.
.

Controller USB 0 (XML content) as follows:-

```
<controller type="usb" index="0" model="qemu-xhci" ports="15">
  <alias name="usb"/>
  <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
</controller>
```

---

### Post by Dennis N on 2020-11-28
> Insert USB > Virtual Machine > Redirect USB Device
This manual redirection isn't necessary on initial insertion of a USB - at least in newer versions of Virt Manager GUI,  it can be set to automatically appear on the active screen - host or guest. Go to Virt Manager Preferences and  select "Console" tab, then see "Spice USD redirection". Set this to "Auto Redirect on USB attach" See the attached image!

---

### Post by Quarkrad on 2020-11-28
My personal need for a share folder is for itunes so I can have all my mp3 files stored on a separate hd rather than the same disc that the VM is installed on. That is how I currently have it configured using VBox.   For all other vm activities I am 99.9% internal only - however, I do take all the issues re security.

Dennis N  what version of Virt Man are you using?  Mine is 2.2.1

---

### Post by TheFu on 2020-11-28
> **tea for one said:**
> Controller USB 0 (XML content) as follows:-

```
<controller type="usb" index="0" model="qemu-xhci" ports="15">
  <alias name="usb"/>
  <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
</controller>
```

Thanks.  Tried to change to the qemu-xhci devide model and virsh edit refused.
```
error: XML document failed to validate against schema: Unable to validate doc against /usr/share/libvirt/schemas/domain.rng
Extra element devices in interleave
Element domain failed to validate content
```

Guess the libvirt is too old.  I have 3 VM-hosts. 
[LIST]
[*]1 of them isn't critical and will end up being the first of my older systems to be moved to 20.04 when that time comes.  
[*]1 of them is too critical to risk due to all the production VMs it runs.
[*]The last one is also the backup server for the LAN, connected to multiple backup LANs.  My backup software broke with the python2-->python3 move in 20.04, so I'm afraid to move it for now.
[/LIST]
There are always dependencies that slow things down around here. ;(  

Guess I'm out of the USB passthru stuff on Windows ... but it works flawlessly to Linux VMs.

---

### Post by tea for one on 2020-11-28
> **Quarkrad said:**
> My personal need for a share folder is for itunes so I can have all my mp3 files stored on a separate hd rather than the same disc that the VM is installed on. That is how I currently have it configured using VBox.   For all other vm activities I am 99.9% internal only - however, I do take all the issues re security.

If you have a look at this site [https://www.spice-space.org/spice-user-manual.html](https://www.spice-space.org/spice-user-manual.html)

There is some info about:- > Agent support allows better integration with the guest. For example, it allows copy and paste between the guest and the host OSes, dynamic resolution changes when the client window is resized/full-screened, file transfers through drag and drop, 

Under Download tab:- > Windows guest tools - spice-guest-tools

I haven't explored it completely because I'm happy with using USB re-direction at the moment.

Good luck

---

### Post by Dennis N on 2020-11-28
> My personal need for a share folder is for itunes so I can have all my mp3 files stored on a separate hd rather than the same disc that the VM is installed on.

I use a separate virtual data disk (qcow2) so my VMs can each use the same set of music files. You just use the "Add Hardware" feature in the VM Console screen.

My host also has it's own separate data disk. If I want to use files from that data disk in the VM, it's accessed by connecting over network through the host file system where the data disk has been mounted. 

_Automatic Redirection:_
I qualified the post with "at least in newer versions" because I know automatic redirection is not offered in Ubuntu 18.04's virt manager (1.5.1). Two years ago, I switched host to Fedora 29,  partly to get a newer versions of the virtualization software. Back then, it already had the automatic redirection. 

In the current Fedora 33, Virt Manager is version 3.2.0 which is the one shown in the image.

---

### Post by ajgreeny on 2020-11-28
_Automatic Redirection_ for USB is certainly available in virt-manager 2.2.1; I have it enabled.

For other file sharing on Linux distros I simply use ssh. I need host files available in the guest only not the other way round so that fits my requirements exactly.

---

### Post by Quarkrad on 2020-11-29
Dennis N:  I would love some more detail on your set up/configuration - from what you say this looks like the way for me to go.  Have a vm that manages my music library but the actual physical files(mp3) are located outside the vm environment.  (This is similar to my current setup - I use itunes/VBox but currently testing alternatives to itunes.  Hoping to have a linux based music manager (rather than using wine) but would still like to use kvm and store library on separate disc).

---

### Post by TheFu on 2020-11-29
> **Quarkrad said:**
> Dennis N:  I would love some more detail on your set up/configuration - from what you say this looks like the way for me to go.  Have a vm that manages my music library but the actual physical files(mp3) are located outside the vm environment.  (This is similar to my current setup - I use itunes/VBox but currently testing alternatives to itunes.  Hoping to have a linux based music manager (rather than using wine) but would still like to use kvm and store library on separate disc).

Just use nfs.
```
tf@posc:/R/Music$ dft
Filesystem                            Type  Size  Used Avail Use% Mounted on
romulus:/raid/media                   nfs   1.8T  1.7T   19G  99% /R

```
I'm on the nfs client in the "Music" directory above. Not sure what a music manager is. I use easytag to have te ID3 tags correct, nextcloud, plex, and mpd to make those files available in multiple ways. Also use kodi for playback, but mostly use **ncmpd** from **any** client to play on specific speakers around the house.

---

### Post by Dennis N on 2020-11-29
> ...would still like to use kvm and store library on separate disc).

if the 'separate disk' you envision is not virtual, you can connect via local network. I still use that method.
I also have a separate virtual disk, that is mounted in the VMs, but not networked.

See the attached sketch for my setup. 

solid lines: mounts 
dashed lines: network connection
circles: virtual disks

Virtual Data Disk: Use 'Add Hardware' button in the VM details page to create (if necessary) and add to each VM. 

When you add this new disk to additional VMs, you are warned it is used by another OS, but you can add it anyway as long as you don't plan to have two VMs using it simultaneously. After partitioning the new disk, add an entry to fstab of the VM to mount it at the VM's startup. Repeat for other VMs.

You can play music files from the host over the network using the VM's player if you don't want to use this virtual data disk idea. I originally used that kind of setup and still do for some less-used music not on the virtual data disk. 

Music aside, I needed the shared virtual data disk for other compelling reasons as well, so there it is.

I skipped a lot of the details, assuming you know or will figure it out. 

Every OS involved is Linux - no Windows.

---

### Post by tea for one on 2020-11-29
@Quarkrad

If you still require to share folders and usb devices with Ubuntu host and Windows 10 guest, then have a look at [https://wiki.gnome.org/Apps/Boxes](https://wiki.gnome.org/Apps/Boxes)

It's not completely obvious how to arrange the folder sharing but it is possible.

I'm a bit of a novice with VMs and it took me a couple of hours, searching the internet for various instructions etc.

I can jot down my procedure in this thread if you wish but I'm not exactly proficient at writing absolute precise instructions.

---

### Post by tea for one on 2020-12-02
> **Quarkrad said:**
> Have you had any luck/tried a shared folder(?) - this is a biggie for me as if I could do this I can do away with my win10 dual boot.

Here is a website to show the steps to allow a shared folder between Ubuntu host and Windows 10 guest. USB re-direction also works.

The Cockpit Web-UI used in the instructions looks complicated but it is manageable with care. Luckily, you do not have to navigate the Cockpit interface again after the shared connection and path has been set up.

[https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/](https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/)

N.B. Make sure that you download the correct version (32 or 64bit) of spice-webdavd

I followed the instructions and managed to share the folder /home/user/Public.

The connection to the shared folder is lost when the Windows virtual machine is powered off. However, the path remains and can be restored as follows:-

Open Virtual Machine Manager > Select Windows 10 > **Only** Power On Virtual Machine

Minimise the Window Virtual Machine Manager

Open a terminal
```
virt-viewer
```
New dialogue box appears > Connect to Windows 10 (which then opens graphically)

Open File in top left > Preferences > Check box for your pre-arranged folder

Close dialogue box

Log in to Windows 10 > Open File Explorer > This PC > Network Drive (Z)

Always keep the Ubuntu terminal open as virt-viewer controls the process and the connection

---


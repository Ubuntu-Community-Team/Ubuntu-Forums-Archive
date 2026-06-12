---
title: "Make a ubuntu virtual PC BEST tutorial for install guest additions"
date: 2010-12-24
forum: Virtualisation
---

### Post by marcoftheknight on 2010-12-24
Are you confused by how to install guest additions --> finaly the answer is in this video and How to get your screen size bigger for the virtual pc using oh and for sharing files this is also useful.
 
Use the following LINK :
[http://johnsonyip.com/wordpress/2010/03/27/install-virtual-boxs-virtual-additions-on-ubuntu-9-10-and-linux-video/](http://johnsonyip.com/wordpress/2010/03/27/install-virtual-boxs-virtual-additions-on-ubuntu-9-10-and-linux-video/)
 
 
 
 
ALSO LITTLE INFORMATION HOW TO SHARE FOLDER FROM HOST TO VIRTUAL PC 
 
INFO is from ORACLE VMWARE
 
**4.3. [COLOR=#ffffff]Shared folders[/COLOR]**
 
 
 
 
With the "[COLOR=#ffffff]shared folders[/COLOR]" feature of VirtualBox, you can access files of your host system from within the guest system. This is similar how you would use network [COLOR=#ffffff]shares[/COLOR] in Windows networks -- except that [COLOR=#ffffff]shared folders[/COLOR] do not need require networking, so long as the Guest Additions are installed. [COLOR=#ffffff]Shared Folders[/COLOR] are supported with Windows (2000 or newer), Linux and Solaris guests.
[COLOR=#ffffff]Shared folders[/COLOR] must physically reside on the *host* and are then [COLOR=#ffffff]shared[/COLOR] with the guest; [COLOR=#ffffff]sharing[/COLOR] is accomplished using a special service on the host and a file system driver for the guest, both of which are provided by VirtualBox. For Windows guests, [COLOR=#ffffff]shared folders[/COLOR] are implemented as a pseudo-network redirector; for Linux and Solaris guests, the Guest Additions provide a virtual filesystem driver which handles communication with the host.
To [COLOR=#ffffff]share[/COLOR] a host [COLOR=#ffffff]folder[/COLOR] with a virtual machine in VirtualBox, you must specify the path of that [COLOR=#ffffff]folder[/COLOR] and choose for it a "[COLOR=#ffffff]share[/COLOR] name" that the guest can use to access it. Hence, first create the [COLOR=#ffffff]shared folder[/COLOR] on the host; then, within the guest, connect to it.
 
 

There are several ways in which [COLOR=#ffffff]shared folders[/COLOR] can be set up for a particular virtual machine:
[LIST]
[*]In the graphical user interface of a running virtual machine, you can select "[COLOR=#ffffff]Shared folders[/COLOR]" from the "Devices" menu, or click on the [COLOR=#ffffff]folder[/COLOR] icon on the status bar in the bottom right corner of the virtual machine window.
[*]If a virtual machine is not currently running, you can configure [COLOR=#ffffff]shared folders[/COLOR] in each virtual machine's "Settings" dialog.
[*]From the command line, you can create [COLOR=#ffffff]shared folders[/COLOR] using the VBoxManage command line interface; see [Chapter 8, *VBoxManage*]("mk:@MSITStore:C:\PROGRA~1\Oracle\VIRTUA~1\VirtualBox.chm::/ch08.html"). The command is as follows: 
VBoxManage sharedfolder add "VM name" --name "sharename" --hostpath "C:\test"
[/LIST]There are two types of [COLOR=#ffffff]shares[/COLOR]:[LIST=1]
[*]VM [COLOR=#ffffff]shares[/COLOR] which are only available to the VM for which they have been defined;
[*]transient VM [COLOR=#ffffff]shares[/COLOR], which can be added and removed at runtime and do not persist after a VM has stopped; for these, add the --transient option to the above command line.
[/LIST][COLOR=#ffffff]Shared folders[/COLOR] have read/write access to the files at the host path by default. To restrict the guest to have read-only access, create a read-only [COLOR=#ffffff]shared folder[/COLOR]. This can either be achieved using the GUI or by appending the parameter --readonly when creating the [COLOR=#ffffff]shared folder[/COLOR] with VBoxManage.
 
 

Then, you can mount the [COLOR=#ffffff]shared folder[/COLOR] from inside a VM the same way as you would mount an ordinary network [COLOR=#ffffff]share[/COLOR]:
[LIST]
[*]In a Windows guest, starting with VirtualBox 1.5.0, [COLOR=#ffffff]shared folders[/COLOR] are browseable and are therefore visible in Windows Explorer. So, to attach the host's [COLOR=#ffffff]shared folder[/COLOR] to your Windows guest, open Windows Explorer and look for it under "My Networking Places" -> "Entire Network" -> "VirtualBox [COLOR=#ffffff]Shared Folders[/COLOR]". By right-clicking on a [COLOR=#ffffff]shared folder[/COLOR] and selecting "Map network drive" from the menu that pops up, you can assign a drive letter to that [COLOR=#ffffff]shared folder[/COLOR].
Alternatively, on the Windows command line, use the following:
net use x: \\vboxsvr\sharenameWhile vboxsvr is a fixed name (note that vboxsrv would also work), replace "x:" with the drive letter that you want to use for the [COLOR=#ffffff]share[/COLOR], and sharename with the [COLOR=#ffffff]share[/COLOR] name specified with VBoxManage.
[*][COLOR=royalblue]In a Linux guest, use the following command:[/COLOR]
[COLOR=royalblue]mount -t vboxsf [-o OPTIONS] sharename mountpoint[/COLOR]
[*][COLOR=#4169e1]Note ( dont nee the Options thing I dont even know what it is ignore it mountpont= /home/whateverfolderpathyouwant takes a little to load but you can get all your music and use rythm box wahoo!) share name = name of the folder you shared or will be for example name of a drive you shared ex: E_DRIVE[/COLOR]
[*][COLOR=royalblue]To mount a shared folder during boot, add the following entry to /etc/fstab:[/COLOR]
[COLOR=royalblue]sharename mountpoint vboxsf defaults 0 0[/COLOR]
[/LIST]

[LIST]
[*]In a Solaris guest, use the following command:
mount -F vboxfs [-o OPTIONS] sharename mountpointReplace sharename (use lowercase) with the [COLOR=#ffffff]share[/COLOR] name specified with VBoxManage or the GUI, and mountpoint with the path where you want the [COLOR=#ffffff]share[/COLOR] to be mounted on the guest (e.g. /mnt/[COLOR=#ffffff]share[/COLOR]). The usual mount rules apply, that is, create this directory first if it does not exist yet.
Here is an example of mounting the [COLOR=#ffffff]shared folder[/COLOR] for the user "jack" on OpenSolaris:
$ iduid=5000(jack) gid=1(other)$ mkdir /export/home/jack/mount$ pfexec mount -F vboxfs -o uid=5000,gid=1 jackshare /export/home/jack/mount$ cd ~/mount$ lssharedfile1.mp3 sharedfile2.txt$Beyond the standard options supplied by the mount command, the following are available:
iocharset CHARSETto set the character set used for I/O operations (utf8 by default) and
convertcp CHARSETto specify the character set used for the [COLOR=#ffffff]shared folder[/COLOR] name (utf8 by default).
The generic mount options (documented in the mount manual page) apply also. Especially useful are the options uid, gid and mode, as they allow access by normal users (in read/write mode, depending on the settings) even if root has mounted the filesystem.
[/LIST]Thanks 
WAHOO I CAN PLAY STARCRAFT USE ANY WINDOWS PROGRAM AND USE GIMP IN UBUNTU AND BLENDER TO DO MY ART WORK I CAN SHARE FILES BETWEEN MY VIRTUAL AND REAL PC I CAN SHARE MUSIC VIDEO AND FILES oh and try all kinds of new stuff out with ubuntu WAHOOO. virtual pc rocks!!!

---

### Post by b0b138 on 2010-12-25
wow thats way too complicated

whats wrong with going to devices-->install guest additions (or Host+D)

This mounts the guest additions image. If in windows, the installer will autorun.
If anything else, just navigate to the mounted image and run the appropriate script.

---

### Post by karthick87 on 2010-12-25
+1 on post #2

---


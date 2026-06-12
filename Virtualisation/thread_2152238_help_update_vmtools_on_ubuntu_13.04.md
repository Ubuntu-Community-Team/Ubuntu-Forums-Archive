---
title: "help update vmtools on ubuntu 13.04"
date: 2013-06-07
forum: Virtualisation
---

### Post by linux.girl on 2013-06-07
Hello forum,

I need help updating vmtools on ubuntu 13.04 - I keep getting the linux kernel error and dont know what to do - I tried a few fixes, but nothing helped yet.

Any suggestions?

This is what I get (main problem marked in red):

# ./vmware-install.pl 
A previous installation of VMware Tools has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

You have a version of VMware Tools installed.  Continuing this install will 
first uninstall the currently installed version.  Do you wish to continue? 
(yes/no) [yes] 

Uninstalling the tar installation of VMware Tools.

Stopping services for VMware Tools

initctl: Unknown instance: 
This program previously created the file 
/usr/lib/vmware-tools/lib64/libconf/etc/pango/pango.modules, and was about to 
remove it.  Somebody else apparently did it already.

File /etc/vmware-tools/vmware-user.desktop is backed up to 
/etc/vmware-tools/vmware-user.desktop.old.10.

File /usr/lib/vmware-tools/lib64/libconf/etc/gtk-2.0/gtk.immodules is backed up
to /usr/lib/vmware-tools/lib64/libconf/etc/gtk-2.0/gtk.immodules.old.10.

File /usr/lib/vmware-tools/lib64/libconf/etc/fonts/fonts.conf is backed up to 
/usr/lib/vmware-tools/lib64/libconf/etc/fonts/fonts.conf.old.10.

File /usr/lib/vmware-tools/lib64/libconf/etc/gtk-2.0/gdk-pixbuf.loaders is 
backed up to 
/usr/lib/vmware-tools/lib64/libconf/etc/gtk-2.0/gdk-pixbuf.loaders.old.10.

This program previously created the file 
/usr/lib/vmware-tools/libconf/etc/gtk-2.0/gdk-pixbuf.loaders, and was about to 
remove it.  Somebody else apparently did it already.

This program previously created the file 
/usr/lib/vmware-tools/lib64/libconf/etc/pango/pangorc, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file 
/usr/lib/vmware-tools/libconf/etc/gtk-2.0/gtk.immodules, and was about to 
remove it.  Somebody else apparently did it already.

This program previously created the file 
/usr/lib/vmware-tools/lib64/libconf/etc/pango/pangox.aliases, and was about to 
remove it.  Somebody else apparently did it already.

This program previously created the directory /etc/vmware-tools, and was about 
to remove it. Since there are files in that directory that this program did not
create, it will not be removed.

File /etc/pulse/default.pa is backed up to /etc/pulse/default.pa.old.10.

update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-19-generic
The removal of VMware Tools 8.8.6 build-1035889 for Linux completed 
successfully.

Installing VMware Tools.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 8.8.6 build-1035889 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 

Initializing...


Making sure services for VMware Tools are stopped.



[EXPERIMENTAL] The VMware FileSystem Sync Driver (vmsync) is a new feature that
creates backups of virtual machines. Please refer to the VMware Knowledge Base 
for more details on this capability. Do you wish to enable this feature? 
[no] 


Before you can compile modules, you need to have the following installed... 

make
gcc
kernel headers of the running kernel


Searching for GCC...
Detected GCC binary at "/usr/bin/gcc".
The path "/usr/bin/gcc" appears to be a valid path to the gcc binary.
Would you like to change it? [no] 

[COLOR=#ff0000][B]Searching for a valid kernel header path...
The path "" is not a valid path to the 3.8.0-23-generic kernel headers.
Would you like to change it? [yes] 

Enter the path to the kernel header files for the 3.8.0-23-generic kernel? 

The path "" is not a valid path to the 3.8.0-23-generic kernel headers.
Would you like to change it? [yes] no


WARNING: This program cannot compile any modules for the following reason(s)...

- This program could not find a valid path to the kernel headers of the running
kernel.  Please ensure that the header files for the running kernel are 
installed on this sytem.

[ Press Enter key to continue ] [/B][/COLOR]


The communication service is used in addition to the standard communication 
between the guest and the host.  The rest of the software provided by VMware 
Tools is designed to work independently of this feature.
If you wish to have the VMCI feature, you can install the driver by running 
vmware-config-tools.pl again after making sure that gcc, binutils, make and the
kernel sources for your running kernel are installed on your machine. These 
packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 


The VM communication interface socket family is used in conjunction with the VM
communication interface to provide a new communication path among guests and 
host.  The rest of this software provided by VMware Tools is designed to work 
independently of this feature.  If you wish to have the VSOCK feature  you can 
install the driver by running vmware-config-tools.pl again after making sure 
that gcc, binutils, make and the kernel sources for your running kernel are 
installed on your machine. These packages are available on your distribution's 
installation CD.
[ Press the Enter key to continue.] 

The module vmxnet3 has already been installed on this system by another 
installer or package and will not be modified by this installer.  Use the flag 
--clobber-kernel-modules=vmxnet3 to override.

The module pvscsi has already been installed on this system by another 
installer or package and will not be modified by this installer.  Use the flag 
--clobber-kernel-modules=pvscsi to override.

The module vmmemctl has already been installed on this system by another 
installer or package and will not be modified by this installer.  Use the flag 
--clobber-kernel-modules=vmmemctl to override.

The VMware Host-Guest Filesystem allows for shared folders between the host OS 
and the guest OS in a Fusion or Workstation virtual environment.  Do you wish 
to enable this feature? [yes] 


The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 


The vmblock module enables dragging or copying files from within a host and 
dropping or pasting them onto your guest (host to guest drag and drop and file 
copy/paste).  The rest of the software provided by VMware Tools is designed to 
work independently of this feature (including guest to host drag and drop and 
file copy/paste).

If you would like the host to guest drag and drop and file copy/paste features,
you can install the driver by running vmware-config-tools.pl again after making
sure that gcc, binutils, make and the kernel sources for your running kernel 
are installed on your machine. These packages are available on your 
distribution's installation CD.
[ Press Enter key to continue ] 

!!! [EXPERIMENTAL] !!!
VMware automatic kernel modules enables automatic building and installation of
VMware kernel modules at boot they are not already present.  By selecting yes,
you will be enabling this experimental feature.  You can always disable this
feature by re-running vmware-config-tools.pl.

Would you like to enable VMware automatic kernel modules?
[no] 


Disabling timer-based audio scheduling in pulseaudio.



Detected X server version 1.13.3



Distribution provided drivers for Xorg X server are used.

Skipping X configuration because X drivers are not included.

Creating a new initrd boot image for the kernel.
update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
vmware-tools start/running
The configuration of VMware Tools 8.8.6 build-1035889 for Linux for this 
running kernel completed successfully.

You must restart your X session before any mouse or graphics changes take 
effect.

You can now run VMware Tools by invoking "/usr/bin/vmware-toolbox-cmd" from the
command line or by invoking "/usr/bin/vmware-toolbox" from the command line 
during an X server session.

To enable advanced X features (e.g., guest resolution fit, drag and drop, and 
file and text copy/paste), you will need to do one (or more) of the following:
1. Manually start /usr/bin/vmware-user
2. Log out and log back into your desktop session; and,
3. Restart your X session.

Enjoy,

--the VMware team

---

### Post by linux.girl on 2013-06-07
Friends, found the solution at the vmware forum, I dont know if I am allowed to post links here, if yes let me know and I will point you to the correct solution.

Thanks!

---


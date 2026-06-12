---
title: "About VirtualBox installation and VMs migration"
date: 2012-12-10
forum: Virtualisation
---

### Post by satimis on 2012-12-10
Hi all,

Host - Ubuntu 12.04 desktop 64bit
Virtualizer - Oracle VirtualBox
AMD 8-core

Please advise where can I find howto/instruction re installing VirtualBox from the package download on;
Download VirtualBox for Linux Hosts
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

NOT installed from the package, oracle_vbox.asc.

Most of the threads found with googling are installing on oracle_vbox.asc.

I have a box here running for several years and been upgraded many times;
Host - Ubuntu 12.04 desktop 64bit
Virtualizer - Oracle VirtualBox
AMD 4-core

I already forgot how to install VirtualBox.  The Original host was Ubuntu 7.0/8.0

Besides where can I find instruction migrating the VMs from the old host to new host (on another PC)

TIA

B.R.
satimis

---

### Post by SeijiSensei on 2012-12-10
Follow the instructions on the VirtualBox [Linux downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads") for "Debian-based" distributions to add the repository and its public key.  Then you can just use:

```

sudo apt-get update
sudo apt-get install virtualbox-4.2

```

This method lets the OS manage updates for you as well.

---

### Post by gwm on 2012-12-12
Hi,
This is working for me. I too had forgotten how to ...
Package manager figured I didn't even have Virtual box installed.
Following the lead in **SeijiSensei's** post I went to synaptic and edited the repositories. There I found a whole bunch that were disabled when I last upgraded to "precise" (12.04). So I edited them one at a time, removing the comments and ensuring that the check boxes were ticked (I want them enabled).
Then I reloaded and marked all upgrades but nothing was available!? So I went looking for virtualbox and found 4.2 was now listed. I checked it for install and selected "apply".
Synaptic told me it was removing 4.1 and installing 4.2 together with a required library and away we go!
It is still in progress, so I don't know whether I'll have to re-link my virtual machines. I do remember having to manually reactivate my Microsoft software (windows, office and visual studio etc.) after previous upgrades though.
:guitar:

---

### Post by SeijiSensei on 2012-12-12
All my VMs worked as expected after upgrading from 4.1 to 4.2.

---

### Post by gwm on 2012-12-12
Mine seem to be working fine too.
Be sure to install the new extension pack. If all else fails, you can download it from **[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)**
then double click the downloaded file in the downloads directory.
Once windows has started, find the **devices** menu item and upgrade the guest additions.
:p

---

### Post by JKyleOKC on 2012-12-12
To move the VMs from one hard disk to another, whether on the same system or a different one, just copy the virtualbox directories and all their contents using normal Linux copy methods. My older vbox 3.x installation had just one directory, a hidden one in my home directory, that held everything. The newer 4.x installations have multiple directories, so you need to copy all of them. However there's no need to go through the detailed export-import techniques described in the vbox manuals. So long as you have the vbox program itself in place on the new system, everything will work properly after the move.

---

### Post by CharlesA on 2012-12-12
> **SeijiSensei said:**
> All my VMs worked as expected after upgrading from 4.1 to 4.2.
Just to add to this - all my VMs worked fine when I moved from 3.2 to 4.x.

---

### Post by satimis on 2012-12-12
> **JKyleOKC said:**
> To move the VMs from one hard disk to another, whether on the same system or a different one, just copy the virtualbox directories and all their contents using normal Linux copy methods....
Hi,

On my old box
=============

$ ls /home/satimis/VirtualBox\ VMs/```

    cloudera    deb60ser02   deb60ser05             essex4       ub1024dk00
    cloudoncd   deb60ser02a  enlightmntdk_ub1204dk  fedora1700   ub1204dk00
    deb600dk02  deb60ser02b  essex1                 fedora1701   ub1204ser00
    deb60ser00  deb60ser03   essex2                 linuxmint13  ub1204ser01
    deb60ser01  deb60ser04   essex3                 stackops01   win86400

```

$ ls /home/satimis/VirtualBox\ VMs/deb600dk02/```

    deb600dk02.vbox  deb600dk02.vbox-prev  Logs

```


On my new box
=============

I could not find following directory```

/home/satimis/VirtualBox\ VMs/

```

There is no "VirtualBox VMs" under /home/satimis/

I download;
virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb

on their site:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

and ran "dpkg -i virtualbox-4.2_4.2.4-81684~Ubuntu~quantal_amd64.deb" to install VirtualBox.

Whether I have to create "VirtualBox VMs" directory manually?  

Can Virt-Manager find this directory automatically on starting?

TIA

B.R.
satimis

---

### Post by JKyleOKC on 2012-12-13
Here's the drill step by step:
1. On the old box, get the total size of your VirtualBox\ VMs folder, including all its content.
2. Mount an external drive large enough to hold all those bytes; in my case it was more than 100 GB. Yours might be much smaller, or larger.
3. Use the cp command with the -r option to copy the whole directory onto the external drive, using its original name.
4. Unmount the drive, connect it to the new box, and be sure you're in the external drive.
5. Use "cp -r VirtualBox\ VMs $HOME" to copy everything from the external drive to your home directory in the new box. This will create the vbox directory automatically as its first step. Using the HOME environment variable will take care of the destination address.
6. If you have a ".virtualbox" hidden directory on the old box, repeat the process with it to take it to the new one.

You may need to fill in details that I may have overlooked, but the key part of the process is to use the "-r" option with "cp" to move everything with a single command.

---

### Post by CharlesA on 2012-12-13
> **JKyleOKC said:**
> Here's the drill step by step:
1. On the old box, get the total size of your VirtualBox\ VMs folder, including all its content.
2. Mount an external drive large enough to hold all those bytes; in my case it was more than 100 GB. Yours might be much smaller, or larger.
3. Use the cp command with the -r option to copy the whole directory onto the external drive, using its original name.
4. Unmount the drive, connect it to the new box, and be sure you're in the external drive.
5. Use "cp -r VirtualBox\ VMs $HOME" to copy everything from the external drive to your home directory in the new box. This will create the vbox directory automatically as its first step. Using the HOME environment variable will take care of the destination address.
6. If you have a ".virtualbox" hidden directory on the old box, repeat the process with it to take it to the new one.

You may need to fill in details that I may have overlooked, but the key part of the process is to use the "-r" option with "cp" to move everything with a single command.

This will grab everything. I prefer rsync to cp, but they get the job done.

If you want to store the VMs in a directory other than your home directory, symlinks are your best friend. ;)

---

### Post by satimis on 2012-12-13
> **CharlesA said:**
> This will grab everything. I prefer rsync to cp, but they get the job done.

If you want to store the VMs in a directory other than your home directory, symlinks are your best friend. ;)

Thanks for your advice.

I'm a little bid confused about the VMs on the old PC, with both .xml and .vbox extension.  This old PC has been running for several years.  Ubuntu has been upgraded from 7.0/8.0 to now 12.04 and VirtualBox upgraded from ver-3 to now ver-4

# find / -name *.xml```

    /home/satimis/.VirtualBox/VirtualBox.xml
    /home/satimis/.VirtualBox/Machines/ub10041ser00/ub10041ser00.xml
    /home/satimis/.VirtualBox/Machines/sugarub910zh/sugarub910zh.xml
    /home/satimis/.VirtualBox/Machines/ub1010server00/ub1010server00.xml
    /home/satimis/.VirtualBox/Machines/ub10041ser02/ub10041ser02.xml
    /home/satimis/.VirtualBox/Machines/deb600dk01/deb600dk01.xml
    /home/satimis/.VirtualBox/Machines/ub1010dk03/ub1010dk03.xml
    /home/satimis/.VirtualBox/Machines/ub1010server01/ub1010server01.xml
    /home/satimis/.VirtualBox/Machines/win73203/win73203.xml
```

# ls /home/satimis/.VirtualBox/Machines/```

    deb600dk00    sugarub910zh  ub1004dk02      ub1010server01  win73203  win76405a
    deb600dk01    ub10041ser00  ub1010dk01      ub1010server02  win73204  win76406
    MyDLP         ub10041ser01  ub1010dk02      uc1010node1     win764    win76408
    sugarub910    ub10041ser02  ub1010dk03      ucld101000      win76403  ws20086402
    sugarub910cn  ub10041ser03  ub1010server00  win732          win76405  ws20086405

```

$ ls /home/satimis/VirtualBox\ VMs/```

    cloudera    deb60ser02   deb60ser05             essex4       ub1024dk00
    cloudoncd   deb60ser02a  enlightmntdk_ub1204dk  fedora1700   ub1204dk00
    deb600dk02  deb60ser02b  essex1                 fedora1701   ub1204ser00
    deb60ser00  deb60ser03   essex2                 linuxmint13  ub1204ser01
    deb60ser01  deb60ser04   essex3                 stackops01   win86400

```

$ ls /home/satimis/VirtualBox\ VMs/deb600dk02/```

    deb600dk02.vbox  deb600dk02.vbox-prev  Logs

```


On the new PC I expect to have one extension, .vbox.  How can I do it?  

Which is the official directory created by VirtualBox at time of installation?  I expect to have all VMs on the official directory.

TIA

I'll run rsync to copy all VMs from the old PC to new PC via the router on Intranet.

B.R.
satimis

---

### Post by JKyleOKC on 2012-12-13
> **satimis said:**
> On the new PC I expect to have one extension, .vbox.  How can I do it?  

Which is the official directory created by VirtualBox at time of installation?  I expect to have all VMs on the official directory.You can't have a single extension. The XML files contain the definitions of the VMs themselves, while the VDI files are the virtual drives. Don't try to change the naming conventions; that will simply make things fail to work.

In my case, both directories are "official." The hidden directory was created by my old vbox 3.2 installation; the un-hidden one was created when I upgraded to vbox 4.x, but the older one was left in place and is still used for VMs that were originally there. I don't know whether 4.x creates the hidden directory still, or just the one in the open; that's why my "if you have it" statement...

---

### Post by CharlesA on 2012-12-13
> **JKyleOKC said:**
> You can't have a single extension. The XML files contain the definitions of the VMs themselves, while the VDI files are the virtual drives. Don't try to change the naming conventions; that will simply make things fail to work.

In my case, both directories are "official." The hidden directory was created by my old vbox 3.2 installation; the un-hidden one was created when I upgraded to vbox 4.x, but the older one was left in place and is still used for VMs that were originally there. I don't know whether 4.x creates the hidden directory still, or just the one in the open; that's why my "if you have it" statement...

What he said.

If you have snapshots on the VMs, just leave them as they are. If you don't have any snapshots and it really bugs you, export the VM, delete it and then import it again.

As always keep a backup of the original until you are sure everything is working ok.

---

### Post by satimis on 2012-12-13
Hi JKyleOKC and CharlesA,

Thanks for your advice.

The old PC has been running for several years and I couldn't recall what has happened before.  Nor I have recollection how VirtualBox was installed.

I wonder why there are several directories?  The old PC is still running.  I haven't touched anything on it.  I'll keep the old PC until all VMs have been migrated to the new PC and running without problem.

Virtual Machine Manager is running on the old PC (pls see attached picture).  I'll install it on the new PC

Thanks

Edit:

I'm sure that I installed VirtualBox downloading the software on Sun's website (now Oracle)

B.R.
satimis

---

### Post by JKyleOKC on 2012-12-13
You may well have multiple directories, then. The VMs created before upgrading to 4.x will be in the hidden one while those created afterward will be in the un-hidden one.

My guess as to "why" is simply that Oracle decided the directory should be out in the open rather than hidden, but it might also have to do with features added in 4.x that didn't quite fit the older directory structure (although I can't think of any). Perhaps Charles will have a better idea...

---

### Post by CharlesA on 2012-12-13
> **satimis said:**
> 
The old PC has been running for several years and I couldn't recall what has happened before.  Nor I have recollection how VirtualBox was installed.

I wonder why there are several directories?  The old PC is still running.  I haven't touched anything on it.  I'll keep the old PC until all VMs have been migrated to the new PC and running without problem.

Not sure why there are several directories, as all the VMs I created in 3.2 resided in a single directory.

> Virtual Machine Manager is running on the old PC (pls see attached picture).  I'll install it on the new PC

Judging from the screenshot, it looks like there are no snapshots, but check the snapshot tab on each VM and see if there is anything there. If there aren't you can just export them and import them on the new machine.

> **JKyleOKC said:**
> 
My guess as to "why" is simply that Oracle decided the directory should be out in the open rather than hidden, but it might also have to do with features added in 4.x that didn't quite fit the older directory structure (although I can't think of any). Perhaps Charles will have a better idea...

I don't really know, but I think it has to do with having them better organized.

---

### Post by satimis on 2012-12-14
> **CharlesA said:**
>  -snip -

Judging from the screenshot, it looks like there are no snapshots, but check the snapshot tab on each VM and see if there is anything there. If there aren't you can just export them and import them on the new machine.

Please explain in more detail where to export and import?  On VirtualBox "Virtual Box Manager"?

Thanks.

I'm still struggling on sound problem.  It is the Realtek chipset.  If I couldn't find a solution I'm compelled running other OS as host.

Fedora 17 desktop doesn't have sound problem on this PC.  I have tested it on another HD.  I'll test Debian 6.0 desktop later.

B.R.
satimis

---

### Post by CharlesA on 2012-12-14
If you select the VM and right click on it, it should give you the option to export. If you have any snapshots on the VM, they will be "flattened" and only the current state will be exported.

You would just need to copy the exported files to the new machine and import them from the VM Manager.

---

### Post by satimis on 2012-12-19
> **CharlesA said:**
> If you select the VM and right click on it, it should give you the option to export. If you have any snapshots on the VM, they will be "flattened" and only the current state will be exported.

You would just need to copy the exported files to the new machine and import them from the VM Manager.
Hi,

Right click VM.  No such "export" item there.

Click;
Snapshots
-> Current State ->
start "Take Snapshot of VM window

Snapshot Name:
Snapshot 1 (automatically popup)

Snapshot Description:
(Empty)

What shall I fill in there?  Thanks

B.R.
satimis

---

### Post by CharlesA on 2012-12-19
Whoops, it looks like the export option is in the file menu.

[http://grok.lsu.edu/article.aspx?articleid=13838](http://grok.lsu.edu/article.aspx?articleid=13838)

Don't bother with snapshots if you don't have any now.

---

### Post by satimis on 2012-12-21
> **CharlesA said:**
> Whoops, it looks like the export option is in the file menu.

[http://grok.lsu.edu/article.aspx?articleid=13838](http://grok.lsu.edu/article.aspx?articleid=13838)

Don't bother with snapshots if you don't have any now.
Hi,

I don't have File menu on VirtualBox Manager.  Pls see attached screenshot

---

### Post by CharlesA on 2012-12-21
What happens if you move the mouse to the top of the screen? The menu bar should show up there.

---

### Post by satimis on 2012-12-24
> **CharlesA said:**
> What happens if you move the mouse to the top of the screen? The menu bar should show up there.
Yes, I found it there.  Thanks

Now I have virtualbox-4.2 install on the new HD running;```

sudo apt-get update
sudo apt-get install virtualbox-4.2

```

dkms already installed during installing Ubuntu12.04

$ virtualbox```

Error opening file for reading: Permission denied
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28 

```

virtualbox manager starts disregarding the warning.  Anything I have to do in respect of the warning?

What will be the next step migrating all VMs from the old HD to the new HD?  TIA

B.R.
satimis

---

### Post by CharlesA on 2012-12-24
If you are running virtualbox from a terminal, those messages are normal, don't worry about it.

As far as migration is concerned, export from old box, and import to new box.

---

### Post by satimis on 2012-12-24
> **CharlesA said:**
> If you are running virtualbox from a terminal, those messages are normal, don't worry about it.

Noted.  Thanks

> 
As far as migration is concerned, export from old box, and import to new box.
What I can't resolved is "there are many directories for the VM images in the OLD HD."

I'll boot up the OLD HD with the NEW HD connected as /dev/sdb.  On "export" will it find the path to the NEW HD automatically?  If I have to supply the path to VMs destination which directory on the NEW HD shall I use?  TIA

B.R.
satimis

---

### Post by CharlesA on 2012-12-24
> **satimis said:**
> 
I'll boot up the OLD HD with the NEW HD connected as /dev/sdb.  On "export" will it find the path to the NEW HD automatically?  If I have to supply the path to VMs destination which directory on the NEW HD shall I use?  TIA

As long as you have the new HD mounted, you can export the files to it. You will still need to import them from the GUI before you can use them, but that shouldn't be a problem.

As for the extra folders on the old machine. I have no idea as I haven't seen that before.

---

### Post by satimis on 2012-12-27
> **CharlesA said:**
> As long as you have the new HD mounted, you can export the files to it. You will still need to import them from the GUI before you can use them, but that shouldn't be a problem.

As for the extra folders on the old machine. I have no idea as I haven't seen that before.
Hi,

On starting migration I discovered space is my problem.  The total capcity of VMs is about 500G.  The HD to be used is only 600G, insufficient space.  I'll purchase a new WD 1.5TB black series HD.

Meanwhile please advice:
On export, there are 2 items for selection;
- Write legacy OVF 0.9
- Write Manifest file
Whether I need to select them?

On import following warning popup;```

Failed to open a session for the virtual machine cloudera.
Implementation of the USB 2.0 controller not found!
Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

```

$ apt-cache search virtualbox | grep virtualbox```

...
virtualbox - x86 virtualization solution - base binaries
virtualbox-dbg - x86 virtualization solution - debugging symbols
virtualbox-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-fuse - x86 virtualization solution - virtual filesystem
virtualbox-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-guest-source - x86 virtualization solution - guest addition module source
virtualbox-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-guest-x11 - x86 virtualization solution - X11 guest utilities

```
Which package/packages I need to install?

TIA

B.R.
satimis

---

### Post by CharlesA on 2012-12-27
> **satimis said:**
> Hi,

On starting migration I discovered space is my problem.  The total capcity of VMs is about 500G.  The HD to be used is only 600G, insufficient space.  I'll purchase a new WD 1.5TB black series HD.

Meanwhile please advice:
On export, there are 2 items for selection;
- Write legacy OVF 0.9
- Write Manifest file
Whether I need to select them?

None, you shouldn't need either of those.


> 
On import following warning popup;```

Failed to open a session for the virtual machine cloudera.
Implementation of the USB 2.0 controller not found!
Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

```

$ apt-cache search virtualbox | grep virtualbox```

...
virtualbox - x86 virtualization solution - base binaries
virtualbox-dbg - x86 virtualization solution - debugging symbols
virtualbox-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-fuse - x86 virtualization solution - virtual filesystem
virtualbox-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-guest-source - x86 virtualization solution - guest addition module source
virtualbox-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-guest-x11 - x86 virtualization solution - X11 guest utilities

```
Which package/packages I need to install?

TIA

B.R.
satimis

None of them. You just need to install the extension pack from here:
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by satimis on 2012-12-27
> **CharlesA said:**
> None, you shouldn't need either of those.

Noted.  Thanks

> 
None of them. You just need to install the extension pack from here:
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
I followed ;

Download VirtualBox for Linux Hosts
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Performed following steps installing VirtualBox;

$ sudo gedit /etc/apt/sources.list
adding;
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

$ wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
[sudo] password for satimis: 
OK

$ sudo apt-get update
$ apt-cache search virtualbox | grep virtualbox-4```

virtualbox-4.1 - Oracle VM VirtualBox
virtualbox-4.2 - Oracle VM VirtualBox

```

$ sudo apt-get install virtualbox-4.2```

.....
Adding group `vboxusers' (GID 125) ...
Done.
 * Stopping VirtualBox kernel modules
   ...done.
 * Uninstalling old VirtualBox DKMS kernel modules
   ...done.
 * Trying to register the VirtualBox kernel modules using DKMS

   ...done.
 * Starting VirtualBox kernel modules
   ...done.
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up python-central (0.6.17ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

dkms already installed

$ apt-cache policy dkms```

dkms:
  Installed: 2.2.0.3-1ubuntu3
  Candidate: 2.2.0.3-1ubuntu3
  Version table:
 *** 2.2.0.3-1ubuntu3 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

Whether I should use the package - "VirtualBox 4.2.6 Oracle VM VirtualBox Extension Pack All supported platforms" ?  Or installing the extension pack on repo?

B.R.
satimis

---

### Post by CharlesA on 2012-12-27
> **satimis said:**
> 
Whether I should use the package - "VirtualBox 4.2.6 Oracle VM VirtualBox Extension Pack All supported platforms" ?  Or installing the extension pack on repo?

Install that extension pack. it isn't available in the repos.

---

### Post by satimis on 2012-12-28
> **CharlesA said:**
> Install that extension pack. it isn't available in the repos.
Hi,

I got it done.  Thanks

I'm now migrating the VMs on the OLD HD to NEW HD.  It'll take sometime.

I have following questions please shed me some light.

I keep all VMs on /data partition which is owned by root

To allow users running VMs

1)
Whether
Keep /data owned by root
drwxr-xr-x 7 root root 4096 Dec 29 00:48 /data

Give rwx permission to the users of the group
$ sudo chmod go+rwx -R /data

$ cat /etc/group | grep data
www-data:x:33:

Add users allowed to group
```

www-data:x:33:userA userB userC etc

```


2)
How to allow userA userB userC etc running the VM owned by them only?

Now;
$ ls -al /data/VirtualBox\ VMs/```

total 12
drwxrwxr-x 3 satimis satimis 4096 Dec 29 00:49 .
drwxr-xr-x 7 satimis satimis 4096 Dec 29 00:48 ..
drwx------ 3 satimis satimis 4096 Dec 29 00:52 cloudera
drwx------ 2 satimis satimis 4096 Dec 29 10:50 deb600dk00
etc.

```

satimis is the Administrator
e.g. 
userA owns cloudera
userB owns deb600dk00

TIA


Regards
satimis

---

### Post by CharlesA on 2012-12-28
You would need to change the permissions and then add each VM to each user's' VBox instance.

---

### Post by satimis on 2012-12-29
> **CharlesA said:**
> You would need to change the permissions and then add each VM to each user's' VBox instance.
Could you please explain in more detail?  Thanks

Regards
satimis

---

### Post by CharlesA on 2012-12-29
> **satimis said:**
> Could you please explain in more detail?  Thanks

Regards
satimis
Each of these users will need their respective VMs in their own home directory which means importing it when they are logged in. This would mean you do not have to deal with permissions problems.

---

### Post by satimis on 2012-12-29
> **CharlesA said:**
> Each of these users will need their respective VMs in their own home directory which means importing it when they are logged in. This would mean you do not have to deal with permissions problems.
If I understand your advice correctly.

After creating userA account start VirtualBox and from there import the VM which is allowed to view?  Can adminstrator view UserA's VM without login its account?

For new VM I found following reference
VBoxManage registervm / unregistervm
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-registervm](http://www.virtualbox.org/manual/ch08.html#vboxmanage-registervm)

# VBoxManage createvm --register

Then how about /data which is owned by root.  The *.ova are now stored there under /data/OVA directory

Regards
satimis

---

### Post by CharlesA on 2012-12-30
> **satimis said:**
> If I understand your advice correctly.

After creating userA account start VirtualBox and from there import the VM which is allowed to view?  Can adminstrator view UserA's VM without login its account?

That is pretty much what you would have to do. VBox doesn't support access controls and only sees VMs on a user-only level - so each user would need to import their own VMs. This gets problematic with more than one or two users.

As far as Viewing the VMs, they would need to use that user's account to view them (or if they are running, they can use some sort of remote access to view them, but I do not recommend that.)

---

### Post by satimis on 2012-12-31
> **CharlesA said:**
> That is pretty much what you would have to do. VBox doesn't support access controls and only sees VMs on a user-only level - so each user would need to import their own VMs. This gets problematic with more than one or two users.

As far as Viewing the VMs, they would need to use that user's account to view them (or if they are running, they can use some sort of remote access to view them, but I do not recommend that.)
Performed following steps


1)
login administrator, satimis

(remark: I can't create folders/directoris direct on Preference -> General -> Default Machine Folder
because /data is owned by root)

On terminal:-
$ sudo mkdir -p /data/VirtualBox/satimis

$ ls -ald /data/
drwxr-xr-x 8 root root 4096 Dec 31 22:34 /data/

$ ls -ald /data/VirtualBox
drwxr-xr-x 3 root root 4096 Dec 31 22:34 /data/VirtualBox

$ ls -ald /data/VirtualBox/satimis/
drwxr-xr-x 2 root root 4096 Dec 31 22:34 /data/VirtualBox/satimis/

$ cd /data/
$ sudo chown -R satimis:satimis VirtualBox

import VM.voa is without problem. All VMs imported work after changing network

2)
login as userA and create /data/VirtualBox/userA

But I'm not allowed to import its VMs because /VirtualBox is owned by administrator.

Any suggestion. TIA

B.R.
satimis

---

### Post by JKyleOKC on 2012-12-31
> **satimis said:**
> Any suggestion. TIAHere's one way to do it:

1) login administrator, satimis

2) On terminal:
```
$ sudo mkdir -p /data/VirtualBox/userA
$ sudo mkdir -p /data/VirtualBox/userB
$ sudo mkdir -p /data/VirtualBox/userC
and so on as needed
```
3) next, still logged in as yourself:
```
$ sudo chown -R userA:userA /data/VirtualBox/userA
$ sudo chown -R userB:userB /data/VirtualBox/userB
$ sudo chown -R userC:userC /data/VirtualBox/userC
and so on as needed
```
4) Logout as administrator, login as userA, and import VMs to /data/VirtualBox/userA.
Repeat for other users.

Others ways exist but this seems to me to be the most straightforward. With sudo you can create all the user-specific directories, and can chown them to the desired users and groups. Once that is done, each user has access to his/her own area with full permissisons.

---

### Post by satimis on 2013-01-01
> **JKyleOKC said:**
> Here's one way to do it:

1) login administrator, satimis

2) On terminal:
```
$ sudo mkdir -p /data/VirtualBox/userA
$ sudo mkdir -p /data/VirtualBox/userB
$ sudo mkdir -p /data/VirtualBox/userC
and so on as needed
```
3) next, still logged in as yourself:
```
$ sudo chown -R userA:userA /data/VirtualBox/userA
$ sudo chown -R userB:userB /data/VirtualBox/userB
$ sudo chown -R userC:userC /data/VirtualBox/userC
and so on as needed
```
4) Logout as administrator, login as userA, and import VMs to /data/VirtualBox/userA.
Repeat for other users.

Others ways exist but this seems to me to be the most straightforward. With sudo you can create all the user-specific directories, and can chown them to the desired users and groups. Once that is done, each user has access to his/her own area with full permissisons.

Hi,

Thanks for your advice.  Performed following steps;

login satimis (administrator)

$ sudo mkdir -p /data/VirtualBox/userA

$ ls -ald /data/VirtualBox/userA```

drwxr-xr-x 2 root root 4096 Jan  1 21:20 /data/VirtualBox/userA

```

$ ls -ald /data/VirtualBox```

drwxr-xr-x 4 satimis satimis 4096 Jan  1 21:20 /data/VirtualBox

```

$ sudo chown userA:userA /data/VirtualBox/userA

$ ls -ald /data/VirtualBox/userA```

drwxr-xr-x 2 userA userA Jan  1 21:20 /data/VirtualBox/userA

```

logout satimis and login userA

Start VirtualBox
-> import appliance

Failed to import appliance /data/OVA/deb600dk01.ova
Could not open OVA file 'data/OVA/deb600dk01.ova

All export VMs are on /data/OVA/

userA is not on /etc/sudoer.  Neither I expect /VirtualBox owned by userA

satimis

---

### Post by CharlesA on 2013-01-01
Check permissions on /data/OVA.

---

### Post by satimis on 2013-01-01
> **CharlesA said:**
> Check permissions on /data/OVA.
$ ls -ald /data/OVA```

drwxrwxr-x 2 satimis satimis 4096 Dec 29 00:21 /data/OVA
```

$ ls -ald /data```

drwxr-xr-x 8 root root 4096 Dec 31 22:34 /data

```

---

### Post by JKyleOKC on 2013-01-01
Try changing the "group" settings (but not owner) for /data/OVA to "vboxusers" instead of the current owner, and allowing group write permissions (drwxr[COLOR="Red"]w[/COLOR]xr-x) for only the duration of the time that you are doing the imports. Since each user must belong to the vboxusers group, this should allow them to do their importing; however it would also allow UserA to make changes to UserB's area, if you leave that write permission in place.

---

### Post by satimis on 2013-01-01
> **JKyleOKC said:**
> Try changing the "group" settings (but not owner) for /data/OVA to "vboxusers" instead of the current owner, and allowing group write permissions (drwxr[COLOR="Red"]w[/COLOR]xr-x) for only the duration of the time that you are doing the imports. Since each user must belong to the vboxusers group, this should allow them to do their importing; however it would also allow UserA to make changes to UserB's area, if you leave that write permission in place.

$ cat /etc/group | grep vboxusers```

vboxusers:x:125:satimis

```

Whether adding userA, userB etc. to the vboxusers?

$ ls -ald /data/OVA```

drwxrwxr-x 2 satimis satimis 4096 Dec 29 00:21 /data/OVA

```
How to change the permission here?  Thanks

---

### Post by JKyleOKC on 2013-01-01
I'll have to leave the answer to that for CharlesA since he's been working you through the trickier parts of changing permissions, and knows better than I just how to explain it to you.

---

### Post by CharlesA on 2013-01-02
Do you have any shared folders enabled on those VMs?

It seems like if you do, the VM won't import. The import screen should tell you if you have any shared folders or not.
[https://forums.virtualbox.org/viewtopic.php?f=6&t=38275](https://forums.virtualbox.org/viewtopic.php?f=6&t=38275)

---

### Post by satimis on 2013-01-02
> **CharlesA said:**
> Do you have any shared folders enabled on those VMs?

It seems like if you do, the VM won't import. The import screen should tell you if you have any shared folders or not.
[https://forums.virtualbox.org/viewtopic.php?f=6&t=38275](https://forums.virtualbox.org/viewtopic.php?f=6&t=38275)
Shared folders?  I'm not on Windows.  Where can I find the shared folders?  On the new HD?  Tks

---

### Post by CharlesA on 2013-01-02
> **satimis said:**
> Shared folders?  I'm not on Windows.  Where can I find the shared folders?  On the new HD?  Tks

They should be in the VM properties window when you try to import it.

Did it say anything else other than failed to import?

---

### Post by satimis on 2013-01-02
> **CharlesA said:**
> They should be in the VM properties window when you try to import it.

Yes, I found it on "VM VirtualBox Manager"

Shared Folder
None
(I'm now on the OLD HD)

> 
Did it say anything else other than failed to import?

IIRC only mentioned "permission problem"

---

### Post by CharlesA on 2013-01-02
Ok, so it's not a shared folder problem.

Check the permissions inside the /data/OVA folder and post the results.

```
ls -l /data/OVA/
```

---

### Post by satimis on 2013-01-02
> **CharlesA said:**
> Ok, so it's not a shared folder problem.

Check the permissions inside the /data/OVA folder and post the results.

```
ls -l /data/OVA/
```

$ ls -ald /data/OVA```

drwxrwxr-x 2 satimis satimis 4096 Jan  2 22:58 /data/OVA
```

$ ls -al /data/OVA/```

total 158665300
drwxrwxr-x 2 satimis satimis        4096 Jan  2 22:58 .
drwxr-xr-x 8 root    root           4096 Dec 31 22:34 ..
-rw------- 1 satimis satimis  6453506560 Dec 27 16:22 cloudera.ova
-rw------- 1 satimis satimis      736768 Dec 28 23:42 cloudoncd.ova
-rw------- 1 satimis satimis  6901194240 Jan  1 12:37 deb600dk00_1.ova
-rw------- 1 satimis satimis  6901194240 Dec 28 23:55 deb600dk00.ova
-rw------- 1 satimis satimis  5569650688 Dec 29 00:13 deb600dk01.ova
-rw------- 1 satimis satimis  6330367488 Jan  1 10:47 deb600dk02.ova
-rw------- 1 satimis satimis   627798528 Jan  1 10:52 deb60ser00.ova
-rw------- 1 satimis satimis   664978944 Jan  1 10:54 deb60ser01.ova
-rw------- 1 satimis satimis   827026432 Jan  1 10:59 deb60ser02a.ova
-rw------- 1 satimis satimis   869670912 Jan  1 11:02 deb60ser02b.ova
-rw------- 1 satimis satimis   811467776 Jan  1 10:57 deb60ser02.ova
-rw------- 1 satimis satimis   660776448 Jan  1 11:05 deb60ser03.ova
-rw------- 1 satimis satimis   590995456 Jan  1 12:04 deb60ser04.ova
-rw------- 1 satimis satimis   823435776 Jan  1 12:51 deb60ser05.ova
....
....
-rw------- 1 satimis userA  2452633600 Jan  1 12:59 essex1.ova
-rw------- 1 satimis userA  2660953088 Jan  1 13:10 essex2.ova
-rw------- 1 satimis userA   710354432 Jan  1 13:16 essex3.ova
-rw------- 1 satimis userA   918861824 Jan  1 13:19 essex4.ova
-rw------- 1 satimis userA  2105741312 Jan  1 13:25 fedora1700.ova
-rw------- 1 satimis userA  3591307264 Jan  1 13:33 fedora1701.ova
-rw------- 1 satimis userA  1751297024 Jan  1 13:43 linuxmint13.ova
-rw------- 1 satimis userA  2598827520 Jan  1 13:50 MyDLP.ova
-rw------- 1 satimis userA   849887232 Jan  1 13:53 stackops01.ova
-rw------- 1 satimis userA  3709683200 Jan  1 22:35 sugarub910cn.ova
-rw------- 1 satimis userA  2921337856 Jan  1 13:59 sugarub910.ova
-rw------- 1 satimis userA  9267556864 Jan  2 22:16 win73203.ova
-rw------- 1 satimis userA  4141147648 Jan  2 21:15 win73204.ova
-rw------- 1 satimis userA  6849847296 Jan  2 20:56 win76400.ova
-rw------- 1 satimis userA  7682361856 Jan  2 20:30 win76403.ova
....
...

```

Performed following tests;


Test-1
======
login userA

Import Appliance "fedora1700.ova"```

-rw------- 1 satimis userA  2105741312 Jan  1 13:25 fedora1700.ova

```

Failed```

Failed to import appliance /data/OVA/fedora1700.ova.

Could not open OVA file '/data/OVA/fedora1700.ova' (VERR_ACCESS_DENIED).

Result Code: VBOX_E_FILE_ERROR (0x80BB0004)
Component: Appliance
Interface: IAppliance {3059cf9e-25c7-4f0b-9fa5-3c42e441670b}

```


Test-2
======

login satimis (adminstrator)

Import Appliance "essex1.ova"
```

-rw------- 1 satimis userA  2452633600 Jan  1 12:59 essex1.ova
```

Import Appliance without problem but couldn't start the VM on converting the network

Warning:```

Failed to open a session for the virtual machine essex1.

Nonexistent host networking interface, name 'vboxnet0' (VERR_INTERNAL_ERROR).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {db7ab4ca-2a3f-4183-9243-c1208da92392}

```

---

### Post by CharlesA on 2013-01-03
That would be why only your user has rw permissions.

Run this:

```
chmod -R 666 /data/OVA/
```

Use sudo if it gives you permission denied errors.

Then try importing again.

---

### Post by satimis on 2013-01-03
> **CharlesA said:**
> That would be why only your user has rw permissions.

Run this:

```
chmod -R 666 /data/OVA/
```

Use sudo if it gives you permission denied errors.

Then try importing again.

$ sudo chmod -R 666 /data/OVA/                               
[sudo] password for satimis: 
(no complaint)

I must run sudo otherwise it doesn't work.

But something strange happened.

$ ls -l /data/OVA/```

ls: cannot access /data/OVA/win76406.ova: Permission denied
ls: cannot access /data/OVA/deb60ser02a.ova: Permission denied
ls: cannot access /data/OVA/deb60ser01.ova: Permission denied
ls: cannot access /data/OVA/linuxmint13.ova: Permission denied
ls: cannot access /data/OVA/win76405.ova: Permission denied
ls: cannot access /data/OVA/fedora1700.ova: Permission denied
ls: cannot access /data/OVA/deb600dk00_1.ova: Permission denied
ls: cannot access /data/OVA/fedora1701.ova: Permission denied
ls: cannot access /data/OVA/MyDLP.ova: Permission denied
ls: cannot access /data/OVA/deb60ser04.ova: Permission denied
ls: cannot access /data/OVA/essex4.ova: Permission denied
ls: cannot access /data/OVA/win86400.ova: Permission denied
ls: cannot access /data/OVA/win76408.ova: Permission denied
ls: cannot access /data/OVA/sugarub910.ova: Permission denied
ls: cannot access /data/OVA/enlightmntdk_ub1204dk.ova: Permission denied
ls: cannot access /data/OVA/cloudera.ova: Permission denied
ls: cannot access /data/OVA/deb60ser02.ova: Permission denied
ls: cannot access /data/OVA/deb60ser03.ova: Permission denied
ls: cannot access /data/OVA/essex2.ova: Permission denied
ls: cannot access /data/OVA/ws20086405.ova: Permission denied
ls: cannot access /data/OVA/win76403.ova: Permission denied
ls: cannot access /data/OVA/deb600dk01.ova: Permission denied
ls: cannot access /data/OVA/deb600dk02.ova: Permission denied
ls: cannot access /data/OVA/win76405a.ova: Permission denied
ls: cannot access /data/OVA/essex3.ova: Permission denied
ls: cannot access /data/OVA/deb60ser02b.ova: Permission denied
ls: cannot access /data/OVA/deb60ser05.ova: Permission denied
ls: cannot access /data/OVA/stackops01.ova: Permission denied
ls: cannot access /data/OVA/win76400.ova: Permission denied
ls: cannot access /data/OVA/win73204.ova: Permission denied
ls: cannot access /data/OVA/sugarub910cn.ova: Permission denied
ls: cannot access /data/OVA/deb60ser00.ova: Permission denied
ls: cannot access /data/OVA/essex1.ova: Permission denied
ls: cannot access /data/OVA/win73203.ova: Permission denied
ls: cannot access /data/OVA/deb600dk00.ova: Permission denied
ls: cannot access /data/OVA/ws20086402.ova: Permission denied
ls: cannot access /data/OVA/cloudoncd.ova: Permission denied
total 0
-????????? ? ? ? ?            ? cloudera.ova
-????????? ? ? ? ?            ? cloudoncd.ova
-????????? ? ? ? ?            ? deb600dk00_1.ova
-????????? ? ? ? ?            ? deb600dk00.ova
-????????? ? ? ? ?            ? deb600dk01.ova
-????????? ? ? ? ?            ? deb600dk02.ova
-????????? ? ? ? ?            ? deb60ser00.ova
-????????? ? ? ? ?            ? deb60ser01.ova
-????????? ? ? ? ?            ? deb60ser02a.ova
-????????? ? ? ? ?            ? deb60ser02b.ova
-????????? ? ? ? ?            ? deb60ser02.ova
-????????? ? ? ? ?            ? deb60ser03.ova
-????????? ? ? ? ?            ? deb60ser04.ova
-????????? ? ? ? ?            ? deb60ser05.ova
-????????? ? ? ? ?            ? enlightmntdk_ub1204dk.ova
-????????? ? ? ? ?            ? essex1.ova
-????????? ? ? ? ?            ? essex2.ova
-????????? ? ? ? ?            ? essex3.ova
-????????? ? ? ? ?            ? essex4.ova
-????????? ? ? ? ?            ? fedora1700.ova

```


$ sudo ls -l /data/OVA/```

total 158665292
-rw-rw-rw- 1 satimis satimis  6453506560 Dec 27 16:22 cloudera.ova
-rw-rw-rw- 1 satimis satimis      736768 Dec 28 23:42 cloudoncd.ova
-rw-rw-rw- 1 satimis satimis  6901194240 Jan  1 12:37 deb600dk00_1.ova
-rw-rw-rw- 1 satimis satimis  6901194240 Dec 28 23:55 deb600dk00.ova
-rw-rw-rw- 1 satimis satimis  5569650688 Dec 29 00:13 deb600dk01.ova
-rw-rw-rw- 1 satimis satimis  6330367488 Jan  1 10:47 deb600dk02.ova
-rw-rw-rw- 1 satimis satimis   627798528 Jan  1 10:52 deb60ser00.ova
-rw-rw-rw- 1 satimis satimis   664978944 Jan  1 10:54 deb60ser01.ova
-rw-rw-rw- 1 satimis satimis   827026432 Jan  1 10:59 deb60ser02a.ova
-rw-rw-rw- 1 satimis satimis   869670912 Jan  1 11:02 deb60ser02b.ova
-rw-rw-rw- 1 satimis satimis   811467776 Jan  1 10:57 deb60ser02.ova
-rw-rw-rw- 1 satimis satimis   660776448 Jan  1 11:05 deb60ser03.ova
-rw-rw-rw- 1 satimis satimis   590995456 Jan  1 12:04 deb60ser04.ova
-rw-rw-rw- 1 satimis satimis   823435776 Jan  1 12:51 deb60ser05.ova
-rw-rw-rw- 1 satimis satimis  2226749440 Jan  1 12:48 enlightmntdk_ub1204dk.ova
-rw-rw-rw- 1 satimis userA  2452633600 Jan  1 12:59 essex1.ova
-rw-rw-rw- 1 satimis userA  2660953088 Jan  1 13:10 essex2.ova
-rw-rw-rw- 1 satimis userA   710354432 Jan  1 13:16 essex3.ova
-rw-rw-rw- 1 satimis userA   918861824 Jan  1 13:19 essex4.ova
-rw-rw-rw- 1 satimis userA  2105741312 Jan  1 13:25 fedora1700.ova
-rw-rw-rw- 1 satimis userA  3591307264 Jan  1 13:33 fedora1701.ova
-rw-rw-rw- 1 satimis userA  1751297024 Jan  1 13:43 linuxmint13.ova
-rw-rw-rw- 1 satimis userA  2598827520 Jan  1 13:50 MyDLP.ova
-rw-rw-rw- 1 satimis userA   849887232 Jan  1 13:53 stackops01.ova
-rw-rw-rw- 1 satimis userA  3709683200 Jan  1 22:35 sugarub910cn.ova
-rw-rw-rw- 1 satimis userA  2921337856 Jan  1 13:59 sugarub910.ova
-rw-rw-rw- 1 satimis userA  9267556864 Jan  2 22:16 win73203.ova
-rw-rw-rw- 1 satimis userA  4141147648 Jan  2 21:15 win73204.ova
-rw-rw-rw- 1 satimis userA  6849847296 Jan  2 20:56 win76400.ova
-rw-rw-rw- 1 satimis userA  7682361856 Jan  2 20:30 win76403.ova
-rw-rw-rw- 1 satimis userA 15108390912 Jan  2 18:47 win76405a.ova
-rw-rw-rw- 1 satimis userA 14303747072 Jan  2 19:26 win76405.ova
-rw-rw-rw- 1 satimis userA 10331489792 Jan  2 19:57 win76406.ova
-rw-rw-rw- 1 satimis satimis 15618504192 Jan  1 23:38 win76408.ova
-rw-rw-rw- 1 satimis satimis  4086231552 Jan  1 23:07 win86400.ova
-rw-rw-rw- 1 satimis userA  5036638208 Jan  2 18:13 

```


I couldn't import VM anymore neither as satimis(administrator) NOR as userA

satimis

---

### Post by CharlesA on 2013-01-03
Forgot the execute bit.

```
sudo chmod -R 775 /data/OVA/
```

---

### Post by satimis on 2013-01-03
> **CharlesA said:**
> Forgot the execute bit.

```
sudo chmod -R 775 /data/OVA/
```

Hi,

Your advice works.  satimis(administrator) and users can import VMs after login their accounts.  Thanks

But there are 2 problems popup;

1)
After login their own accounts users can import any VM.

2)
Administrator can't view all VMs, running on the PC, on his account unless login users' account.

How to setup:-
1)
User can't import VM or even unable to visit /data folder/directory.  Only administrator can import the VMs on user's account allowing user running the VMs.  Users are only allowed running the VMs on their own accounts

2)
Administrator can view all imported VMs running on the PC

TIA

Regards
satimis

---

### Post by CharlesA on 2013-01-03
Not possible with Virtualbox because it doesn't support fine grained permissions and each user only has access to their VMs.

---

### Post by satimis on 2013-01-04
> **CharlesA said:**
> Not possible with Virtualbox because it doesn't support fine grained permissions and each user only has access to their VMs.

Advice noted.

I'm considering allowing the users working on remote desktop.  The VMs are running on the host PC but the users is only allowed to access the VMs remotely, i.e. starting the desktop of VM on their local PCs.  Users are NOT allowed to use the host PC,  Would it be a solution?  Comment and suggestion would be appreciated.


I haven't run remote desktop for sometimes.  Just tested it with following steps;

(without freenx-server.  I did it quite often in the past)

Server Port: 3389
IP of VM: 192.168.0.247

On user's PC run;

$ ssh -X satimisd600dk00@192.168.0.247

satimisd600dk00@deb600dk00:~$ gnome-session

Remote desktop started but the background is still local desktop.

The top bar of the remote desktop is on the left top bar.  I can start its applications.  But I couldn't figure out how to display the complete remote desktop with background on the local screen.  IIRC I did it in the past.

Advice would be appreciated.  TIA

satimis

---

### Post by CharlesA on 2013-01-04
You could do that but it would be easier to just run NX on the VM and let them connect that way.

---

### Post by satimis on 2013-01-04
> **CharlesA said:**
> You could do that but it would be easier to just run NX on the VM and let them connect that way.
Whether following link;
Tutorial: Delivering Linux VMs via the NoMachine NX Protocol
[http://www.leostream.com/resources/Linux-LDAP-NX.php](http://www.leostream.com/resources/Linux-LDAP-NX.php)

is relevent to its setup?  Thanks

---

### Post by CharlesA on 2013-01-04
> **satimis said:**
> Whether following link;
Tutorial: Delivering Linux VMs via the NoMachine NX Protocol
[http://www.leostream.com/resources/Linux-LDAP-NX.php](http://www.leostream.com/resources/Linux-LDAP-NX.php)

is relevent to its setup?  Thanks
That only applies if you want to do single-signon. If each user has their own account on each VM, you don't need to worry about it.

---

### Post by satimis on 2013-01-04
> **CharlesA said:**
> That only applies if you want to do single-signon. If each user has their own account on each VM, you don't need to worry about it.
Noted.  Thanks

I'm not very clear whether just enable PAE/NX

On
Settings -> System -> Processor
Extended Features [v] Enable PAE/NX


Re:
Chapter 3. Configuring virtual machines
[http://www.virtualbox.org/manual/ch03.htm](http://www.virtualbox.org/manual/ch03.htm)

"Processor" tab```

In addition, the "Enable PAE/NX" setting determines whether the PAE and NX capabilities of the host CPU will be exposed to the virtual machine. PAE stands for "Physical Address Extension". Normally, if enabled and supported by the operating system, then even a 32-bit x86 CPU can access more than 4 GB of RAM. This is made possible by adding another 4 bits to memory addresses, so that with 36 bits, up to 64 GB can be addressed. Some operating systems (such as Ubuntu Server) require PAE support from the CPU and cannot be run in a virtual machine without it.

```

Do I need installing NX on the host and the remote machine as well?

Re:
Linux + GNU = Humans Enabled
How to install NX Free Edition on Ubuntu 12.04 Precise Pangolin
[http://www.humans-enabled.com/2012/04/how-to-install-freenx-server-on-ubuntu.html](http://www.humans-enabled.com/2012/04/how-to-install-freenx-server-on-ubuntu.html)

How to connect VM on remote PC via NX displaying its desktop locally?

Regards
satimis

---

### Post by CharlesA on 2013-01-04
You would need to install the server, node and client on the remote machine but only the client on whatever machine you want to connect from.

---

### Post by satimis on 2013-01-04
Hi,

Could you please explain in more detail.

> **CharlesA said:**
> You would need to install the server, node and client on the remote machine 

I got it, installing;
-server
-node
-client
on the remote machine, e.g userA's machine

> 
but only the client on whatever machine you want to connect from.
To install client, ONLY, on the VM (OR on the host) which I allow userA to connnect?

Pointer/link would be appreciated.  TIA

---

### Post by CharlesA on 2013-01-05
> **satimis said:**
> 
To install client, ONLY, on the VM (OR on the host) which I allow userA to connnect?

Pointer/link would be appreciated.  TIA

You'd need to only install the client on the host.. or whatever machine you will be using to connect to the VM.

---

### Post by satimis on 2013-01-05
> **CharlesA said:**
> You'd need to only install the client on the host.. or whatever machine you will be using to connect to the VM.
On userA's PC I installed Freenx following the steps on;
How to install FreeNX on Ubuntu 12.04 Precise Pangolin
[http://www.humans-enabled.com/2012/05/how-to-install-freenx-on-ubuntu-1204.html](http://www.humans-enabled.com/2012/05/how-to-install-freenx-on-ubuntu-1204.html)

Installation went through w/o difficulty.

Evoke QtNX
Username - Is it the username of userA's PC or the username of the VM alloted to userA?
Configure.. -> QtNX Settings
Session Name - What shall I enter here?
Hostname - Is it the hostname of userA's PC or the hostname of the VM alloted to userA

On the host of VirtualBox PC
Whether install QtNX only?

I have following querry:-
Whether userA access the host first and from there start the VM allotted via VirtualBox Manager?  If YES then userA can also view other VMs

Regards
satimis

---

### Post by CharlesA on 2013-01-05
I don't use that version of FreeNX, so I don't really know what you need to install, but it looks like qtNX is only installed on the machine you want to access the VM from, not the host.

Leave the host alone and let the user access the VMs directly.

---

### Post by satimis on 2013-01-06
> **CharlesA said:**
> I don't use that version of FreeNX, ........
Are you running following version;

NOMACHINE
[http://www.nomachine.com/index.php](http://www.nomachine.com/index.php)

But it is NOT free to use

satimis

---

### Post by CharlesA on 2013-01-06
> **satimis said:**
> Are you running following version;

NOMACHINE
[http://www.nomachine.com/index.php](http://www.nomachine.com/index.php)

But it is NOT free to use

satimis

They have two versions.

> NX Free Edition

A complete solution for remote access to your Linux or Solaris workstation. It allows 2 users to connect at the same time no matter what their location is, and share the desktop. NX Free Edition is incredibly easy to install and run, leverages the competence and quality of the company that makes NX and, most importantly, is free forever.

Unless you are doing this on an enterprise level and have more than two users connecting to the same machine at the same time, you can use this.

---

### Post by puebloan on 2013-01-07
Hmmm. I think by far the easiest way to do this is to export your vm's on your old box to a .ova file. Then copy to your new box and import. Directories and configurations are rebuilt.

Go to Youtube. They have some great videos.

---

### Post by satimis on 2013-01-07
> **puebloan said:**
> Hmmm. I think by far the easiest way to do this is to export your vm's on your old box to a .ova file. Then copy to your new box and import. Directories and configurations are rebuilt.

Go to Youtube. They have some great videos.
Hi,

That is what I'm doing.  Export all VMs on the old HD to the new HD on /data/VOA.  Then import them to VirtualBox.  Everythings are done automatically.

Thank.

satimis

---

### Post by satimis on 2013-01-07
> **CharlesA said:**
> They have two versions.



Unless you are doing this on an enterprise level and have more than two users connecting to the same machine at the same time, you can use this.
Thanks

I think the easiest way for remote-access, displaying remote desktop locally is running "Remmina Remote Desktop Client".  I'm now testing it.  It seems not stable on this PC.  Sometime it works and another occasion fails.  May-be I have installed too many versions of remote-desktop packages.  I'm now trying removing them.  In the worst sitution if failure I'll reinstall Ubuntu 12.04 desktop.  This PC is for testing not for production.

---


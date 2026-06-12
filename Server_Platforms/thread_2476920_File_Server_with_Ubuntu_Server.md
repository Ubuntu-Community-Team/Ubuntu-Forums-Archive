---
title: "File Server with Ubuntu Server"
date: 2022-07-12
forum: Server Platforms
---

### Post by carnagelan on 2022-07-12
Hi All,
It is the first time i am using Ubuntu Server.
Which is the most stable version?
I would like to install terminal based only with out the gui. Is there a web based software i can use to monitor the server as well as add users to samba

Thank you

---

### Post by guiverc on 2022-07-12
All released products of Ubuntu are *stable*.

Ubuntu *kinetic* is the current development release, it'll change name when it's RC (*Released Candidate*) and be released as Ubuntu 22.10 when it's deemed *stable*.

- Ubuntu 18.04 LTS is the 2018-April release of Ubuntu.
- Ubuntu 20.04 LTS is the 2020-April release of Ubuntu.
- Ubuntu 21.10 is the 2021-October release of Ubuntu.
- Ubuntu 22.04 LTS is the 2022-April release of Ubuntu.

All are *stable*, but some hardware may perform better with some kernel stacks when compared to others, but we have no clues as to your hardware.  Ubuntu LTS releases have two kernel stacks to choose from (GA & HWE) plus some hardware also has OEM options.

FYI:  The LTS are *long-term-support* releases; and I'd not install[ Ubuntu 21.10 as it reaches it's EOL (*end of life*) thus thursday]("https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/"). You generally want the newest version available, as for example 18.04 being released in 2018-April with 5 years of *standard* supported life, reaches it's EOL in 2023-April, where if you install 22.04 LTS you have most of the 5 years of *standard *supported life still in front of you.  ie. the version number relates to date of release.

Ubuntu Server does **not** have a GUI, if you add a GUI you convert the system to a desktop system.

PS:  *If you want more details on kernel stacks; the following maybe helpful - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack ]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). I won't provide details on browser based management products, as I've not found any I'm happy with, the costs all exceeding any benefits in my opinion.*

---

### Post by carnagelan on 2022-07-12
Thank you,
This is only going to be a file server. I am changing from windows to Ubuntu.
there is a 1tb hard drive(secondary) with all the shared folders on. 
Will it be better to backup and format in EXT4 or will the NTFS be ok. 
The main hard drive is going to be ext4

---

### Post by ajgreeny on 2022-07-12
Use NTFS only if you need to share those files with a Windows system as many problems with the NTFS filesystem can not be repaired using Linux.

For a Linux server I believe ext4 would be the better choice anyway.

---

### Post by carnagelan on 2022-07-12
OK Thank you. All these folders are going to be shared with about 30 windows laptops. 
So it will be better then if i format it in a linux file system. 
Thanks for the info

---

### Post by ajgreeny on 2022-07-12
If the files are to be shared directly with Windows, ie, the disk will be connected to a Windows machine it will have to be NTFS or some other Windows file system as the Linux filesystems are not usable in Windows machines.

---

### Post by carnagelan on 2022-07-12
Thjis files are to be shared with a windows network but the shared hard drive will be in a linux server

---

### Post by SeijiSensei on 2022-07-12
It's perfectly fine to use ext4 to create the filesystem that will be exported. Samba will automatically make the filesystem compatible for remote Windows clients. You do not need to use NTFS on a Linux box running Samba. I have had Samba shares running on my Linux server with ext4 filesystems for years. 

If all you want to do is set up exported shares for Windows users, you don't need a GUI on the server. There is plenty of Samba documentation that explains how to do this from a terminal. You only need to install the software then edit one file, smb.conf, using the "nano" editor as described here: [https://ubuntu.com/tutorials/install-and-configure-samba#1-overview](https://ubuntu.com/tutorials/install-and-configure-samba#1-overview)

---

### Post by mIk3_08 on 2022-07-13
> **carnagelan said:**
> Hi All,
It is the first time i am using Ubuntu Server.
Which is the most stable version?
I would like to install terminal based only with out the gui. Is there a web based software i can use to monitor the server as well as add users to samba

Thank you
I don't know if this is what you mean. here's the link. [Click here]("https://help.ubuntu.com/community/Servers#Monitoring"). Hope it helps. Regards and cheers.

---

### Post by TheFu on 2022-07-13
There are a number of webguis for managing servers.  When I was new to Linux, I searched and searched, but found them all to be worse than the problem they were trying to solve.  Best to just learn to use ssh and the CLI to manage the system.

Only use NTFS as a file system on storage which will be physically connected to a Windows computer. Otherwise, use a native Linux file system, like ext4.  It will make life easier.

Switching from Windows to Linux without a GUI has a very, very, steep learning curve, beyond what most people are prepared to handle. There will be lots of frustration, because Unix/Linux is NOT Windows.  Being a Windows guru doesn't help much with Linux knowledge. In many ways, it is detrimental, since many assumptions learned over years just aren't true.  If you are new to Linux, you should understand that there isn't any artificial limitation in Linux between the server programs and the desktop programs.  A Linux desktop can install any server program and perform as the server does with relatively little concern.  If you don't have at least 6 months of **daily** Linux use, install a desktop distro.  Please.

Of course, if you WANT to force yourself to learn Ubuntu server management, then install the server and perform all management over ssh without any GUI or webGUI.  That's how we pros do it.

I doubt you'll listen to me.  You'll probably try cockpit and webmin as gui management.  Hopefully, the resulting system won't be cracked when those tools are added.  A webgui that can be reached by bad people just makes for multiple added attack vectors.  Admins should be reducing attack vectors on all their systems.

If you are going to use Samba (and you probably should for multiple Windows systems to have network file access), remember that there are 2 users - 
1) Unix username
2) Samba username
Both are mandatory for samba to work.  There is a separate samba password too, which must be set.  I've never understood why the samba team doesn't use the Unix password, but they don't.

These days, rather than using samba for file storage, it might make more sense to use a private cloud, like Nextcloud so that some files can be shared/synchronized by users across multiple devices.  Just a thought. Ponder.  The downside is that desktop integration for Nextcloud is either through webdav or a bloated client, each have huge problems (security and performance), but on phones and tablets, Nextcloud integration is actually pretty good.

---

### Post by kevdog on 2022-07-13
I'd only like to chime in here with just some other considerations about your file server -- If the server is serving 30 computers I'm guessing the files are likely pretty important so don't neglect exploring how you are going to back these up.  Anticipate how large of storage space you'll need.  How big are the files likely to be?  I'd also consider using a file systems OS, specifically like TrueNAS scale or core if really wanting your system to act solely as a NAS.  A lot of the hard work has been setup with these systems.

---

### Post by carnagelan on 2022-07-15
Thanks  for all the replies.

Originally it is a basic windows 10 pc(specs are an i3, 6th gen, 4gb ram) 30 pcs wont be connected at the same time. Mostly its about 4 pcs that backup to the server. The rest dont really do that.  I am doing this change over tomorrow and this is my plan. Please let me know if i am correct here. I have used linux before so i know the basic of the terminal.

[B]Before change over.
[/B]Backup the 2tb hdd.
install Ubuntu on the 500gb hdd
Put the original 2tb hard drive in the ubuntu server and format as ext4
put the backup drive(ntfs) in the server and copy all the files to the newly format drive(ext4).
take backup drive out
setup samba

Ubuntu auto mounts sata drives? Am i correct?

---

### Post by carnagelan on 2022-07-15
Thanks  for all the replies.

Originally it is a basic windows 10 pc(specs are an i3, 6th gen, 4gb ram) 30 pcs wont be connected at the same time. Mostly its about 4 pcs that backup to the server. The rest dont really do that.  I am doing this change over tomorrow and this is my plan. Please let me know if i am correct here. I have used linux before so i know the basic of the terminal.
1. Backup the 2tb hdd.
2. install Ubuntu on the 500gb hdd
3. Put the original 2tb hard drive in the ubuntu server and format as ext4
4 put the backup drive(ntfs) in the server and copy all the files to the newly format drive(ext4).
5. take backup drive out
6. setup samba

Ubuntu auto mounts sata drives? Am i correct?

---

### Post by TheFu on 2022-07-15
> **carnagelan said:**
> T
Ubuntu auto mounts sata drives? Am i correct?

God, I hope not!   The power to mount is the power to destroy.  It is not automatic and shouldn't be.

If you are setting up backups, don't use NTFS.  That will lose 50% of the metadata required for a restore. Use a native Linux file system, like ext4. There are other choices.
Backups should be "pulled", not "pushed".  The Linux system should use a client-server architecture, not a network storage architecture, to connect to each client machine an "pull" the data to be backed up. This means that windows malware doesn't have a chance to corrupt the backup server and destroy all the backup data.  That is broken if we use any network storage methods. These days, our backups need to handle crypto-ware and other malware too.

Don't use CIFS, Samba, NFS, or any network storage protocol for backup purposes. Please.

---


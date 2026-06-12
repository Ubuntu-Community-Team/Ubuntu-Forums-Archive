---
title: "[SOLVED] Virtualbox: Problems setting up a shared folder"
date: 2008-12-09
forum: Virtualisation
---

### Post by MaindotC on 2008-12-09
The VirtualBox documentation is rather confusing regarding this issue.  It would really help if they would accompany an exact example.  This is from page 62 of the user manual regarding shared folders:
```

The command is as follows:
[i]VBoxManage sharedfolder add "VM name" -name "sharename"
                   -hostpath "C:\test"[/i]

```

Here's what I did.  First, instead of following the directions for the command prompt, I opened VirtalBox, clicked on a Fedora 9 VM, clicked "Shared Folders", clicked "Add a new shared folder", entered the path on my host OS of the shared folder I created, and clicked "Ok".  My shared folder is located at /home/a34lkj2348dsf311/Desktop/shared_folder.  Now I have to tell the VM where the shared folder is and where to mount it.  So, page 62 continues:
```

In a Linux guest, use the following command:
*mount -t vboxsf [-o OPTIONS] sharename mountpoint*

```
So I created a directory in my Fedora VM.  It's in /root/Desktop/fedora_share.  Here's what I entered and the associative output:
```

[i][root@localhost Desktop]# mount -t vboxsf /home/a34lkj2348dsf311/Desktop/shared_folder fedora_share/
/sbin/mount.vboxsf: mounting failed with the error: Protocol error
[root@localhost Desktop]#[/i]

```

It's difficult for me to pinpoint the problem because if I want to do it via the command line on the host o/s I get the following output:
```

a34lkj2348dsf311@a34lkj2348dsf311-desktop:~$ sudo VBoxManage sharedfolder remove Fedora -name ~/Desktop/shared_folder/
[sudo] password for a34lkj2348dsf311: 
VirtualBox Command Line Management Interface Version 2.0.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 7455!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Could not find a registered machine named 'Fedora'
[!] Component   = VirtualBox, Interface: IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
[!] Callee      = IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
a34lkj2348dsf311@a34lkj2348dsf311-desktop:~$

```

I tried it as the regular user and I also tried it as sudo.  I tried changing the path of shared_folder in the Fedora VM just to see if it would return a different error, but got the same thing.  So now, I don't even know if the VM is reading the path properly, much less this protocol error.

What am I doing wrong?

---

### Post by Dedoimedo on 2008-12-10
Hello,

1. Make sure you have guest addons installed.

2. On host, select the share you want to share and remember what it's called. Its real path does not matter! So let's say your share is called Dedoimedo.

3. Launch virtual machine guest. In terminal, type:

```

cd /mnt
sudo mkdir shares
sudo mount -t vboxsf Dedoimedo shares

```

And that's it. Don't worry about the absolute paths. You don't need them. For all practical purposes, VB will take care of the real path behind the share name, in this case Dedoimedo.

See if this works out for you.

Dedoimedo

---

### Post by MaindotC on 2008-12-10
Thanks for your help, but I'll still getting protocol error.  I'm going to reinstall and start clean.  I'll let you know how it goes.

---

### Post by bodhi.zazen on 2008-12-10
That is not how you mount a share in the guest.

First, on the host, you need to use the name of the guest. You are getting an error message : "Could not find a registered machine named 'Fedora'". Is the guest named "Fedora VM" ?

Second, you use the full path on the HOST when you make a share available, but when you do so you give the share a name, let us say "foo".

On the guest the commands are then

mount [share_name] [mount_point]

You do NOT use the path for the share name , so

```
sudo mkdir /media/foo
sudo mount -t vboxsf foo /media/foo
```

Last, you may need to make the share available Before you boot the guest.

---

### Post by Fatsobob on 2008-12-11
I had a similar problem occur for me though I was on a Windows XP host and an Ubuntu Guest. The following worked for me.

Instead of manually using "mount -t" try using the "mount.vboxsf" command as root that is installed with the guest additions.
```

mount.vboxsf <Share Name> <Mount Location>

```

If that works, you should also add an entry to your /etc/fstab file so it will automount and you can write to it without sudo.


```
sudo nano /etc/fstab
```

Add the following entry and replace where applicable
```

<Share Name>	<Mount Location> vboxsf rw,uid=1000,gid=1000 0 0

```
Example: Share name "Shared" and mount point "/home/fatsobob/Shared_Folder"
```

Shared		/home/fatsobob/Shared_Folder vboxsf rw,uid=1000,gid=1000 0 0

```

---

### Post by Fatsobob on 2008-12-11
Accidental double post, delete me

---

### Post by MaindotC on 2008-12-11
> **bodhi.zazen said:**
> 
First, on the host, you need to use the name of the guest. You are getting an error message : "Could not find a registered machine named 'Fedora'". Is the guest named "Fedora VM" ?


It turns out you need to put the name of the vm in quotes and the hostpath has to be absolute as you suggested Bodhi:
```

a34lkj2348dsf311@a34lkj2348dsf311-desktop:~/.VirtualBox$ VBoxManage sharedfolder add "Fedora" -name fedora_share -hostpath ../Desktop/shared_folder
VirtualBox Command Line Management Interface Version 2.0.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath), fWritable) at line 7534!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Shared folder path '../Desktop/shared_folder' is not absolute
[!] Component   = SharedFolder, Interface: ISharedFolder, {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
[!] Callee      = IMachine, {1e509de4-d96c-4f44-8b94-860194f710ac}
a34lkj2348dsf311@a34lkj2348dsf311-desktop:~/.VirtualBox$ VBoxManage sharedfolder add "Fedora" -name fedora_share -hostpath ~/Desktop/shared_folder
VirtualBox Command Line Management Interface Version 2.0.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

a34lkj2348dsf311@a34lkj2348dsf311-desktop:~/.VirtualBox$

```
Second, you use the full path on the HOST when you make a share available, but when you do so you give the share a name, let us say "foo".

On the guest the commands are then

mount [share_name] [mount_point]

You do NOT use the path for the share name , so

```
sudo mkdir /media/foo
sudo mount -t vboxsf foo /media/foo
```

Last, you may need to make the share available Before you boot the guest.[/QUOTE]

THE ABOVE PART WAS VERY IMPORTANT IN UNDERSTANDING THIS SHARED FOLDER BUSINESS!!!!!  The following is on the fedora guest:
```

[root@localhost ~]# mount -t vboxsf fedora_share Desktop/fed_share/
[root@localhost ~]# cd Desktop/fed_share/
[root@localhost fed_share]#

```

As you can see, the host folder name is ~/Desktop/shared_folder, in the VBoxManage command I named it "fedora_share" which I'm assuming is how VBoxManage and the guest refers to the folder instead of its actual host name.  I then called the folder from within the guest referring to it as "fedora_share" and mounting it on the guest in /root/Desktop/fed_share.

Thank you very much for your help.  My mystery is solved.  Maybe it's just me but I think the directions in the manual are very unclear.  Thank you again for all your help.

---

### Post by scalyanteater on 2010-09-22
> **strAlan said:**
> It turns out you need to put the name of the vm in quotes and the hostpath has to be absoluteI am able to get it to work without the quotes. But what made the difference for me was not using "defaults" in the options column in /etc/fstab ; I used explicit permissions, instead:
```
sharename    mountpoint vboxsf  rw,uid=1000,gid=1000    0       0
```Ubuntu 9.10 guest on VB 3.2.8, on OS 10.5.8.

---

### Post by whitebloodcell on 2012-06-25
> **Fatsobob said:**
> I had a similar problem occur for me though I was on a Windows XP host and an Ubuntu Guest. The following worked for me.

Instead of manually using "mount -t" try using the "mount.vboxsf" command as root that is installed with the guest additions.
```

mount.vboxsf <Share Name> <Mount Location>

```

If that works, you should also add an entry to your /etc/fstab file so it will automount and you can write to it without sudo.


```
sudo nano /etc/fstab
```

On a Windows 7 host the above worked for me, up until the instructios to automount on reboot, the folder is still there, but is no longer a shared folder it would seem. I realise this is an old thread, but any ideas?

Add the following entry and replace where applicable
```

<Share Name>	<Mount Location> vboxsf rw,uid=1000,gid=1000 0 0

```
Example: Share name "Shared" and mount point "/home/fatsobob/Shared_Folder"
```

Shared		/home/fatsobob/Shared_Folder vboxsf rw,uid=1000,gid=1000 0 0

```

The above worked for me, up until the automount instructions anyway. This is an old thread I know but, any ideas on how to get it to automount?

---


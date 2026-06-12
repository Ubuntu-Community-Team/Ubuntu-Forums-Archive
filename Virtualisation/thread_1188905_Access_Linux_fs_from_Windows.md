---
title: "Access Linux fs from Windows"
date: 2009-06-16
forum: Virtualisation
---

### Post by WitchCraft on 2009-06-16
Hi, question:

How can I access a directory of the Ubuntu Linux guest running in a VirtualBox on Windows FROM Windows?

(Without samba shares, please!)

---

### Post by mhgsys on 2009-06-16
I don't know how  it works for a VirtualBox, 
But you can use putty in windows to start a ssh connection to any linux machine on the network.

---

### Post by WitchCraft on 2009-06-16
> **mhgsys said:**
> I don't know how  it works for a VirtualBox, 
But you can use putty in windows to start a ssh connection to any linux machine on the network.

Going over the network is just what I try to avoid for performance reasons - hence the NO SAMBA PLEASE...

Maybe I should add: and no NFS & ssh, too.

Accessing an EXT2/3 partition from Windows is not a problem, but I don't know how to access the Vbox fs...

---

### Post by mhgsys on 2009-06-16
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

EDIT: never mind, since accessing an ext2/3 partition is not a problem.

---

### Post by Clorow on 2009-06-17
Shut down your virtual Windows. Go to the settings of your virtual Windows and Make a shared folder. Sorry, I think this does use Samba, but it does not actually use a network.

Once you've got that configured, run your virtual Windows. Once it's up and running, open a command prompt in Windows and type in:
```
net use x: \\vboxsvr\shared_folder
```
and replace shared_folder with what you named your shared folder.

---

### Post by fdbk on 2009-06-18
Is ubuntu the host or the guest? 

> **WitchCraft said:**
> Hi, question:

How can I access a directory of the **Ubuntu Linux host running in a VirtualBox on Windows** FROM Windows?

(Without samba shares, please!)

---

### Post by niteshifter on 2009-06-19
> **Clorow said:**
>  ... Sorry, I think this does use Samba, but it does not actually use a network. ... 

No. Not Samba. From the VirtualBox User Manual, section 4.6:
> Shared folders allow you to access files of your host system from within the guest
system, much like ordinary shares on Windows networks would – except that shared
folders do not need a networking setup. Shared folders must physically reside on
the host and are then shared with the guest; sharing is accomplished using a special
service on the host and a file system driver for the guest, both of which are provided
by VirtualBox.


---

### Post by WitchCraft on 2009-06-19
> **fdbk said:**
> Is ubuntu the host or the guest?

That's the correct question. Ubuntu is the guest (Sorry, I mixed it up, corrected it now in the previous post.)!

Windows is the host: VirtualBox runs on Windows
Ubuntu is the guest: Ubuntu runs **in** VirtualBox

Required task: I want to access a folder of the Ubuntu filesystem from Windows.
Vice-versa is already achieved via a Vbox share, so I can access windows from Ubuntu, but I currently can't access Ubuntu from Windows (except if I make network shares).

---

### Post by HermanAB on 2009-06-19
Samba, NFS, FTP, Filezilla, Xming + PuTTY...

---

### Post by fdbk on 2009-06-19
[SIZE=3]> **WitchCraft said:**
> That's the correct question. Ubuntu is the guest (Sorry, I mixed it up, corrected it now in the previous post.)!

Windows is the host: VirtualBox runs on Windows
Ubuntu is the guest: Ubuntu runs **in** VirtualBox

Required task: I want to access a folder of the Ubuntu filesystem from Windows.
Vice-versa is already achieved via a Vbox share, so I can access windows from Ubuntu, but I currently can't access Ubuntu from Windows (except if I make network shares).

So you asked the same question I am asking. :-)  

According to the virtualbox manual, I used 

sudo mount -t vboxfs [-o OPTIONS] sharename mountpoint

But got the following error:

unknown filesystem type 'vboxfs'

Can't find vboxfs definition anywhere, including /etc/fstab, /etc/mtab and /proc/mounts.  vboxfs is not naturally supported by ubuntu, so I thought the virtualbox guest additions defined it.  Apparently not.[/SIZE]       :-(

---

### Post by niteshifter on 2009-06-19
Hi,

> **WitchCraft said:**
> That's the correct question. Ubuntu is the guest (Sorry, I mixed it up, corrected it now in the previous post.)!

Windows is the host: VirtualBox runs on Windows
Ubuntu is the guest: Ubuntu runs **in** VirtualBox

Required task: I want to access a folder of the Ubuntu filesystem from Windows.
Vice-versa is already achieved via a Vbox share, so I can access windows from Ubuntu, but I currently can't access Ubuntu from Windows (except if I make network shares).

Sharing - as done by VirtualBox - is host-centric, it can share a host folder with the guest. Which you have working.

For the other way around - sharing a guest folder with the host - requires that the guest run the sharing mechanism. Which means some form of network sharing: Samba / NFS or the like.

---

### Post by WitchCraft on 2009-06-22
> **fdbk said:**
> 
 
[SIZE=2]But got the following error:[/SIZE]
[SIZE=2][COLOR=red]unknown filesystem type 'vboxfs'[/COLOR][/SIZE]
 
[SIZE=2]Can't find vboxfs definition anywhere, including /etc/fstab, /etc/mtab and /proc/mounts. vboxfs is not naturally supported by ubuntu, so I thought the virtualbox guest additions defined it. Apparently not. :-([/SIZE]
 
No, Ubuntu supports it perfectly. But you probably have to install Vbox Additions, as you did.
But I know what your problem is:
 
I for example shared folder c: from windows as cadmin to linux
 
Then I wanted to mount it in /mnt/cadmin in Linux
So I went to /mnt/ 
created the cadmin directory (mkdir cadmin)
and typed: mount -t vboxfs cadmin /mnt/cadmin
 
and i got 
[SIZE=2][COLOR=#ff0000]unknown filesystem type 'vboxfs'[/COLOR][/SIZE]
which is because you're in a root node of your share mount folder.
It's a Vbox bug, just go to ~ (home)
and type:
mount -t vboxfs cadmin /mnt/cadmin
 
and it mounts it without error ;-)

---

### Post by fdbk on 2009-06-22
yes! works now.  

```
/etc/init.d/vboxadd start
sudo mount -t vboxsf shared /mnt
```

---

### Post by WitchCraft on 2009-06-24
> **niteshifter said:**
> 
For the other way around - sharing a guest folder with the host - requires that the guest run the sharing mechanism. Which means some form of network sharing: Samba / NFS or the like.
 
So in other words, there is no other way besides Samba/NFS/SSHFS...

---


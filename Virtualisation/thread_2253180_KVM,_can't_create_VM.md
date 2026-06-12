---
title: "KVM, can't create VM"
date: 2014-11-17
forum: Virtualisation
---

### Post by mbuell on 2014-11-17
I've been trying to create a VM. ANY VM. But 1st case is WinXP. 

Virt-manager doesn't like the space I give it - and won't create a vm. 

Back story. I read some before getting into this. Ppl say a 2nd hdd gives better performance. Ok - no prob. I install a 2nd hdd. Try to give the raw hdd space to the VM - it doesn't like it. Doesn't even see it. Ok - I partition the drive, 3 partitions, all ext4. But not mounted. Virt mgr can't see it. I mount a partition - and make sure it is in my group, my user name, permissions 770. Almost wide open. 

Virt mgr still doesn't like it. 

I get to step 4 out of 5 in virt mgr - and it is confusing as hell. I've been standing on my head whilst drinking water to make this happen - and it still can't write to the directory. 

I know I've probably missed some minor, but obviously essential, point - something easily remedied if I only had some idea of what it was. I'm thinking I've given permission to the whole world to work in the directory - and virt-mgr doesn't like it. 

The online how-to's I find say this should be easy. Nobody mentions permissions on the hdd. I'll bitch about virt-mgr - the dialogue for assigning hdd real estate is highly confusing. 

Suggestions are now being welcomed. Any thoughts about what I'm doing wrong?

---

### Post by Tadaen_Sylvermane on 2014-11-17
> [COLOR=#000000] I read some before getting into this. Ppl say a 2nd hdd gives better performance. [/COLOR]

Makes minimal difference if it's even measureable. Even less on an SSD

KVM by default stores the vms in /var/lib/libvirt/images. If your /var isn't big enough then nothing you do will change, no matter how many hard drives you install unless you put /var in a big enough space.

> [COLOR=#000000] the dialogue for assigning hdd real estate is highly confusing. [/COLOR]

What version are you using because on my Arch install right now virt-manager is nearly foolproof. Theres only 1 way to go.

> [COLOR=#000000]Any thoughts about what I'm doing wrong?[/COLOR]

Did you add your user to the libvirtd group on the server or host?

---

### Post by TheFu on 2014-11-18
libvirt (the backend for virt-manager) uses "storage pools." These are added at the VM server and are not in-your-face (i.e. storage management is found only when specifically searching for it) - connect to the server, right click on it (not any VM name under it), **Details** - there is a multi-tabbed interface.  
* Overview
* Virtial Networks
* **Storage**
* Network Interfaces

You want **Storage**.  The default storage pool is under /var - I never use that ... except on 100% pure VM servers.  Even then, I usually create a symlink from /var/lib/libvirt/images to some other storage/directory on a different file system mounted to the host.  I think it is common to have different pools for pre-built VMs, ISOs, and others for read-write VMs.  Whatever the storage is, root much have full control over it - that means NFS storage needs to be exported in the way that allows remote root control (security issue).  You can add different sorts of storage pools to the VM host - there are 8 different types - iSCSI, NFS, directory, block devices, LVM partitions, etc...

Most of the storage options are server stuff - not desktop.

If a storage pool list of files changes, either the libvirt backend needs to be reloaded or this interface must be used to force a refresh. You'll see it when moving a new ISO into a storage pool, but it doesn't show up as available to when modifying VM storage.

virt-manager can be used over the network to manage libvirt VM servers over an ssh tunnel. In that case, the storage is on the remove VM server, not the local client.  virt-manager honors ssh keys, ~/.ssh/config settings and behaves like it should in relation to ssh use.  The main thing to remember is NEVER run virt-manager as root and never connect to a remote VM server using root.  

Hope this is clear. If not, ask.

---

### Post by mbuell on 2014-11-18
> **Tadaen_Sylvermane said:**
> Makes minimal difference if it's even measureable. Even less on an SSD . . .
TY.

> **Tadaen_Sylvermane said:**
> 
KVM by default stores the vms in /var/lib/libvirt/images. If your /var isn't big enough then nothing you do will change, no matter how many hard drives you install unless you put /var in a big enough space.


Excellent, excellent, excellent. Here we go - vital bit of information - default location. Knowing this the gui now makes sense - it was asking for an 8GB size, telling me only 1GB available - which is only true in like one place for me - /var. I limit /var to a single small partition to prevent a logged error from filling the hdd. So, I have to figure out how to change the default location. 

> **Tadaen_Sylvermane said:**
>  . . .What version are you using because on my Arch install right now virt-manager is nearly foolproof. Theres only 1 way to go.

Did you add your user to the libvirtd group on the server or host?

I did not check the libvirtd group members - will do that. Working this on xubuntu for ubuntu 14.04. I'd have to look the virt-mgr ver up. That computer is currently offline - I'll have to check later - but you've already given me a gold nugget to chase - so I'll get back to version number later!

:)

---

### Post by mbuell on 2014-11-18
@thefu: You've added info to sylvermane's answer - good info. TY. I may use the symlink technique - as the /var default location is likely one of the roadblocks for me. 

TY!

Will get back to thread later after I've worked thru this a little more.

---

### Post by Tadaen_Sylvermane on 2014-11-18
+1 @thefu as well. Simple ideas elude me completely, never even considered linking to another location.

---

### Post by KillerKelvUK on 2014-11-21
Another option is to pass an entire block device (your 2nd HDD) through to the guest for guest os storage.  Have a read of the linked solution, you'll need to amend the <source dev='/dev/your_2nd_HDD'/> line and possibly the <target dev='vdX'...reference.

[http://ronaldevers.nl/2012/10/14/adding-a-physical-disk-kvm-libvirt.html](http://ronaldevers.nl/2012/10/14/adding-a-physical-disk-kvm-libvirt.html)

---

### Post by mbuell on 2014-11-23
> **TheFu said:**
> libvirt (the backend for virt-manager) uses "storage pools." These are added at the VM server and are not in-your-face (i.e. storage management is found only when specifically searching for it) - connect to the server, right click on it (not any VM name under it), **Details** - there is a multi-tabbed interface.  
* Overview
* Virtial Networks
* **Storage**
* Network Interfaces

You want **Storage**.  The default storage pool is under /var - . . ..

Ok! That works. Instead of creating a symlink, I used the VM interface as you suggested, and created a new storage space. It appears to me that I COULD have used the raw disk by letting Virt Manager format a block. But that seemed to be more steps, since I already had an fs in place. Once the space was created in the VM server (localhost in Virt Manager), it came up as available when creating the VM. 

Now I'm down to other niggling problems - like sound and vid card assignment!  Different topics tho!

Thanks for all the help!

---

### Post by TheFu on 2014-11-23
Glad it helped.  Sometimes I miss the "clarity mark."
Please mark thread as SOLVED.

GPU passthru, if that is what you mean is something very few people use - there is a thread here specifically for it.  I never tried, find xg20 excellent for "productivity apps", if ssh isn't enough.  x2go handles the remote audio better than anything else I've tried. Nothing special needed - at least I've never needed to setup anything special.  Of course, I don't ever sit behind the same PC where the VMs are running.  Right now, the desktop I'm using is ... 4200 mi away from me.

---


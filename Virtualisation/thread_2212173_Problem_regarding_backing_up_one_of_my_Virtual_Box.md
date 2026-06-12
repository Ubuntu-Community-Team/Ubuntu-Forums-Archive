---
title: "Problem regarding backing up one of my Virtual Box vdi files."
date: 2014-03-19
forum: Virtualisation
---

### Post by InfiniteDK on 2014-03-19
Dear All,

I have a serious problem regarding backing up one of my Virtual Box vdi files.
Im using Ubuntu 10.10 - Maverick Meerkat - released oktober 2010 og supported until april 2012.
Unfortunately, something went wrong during update and I'm not able to update Ubuntu.
Anyway the system runs fine.v
I'd like to upgrade to a new Ubuntu version, and therefore I want to backup my Virtual Box vdi files.
When I try to I get this error message- See attachement: 
0%...10%...20%...30%...
Progress state: NS_ERROR_FAILURE
Error: failed to clone hard disk. Error message: Could not create the clone medium '/media/virbox/XP1.vdi' (VERR_DEV_IO_ERROR)

Thanks in advance.
Lars

---

### Post by TheFu on 2014-03-20
Copy the vdi file. There is a 100% backup.  On my VBox GUI, there is an "Export Appliance" choice too - basically the same thing.

However, it won't help you at all with any upgrades.

People like you and I need to run LTS supported releases of Ubuntu.  12.04, 14.04(when released).  We shouldn't run short-term support releases. See my signature for more reasons why not.

If you can still run the VM itself, it would be a good idea to perform a backup using nominal Linux methods. Then you can create a new VM with 12.04 or 14.04 (when released) and restore much of the settings and data from that backup.  [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use) shows how I do it. There are other posts here about backups where we've helped people get a backup solution going. We all sleep better at night knowing our backups are restorable. If a backup (or selected sub-part of a backup) cannot be restored, what is the point?

---

### Post by JKyleOKC on 2014-03-22
> **InfiniteDK said:**
> I'd like to upgrade to a new Ubuntu version, and therefore I want to backup my Virtual Box vdi files.Simply copy the VDI files -- or even the entire hidden .VirtualBox subdirectory of your home directory -- to an external drive that's large enough to hold them. That is, if you have 10 VMs with 30-GB virtual drives on each, you will need more than 300 GB available on the external drive. After you wipe the original drive and do a clean install of the current LTS (12.04.4) or upcoming LTS (14.04), put the hidden VirtualBox subdirectory back into your home directory.

If you copied the whole subdirectory, that's all you have to do to restore the VMs and their virtual disks, assuming that you've not yet upgraded VirtualBox to 4.x (they quit using the hidden directory for new VMs at the start of 4.x). Then instaii the latest VBox from the Oracle site, and install its extension pack as well. It will pick up the content of the hidden subdirectory automatically and you will find all of your VMs ready for use. Any new ones that you create will be in the directory created by 4.x, which is "$HOME/VirtualBox VMs" and is NOT hidden.

If you copied only the VDI files, then you will need to create new VMs with the same attributes as the old ones, but don't create new VDI files for them. Instead, assign the copied-over VDI, which will have all the configuration information for the guest system it contains.

I've done it both ways. If an adequately large external drive is available, the whole-directory routine is much less work, but either will succeed.

If your VMs were created by 4.x versions, then also save that additional directory and restore it as well before installing the new copy of VBox itself. Ditto if the additional visible directory exists. I would copy both if they exist but not worry if either is totally missing.

You may find that VMs which are in "saved" state rather than "powered down" when you do this may refuse to load after the upgrade. Apparently there's a new internal variable that isn't fully compatible with the snapshots created by pre-4.x versions. I've been able to solve that problem by using the "discard" option to throw away the saved snapshot and return the VM to "powered down" and if you take care to power down each VM before starting the process, the problem never arises.

Hope this helps. These days I don't try to back up any of the guests, just copy their VDI files to a large external drive from time to time so that I can roll back in case of disaster.

---


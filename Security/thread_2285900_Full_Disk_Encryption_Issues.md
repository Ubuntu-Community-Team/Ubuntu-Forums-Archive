---
title: "Full Disk Encryption Issues"
date: 2015-07-08
forum: Security
---

### Post by DBQ on 2015-07-08
Hi everybody.

So my admin installed Ubuntu Server 14.04 Server Eddition on my server machine and he setup home directory encryption, which is cool.

They gave me an initial password which I changed soon after logging in (through SSH) -- now, now -- yes, I know the consequences...need to also change the passphrase...please hear me out...

Once I change my password I get Access-Your-Private-Data.desktop  README.txt files in the home directory and thats it -- yes, expected and yes, I Googled it. I know I need to update the passphrase.

My issue is this -- I tried using cryptsetup to set/remove passphrase but no matter what /dev/sdaXX I supply, I get an error saying that this is not a LUKS device. 

Need a hero to save the day. I bet you are that hero :-)

---

### Post by DBQ on 2015-07-08
BTW, not sure if this helps, but here is the output of lsblk

```

sudo lsblk -o name,uuid,mountpoint                                                                     
NAME                        UUID                                   MOUNTPOINT
sda                                                                
&#9500;&#9472;sda1                      02685d92-8cdb-4e4b-a453-c8dcf9416612   /boot
&#9500;&#9472;sda2                                                             
&#9492;&#9472;sda5                      PC7qJ8-cgPu-qJ44-oQgv-F6o9-2Z0e-LtauoP 
  &#9500;&#9472;steamer--vg-root (dm-0)   c11e5329-f8e0-429a-b886-908934a840f0   /
  &#9492;&#9472;steamer--vg-swap_1 (dm-1) c978293a-84cd-4b9d-a83c-aefcb72a3b38   
    &#9492;&#9472;cryptswap1 (dm-2)                                            

```

---

### Post by DBQ on 2015-07-09
Made some progress: So I found that the commands I need run should be targeting the /dev/steamer-vg volume. However, when run sudo cryptsetup luksChangeKey /dev/topaz-vg , it does not prompt me for a passphrase or anything of the kind. The command just silently exists.

Please help!

---

### Post by ahears on 2015-07-09
> **DBQ said:**
> 
Hi everybody.

So my admin installed Ubuntu Server 14.04 Server Eddition on my server  machine and he setup home directory encryption, which is cool.
They gave me an initial password which I changed soon after logging in  (through SSH) -- now, now -- yes, I know the consequences...need to also  change the passphrase...please hear me out...
Once I change my password I get Access-Your-Private-Data.desktop   README.txt files in the home directory and thats it -- yes, expected and  yes, I Googled it. I know I need to update the passphrase.

My issue is this -- I tried using cryptsetup to set/remove passphrase  but no matter what /dev/sdaXX I supply, I get an error saying that this  is not a LUKS device. 
Need a hero to save the day. I bet you are that hero [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Made some progress: So I found that the commands I  need run should be targeting the /dev/steamer-vg volume. However, when  run sudo cryptsetup luksChangeKey /dev/topaz-vg , it does not prompt me  for a passphrase or anything of the kind. The command just silently  exists.

Please help!


**I'm not an expert** therefore someone may correct me here. From what I can tell "/dev/steamer-vg" is not in your previous output from "lsblk" as a device,  for starters. Also, neither is "/dev/topaz-vg" as you previously  stated. Be careful of clerical errors on the command line. It seems you  changed passwords for volumes that don't exist, thus no result!

That being said, the "[COLOR=#008000]gnome-disk-utility[/COLOR]" is the graphical user interface that will allow you to change the Luks key.

I will be using "[COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR]" for this session because I assume this is the volume you want unlocked from the output you posted. Copy this article and conduct a "find and Replace" for the volume name you need so it makes sense to you.

**FIRST:**  

The fix to your login issue: add "[COLOR=#008000]ecryptfs-mount-private[/COLOR]" to your *unmounted* "[COLOR=#ff0000]$HOME/.profile[/COLOR]" when logging in from ssh. This will unlock everything.
Your crypto disks seem to be mounted also.

**SECOND:**

[B][COLOR=#008000]sudo apt-get update && sudo apt-get install lvm2 cryptsetup[/COLOR] "Install crypto modules etc.."
[COLOR=#008000]sudo modprobe dm-crypt[/COLOR] "Load the encryption modules..."
[COLOR=#008000]sudo modprobe aes[/COLOR][COLOR=#000000] "Again.."[/COLOR]
[COLOR=#008000]sudo modprobe sha256[/COLOR] "and again..."[/B]
[B]
THIRD:
[/B]
**_Please show the output of these commands:_**
> 
[COLOR=#008000]sudo fdisk -l[/COLOR] "This will always show that cryptoswap1 has an invalid partition table. That is because it is encrypted **or** it has not yet been made into a swap. If it has not been made into swap yet, you can correct it with "[COLOR=#008000]sudo mkfs.swap /dev/mapper/cryptoswap1[/COLOR]" and "[COLOR=#008000]sudo swapon /dev/mapper/cryptoswap1[/COLOR]" and look for errors, _BUT it is normal to have this error on encrypted disks so don't waste your time unless it doesn't mount_!" If you don't know, you can run "[COLOR=#008000]sudo cryptsetup status cryptoswap1[/COLOR]" or "[COLOR=#008000]cat /proc/swaps[/COLOR]" to check the status."
[COLOR=#008000]cat /etc/fstab[/COLOR] "Mappings for mounted drives..."
[COLOR=#008000]cat/etc/crypttab[/COLOR] "Mappings for Encrypted drives. This is where your Luks entry will be..."
[COLOR=#008000]ls -asl /dev/disk/by-id[/COLOR] "Using the output  from this command in your /etc/crypttab prevents the drive from  being incorrectly loaded when using encrypted drives. This is because  encrypted drives can have a tendency to get a new UUID every _boot_. We won't use UUID. Why? Because this includes encrypting the UUID data! (This depends on your partition  configuration and isn't always true) This can be corrected in your  /etc/crypttab using an "offset=36" command... but I digress and that  method is Hacky in my opinion, and outdated We will simply use the  output from [COLOR=#008000]ls -asl /dev/disk/by-id[/COLOR][COLOR=#000000] to point to the drive correctly and circumvent the UUID issue[/COLOR]." *Note: 36 bytes is the length of the disk UUID.* ***Allow me to re-iterate that I may be corrected here.***
[COLOR=#008000]sudo blkid[/COLOR] "This will show which drives are Luks etc... "

Did you remember to reload crypto disks? "[COLOR=#008000]sudo /etc/init.d/cryptdisks-early reload[/COLOR]" and "[COLOR=#008000]sudo /etc/init.d/cryptdisks reload[/COLOR]"

[COLOR=#800080]I will be able to help set up your "/etc/fstab" and "/etc/crypttab" permanent mapping entries after you post the above info![/COLOR]

>  
**L.U.K.S (Linux Unified Key Setup) Crash Course:**

**NEW LUKS:** (This will _destroy_ your previous[COLOR=#0000cd] /dev/sda5/steamer--vg-root [/COLOR]disk!)

```
[COLOR=#008000]sudo umount[/COLOR] [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] "Unmount the mounted disk..."
[COLOR=#008000]sudo /sbin/badblocks -c 10240 -s -w -t random -v [/COLOR][COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] "Scan for disk errors...this is slow."
[COLOR=#008000]sudo dd if=/dev/urandom of=[/COLOR][COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] "Wipe residual data from the disk..."
[COLOR=#008000]sudo cryptsetup --verify-passphrase --hash=sha256 --cipher=aes-cbc-essiv:sha256 --key-size=256 luksFormat[/COLOR][COLOR=#0000cd] /dev/sda5/steamer--vg-root[/COLOR] "Create Luks!"
[COLOR=#008000]sudo cryptsetup luksOpen[/COLOR] [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] [COLOR=#800000]disk[/COLOR] "Unlock new Luks Disk..."
[COLOR=#008000]sudo mke2fs -j -O dir_index,filetype,sparse_super [/COLOR][COLOR=#0000cd]/dev/mapper/[/COLOR][COLOR=#800000]disk[/COLOR] "Create the file system inside the new disk..."

```

*Here is where I simply unplug the drive and plug it back in and enter the password, but you can do this...*

```

[COLOR=#008000]sudo umount[/COLOR] [COLOR=#0000cd]/dev/mapper/[/COLOR][COLOR=#800000]disk[/COLOR] "Unmount the mounted disk...again..."
[COLOR=#008000]sudo mount -t [/COLOR][COLOR=#ffa500]ext3[/COLOR] [COLOR=#0000cd]/dev/mapper/[/COLOR][COLOR=#800000]disk[/COLOR] "Mount the new Luks disk, enter your password and you're done!"

```

To add a Keyfile to Luks:

```

[COLOR=#008000]sudo dd if=/dev/urandom of=[/COLOR][COLOR=#800000]/home/[COLOR=#000000]**username**[/COLOR]/keyfile[/COLOR][COLOR=#008000] bs=1 count=2048 [/COLOR][COLOR=#000000]"Use random data to generate a key...this is slow also."[/COLOR][COLOR=#008000]
sudo chmod 0400 [/COLOR][COLOR=#800000]/home/[/COLOR][COLOR=#000000]**username**[/COLOR][COLOR=#800000]/keyfile[/COLOR] "Change permissions of keyfile"
[COLOR=#008000]sudo cryptsetup luksAddKey -S 1[/COLOR][COLOR=#0000cd] /dev/sda5/steamer--vg-root[/COLOR] [COLOR=#800000]/home/[/COLOR][COLOR=#000000]**username**[/COLOR][COLOR=#800000]/keyfile[/COLOR] "Install the keyfile into slot #1. "

```

Substitute "[COLOR=#800000]/home/[/COLOR][COLOR=#000000]**username**[/COLOR][COLOR=#800000]/keyfile"[/COLOR] for wherever you want to store the key. I recommend a USB stick designated just for booting. This is multi-factor authentication[B].

Do not move the [COLOR=#800000]keyfile[/COLOR] after you have installed it or you will not be able to unlock your disk.[/B] This can be usefull if you were to store the key in your encrypted /home...but *only* for _removable disks_!
[U]

/etc/fstab entry:[/U] NOTE: FOR _REMOVABLE_ ENCRYPTED DISKS DO [COLOR=#ff0000]NOT[/COLOR] ADD AND ENTRY TO THIS FILE.

[QUOTE][COLOR=#800000]/dev/mapper/disk      [/COLOR]/[COLOR=#ffa500]             ext3[/COLOR]                     defaults             0                   1

Put the  result from the command "[COLOR=#008000]ls -asl /dev/disk/by-id[/COLOR]" _which matches the partition entry for_ "[COLOR=#0000cd]/dev/sda5/steamer--vg-root"[/COLOR] in the field** *BELOW***.

_/etc/crypttab entry_:

> [COLOR=#800000]disk[/COLOR]                         /dev/disk/by-id/***HERE*** [COLOR=#800000]/home/[/COLOR]**[COLOR=#000000]username[/COLOR]**[COLOR=#800000]/keyfile[/COLOR]                         luks
Note: Only use [COLOR=#800000]"/home/[/COLOR][COLOR=#000000]username[/COLOR][COLOR=#800000]/keyfile"[/COLOR] if you created one! Otherwise omit the entry for it but leave the rest!

To unlock your Luks disk: "[COLOR=#008000]sudo cryptsetup luksOpen[/COLOR] [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] [COLOR=#800000]disk[/COLOR]" (It doesn't have to be [COLOR=#800000]disk[/COLOR] maybe [COLOR=#800000]/media/disk[/COLOR] or where-ever you want it to be mapped. Just be consistent.) 
Then to change the Luks key: "[COLOR=#008000]sudo cryptsetup -y luksAddKey [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR][/COLOR]" or "[COLOR=#008000]sudo cryptsetup -y luksRemoveKey [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR][/COLOR]"
Then to check the status of the Luks: "[COLOR=#008000]sudo cryptsetup luksDump [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR][/COLOR]"
[U]
Take ownership of the root in the encrypted drive!:[/U] ```
sudo chown **user:group** [COLOR=#800000]/disk[/COLOR]
```

Remember, substitute [COLOR=#0000cd]/dev/sda5/steamer--vg-root[/COLOR] for the appropriate drive you are operating on!


NOTE: Also, if you stored the volume password in your keyring than it will unmount automatically which is why you aren't prompted for a password to unlock it.

[/QUOTE]

---


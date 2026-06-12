---
title: "Remote/unattended reboot with dmcrypt-ed root partition"
date: 2009-08-09
forum: Security
---

### Post by lbcongo on 2009-08-09
Hi All,

I was wondering...is it was possible to perform a remote and/or unattended reboot when the root partition is encrypted via dmcrypt? I was thinking something like specifying a password or temporary keyfile in the unencrypted /boot partition? Basically, at times I would like to be able to reboot my home server from the office but no one is available to enter the passphrase for my encrypted partition.

Thanks,
adam

---

### Post by cariboo on 2009-08-10
Is there a reason why you need to reboot the server? If you make changes to any configuration files just restart the service you made the changes to, for example if you changed /etc/samba/smb.conf all you have to do is restart samba:

```
sudo /etc/init.d/samba restart
```

this works for any service you are running, they are all located in /etc/init.d.

---

### Post by lbcongo on 2009-08-10
Hello, thanks for the reply. Hmmm...rarely a good reason to reboot (especially my server). Updates have asked me to reboot a couple times. And kernel upgrades. There are also the times where power outages have required a shutdown and this little server is headless, so I usually have to drag a monitor and keyboard down to the basement to boot back up (although in this situation a temporary keyfile wouldn't matter unless I had time to log in before my UPS battery gave out and adjust power scripts to give me time to supply the temporary keyfile/one-time preboot password/whatever allows me to pre-supply a key for booting).

For the sake of an unattended execution, here's perhaps a better example: I also have another dual-boot server that also has no dedicated monitor/keyboard. It dual boots Windows for compiling some of my Windows-specific programming projects and Ubuntu Server for...well...everything else. I'd like to be able to simply modify the 'default' in Grub's menu.lst before the boot and know that I can do the same to boot back into Ubuntu. In this scenario I also have to drag a keyboard (at the minimum) and monitor down to the physical machine to supply a key to perform the reboot.

Bottom line is that there are times where I know I want to reboot ahead of time and would like to...say...enter a key/supply a key file/etc ahead of time so that the encrypted partition can mount and Ubuntu can boot.

Thanks again!

-Adam

---

### Post by anthro398 on 2009-08-11
Providing a key that dmcrypt can use to unlock an encrypted partition or disk is as secure as not encrypting the drive at all.  I do wonder, though, if you could scp a keyfile to the boot partition, which is never encrypted, and then edit the grub configuration to point dmcrypt at the keyfile.  On successful reboot, one could then wipe the key.

As I said, it's still only the semblance of security.  If the reboot fails for some reason, your key is left sitting in the boot partition.  

When confronted with this situation and after realizing that unattended reboots weren't possible I decided to migrate from encrypted disks to encrypted Private directories and a Truecrypt partition.

---

### Post by lbcongo on 2009-08-11
> **anthro398 said:**
> Providing a key that dmcrypt can use to unlock an encrypted partition or disk is as secure as not encrypting the drive at all.

Not AS (in)SECURE if 'keyfile' and config that accepts keyfile as key is temporary. Less secure? Yes. But as you pointed out, this breaks down when the system fails to boot, but I don't see how the system is seriously exposed during a reboot cycle; especially if a mechanism is in place remove this temporary key/config immediately after booting [effectively putting the system back into the state it would be in if one were to hand-enter a key].

> **anthro398 said:**
> I do wonder, though, if you could scp a keyfile to the boot partition, which is never encrypted, and then edit the grub configuration to point dmcrypt at the keyfile.  On successful reboot, one could then wipe the key.

YES. This is what I was thinking as well...do you know what I would need to edit in grub? I didn't know that grub orchestrated any of the decryption or store config info about the encrypted partition(s). This is the kind of information I need...do you have the details? 

The more I read about it, the more I think that the solution requires consuming one of the LUKS key slots with a 'temporary' key via 'cryptsetup' and deleting the key in this slot after reboot. I didn't want fiddle with it on my server though. I may have to create a throw-away virtual system using VirtualBox or something and bang on it until I figure it out.

One of the better documents I have found related to the subject is: [http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt]("http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt")

> **anthro398 said:**
> 
When confronted with this situation and after realizing that unattended reboots weren't possible I decided to migrate from encrypted disks to encrypted Private directories and a Truecrypt partition.

How did this resolve the situation? I think what you're saying is that you have no compelling need to encrypt an entire file system so encrypting Private directories is sufficient, but I don't know what Truecrypt has to do with resolution. In other words, what does Truecrypt provide that dmcrypt does not? I currently only use Truecrypt to encrypt my Windows partition. Do you think it's a better solution than dmcrypt with LUKS extension?

Thanks for the reply!

---

### Post by anthro398 on 2009-09-04
> **lbcongo said:**
> 
How did this resolve the situation? I think what you're saying is that you have no compelling need to encrypt an entire file system so encrypting Private directories is sufficient, but I don't know what Truecrypt has to do with resolution. In other words, what does Truecrypt provide that dmcrypt does not? I currently only use Truecrypt to encrypt my Windows partition. Do you think it's a better solution than dmcrypt with LUKS extension?


Well, I suppose it depends on your goal.  I want 2 things, really.  First, I want to secure my personal data.  The burglary rate in neighborhood is very high (thanks crappy economy!) and I want to know that if someone steals my computer they aren't getting my photos, tax returns, etc.  Second, I want to run a headless file server in the closet.  With dmcrypt, the first is possible, but the second is not.  I'd like to encrypt the entire disk, but that isn't possible in a headless environment.  

However, after thinking about this problem, I wonder if a virtual machine isn't a nice solution.  So, imagine you have a minimal Ubuntu installation running on your file server.  Really, it's just there to bootstrap your Virtualbox image.  The Virtualbox image is encrypted using dmcrypt.  The images could be stored on a Truecrypt partition or not.  The only vulnerability I can see is the swap partition on the bootstrap installation.  I recall you can use dmcrpt to generate a random key on boot for the swap partition so it's re-encrypted at each boot and thus protected from disk recovery software.  

With this configuration, your system is encrypted and you can manage unattended boots.  When you remotely boot the bootstrap installation, you'd need to connect to the box, start the virtual machine, and enter your passphrase or provide your key.  Virtualbox is pretty efficient, so the overhead wouldn't be that great.  FreeNX makes remote GUI connections painless, but I think Virtualbox provides a remote GUI, too.

---

### Post by HermanAB on 2009-09-04
There are devices that can extend the KVM over Ethernet:
[http://www.belkin.com/kvm/sms/](http://www.belkin.com/kvm/sms/)

I don't encrypt the root partitions of my servers because of this problem.  In any case, encrypting root doesn't buy you much since the whole OS is free and public knowledge anyway, so why encrypt it?  Encrypting the OS just slows things down.  It should normally be sufficient to encrypt /home and /swap and make /tmp a RAMdisk with tmpfs.

---

### Post by bodhi.zazen on 2009-09-04
> **HermanAB said:**
> There are devices that can extend the KVM over Ethernet:
[http://www.belkin.com/kvm/sms/](http://www.belkin.com/kvm/sms/)

I don't encrypt the root partitions of my servers because of this problem.  In any case, encrypting root doesn't buy you much since the whole OS is free and public knowledge anyway, so why encrypt it?  Encrypting the OS just slows things down.  It should normally be sufficient to encrypt /home and /swap and make /tmp a RAMdisk with tmpfs.

+1

There is little to be gained by this as *most* such servers are locked and the remote admins have the keys to do maintenance ...

At any rate, it is possible to do this :

[http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu)

---


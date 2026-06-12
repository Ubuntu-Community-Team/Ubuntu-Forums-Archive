---
title: "Encripting with dual boot"
date: 2018-04-06
forum: Security
---

### Post by gabo.cr on 2018-04-06
Hi,

I have a laptop with Windows 7 and Ubuntu 16.04. I would like to encrypt my files, however I'm not sure what is the best option, or if I may break something in the process. 
I hear about encrypting the whole computer, or certain partitions, or just the home folder.

I don't care about the Windows partition because I have nothing there, except some programs that I rarely use.
All my files are in Ubuntu synchronized with Insync to Google Drive. So I wonder if just encrypting the home folder would be sufficient, or do I need to worry about anything else ?
And I wonder if Insync will have problems too (I can ask them that).

I would also like to upgrade to Ubuntu 18.04, so I think I will re-install Ubuntu from scratch (keeping Windows) instead of a do-release-upgrade.
Should I just encrypt the home folder when I do that ?

Here are my partitions:
```

device                       fs_type     label        mount point 
-------------------------------------------------------------------
/dev/sda1                    vfat        DellUtility   (not mounted)
/dev/sda2                    ntfs        RECOVERY      (not mounted)
/dev/sda3                    ntfs        OS            (not mounted)
/dev/sda6                    ext4                      /            
/dev/sda5                    swap                      [SWAP]
/dev/sda7                    ext4                      /home

```

I appreciate your advice !

---

### Post by HermanAB on 2018-04-06
The more encryption, the better.

When you use 'whole disk' encryption, the /boot partition is still plain text, so that the machine can boot up, so it is more like 99.999% encryption.  This is the best way to do it.

If you only encrypt the /home partition, then /swap and /tmp etc are left unencrypted, so temporary files can leak sensitive information.  This is not good, but better than nothing.

The main reason for using encryption is that when your machine gets stolen, your data is safe.

The downside to encryption is that if there is any error on the disk, you typically lose everything.  So you absolutely must have backups.  Since you must have backups anyway, this is not much of a problem.  Solid state drives also tend to fail completely all of a sudden, so this problem is now becoming the rule even without encryption.

---

### Post by TheFu on 2018-04-07
HermanAB nails it again!

Whole disk encryption is faster on modern CPUs than encrypting just the HOME directory.

About 2 months ago, an SSD died on me.  The system was whole drive encrypted, but I've had backup religion (daily,automatic, versioned) for well over a decade, so it was a minor inconvenience to get a working system back, even though I put in a new SSD that was 50% the size of the original. Without backups, all that data would be gone, gone, gone.

I tried encrypted HOME only for a few months.  Found that it broke my backups, so I switched to whole disk encryption.  Never looked back. No regrets.  I encrypt all portable devices after having 1 stolen that wasn't encrypted.  I also use 2FA to unlock the disk during boot and non-trivial passwords for all devices which can connect to our infrastructure.  That includes smartphones and tablets. No 6 digit pins and definitely NOT fingerprint or face-based logins.

If you do whole disk encryption, it is non-trivial to setup with another OS on the same physical disk. The Ubuntu installer wants to wipe the disk.  I recall a how-to guide was written about 18 months ago that got put into the Ubuntu wiki or help websites.  Google should find it.

And this is very important, do not hibernate or suspend a system that uses whole disk encryption if you care about real security during travel. I always shutdown the system when moving to different buildings/locations. Suspend is fine while you are nearby in a secure location, but I wouldn't trust it in a cafe or in-transit.

If you barely use Windows, perhaps moving that install into a virtual machine would make things easier and more secure?  Just a thought.  Might not work for your needs. IDK.

---


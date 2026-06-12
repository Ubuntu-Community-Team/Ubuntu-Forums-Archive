---
title: "Boot Partition Full -- Which &amp; How to Remove Old files"
date: 2011-12-02
forum: Server Platforms
---

### Post by John Raycheba on 2011-12-02
Hi,
 
I'm sure this is simple.
 
THE BACKGROUND:
The system is a DELL Notebook with a 160 GB HD running Ubuntu 10.04.3 LAMP server which is used to run a small phpBB bulletin board. There also is a much larger external (USB) HD that is used for backups.
 
I usually apply the standard updates / upgrades using apt-get.
 
The most recent dist upgrade generated a couple of error messages indicating that there was not sufficient disk space in the /boot partition.
 
In spite of the above, the system seems to be working properly.
 
I've checked the file space and found that /boot is, indeed, full.
 
The result of: "df -h" is:
 
Filesystem            Size  Used Avail Use% Mounted on
                         144G  8.3G  129G   7% /
none                  479M  276K  478M   1% /dev
none                  484M     0  484M   0% /dev/shm
none                  484M  552K  484M   1% /var/run
none                  484M     0  484M   0% /var/lock
none                  484M     0  484M   0% /lib/init/rw
none                  144G  8.3G  129G   7% /var/lib/ureadahead/debugfs
/dev/sda1             228M  226M     0 100% /boot
/dev/sdb1             917G   45G  827G   6% /mnt/sdb1

An abbreviated listing of the contents of the /boot directory is:
 
abi-2.6.32-21-generic-pae     
abi-2.6.32-24-generic-pae     
abi-2.6.32-25-generic-pae     
.
abi-2.6.32-35-generic-pae     
abi-2.6.32-36-generic-pae     
config-2.6.32-21-generic-pae  
config-2.6.32-24-generic-pae  
.
.
vmlinuz-2.6.32-35-generic-pae
vmlinuz-2.6.32-36-generic-pae

Clearly, there are several copies of older versions of the system files.
 
THE QUESTIONS:
 
1. Can / should I simply delete the old versions of the files or is there some other preferred procedure? 
 
2. Is there a setting that I can set so that only two or three of the earlier versions of the files will be retained?
 
Thanks for your help /suggestions and recommendations.
 
Regards,
 
John

---

### Post by volkswagner on 2011-12-03
I found [this how to]("http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html").

I ran it on my server running Ubuntu Server 10.04.

I already had aptitude installed so that was not needed.  Also running the purge automatically ran update-grub so the last command was not needed.

I had 5 old kernels to be removed which freed up 455MB! 

I don't think the purge can remove the running kernel, but it is good just to double check the result of "uname -r" is not on the list of kernels to be removed!  That would be bad.

---

### Post by Lampi on 2011-12-03
don't forget to remove the matching headers, they eat up even more space and are useless now.

---

### Post by volkswagner on 2011-12-03
> **Lampi said:**
> don't forget to remove the matching headers, they eat up even more space and are useless now.


The purge also will remove headers:

```
The following packages will be REMOVED:
  linux-headers-2.6.32-35{u} linux-headers-2.6.32-35-generic-pae{u} linux-image-2.6.32-36-generic-pae{p}
```


:)

---

### Post by volkswagner on 2011-12-03
I think you need to be very careful with this.

While I was testing this, I deleted all old kernels.  Then ran dist-upgrade.  I ran the command again it wanted to delete the most recent kernel.  I assume this is because I did not reboot after the dist-upgrade.

---

### Post by Lampi on 2011-12-03
> **volkswagner said:**
> The purge also will remove headers: :)
nice, didn't know ... it makes sense though

---

### Post by John Raycheba on 2011-12-03
Thank you All,
 
I knew there had to be a "proper" way of dealing with this.
 
I'll mark the original post as "SOLVED".
 
Thanks again.
 
Regards,
 
John

---


---
title: "Clonezilla and Encrypted Home"
date: 2012-02-18
forum: Security
---

### Post by paul_h on 2012-02-18
When upgrading my laptop to 11.10 I elected to encrypt my home directory. For years I have been using Clonezilla to backup my system and have used it to recover from disasters and to install larger disk drives.

I have used Clonezilla to create clone "images" and, when needed, to restore those images. I understand that Clonzilla omits what it sees as empty space.

My concern now is ... does Clonezilla identify the encrypted data that is my home directory, or see it as empty (unused) and therefore not include it in the image?

My immediate thought was to try it out ... to do a clone image and restore it. Then I realised that if Clonezilla did not include the encrypted home directory then I'd end up with a pretty useless system.

I would appreciate advice before I try anything drastic.

---

### Post by winh8r on 2012-02-18
Probably getting into territory where experiments in virtual box would be a lot safer!!!
   


There is some stuff here:

[http://theholyjava.wordpress.com/2010/08/10/disk-backup-with-clonezilla/]("http://theholyjava.wordpress.com/2010/08/10/disk-backup-with-clonezilla/")

which might be useful, (its about halfway down the page)

hope this helps

---

### Post by paul_h on 2012-02-18
Thanks winh8r.

Virtual box may provide a safe testing option.

[http://theholyjava.wordpress.com/2010/08/10/disk-backup-with-clonezilla/](http://theholyjava.wordpress.com/2010/08/10/disk-backup-with-clonezilla/) is an interesting read but it talks of encrypting the backup, rather than backing-up an encrypted directory.

I'm keen to keep the home directory encrypted as it takes away the worry about "losing" the notebook (apart from the financial) because all "sensitive" data is stored in that directory and safe from unauthorized access.

---

### Post by Dave_L on 2012-02-19
You run Clonezilla by booting into it?  If you're not logged in at that time, then Clonezilla will only see the encrypted home directory files, and will back those up.

Make sure you have your encryption passphrase stored in a safe place. You might need it if you ever needed to access encrypted files restored from a backup.

I agree that testing with VirtualBox, if possible, is a good idea. Backup procedures should always be tested.

---

### Post by paul_h on 2012-02-19
Thanks Dave.

I've installed VirtualBox with the intention of testing the theory. But on reflection I concluded that the process could not be done (at least by me) in a VM on my computer.

To run CloneZilla the computer needs to be on a booted from a DVD/CD or USB flash drive containing CloneZilla. There seems to be no opportunity to start a VM to do a test. The only way I can see to safely test whether an encrypted home directory would be included in a whole disk clone image is to clone the drive then restore it to another physical drive. If it were to fail, then I'd still have the original drive untouched.

I would hope that someone has already been been through the process of cloning their similar setup and restoring it successfully.

---

### Post by Grenage on 2012-02-20
In my limited experience, encrypted volumes are filled with data, so there shouldn't be anything to omit.  As you're just copying the drive, there isn't much that can go wrong on the source drive.

Does clonezilla have a "sector for/by sector" option?  That would create a perfect copy of the drive, and should give you no problems; dd (it might even use it) does the same thing.  Bear in mind that such a copy will take much longer, as all white-space is also duplicated.

---

### Post by Cheesemill on 2012-02-20
> **paul_h said:**
> To run CloneZilla the computer needs to be on a booted from a DVD/CD or USB flash drive containing CloneZilla. There seems to be no opportunity to start a VM to do a test. The only way I can see to safely test whether an encrypted home directory would be included in a whole disk clone image is to clone the drive then restore it to another physical drive. If it were to fail, then I'd still have the original drive untouched.

Create an empty VM then just boot your VM from the CloneZilla ISO and try a restore.

---


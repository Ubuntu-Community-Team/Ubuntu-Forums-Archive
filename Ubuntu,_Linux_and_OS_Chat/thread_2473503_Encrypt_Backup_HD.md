---
title: "Encrypt Backup HD"
date: 2022-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2022-04-06
I have a stand alone Desktop machine and about to re-install and encrypt my HD as I have bank/financial details on it.  A thought just occurred to me - I use rdiff-backup to backup to another internal HD.  What is the point of encrypting my main HD if the backup HD is not encrypted?   My backup HD is not mounted when I boot - I have a script that mounts it when I perform the rdiff-backup.  I would appreciate your thoughts on how best to encrypt my backup HD and what the effect will be re my rdiff-backup arrangement. (I will be using the inbuilt LUKS encryption during the new install).

---

### Post by kevdog on 2022-04-06
I'm not sure what your asking.  LUKS encryption is only encryption at rest.  Once mounted and the password supplied, files are available access as unencrypted files.  In terms of backups, there is going to be a very wide opinion on the tool or tools you can use.  Considerations include either file level or block level encryption.  I'm not an expert on rdiff-backup however I'm aware its a backup utility that is able to perform delta file-level backups. A similar tool to this is borg backup, which can also add in encryption as well.  Another possibility would be for you to have a LUKS encrypted partition on your backup disk and use whatever backup utility you would like for your backups.

---

### Post by lammert-nijhof on 2022-04-09
I have my financial stuff encrypted too, but I have it all in a Virtualbox VM for two reasons: 

[LIST]
[*]Virtualbox encrypts the whole virtual disk (vdi); 
[*]the VM is only booted and on-line, when I need that financial stuff. 
[/LIST]
Virtualbox will request the encryption pass phrase every time you start the VM, I use a 15 character passphrase and I skip the login-password. 
I store all my VMs and data on OpenZFS and I use OpenZFS for the backup. During the incremental backup ZFS only sends the modified encrypted 128k records and those encrypted records are added to the backup. 
The sender knows the modified records, because you specify the previous snapshot-id and the current snapshot-id in the send of the backup.  The backup deals with the record-level and does not care whether the records are plain; compressed or encrypted. 
The backup can be on another PC "zfs send | ssh zfs receive" or on a local PC "zfs send | zfs receive".

Nowadays OpenZFS can encrypt a dataset/folder too and the incremental backup will be handled in the same way, but I have not used it yet. 

Note that in servers they prefer to use whole disks, but I always use OpenZFS with partitions. I have to with a 500GB and 1TB HDD. I use a striped datapool (Raid-0; lz4 compressed) with two 500GB partitions. Even one dataset in the datapool has the property copies=2, which means that two records are written, one to each partition, a kind of Raid-1 subset inside Raid-0 :)

---

### Post by Quarkrad on 2022-04-10
Thank you - I hadn't thought of that. Certainly worth considering for my set up.

---

### Post by kevdog on 2022-04-10
I love ZFS -- however just a word of caution -- you are definitely opening up a rabbit hole.   Read about ZFS prior to using it.  As a backup file system you'll need zfs modules added to the kernel modules.  Ubuntu does this now by default, however I don't think a lot of other linux distros due this by default due to potential licensing issues -- the fact Ubuntu offers this is somewhat controversial.  If you would only be restoring the backup on Ubuntu systems -- great, however with other linux systems it might be a little bit more tricky.

---

### Post by baltic on 2022-05-31
Give [this]("https://ubuntuforums.org/showthread.php?t=2475554") a try. I just backup whole home folder with it.

---

### Post by TheFu on 2022-05-31
You can have LUKS encrypted storage that is dynamically mounted on demand.  

P1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak)
P2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0)
or 
if you prefer to read: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)

This way, your backups are using standard, well-known, encryption that the FBI can't break, assuming you don't use weak passphrases or leave the key-file laying around.

---

### Post by Quarkrad on 2022-06-01
Thank you all - problem/issue solved!

---

### Post by TheFu on 2022-06-01
> **Quarkrad said:**
> Thank you all - problem/issue solved!

How?

---

### Post by Quarkrad on 2022-06-02
Apologies in that my *problem/solved* response is not explicit enough - I appreciate a *Solved* tag should really provide a solution to the problem for all users.  What I meant to say was that I have got sufficient information for me to investigate further.  It is going to take me some time to look into these areas and I wanted to close this thread to save time re those who have helped.  If I get into trouble down stream (e.g. zfs - if I go that route) I will open another thread.

---


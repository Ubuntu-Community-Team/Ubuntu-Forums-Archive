---
title: "Remote encrypted backups"
date: 2008-05-22
forum: Security
---

### Post by jonthysell on 2008-05-22
Heya,

I'm currently using dmcrypt to encrypt my entire drive in my desktop (Gutsy).

I'm also running a remote server (Hardy) that I can access over SSH.

I want to be able both securely transfer and store incremental backups from Gutsy to Hardy automatically and regularly.

Right now, I'm using rsync to save local backups of Gutsy onto the same encrypted drive (secure, but eggs all in one basket).

The Hardy server is on 24/7, and I know that I can securely transfer everything over with an ssh/rsync combo, but is there any way to store the end files encrypted?

Since the Hardy server is on all the time, I don't want an encrypted drive always mounted (plus it's headless, so it can't auto mount at startup because if the power cycles then the machine won't boot without prompting for the luks password).

Also, if I create and encrypted image of the files (say with truecrypt or an encrypted 7zip) before transfer, won't rsync copy the whole backup every time?

Any suggestions?

Thanks and be happy!

---

### Post by Dr Small on 2008-05-22
Why not create a encrypted partiton on the Hardy server that can be mounted with fstab at bootup and uses a keyfile. Then securely transfer your backups to the encrypted partition.

---

### Post by jonthysell on 2008-05-22
> **Dr Small said:**
> Why not create a encrypted partiton on the Hardy server that can be mounted with fstab at bootup and uses a keyfile. Then securely transfer your backups to the encrypted partition.

Then the keyfile would have to be on a drive physically attached to the server. I'm using drive encryption in case of physical theft.

If the server accesses the key in an unencrypted space (at bootup), then so can any potential thieves.

Is there any way to say, leave the drive on Hardy unmounted, then only mount/unlock when I'm backing up? Could I store the server keyfile on my desktop then pass it securely to the server, mount the encrypted drive, perform the backup, then unmount and delete the key?

If the key is stored encrypted (via dmcrypt) on my desktop, then it'd only be accessible the same times that my data is: when I'm logged in. Which is of course the only time that backups can occur anyway ;)

---

### Post by Biochem on 2008-05-22
Tar has incremental backup capabilities and can be piped to gpg. Public key don't need password for encryptions and the only the changed files are going to be transfered.

---

### Post by jonthysell on 2008-05-23
Ok I've been searching all day on this, and have cobbled a working solution, I'll probably post a more detailed howto in a bit.

Briefly:

On the server :
1. Setup a dmcrypted drive.
Optional (for password-less script):
2. (Optional) Give the dmcrypted drive a keyfile (but store on desktop).
3. (Optional) Modify sudoers to not ask for permissions for cryptsetup, mount, umount.
4. (Optional) Setup password-less ssh login.

On the desktop (in a script):
1. Copy the keyfile (if exists) to the server (using SCP).
2. Decrypt (open) the drive on the server with the key (using SSH).
3. Delete the keyfile (if exists) from the folder over ssh (using SSH).
4. Mount the drive (using SSH).
5. Transfer files with rsync and ssh.
6. Unmount the drive (using SSH).
7. Encrypt (close) the drive.

The setup can be completely automated if the keyfile and other optional setups are done. Otherwise you'll get password prompts.

It means having a server on 24/7 with an encrypted drive that is only "available" during it's backup period, so if it's stolen, no tears.

I'll post my script once I clean it up.

---

### Post by Steve413z on 2008-05-23
try "duplicity"

[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)

it's in the Ubuntu repositories

---

### Post by Steve413z on 2008-05-23
duplicity uses GnuPG to encrypt your backups, you can have it use public key encryption or symmetric encryption, and it supports SSH transfers, it's very nice, it's been around for a long time, but not many people know about it

---

### Post by hyper_ch on 2008-05-23
is there a reason to not fully encrypt the server also? Only at bootup you'd have to enter the password...

---

### Post by jonthysell on 2008-05-23
> **Steve413z said:**
> try "duplicity"

[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)

it's in the Ubuntu repositories

I'll have to check it out. It would probably be easier than what I have (even though the script works).

---

### Post by Dr Small on 2008-05-23
> **hyper_ch said:**
> is there a reason to not fully encrypt the server also? Only at bootup you'd have to enter the password...
Just a question from a curious mind, How would you enter the password on a headless server? which as he says, is so.

---

### Post by hyper_ch on 2008-05-23
you don't reboot a server ;)

And the server might be at his some attached with keyboard

---

### Post by jonthysell on 2008-05-23
> **hyper_ch said:**
> you don't reboot a server ;)

And the server might be at his some attached with keyboard

I currently have physical access to the server, but that's not always the case (it's in California and I upgraded it from Debian sarge to etch while I was living in East Africa over SSH). Soon I'll be living out of state again.

True, the only time the server is down is after power outages, but it is in California, and with the summer coming, it will happen at least once.

Currently it boots headless fine, the most I can expect is to have someone power cycle it if necessary.

---

### Post by Dr Small on 2008-05-23
> **hyper_ch said:**
> you don't reboot a server ;)

And the server might be at his some attached with keyboard
That isn't always the case with mine. There have been lots of times I have rebooted my (development) server. Also, we have some pretty vilolent storms around here, which also requires powering it down.

If I were to encrypt the whole drive, I don't see how I could enter the password to unlock the drive without plugging a keyboard and monitor into it.

Lucky for me though, my server sets right beside my desk :)

---

### Post by Steve413z on 2008-05-23
duplicity would be perfect for you, because I currently backup my data to a server via SSH, and I like the backups to be encrypted because the server is off-site.

duplicity
1. splits files into manageable file sizes
2. uses rsync to make make incremental backups small
3. encrypts files using GnuPG (either password, or public key)
4. transfers files via: scp/ssh, ftp, rsync, HSI, WebDAV, and Amazon S3

---

### Post by honeydew on 2008-05-23
rsyncrypto.. scriptable seemless and lightweight.  

[http://rsyncrypto.wiki.sourceforge.net/](http://rsyncrypto.wiki.sourceforge.net/)

---

### Post by jonthysell on 2008-05-23
> **jonthysell said:**
> 
On the server :
1. Setup a dmcrypted drive.
Optional (for password-less script):
2. (Optional) Give the dmcrypted drive a keyfile (but store on desktop).
3. (Optional) Modify sudoers to not ask for permissions for cryptsetup, mount, umount.
4. (Optional) Setup password-less ssh login.

On the desktop (in a script):
1. Copy the keyfile (if exists) to the server (using SCP).
2. Decrypt (open) the drive on the server with the key (using SSH).
3. Delete the keyfile (if exists) from the folder over ssh (using SSH).
4. Mount the drive (using SSH).
5. Transfer files with rsync and ssh.
6. Unmount the drive (using SSH).
7. Encrypt (close) the drive.

The setup can be completely automated if the keyfile and other optional setups are done. Otherwise you'll get password prompts.

It means having a server on 24/7 with an encrypted drive that is only "available" during it's backup period, so if it's stolen, no tears.


I've attached the shell script I made, one version that transfers a keyfile to decrypt the remote volume, one that just prompts for a password.

rsync+ssh+dmcrypt&keyfile and a well managed /etc/sudoers means complete automation. I appreciate any feedback on the scripts (they're pretty short).

I misspoke/understood before when I said I want "incremental" backups: what I want is the rsync method of only transferring what is saved to update the remote files, not a "base" backup with a chain of compressed diffs (ala tar).

So that means duplicity is out.

As for rsyncsrypto:

"Rsyncrypto does, however, do one thing differently. It changes the encryption schema from plain CBC to a *slightly modified version*. This modification ensures that two almost identical files, such as the same file before an after a change, when encrypted using rsyncrypto and the same key, *will produce almost identical encrypted files*. This means that both objectives can be achieved simultaneously."

Ummm, makes me nervous.

---

### Post by userid on 2008-06-04
my server has 1 encrypted partition, which i mount after boot. its got a luks password container in there. the partition is thus always mounted and could be breached if someone entered the headless server without interrupting the power supply. i think this is ratehr unlikely though.

---


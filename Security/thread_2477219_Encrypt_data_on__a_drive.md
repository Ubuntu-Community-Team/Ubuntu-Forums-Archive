---
title: "Encrypt data on  a drive?"
date: 2022-07-18
forum: Security
---

### Post by Elmi77 on 2022-07-18
Hi,

I have a server which shares a directory via SSH. This works well, this directory is mounted using SSHFS on all my Windows and Linux boxes.

Now the problem is: while the transmission of the data to and from that server is secure, they are not really secure on the server itself - as they are stored there completely unencrypted. So I'm looking for a solution to encrypt the data on that SSH-share so that nobody on the server can read them but only the clients that make use of SSHFS:


[LIST]
[*]BitLocker would do the job but is not available for Windows
[*]VeraCrypt is extremely buggy (no auto-mount of encrypted drives, random error messages when mounting an encrypted remote file, UI permanently forgets all settings which once have been done)
[/LIST]

So...can anybody recommend a local encryption solution which works smoothly (like BitLocker) but is available for windows AND Linux?

Thanks!

---

### Post by TheFu on 2022-07-18
Wrong forum.

LUKS is the way to encrypt storage on Linux, but the storage cannot be accessed while it isn't 'opened" using cryptsetup.  Once it is 'opened' normal Unix permissions apply, so anyone with access, like anyone with sudo, can access the unlocked storage, reading everything.

Encryption is to protect storage at rest, not storage that has been mounted and is being accessed by **any** userid.  This applies to all encrypted storage, including the other tools that you've mentioned.

You can setup LUKS containers to be opened at boot using a passphrase, challenge-response, or by using a file that is available on unencrypted storage or USB storage, if you like.  The first two will prevent booting of the system until the correct data is entered.
If you want the storage NOT to be mounted, except on-demand, then only sudo/root can do that.

[Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) explains how to setup a flash drive with LUKS encryption.  Or you can read the cryptsetup manpage, which is always a good idea.

Lastly, whenever using any encryption, be 100% certain you have excellent backups and know how to restore the data, since a small logical issue with the encryption header will prevent access to the data 100%. There aren't any back doors. Encryption looks like random data without the ability to open/unlock the encryption.  I'm using 'open' because that's the cryptsetup option.  There's a cryptsetup 'close' option when you are done, but remember to mount and umount the file system to prevent corruption.

---

### Post by Elmi77 on 2022-07-19
Sounds good...but is not available for Windows? There seems to be only LibreCrypt, which is not further deeloped for several years now.

---

### Post by TheFu on 2022-07-19
I wouldn't use Windows.  The EULA is privacy-sucking, so no encryption would be secure in my mind.

But what would Windows have to do with encrypted storage on a Linux system?  You've lost me there.

---

### Post by Elmi77 on 2022-07-20
But I am using Windows and I have to use Windows!

As explained in my question: the drive is mounted via SSHFS on both, my Linux-Systems and my Windows-Systems. And as both have to access this drive in the same way, I need an encryption solution for both.

---

### Post by Irihapeti on 2022-07-20
*Thread moved to **Security**, since it's a support request.*

---

### Post by kpatz on 2022-07-20
Is this server hosting the sshfs share a Windows or Linux server?

Normally the encryption would be handled there, but encrypting data on a drive just protects the data while it sits on the drive.  It has to be unlocked (decryptable) in order to be able to access the data in any way (via a share or otherwise).  Encryption using bitlocker, veracrypt or LUKS is just a layer between the physical/logical volume and the filesystem, that encrypts the data blocks as they are written and decrypts them as they are read.  This encryption would prevent someone from rebooting the machine with a live OS and accessing the data, or physically removing the drive and accessing the data on it elsewhere.  Someone who can physically log in to the server (via ssh, rdp etc.) could access the encrypted data as long as the encrypted volume is open and mounted and their login has the necessary permissions, the same as on an unencrypted volume/drive.

Also, Bitlocker is included with Windows (maybe only on Pro and higher?)  My Windows work PC has its drive encrypted with it.

---

### Post by TheFu on 2022-07-20
> **Elmi77 said:**
> But I am using Windows and I have to use Windows!

As explained in my question: the drive is mounted via SSHFS on both, my Linux-Systems and my Windows-Systems. And as both have to access this drive in the same way, I need an encryption solution for both.

A windows client can mount an unlocked LUKS encrypted store over ssh, just like any other client. Then you can mount it using sshfs.  On Linux, you could setup a method via the ~/.ssh/config settings to almost automate those steps. Perhaps Windows can do the same?

The fact that the storage is connected to a Linux system is what matters, not what the client machine runs.

---

### Post by C.S.Cameron on 2022-07-21
What about 7Zip or P7Zip to encrypt the individual file or directory?

---

### Post by TheFu on 2022-07-21
If you know in advance that you'll be transmitting a file, you can use magic wormhole as a secure transfer method between many different systems without having control over the routers.  Using it requires forethought, since the "sender" has to be setup and running with the file to be transferred before the receiver can accept the file.  There aren't any size limitations that I've seen with wormhole and I've transferred 35GB of data using it.

The ZIP-based tools can be used, but know that there are flaws in the encryption that make brute force attacks possible.  I have a ZIP cracking tool that can brute force any 12 character or less password in less than a week, usually less than a day, if I apply a dictionary attack.  Also, PeaZIP is probably the desired tool, since it can handle more ZIP file flavors than the others.  When transferring data with my accountant, we use PeaZIP because anything actually secure was just too hard for them to understand.  What is the saying, "perfect is the enemy of good enough"?  Sure, financial data is sensitive, but it isn't a national secret (and I won't go to jail for leaking it). I know that ZIP encryption was never considered secure enough to be used by DoD, but if we are transferring Mom's special potato salad recipe, it is probably good enough.

There are options like encfs, encryptfs, and a few others, but those have known metadata leakage issues and have been deprecated for 5-7 yrs in Ubuntu.  People do still use them and if those tools meet your needs, fine.  EXT4 and ZFS have added built-in encryption too. That can be considered, though the ext4 version is very much alpha-code.  All of these would require the same "open" of the encrypted container then mounting of the file system before accessing it. Again, all of this can be automated - really just 2-3 commands which could be run from a remote system over an ssh connection.  Just be certain to umount file system and 'close' the encrypted container when done.

---


---
title: "encrypting as much of filesystem as possible"
date: 2008-01-30
forum: Server Platforms
---

### Post by pytheas22 on 2008-01-30
I am searching for an encryption solution for use on both Ubuntu and Windows that would encrypt as much of the system as possible, up to the whole system partition.  I am not sure that this can be done, but it would be ideal if it could.  I know that I can easily create an encrypted folder within someone' s directory, but I would rather encrypt as much of the system as possible, because I don't trust the users whom I'm supporting to always save sensitive data to the encrypted partition; it would be better if all of the data that they could save were automatically sent to an encrypted directory.  For the same reasons of end-user incompetence, it would be ideal for the mounting of encrypted directories to be as seamless as possible.

The next best option to encrypting the entire system filesystem would be to encrypt all of /home or \Documents and Settings, and have the appropriate sub directories automatically mounted (after prompting for a password) after the relevant user logs in.  I think that this should definitely be feasible with enough work (e.g. I think that I could do it by writing a lot of scripts), but I would appreciate suggestions on setting this up with as little labor as possible.

I've done a lot of research, and Truecrypt is the avenue I'm taking now; I just need to figure out how to get it to do what I need.  I am open to other options (open-source preferred) is someone has a better idea than Truecrypt.

Any suggestions on the best way to get these things done are much appreciated.

---

### Post by CyberDean on 2008-01-30
I have also been looking at TrueCrypt, but having trouble understanding the complete concept.  Here is a statement from the internet.

TrueCrypt real-time file encryption

TrueCrypt is an open-source encryption software that enables you to create a virtual encrypted disk within a file and mount it as a virtual disk, that can be accessed via a drive letter. Any file that is stored on this virtual drive is automatically encrypted on-the-fly, and can only be accessed while the drive is mounted with the correct password or key. TrueCrypt supports a variety of encryption algorithms, including AES-256, Blowfish (448-bit key), CAST5, Serpent, Triple DES, and Twofish. Other features include support for FAT32 or NTFS formatting, hidden volumes, hotkeys for mounting/dismounting and more. 

The new release is scheduled for Feb 4, 2008.  I'm going to keep my eye on this release and this thread.

---

### Post by pytheas22 on 2008-01-31
Truecrypt itself I understand...it's just a program to encrypt data, and in order to access the encrypted data, you have to mount the partition or volume through Truecrypt.  It provides an extremely high amount of security, especially if you use the "hidden volume" feature, which means creating an encrypted partition inside an encrypted partition.  The idea is that that way, even if someone were to put a gun to your head and demand the password, they would get into the first partition but would still never even know that the second one existed, so your data would be safe.  You can give it a try; truecrypt is pretty straight-forward, especially in Windows where it has a good GUI.  There's supposed to be a GUI for Linux called forcefield, but I've never used it.

The major issue with streamlining truecrypt, especially for incompetent end-users, is that some amount of user interaction is required to mount the volume.  And when it comes to encrypting the whole filesystem, the big problem is that you need to figure out a way to run truecrypt in order to unencrypt your system partition before you start booting the system; otherwise it would be unreadable and unable to boot.  I've been reading that this can be done in different ways, so I'll see how it sorts out.  Basically I think that I will need to create a small boot partition that's capable of running truecrypt (which will also require some kind of operating system to run on top of, of course), and boot the real system from there.  The concept is simple; implementing it is trickier.

---

### Post by UbuWu on 2008-01-31
[http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

---

### Post by UbuWu on 2008-01-31
[https://help.ubuntu.com/community/?action=fullsearch&value=encryptedfilesystem&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&value=encryptedfilesystem&titlesearch=Titles)

---


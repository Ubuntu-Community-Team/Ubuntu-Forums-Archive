---
title: "How do I Change the Root Password?"
date: 2011-08-18
forum: Security
---

### Post by Entyrion on 2011-08-18
Hello, I'm not a Linux or Ubuntu expert, though I do like using 11.04 on my old laptop. Unfortunately the other evening an annoying security risk came to my attention. A friend of mine who apparently knows more about Linux than I was able to bypass the user login process completely and log into my Ubuntu laptop as root. When I asked how he did it, spammed one of the F- keys during startup, which brought him to a text-based command prompt where he logged in as root by guessing the password. He claimed that I had left the root pw set at the default.

As you can see, this was rather annoying and I would like to fix it. How can I change the root and/or sudo passwords to completely prevent something like this in the future?

Thanks in advance.

---

### Post by collisionystm on 2011-08-18
lock/disable the root account with sudo passwd -l root

then change your user account password. sudo passwd username

---

### Post by bodhi.zazen on 2011-08-18
This question comes up all the time.

Physical access is root access with any operating system.

Setting a root password will not help.

Likewise setting a BIOS or grub password adds very little. Sure it will stop casual intruders, but that is about it.

Your best option IMO would need to encrypt the entire installation, or at least your data / home directory. This can be done from the alternate CD.

To answer your question, Ubuntu uses sudo, see:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2011-08-18
> **collisionystm said:**
> lock/disable the root account with sudo passwd -l root

then change your user account password. sudo passwd username

None of that will help as the "cracker" simply booted into recovery mode.

---

### Post by collisionystm on 2011-08-18
so let's say you set a root password, would you have to enter that in recovery mode? or would recover still present the root account with no password

---

### Post by wojox on 2011-08-18
By default root account is locked under Ubuntu. Are you sure he didn't boot of a Live-CD?

Did you personally activate the root account?

---

### Post by sisco311 on 2011-08-18
EDIT: I'm a little bit slow today. :) 


[thread=989517]Physical access is root access.[/thread] ;)



He probably just booted in *single user mode (a.ka.a recovery mode)*.

In Ubuntu, by default, the root account password is locked, hence sulogin is patched to allow you to boot in recovery mode without being prompted for the root password. See: [uhelp]community/RootSudo[/uhelp]

My suggestions:
[list]
[*] Learn more about Ubuntu's security model, start with the sticky in the Security forum.

[*] Once again, physical access is root access, so simply, don't let him or any untrusted user to access your computer. 

[*] encrypt your data and if you want to restrict others from using your computer, then encrypt the root partition as well.

[/list]

---

### Post by zealibib slaughter on 2011-08-18
Recovery mode doesn't require a password, on grub 1 you could password protect recovery mode, I don't know if thats possible in grub 2 but it may be worth investigating.

---

### Post by eveg on 2011-08-18
> **collisionystm said:**
> so let's say you set a root password, would you have to enter that in recovery mode? or would recover still present the root account with no password
 
 
no, no, no! you do not want the root account enabled!
if your root account is not enabled (as it isn't by default in ubuntu), you are not nearly as vulnerable to online 'crackers'. a root account is the first thing they'll look for, and no matter how good your password is, they can crack it, faster than you'd think. 
physical access is root access. anyone who has access to your computer, is in the same room with it ( or the same general vicinity if it's a laptop), has root access. 
 
far better to only have to protect your machine from people with physical access, than the entire weird wide web.
 
p.s. and what sisco 311 said. the more you learn, the better things work.

---

### Post by collisionystm on 2011-08-19
Gotcha. It all makes sense now... lol.

Here is a thread on password protecting GRUB2

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by cariboo on 2011-08-19
> **collisionystm said:**
> Gotcha. It all makes sense now... lol.

Here is a thread on password protecting GRUB2

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

Again having physical access to the computer allows anyone that knows what they are doing to have complete access to your system. The only way to keep your data safe is to encrypt your home directory

---

### Post by zealibib slaughter on 2011-08-19
> **cariboo907 said:**
> Again having physical access to the computer allows anyone that knows what they are doing to have complete access to your system. The only way to keep your data safe is to encrypt your home directory
 
 
Having physical access to the computer means having access to your data.  Doesn't matter if you encrypt the home directory or not.  There are ways around encryption, here is just an example: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
 
The best defense would be to password protect the bios and grub and encrypt the partition, but ultimately physical access with enough time means no security.

---

### Post by bodhi.zazen on 2011-08-19
> **zealibib slaughter said:**
> Having physical access to the computer means having access to your data.  Doesn't matter if you encrypt the home directory or not.  There are ways around encryption, here is just an example: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
 
The best defense would be to password protect the bios and grub and encrypt the partition, but ultimately physical access with enough time means no security.

You can not mount an encrypted home directory without the password or the "mount phrase".

---

### Post by zealibib slaughter on 2011-08-19
> **bodhi.zazen said:**
> You can not mount an encrypted home directory without the password or the "mount phrase".
 My point isn't there is a way to completely bypass the encryption but the fact that all passwords can be brute forced and one method of getting the mount passphrase is to decrypt /home/username/.ecryptfs/wrapped-passphrase which is done with the login password, which can be gained via brute force if the person has enough time.

---

### Post by cariboo on 2011-08-19
It takes a lot less time to reset the bios password, than it does to brute-force an encryption passphrase. Even on a laptop, it only takes 5 - 10 minutes to reset the bios, even if you have to remove the keyboard first.

---

### Post by handy on 2011-08-20
I've not used encrypted partitions, though they bring a few questions to mind. The one that concerns me most of all, is are they reliable?

I've seen quite a few threads in this forum over the years with people having terrible trouble with encrypted drives.

Are there strategies to recover from the failure of an encrypted drive quickly?

Do you need to use Clonezilla to keep backups of the encrypted partitions for quick recovery in the event of failure in one area or another that would make your data unrecoverable?

---

### Post by bodhi.zazen on 2011-08-20
> **handy said:**
> I've not used encrypted partitions, though they bring a few questions to mind. The one that concerns me most of all, is are they reliable?

I've seen quite a few threads in this forum over the years with people having terrible trouble with encrypted drives.

Are there strategies to recover from the failure of an encrypted drive quickly?

Do you need to use Clonezilla to keep backups of the encrypted partitions for quick recovery in the event of failure in one area or another that would make your data unrecoverable?

That is the downside of encryption. It makes backup and data recovery difficult to impossible. If you loose your password you loose your data.

---

### Post by Dave_L on 2011-08-20
> **bodhi.zazen said:**
> That is the downside of encryption. It makes backup and data recovery difficult to impossible. If you loose your password you loose your data.

A compromise is to make the backups unencrypted.  In my case, I want the files on my laptop encrypted, since if I travel with my laptop it might be lost or stolen.  But since the backups are kept inside my house, I don't feel they need to be encrypted.

---

### Post by bodhi.zazen on 2011-08-20
> **Dave_L said:**
> A compromise is to make the backups unencrypted.  In my case, I want the files on my laptop encrypted, since if I travel with my laptop it might be lost or stolen.  But since the backups are kept inside my house, I don't feel they need to be encrypted.

depending on the value of the data, backup the data to an archive, zip or tar.gz or what have you, then encrypt the archive with gpg.

---

### Post by wacky_sung on 2011-08-20
> **handy said:**
> I've not used encrypted partitions, though they bring a few questions to mind. The one that concerns me most of all, is are they reliable?

I've seen quite a few threads in this forum over the years with people having terrible trouble with encrypted drives.

Are there strategies to recover from the failure of an encrypted drive quickly?

Do you need to use Clonezilla to keep backups of the encrypted partitions for quick recovery in the event of failure in one area or another that would make your data unrecoverable?

I have the same thought as you.I actually keep an encrypted folder instead of an encrypted drive. Being paranoid does not meant it is practical. Likewise it is just a personal preferences.

---


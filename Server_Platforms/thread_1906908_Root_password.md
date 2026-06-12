---
title: "Root password"
date: 2012-01-10
forum: Server Platforms
---

### Post by miltonaguiar on 2012-01-10
Hi all,
I have a big problem.
I'm using Ubuntu Server Edition 11.04 in my work.
It was everything working fine until I try to export the users from another server.
No, I don´t know the root password (and i have activated and set the root password previously :( ) Anyone knows a way to reset the root password? It's because and don´t have any login to make log on in the system..
Please help me

best regards

milton aguiar

---

### Post by Wayne_V on 2012-01-10
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by haqking on 2012-01-10
takes 2 minutes from root console

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by miltonaguiar on 2012-01-10
> **haqking said:**
> takes 2 minutes from root console

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

But when i do that it asks for root password or CTRL D for normal mode...

---

### Post by cariboo on 2012-01-10
Use:

```
sudo -i
```

It will let you do anything that running as root will.

---

### Post by sisco311 on 2012-01-10
If your user has (full) sudo rights than you can use sudo to disable/reset the root password. For more info, check out: [uhelp]community/RootSudo[/uhelp]

If not, then you will have to boot directly in a root shell or boot a Live CD/USB to fix the issue.

---

### Post by miltonaguiar on 2012-01-11
> **Wayne_V said:**
> [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Hi,
When i try what is suggested i cannot execute the command "sudo chroot /mnt". I send a print screen attached in this message,
Any solution or suggestion?

regards..

---

### Post by miltonaguiar on 2012-01-12
> **miltonaguiar said:**
> Hi,
When i try what is suggested i cannot execute the command "sudo chroot /mnt". I send a print screen attached in this message,
Any solution or suggestion?

regards..

 Any suggestion please????

---

### Post by haqking on 2012-01-12
> **miltonaguiar said:**
> Any suggestion please????

boot to root prompt and change your root password, it wont ask you for your old one.

---

### Post by miltonaguiar on 2012-01-12
> **haqking said:**
> boot to root prompt and change your root password, it wont ask you for your old one.

And how I do that?

I'm using a live CD. I want to recover or reset the root password for ubuntu Live Server 11.04..

I have tried to do what is suggested in [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but without success :( This is very important for me... :(

---

### Post by volkswagner on 2012-01-12
When using the live cd can you browse the hard drive via Nautilus?

---

### Post by haqking on 2012-01-12
> **miltonaguiar said:**
> And how I do that?

I'm using a live CD. I want to recover or reset the root password for ubuntu Live Server 11.04..

I have tried to do what is suggested in [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but without success :( This is very important for me... :(

I already posted a link on how to go to root console.

Boot into recovery mode and choose drop to root shell prompt.

then change the password with the

```
passwd
```

command

---

### Post by volkswagner on 2012-01-12
> **haqking said:**
> I already posted a link on how to go to root console.

Boot into recovery mode and choose drop to root shell prompt.



Doesn't booting to recovery require the root password?  If it doesn't that seems like a major security hole for a Linux system.  This would allow anyone with physical access to the machine full root access.

---

### Post by haqking on 2012-01-12
> **volkswagner said:**
> Doesn't booting to recovery require the root password?  If it doesn't that seems like a major security hole for a Linux system.  This would allow anyone with physical access to the machine full root access.

Physical access is root access.

Same as always been, if you boot to a recovery CD/DVD on a system it can give you root access, physical = root.

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by volkswagner on 2012-01-12
I don't want to get off topic nor in a shooting match.

You did not answer my question. "Does booting into recovery mode via grub require a root password"?

I am fully aware of booting a live cd, but if the pc owner sets a BIOS password and disables booting via all but HD, then how will inserting a live CD gain root access?

I am trying to reduce confusion on the topic of gaining root access from grub without any user password on hand.

---

### Post by haqking on 2012-01-12
Well for the OP all they need to do is 

```
sudo passwd root
```

as they set it up in the first place

They already set one, so just reset it using sudo, if the OP is not a sudo user, then i would question why not and is it their machine, if they have sudo access then easy to fix.  if they have messed up sudo then that can be repaired also.

As for physical access, then it will always be root.  if a root password is set then yes maintenance mode will ask for it, however if you have forgotten it then (first of all get a new job ;-) or using the kernel append line init=/bin/bash, you can then run passwd.

or as already said use a boot CD to do it.

As for BIOS passwords etc they can be cracked easily using various tools, so once again physical will always be root access.

physical = root

Cheers

---

### Post by sisco311 on 2012-01-12
> **miltonaguiar said:**
> Hi,
When i try what is suggested i cannot execute the command "sudo chroot /mnt". I send a print screen attached in this message,
Any solution or suggestion?

regards..

Follow this instructions to mount your logical volume: [http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

Once it's mounted you should be able to chroot into it. 


> **haqking said:**
> boot to root prompt and change your root password, it wont ask you for your old one.

sulogin is patched in Ubuntu. It won't prompt you for the root password if the password is locked, but it will, if the root account password is enabled.

One could boot directly to a root shell without being asked for a password with the **rw init=/bin/bash** kernel parameters.

---

### Post by haqking on 2012-01-13
> **sisco311 said:**
> 

sulogin is patched in Ubuntu. It won't prompt you for the root password if the password is locked, but it will, if the root account password is enabled.

One could boot directly to a root shell without being asked for a password with the **rw init=/bin/bash** kernel parameters.

I said that in my post above you [http://ubuntuforums.org/showpost.php?p=11606023&postcount=16](http://ubuntuforums.org/showpost.php?p=11606023&postcount=16)

;-)

Cheers

---

### Post by miltonaguiar on 2012-01-13
Anny suggestion please? I don´t know what should i do.. :s

It will be necessary to reinstall everything?

---

### Post by haqking on 2012-01-13
> **miltonaguiar said:**
> Anny suggestion please? I don´t know what should i do.. :s

It will be necessary to reinstall everything?

How many more suggestions do you want ?

You have at least 3 above ?

If none of them are working then you need to provide more information such as error messages.

---

### Post by miltonaguiar on 2012-01-13
> **sisco311 said:**
> Follow this instructions to mount your logical volume: [http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

Once it's mounted you should be able to chroot into it. 




sulogin is patched in Ubuntu. It won't prompt you for the root password if the password is locked, but it will, if the root account password is enabled.

One could boot directly to a root shell without being asked for a password with the **rw init=/bin/bash** kernel parameters.
 I tray what you suggested.. but my root account is activated and when i enter the recovery mode it ask to introduce the root password or CTRL D to enter normal mode.. I have said this before in this topic

---

### Post by miltonaguiar on 2012-01-13
> **haqking said:**
> I already posted a link on how to go to root console.

Boot into recovery mode and choose drop to root shell prompt.

then change the password with the

```
passwd
```

command

I do this but it ask for password because my root account was activated.
Sorry for the message but there was some answers in this topic that I only see now because i don't have received notifications in my email ..

---

### Post by Wayne_V on 2012-01-13
You are going to have to use the live CD.  It looks like you are using an LVM root disk, which is why you had trouble with /mnt earlier.   See the instructions here:

[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

---

### Post by haqking on 2012-01-13
> **miltonaguiar said:**
> I do this but it ask for password because my root account was activated.
Sorry for the message but there was some answers in this topic that I only see now because i don't have received notifications in my email ..

and once again ;-)

If you read the posts above you will see if you have activated the root account and asks for root password you can still boot to a root shell.

See sisco311 post above.

Also so you cant logon with your usual account ? that should be a sudo account so you can just reset ?

Advice for the future, first of all dont enable the root account you dont need to, use sudo.  Also have a backup of your system.  If you running server as a server and you said for work then you need to be more careful with a production system, make backups and dont forget passwords.

Cheers

---

### Post by miltonaguiar on 2012-01-16
> **haqking said:**
> and once again ;-)

If you read the posts above you will see if you have activated the root account and asks for root password you can still boot to a root shell.

See sisco311 post above.

Also so you cant logon with your usual account ? that should be a sudo account so you can just reset ?

Advice for the future, first of all dont enable the root account you dont need to, use sudo.  Also have a backup of your system.  If you running server as a server and you said for work then you need to be more careful with a production system, make backups and dont forget passwords.

Cheers

Hi,
I have user account but the problem is that i made an export from other linux server : I export /etc/users, groups and after that i can login as any user...

---

### Post by haqking on 2012-01-16
> **miltonaguiar said:**
> Hi,
I have user account but the problem is that i made an export from other linux server : I export /etc/users, groups and after that i can login as any user...

your original question was how to reset the root account ?

there has been multiple posts telling you how to do this so have you or cant you ? if you cant then why not ?

cheers

---


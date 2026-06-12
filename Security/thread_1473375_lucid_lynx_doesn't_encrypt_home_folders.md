---
title: "lucid lynx doesn't encrypt home folders"
date: 2010-05-05
forum: Security
---

### Post by tanoloco on 2010-05-05
Hi guys,

I recently downloaded the final release of lucid lynx (ubuntu 10.04) and processed to a new fresh install on an empty partition.

Unluckly I've got some problems I cannot solve and maybe for that reason I'm thinking on keeping karmic koala waiting for them to be solved. This is my third day spent in trying to configure it out and I think I have no more time for that. So I'm here asking you an help before giving it up.

In my needs I've got:
**[COLOR=DarkRed]1.[/COLOR]** allow users to switch.
**[COLOR=DarkRed]2[/COLOR]**. encrypt some data.

In karmic no problem for that, while in lucid a lot.
[COLOR=DarkRed]**1.**[/COLOR] Switching users in lucid is a big problem on my system as I'm affected by the "blank screen bug" [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578)
and this can seriously cause data loss of the opened documents.
But this is signed as high / medium and perhaps it could be solved quickly.
This problem never affected me while using karmic.

[COLOR=DarkRed]**2.**[/COLOR] For now my needs of data encryption can be solved by using the home encryption option.
So I installed lucid creating an admin account checking the home encryption option and once finished the installation  l logged in and created other users, some of them with the command
[COLOR=Teal]sudo adduser fou --encrypted-home[/COLOR] others with the gui *User settings* tool under System > Administration > Users and groups and checking the encryption option.

In my experience none of them are working. Here is my test:
**[COLOR=DarkGreen]a)[/COLOR]** logged in as admin user (first user created while installing)
[COLOR=DarkGreen]**b)**[/COLOR] switch user to a supposed encrypted user (both using the user switcher panel applet or the indicator applet session)
[COLOR=DarkGreen]**c)**[/COLOR] switch back to admin  and try to reach the encrypted user data using an interactive sudo session and all documents are correctly decrypted (as the encrypted user is logged)
[COLOR=DarkGreen]**d)**[/COLOR] switch again to encrypted user and terminate its session (both using the user switcher panel applet or the indicator applet  session)
[COLOR=DarkGreen]**e)**[/COLOR] log again back to admin (already opened session) and find through an interactive sudo session that all the encrypted user data are still decrypted!! Only 1 time over 10 tests I found them encrypted. 
[COLOR=DarkGreen]**f)**[/COLOR] any time I found them encrypted I rebooted and logged in again as admin user (first user created while installing) and found the encrypted user data still decrypted!!

A few clarification:
**- **encrypted users are testing users created with admin / desktop / personalized privileges
**-** the interactive sudo session I use is both:
[COLOR=Purple]**>>** [/COLOR]press alt+f2 and type gksu nautillus and cd with the root window to /home/user
[COLOR=Purple]**>> **[/COLOR]or open a terminal and type [COLOR=Teal]sudo -i[/COLOR] and cd to /home/user

I googled searchng this problem but no info at all. I tried to install again lucid  with same result.
Is there anyone else affected by this behaviour? Any suggestion how to fix it? Could it be related with he blank screen bug? I mean this bug affects users session in order that they are not properly closed or suspended and results in a blank screen ...

Thanks

---

### Post by bodhi.zazen on 2010-05-05
I suggest you file a new bug report on launchpad.

---

### Post by blujay on 2010-05-05
Log in as the user in question, run $(mount), and see if the user's .Private directory is mounted with ecryptfs.

I'm using ecryptfs home folders on a fresh Lucid install with no problems.

---

### Post by tanoloco on 2010-05-06
Thank you for your reply: here is my bug report
[https://bugs.launchpad.net/ubuntu/+bug/576254](https://bugs.launchpad.net/ubuntu/+bug/576254)

blujay: my users home are correctly encrypted with ecryptfs as expected.
I logged in as admin user, switched to a test encrypted user and typed $(mount)
Here is the result
> 
/dev/sda3 on / type reiserfs (rw,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/admin-user/.Private on /home/admin-user type ecryptfs (ecryptfs_sig=68b34a4b3dd0445e,ecryptfs_fnek_sig=297c962de1db1b82,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/admin-user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=admin-user)
/dev/sdb6 on /media/dati type ext3 (rw,nosuid,nodev,acl,errors=remount-ro)
/home/test-user/.Private on /home/test-user type ecryptfs (ecryptfs_sig=8dcaaf0a865a2a74,ecryptfs_fnek_sig=a07f36675855ea72,ecryptfs_ciph]expecteder=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/test-user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=test-user)
Terminated the test-user session, switched to admin-user and opened a sudo interactive session I can cd to test-user home folder and see its data decrypted (and change them)

Thanks

---

### Post by BWET_AC on 2010-05-06
Sorry that i write in this thread but this question is related.
And sorry for my english.
I discovered that the Ubuntu lucid installer live (desktop) when you create an encrypted home directory does not create an encrypted swap partition.  It can be create manually after installation by use ecryptfs-setup-swap. Is this normal, and intentional in this release? However, Alternate installer create encrypted swap when I choose encrypted home directory. Maybe live don't create crypt swap because hibernate will not work but i can't find information about this.

---

### Post by bodhi.zazen on 2010-05-06
> **BWET_AC said:**
> Sorry that i write in this thread but this question is related.
And sorry for my english.
I discovered that the Ubuntu lucid installer live (desktop) when you create an encrypted home directory does not create an encrypted swap partition.  It can be create manually after installation by use ecryptfs-setup-swap. Is this normal, and intentional in this release?

This is the default behavior.

> However, Alternate installer create encrypted swap when I choose encrypted home directory. Maybe live don't create crypt swap because hibernate will not work but i can't find information about this.

Well, between the desktop and alternate CD you are using different methods.

Desktop -> ecryptfs -> encrypts home

Alternate -> uses LVM and LUKS -> encrypts everything but /boot

---

### Post by tanoloco on 2010-05-07
About swap encryption I would like to ask some guru out there which really could be the advantage of encrypting the swap for a "normal" user (no nasa woker and so on) if I noticed that in my case the use of swap partition is always 0%???

:confused:


Talking about home folder encryption is quite the same questionr: do you really think it's  so important to encrypt the whole home folder?

:confused:

My case is that I need to encrypt only some data (passwords, pin numbers, private documents and so on of me and some other users).
I used the home encryption because it is offered during installation / creation of new user and it's easy to "check and use" ... but after the problem I suffered (lucid doesn't encrypt homes at least on my system) I took again manuals and studied again encfs encryption and now I can affirm it's enough for my needs:
1. I can create private encrypted folders very easily
2. I've understood how to create a shared encrypted folder (a need I sometimes have and that yes took me a while)
[http://ubuntuforums.org/showthread.php?t=1420413](http://ubuntuforums.org/showthread.php?t=1420413)
3. there's even a nice gui tool called cryptkeeper (even if it crashes on my system when switching user)
[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/575918](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/575918)


So ... my quick solution of this problem (lucid doesn't encrypt homes) will be to reinstall it again without homes encrypted and to use encfs for any encryption needs I may have.

I think it's enough or am I wrong?
What can I gain more in encrypting the whole home or/and encrypting the swap-file (0% used!!!)

Thanks

---

### Post by bodhi.zazen on 2010-05-07
> **tanoloco said:**
> About swap encryption I would like to ask some guru out there which really could be the advantage of encrypting the swap for a "normal" user (no nasa woker and so on) if I noticed that in my case the use of swap partition is always 0%???

:confused:


Talking about home folder encryption is quite the same questionr: do you really think it's  so important to encrypt the whole home folder?

:confused:

My case is that I need to encrypt only some data (passwords, pin numbers, private documents and so on of me and some other users).
I used the home encryption because it is offered during installation / creation of new user and it's easy to "check and use" ... but after the problem I suffered (lucid doesn't encrypt homes at least on my system) I took again manuals and studied again encfs encryption and now I can affirm it's enough for my needs:
1. I can create private encrypted folders very easily
2. I've understood how to create a shared encrypted folder (a need I sometimes have and that yes took me a while)
[http://ubuntuforums.org/showthread.php?t=1420413](http://ubuntuforums.org/showthread.php?t=1420413)
3. there's even a nice gui tool called cryptkeeper (even if it crashes on my system when switching user)
[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/575918](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/575918)


So ... my quick solution of this problem (lucid doesn't encrypt homes) will be to reinstall it again without homes encrypted and to use encfs for any encryption needs I may have.

I think it's enough or am I wrong?
What can I gain more in encrypting the whole home or/and encrypting the swap-file (0% used!!!)

Thanks

Everyone has his or her opinion, there is no universal strategy.

The pieces I think you are missing w/ an encrypted $HOME are the configuration files (.bashrc , .ssh, .gnome, etc) as well as the ability for somebody else to install something in to $HOME.

Some people may feel the need to protect even those files as well.

---

### Post by tanoloco on 2010-05-07
I see but setting permissions to home folders to 700 isn't enough?
Only the owner and sudoers could alter them in that way and sudoers might be admins .. trusted people .. :/

---

### Post by Agent ME on 2010-05-07
Permissions are for preventing other users of the system from accessing files that they shouldn't be able to. Filesystem encryption isn't for this. Filesystem encryption is for preventing someone who has direct access to the hard drive from accessing files they shouldn't be able to.

---

### Post by bodhi.zazen on 2010-05-07
> **agent me said:**
> permissions are for preventing other users of the system from accessing files that they shouldn't be able to. Filesystem encryption isn't for this. Filesystem encryption is for preventing someone who has direct access to the hard drive from accessing files they shouldn't be able to.

+1

And for restricting access from untrusted Admins. For example, I trust my sys admin to perform sys admin, but not my personal banding. So I don ot want them to have access to my FF passwords / bank account.

As a sys admin, if I do not have access to sensitive info, I can not be accused of embezzlement, so it can be a win-win. Of course this implies a certain amount of trust with users as well, so trust runs both ways.

---

### Post by BWET_AC on 2010-05-08
> **bodhi.zazen said:**
> This is the default behavior.



Well, between the desktop and alternate CD you are using different methods.

Desktop -> ecryptfs -> encrypts home

Alternate -> uses LVM and LUKS -> encrypts everything but /boot

Sorry bodhi.zazen but you are little wrong. In Alternate I can in pirtition stage uses LVM and LUKS -> encrypts everything but /boot (using dm-crypt) but I can also use ecryptfs -> encrypts home. When I create example 2 partitions / and swap and installer come to a stage of configuring the user account it asks if I want to encrypt the home directory (this stage is the same stage what is in desktop installer and use ecryptfs) check yourself.

The only difference between alternate and desktop installer is that desktop installer don't use ecryptfs-setup-swap (sorry if I mistake the name). In ubuntu 9.10 they create.

Or it is a bug or intended functionality (because of problems with hibernation because ecryptfs-setup-swap creates a random password) ?????

---

### Post by tanoloco on 2010-05-08
Thanks guys for explaining me your idea on using permissions or/and decryption.
Basically I agree. I'm only thinking over how useful is home folders (and swap) encryption.

If you trust your sudoers then setting  permissions correctly is enough.

If you don't tust your sudoers, then save sensitive info in an encrypted home is not safe!
Let me show you how a hooker sudoer could see your data encrypted in your home in 5 min.

Let's say that poor-users store his/her sensitive data blank as they are in his/her home folder
and feel safe because they are encrypted.
Let's say that in his/her office they need the intervention of an external sys admin who has full privileges (sudo account)  and they don' trust this sys admin just because he/she's external but they feel safe because they encrypt their home folders.
But this sys-admin has read this how-to on ubuntuforums and will steal their data!

1. run any live cd who gives you root access like ubuntu live cd or partition magic (quicker boot from ram) or any you want (the quicker the better).
2. mount the ubuntu partition and backup /etc/shadow and /etc/shadow~
3. reboot and login ubuntu as your sudoer user
4. change the password of any user you want to steal data.
5. switch to this user using the new password.
6. logging in the encrypted home will automatically decrypt them so you can cd the user home and steal any data you want for example copying them to an usb pen drive.
7. when finished just reboot your live-cd
8. mount the ubunu partition and restore  /etc/shadow and /etc/shadow~
9. reboot and start ubuntu. now any user will have back again his/her original password and will not know that they have been hooked.

This takes 5 minutes!

So: if you don't trust your sudoers you better learn how to use encfs.

You can set permissions correctly and if any user wants or needs to store some data in a safe place just create an encfs encrypted folder for him/her.
No way to decrypt or to change password without knowing the current one as long as I know.
No way to restore encrypted data even if the user forgets his/her password as long as I know.

:guitar:

---

### Post by OpSecShellshock on 2010-05-08
> **tanoloco said:**
> Thanks guys for explaining me your idea on using permissions or/and decryption.
Basically I agree. I'm only thinking over how useful is home folders (and swap) encryption.

If you trust your sudoers then setting  permissions correctly is enough.

If you don't tust your sudoers, then save sensitive info in an encrypted home is not safe!
Let me show you how a hooker sudoer could see your data encrypted in your home in 5 min.

Let's say that poor-users store his/her sensitive data blank as they are in his/her home folder
and feel safe because they are encrypted.
Let's say that in his/her office they need the intervention of an external sys admin who has full privileges (sudo account)  and they don' trust this sys admin just because he/she's external but they feel safe because they encrypt their home folders.
But this sys-admin has read this how-to on ubuntuforums and will steal their data!

1. run any live cd who gives you root access like ubuntu live cd or partition magic (quicker boot from ram) or any you want (the quicker the better).
2. mount the ubuntu partition and backup /etc/shadow and /etc/shadow~
3. reboot and login ubuntu as your sudoer user
4. change the password of any user you want to steal data.
5. switch to this user using the new password.
6. logging in the encrypted home will automatically decrypt them so you can cd the user home and steal any data you want for example copying them to an usb pen drive.
7. when finished just reboot your live-cd
8. mount the ubunu partition and restore  /etc/shadow and /etc/shadow~
9. reboot and start ubuntu. now any user will have back again his/her original password and will not know that they have been hooked.

This takes 5 minutes!

So: if you don't trust your sudoers you better learn how to use encfs.

You can set permissions correctly and if any user wants or needs to store some data in a safe place just create an encfs encrypted folder for him/her.
No way to decrypt or to change password without knowing the current one as long as I know.
No way to restore encrypted data even if the user forgets his/her password as long as I know.

:guitar:

Well of course this holds. The first thing anyone should understand in any information security issue (and the first thing anyone says in discussions on these boards) is that physical access lays the whole thing wide open. However, in the workplace the enterprise is the owner of the equipment and the data. It doesn't matter if the end user trusts the system administrators or not. If a system administrator has been granted full privileges, then it's clearly at the behest of the management. Also, I don't think you'd get much management support for an encryption method that can't be undone by someone other than the end user, not least because users forget or change passwords all the time or need to recover data following a mechanical failure of the disk. However, in those situations the end users are probably not going to be the ones installing the OS in the first place, so no big deal.

At home, on your own equipment, it's much easier to restrict physical access. If a device is mobile (for example a laptop) then it's probably better to keep sensitive (by each user's own definition of the word) data somewhere other than the disk where the OS resides.

As an aside, I think a lot of users are encrypting their data somewhat out of proportion to the actual risk, but on top of that it seems as though many of them undermine the encryption by leaving their computers booted up all the time.

---

### Post by bodhi.zazen on 2010-05-09
> **BWET_AC said:**
> Sorry bodhi.zazen but you are little wrong. In Alternate I can in pirtition stage uses LVM and LUKS -> encrypts everything but /boot (using dm-crypt) but I can also use ecryptfs -> encrypts home. When I create example 2 partitions / and swap and installer come to a stage of configuring the user account it asks if I want to encrypt the home directory (this stage is the same stage what is in desktop installer and use ecryptfs) check yourself.

The only difference between alternate and desktop installer is that desktop installer don't use ecryptfs-setup-swap (sorry if I mistake the name). In ubuntu 9.10 they create.

Or it is a bug or intended functionality (because of problems with hibernation because ecryptfs-setup-swap creates a random password) ?????

I was referring to the default encryption options.

You are correct, one can use ecryptfs to encrypt ones $HOME directory on either the Desktop or Alternate CD, however, if you wish to get technical there are many differences between the Desktop and Alternate CD.

The desktop CD does not offer LVM or LUKS, for example.

Personally I do not see much of a need to use LUKS and encrypt one's home directory with ecryptfs, but I supose there are those who do so ...

One can NOT encrypt the /boot partition with either LUKS or ecryptfs (well, you can, but you will not be able to boot from an encrypted /boot partition).

---


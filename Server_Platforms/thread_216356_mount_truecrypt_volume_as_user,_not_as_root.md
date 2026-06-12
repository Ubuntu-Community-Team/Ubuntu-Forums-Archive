---
title: "mount truecrypt volume as user, not as root"
date: 2006-07-15
forum: Server Platforms
---

### Post by matthew on 2006-07-15
I've been playing around with the Linux version of TrueCrypt (v4.2a). I can create volumes, open them, close them, etc, but I can't seem to figure out how to open them as any user except root. Here's what I know so far. If anyone sees something I'm missing, please tell me. Thanks!

First, some links for those who want/need them.

main truecrypt site
[http://www.truecrypt.org/](http://www.truecrypt.org/)

truecrypt man page/linux documentation
[http://www.truecrypt.org/user-guide/linux-manpage.php](http://www.truecrypt.org/user-guide/linux-manpage.php)

Okay. Here's what I have done.
```
truecrypt -c
``` brings up a series of questions that help you create a truecrypt volume. I have tried most of the various answers.

```
truecrypt /home/matt/cryptname /home/matt/mountpoint
```is supposed to mount the encrypted volume "cryptname" at the location I specify "mountpoint." However, this returns an error saying only root may open encrypted volumes so I use
```
sudo truecrypt /home/matt/cryptname /home/matt/mountpoint
```and everything works exactly as expected, except I can only write to and read from the mounted volume as root (i.e. using sudo, gksudo nautilus, sudo su to become root, etc). From here I began reading the documentation (linked above) and thought I had found the answer. As user "matt" I tried```
truecrypt -u /home/matt/cryptname /home/matt/mountpoint
```and was told again that only root can mount a truecrypt volume. Okay, I thought. Root mounts it but specifies a user...no problem. However,```
sudo truecrypt -u /home/matt/cryptname /home/matt/mountpoint
```mounts the container as root again. This does the same thing```
sudo truecrypt --user-mount /home/matt/cryptname /home/matt/mountpoint
``` Just to be sure I had the syntax correct I tried the following but they all return errors:```
sudo truecrypt -u matt /home/matt/cryptname /home/matt/mountpoint
sudo truecrypt /home/matt/cryptname /home/matt/mountpoint -u
sudo truecrypt --user-mount matt /home/matt/cryptname /home/matt/mountpoint
``` My feeling is that my problems are probably the result of one of the following. 

First, I'm using sudo to mount because I am required to be root. Is it possible that I could mount properly from a proper root terminal using -u? Let's find out...nope, no joy. I am root so mounting with the -u just mounts as...you guessed it, root.

Second, I can only specify to create a FAT volume or "no filesystem" when creating the volume. I can't seem to get volumes made without specifying a filesystem to mount at all, and FAT does not have journalling and permissions like an ext2/3, reiser, NTFS, etc.

Third option: I'm missing something in my reading of the man page (same as the html documentation I linked to above). Anyone have any ideas??? Has anyone else been successful at mounting a truecrypt volume so that once it is mounted it works like any other drive owned by a specific, non-root user??

EDIT: this was a long question. If you've read this far, thank you! Even if you can't help, that was kind of you. :)

EDIT2: I'm posting this is the security area because I figured that if anyone in these forums would know about truecrypt it would be people interested in security.

---

### Post by matthew on 2006-07-15
I had been searching and searching for an answer, couldn't find one, so I posted a thread. Then what happens? I find the answer! Here it is. I needed to add this at the end of the mount command
```
--mount-options 'umask=000,uid=1000,gid=100'
```which would make the whole mount line```
sudo truecrypt /home/matt/cryptname /home/matt/mountpoint --mount-options 'umask=000,uid=1000,gid=100'
```What this does is mount the volume with write permission, as the first user (who happens to be me), in the first group.

Thanks to this thread where I found the answer: [http://ubuntuforums.org/showthread.php?t=94652](http://ubuntuforums.org/showthread.php?t=94652)

---

### Post by chownsb on 2006-07-20
Awesome!  Thanks for figuring this out.  I had the same little issue with it.  I am now wondering if there is any way to mount Truecrypt volumes without having to use the sudo command.  If many users were using a machine and wanted to mount their own volumes they would not have access to the root password.  Just curious.

---

### Post by matthew on 2006-07-20
> **chownsb said:**
> I am now wondering if there is any way to mount Truecrypt volumes without having to use the sudo command.  If many users were using a machine and wanted to mount their own volumes they would not have access to the root password.  Just curious.As far as I can tell there is no way to mount without being root. It seems that is how the program was written intentionally.

I'm glad my earlier discovery was helpful for someone else, though.

---

### Post by NobodySpecial on 2006-07-22
My original answer was incorrect.  The correct answer is from Zar below.

---

### Post by rottex on 2006-07-24
or simply put this in /etc/sudoers file

Cmnd_Alias TCMOUNT = /usr/batch/TC_mount.cmd, /usr/batch/TC_umount.cmd
[COLOR="blue"](your_username)[/COLOR] localhost=NOPASSWD: TCMOUNT

--------------------------------
for convenience or newbiea or too get a clue here are the actions and scripts to mount a file on my usbstick. 

to get always the same mountpoint from udev for the usbstick and do not have to worry when or where I put the stick in ;-) I add:

US=="scsi", KERNEL=="sd?1", SYSFS{model}=="USB DISK Pro", NAME="usbstick"

to my /etc/udev/rules.d/10-udev.rules file

then create the batchfiles:
touch /usr/batch/TC_mount.cmd
touch /usr/batch/TC_umount.cmd
chmod 700 /usr/batch/TC_mount.cmd
chmod 700 /usr/batch/TC_umount.cmd
chown root:root /usr/batch/TC_mount.cmd
chown root:root /usr/batch/TC_umount.cmd

/usr/batch/TC_mount.cmd could look like this:
==============================================================

MEDIA_SOURCE=usbstick                <--- replace this to your needs
CRYPT_CONTAINER=___encryptedfile.tc  <--- replace this to your needs
MEDIA_MOUNT_POINT=___CRYPT_SAFE      <--- replace this to your needs

#Check if we have an mount point
if [ -d /media/${MEDIA_MOUNT_POINT} ] ; then
        echo "Target /media/${MEDIA_MOUNT_POINT} found."
  else
        echo "Target not found,  createing /media/${MEDIA_MOUNT_POINT}"
        /usr/bin/mkdir /media/${MEDIA_MOUNT_POINT}
        if [ -d /media/${MEDIA_MOUNT_POINT} ] ; then
            echo "Target /media/${MEDIA_MOUNT_POINT} ok. setting rights/ownership..."
        else
            echo Could not create mountpoint ! Exiting.
            exit 1
        fi
fi

truecrypt /media/usbstick/${CRYPT_CONTAINER}  /media/${MEDIA_MOUNT_POINT} \\ --mount-options 'umask=007,uid=[COLOR="RoyalBlue"]1000[/COLOR],gid=[COLOR="RoyalBlue"]1004[/COLOR]'

==============================================================

Note: 
uid=1000  -> put here YOUR uid in 
guid=1004  -> put here YOUR guid in 
you can get it with:
 cat /etc/passwd | grep (your username)
 cat /etc/group | grep (your username):

set the umask to 007 so only you and the group you specified can read the unencrypted content !! ](*,) 

/usr/batch/TC_umount.cmd could look like this:

MEDIA_MOUNT_POINT=___CRYPT_SAFE      <--- replace this to your needs

#Check if we have an mount point
if [ -d /media/${MEDIA_MOUNT_POINT} ] ; then
 echo "Target /media/${MEDIA_MOUNT_POINT} found."
 echo "unmounting..."
 /usr/bin/truecrypt -d /media/${MEDIA_MOUNT_POINT}
 echo "remove mointpoint ..."
 rmdir /media/${MEDIA_MOUNT_POINT}
else
 echo "Target /media/$MEDIA_MOUNT_POINT not found."
 echo "check if carrier medium exists ?!"
 /bin/mount | /bin/grep mapper
fi

---

### Post by Zar on 2006-07-27
There is a much simpler way:
Do this once: sudo chmod u+s /usr/bin/truecrypt
And then a non-root user can open the volume: truecrypt -u /volume /mountpoint

---

### Post by popie on 2006-07-27
Hmmm. I couldn't get Truecrypt to do anything... I kept getting an error relating to the kernal. 

The TC docs mention requirements for the kernal being made for TC (can't remember the details). I'm using the latest 686 kernal. Is that the problem?

---

### Post by odieman on 2008-02-18
Nice help with chmod u+s. Thanks for that.

But I do wonder, how to use truecrypt in environment, where you can't get root permissions or sudo.
Lot's of companies, cafeterias etc, are locking their PCs for obvious security reasons, so there is no chance to get a root, or sudo access.
In that case IMHO there is no way how to mount a device, therefore no way to mount a truecrypt volume/file - is it true?
Does anyone know how to make that work?
Or simply find some other software which just encrypts files as files and not as volumes? Perhaps something like password protected .zip file :-)

---

### Post by opus on 2008-02-19
Truecrypt requires admin permissions on any system it runs on because it essentially is a mediator between the OS and the underlying filesystem.  When the OS (Linux in this case) has to read from an encrypted volume created by TrueCrypt, it essentially needs a driver to do it.  In order to load a driver you have to be root.  

Aaron

---

### Post by odieman on 2008-02-20
@ opus

Yep, I've informed myself, just wanted to be 100% sure, that there is no "mage" out there who might thought of some workaround.
The only thing I can think of, is to use some different software for file encryption, for example KeePassX [http://www.keepassx.org/](http://www.keepassx.org/) is not bad and this is just a LINUX port of KeePass [http://keepass.info/](http://keepass.info/) for Windows, MacOS etc... so wherever you go, you should be able to open your database with passwords and files :-).

---

### Post by skralljt on 2008-03-27
Just wondering, if I try the chmod u+s trick and then get this error when trying to use truecrypt by the commandline:

"truecrypt

(process:10704): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+."

...how should I chmod /usr/bin/truecrypt to be how it used to be???!!

---


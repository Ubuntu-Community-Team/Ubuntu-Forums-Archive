---
title: "[SOLVED] How Do I Boot Up a Remote Server With Encrypted File System?"
date: 2008-03-22
forum: Security Discussions
---

### Post by MountainX on 2008-03-22
**UPDATE:**
The solution is to use a keyfile on a USB flash disk. One guide is listed here:
[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

**UPDATE 2**

There is one small change required for this guide to work with Ubuntu.

I lused modprobe In Ubuntu Hardy and I found these modules :
/lib/modules/2.6.24-12-server/kernel/fs/nls/nls_iso8859-1.ko
/lib/modules/2.6.24-12-server/kernel/fs/nls/nls_cp437.ko

Therefore, in /etc/initramfs-tools/modules  I used these modules:

vfat
fat
nls_cp437
nls_iso8859-1

(The only difference from the original guide being a dash in the last name instead of an underscore.)


NOTE: I have two encrypted volumes (using two separate keyfiles) and the guide above details how to set it up for one volume and one keyfile. I managed to adapt it for use with two key files, but it isn't the most elegant adaptation. I simply doulbled everything, including the shell script. I have two shell scripts that differ only by the name of the key file. This is a bad practice.** If someone knows how, please tell me how to use a single script for two different key files.** Thanks.

**_UPDATE 3_** - From the author of the original guide

I'm glad it worked and that you found the guide useful. :-)

As for the keyfile, well, you can use the "key" parameter in
/etc/crypttab to differentiate among those keys. Check the
"part three" ([http://tinyurl.com/2qs9dy](http://tinyurl.com/2qs9dy)) under the crypttab
dump for more info. Essentially you'll set it up like this:

sda2_crypt /dev/disk/by-uuid/XXX first.key luks,keyscript=/usr/local/sbin/keyscript.sh
sdb1_crypt /dev/disk/by-uuid/YYY second.key luks,keyscript=/usr/local/sbin/keyscript.sh

and it should work just fine. Because the "key" parameter
(third on the line in crypttab) gets passed to keyscript.sh
as $1 and is used internally by the script to determine keyfile.
Btw, I'm using the "root.key" as an default when the script
gets "none" or empty string as this parameter.

Regards,
           Michal

_Original question:_

I am setting up a NAS device (file server) running Hardy beta. It has two 3Ware RAID controllers, and each one is set up as an encrypted volume. Together they are managed by LVM. I'm just in the process of installing Hardy now.

How will I be able to restart this NAS server remotely? Will I be able to?

With my former Windows file server running TrueCrypt, everything would come back up fine after a remote reboot. I just want to be sure the same will be true of this Hardy file server I'm setting up. Thanks.

---

### Post by MountainX on 2008-03-22
I have Hardy installed now and my first impression is that a remote reboot isn't possible with an encrypted file system. 

Of course, I'm a noob. Hopefully I'm wrong. I would appreciate any advice.

---

### Post by HermanAB on 2008-03-22
You need to install OpenSSH for remote access.  You cannot encrypt the root drive - the system has to be able to boot on its own.  However, you can encrypt some partitions eg. /swap /home and /tmp.

When the machine starts up, it will run and fail at some point due to password timeouts.  You then need to log in with SSH and fix it, by manually remounting the failed drives.

Cheers,

Herman

---

### Post by MountainX on 2008-03-22
I have OpenSSH installed.

I did not encrypt /boot

I did encrypt /, /home and swap

Will tihs work?

To manually mount, can I just run:
sudo mount -a
?

Thanks

---

### Post by ubernoob on 2008-03-22
You won't be able to boot this machine. Since the ssh-server files is inside /. So you would have to only encrypt the /home partition, and when the system reboots, you would have to manually log in to the system and mount it. This will of course not give a good encryption as a full disk encryption.

If this is a corporate server, og you have alot of money, you should look at buying a new machine with ILO (Integrated Lights-Out). At least both Sun and HP sells it. It will give you remote access as if you were next to the machine. This connection can also be encrypted with TLS/SSL. So you will still have the security in place.

---

### Post by MountainX on 2008-03-22
This is a home file server. I built the box out of spare parts.

Normally it sits a couple hundred feet away from me, out in my garage. So rebooting would just be an inconvenience. However, if I am traveling and away from home, I will have serious problems if I need to reboot it.

I'm kinda screwed because I want the full filesystem encrypted. Maybe I should look at TrueCrypt....

Any other ideas? Can I install OpenSSH and required libs to /boot (or some other unencrypted partition)? /boot is 200 MB.

Thanks

---

### Post by ubernoob on 2008-03-22
how would truecrypt let you boot without entering the password? Then the whole idea with encryption would be useless.

> Any other ideas? Can I install OpenSSH and required libs to /boot (or some other unencrypted partition)? /boot is 200 MB.
I haven't had this problem before, but i guess there is a boot loader which you can interact with from ssh. If you use a couple of hours with google, you might get lucky! :)
Tell me if you find something.

---

### Post by MountainX on 2008-03-22
> **ubernoob said:**
> how would truecrypt let you boot without entering the password? Then the whole idea with encryption would be useless.
.
It wouldn't be any better I guess. I would have to use it to encrypt only a data partition.


> **ubernoob said:**
> 
I haven't had this problem before, but i guess there is a boot loader which you can interact with from ssh. If you use a couple of hours with google, you might get lucky! :)
Tell me if you find something.

I will put some time into that. Please suggest some google search terms for me, if you don't mind.

All I have so far is "ubuntu OR linux boot loader encryption" and I haven't found any good hits yet.

---

### Post by update_manager on 2008-03-22
> **MountainX said:**
> 
Any other ideas? Can I install OpenSSH and required libs to /boot (or some other unencrypted partition)? /boot is 200 MB.

Thanks

I think an IP KVM would work, but I wasn't able to find any affordable ones with a Google search.

---

### Post by MountainX on 2008-03-22
> **update_manager said:**
> I think an IP KVM would work, but I wasn't able to find any affordable ones with a Google search.

Interesting idea, but it definitely would be a last resort for me given the cost and the need to carry hardware around if I'm traveling.

---

### Post by MountainX on 2008-03-22
I also have another idea:
maybe I could put the decryption password on a USB stick and plug that into the file server. Then I could write a script (with help from the forum!) that would access the USB stick to decrypt the encrypted file system on boot up.
:guitar:

If this would work, it would probably be OK for me. I would just remove the USB stick when needed.

What do you guys think about this idea? If it will work, what would the script look like and where would I call it from? Thanks.

P.S. in regard to the suggestion above, here's another google search term I'm trying:
"LINUX UNIFIED KEY SETUP dm-crypt" 
source:
[http://forums.remote-exploit.org/showthread.php?t=8793&page=2](http://forums.remote-exploit.org/showthread.php?t=8793&page=2)

---

### Post by ubernoob on 2008-03-22
I didn't know that there were KVM over IP! That looks cool. I might buy one myself if i find a cheap one with SSL/TLS. :)

MountainX: you woudn't have to carry it around. You connect it to the server and access it from the network. I don't know about any good search terms either. I tried myself, and can't find what i'm looking for.

---

### Post by MountainX on 2008-03-22
> **ubernoob said:**
> 
MountainX: you woudn't have to carry it around. You connect it to the server and access it from the network.

Thanks.

> **ubernoob said:**
> 
 I don't know about any good search terms either. I tried myself, and can't find what i'm looking for.

Another search term I'm trying is "Grub boot network remote"
I'm just wondering if there is a way to let grub access another computer to get some of the info it needs to boot up... it's a vague idea, but I'm just brainstorming.

---

### Post by tact on 2008-03-22
> **MountainX said:**
> I also have another idea:
maybe I could put the decryption password on a USB stick and plug that into the file server. Then I could write a script (with help from the forum!) that would access the USB stick to decrypt the encrypted file system on boot up.
:guitar:

If this would work, it would probably be OK for me. I would just remove the USB stick when needed.

What do you guys think about this idea? If it will work, what would the script look like and where would I call it from? Thanks.

P.S. in regard to the suggestion above, here's another google search term I'm trying:
"LINUX UNIFIED KEY SETUP dm-crypt" 
source:
[http://forums.remote-exploit.org/showthread.php?t=8793&page=2](http://forums.remote-exploit.org/showthread.php?t=8793&page=2)

No need for a script to be created.   There are posts here and in the DM-CRYPT wiki that give step by step instructions how to put a key onto a USB stick.   With DM-crypt/LUKS there are multiple keyslots and you can assign one of them as the USB stick.

If you cannot find the guides let me know and I will look them up and post links.

Cheers.

Oh...  and yes this will work - letting you remotely reboot - and I do not believe it compromises your security and makes it "like you dont have any encryption at all" as someone suggested.  The reason I say this is:
Whether you are present to type in a passphrase or not (using USB stick as key) at boot time - when the machine is running unattended (as a server 100feet away in a garage or server room is) then if ANYONE can get hands on access to it (running already) then they pwn it already.

Like you mentioned when you want to shutdown the box and leave it secure then take the key with you.   Then you still have protection should someone steal the box or the HDD from it...

Cheers

---

### Post by MountainX on 2008-03-22
Perfect! Thank you. And I would appreciate some links. I've been searching already for quite some time and I didn't find those articles.

---

### Post by tact on 2008-03-22
Give this a try...  if its too brief then we look for more detailed steps for you.


[http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq](http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq)
(scroll down to the section on usb key)

---

### Post by MountainX on 2008-03-23
Thank you, but yes that was way too brief for a noob like me ;)

But it gives me some ideas of what to search for in Google now.

---

### Post by tact on 2008-03-23
a good guide is here....

[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

---

### Post by MountainX on 2008-03-23
> **tact said:**
> a good guide is here....

[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

Thank you! That looks awesome!

---

### Post by MountainX on 2008-03-23
From the guide posted by tact, I have a few questions:
1. is /dev/random better in some way than /dev/urandom? The command to produce the key never completes when I use /dev/random. 

UPDATE: See this: [http://linux.about.com/library/cmd/blcmdl4_urandom.htm](http://linux.about.com/library/cmd/blcmdl4_urandom.htm)
/dev/random blocks if it doesn't have sufficient entropy data to produce the random numbers.

2. The key generated with /dev/urandom contains non-ascii characters. It must be binary. That isn't what's shown in the guide. Should the key contain only ascii chars? 

UPDATE: I'm not using uuencode, so that's probably why I don't have ascii characters.

How can I get more entropy into /dev/random? I'd rather use it than /dev/urandom. Thanks.

---

### Post by MountainX on 2008-03-23
> **tact said:**
> a good guide is here....

[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

This is a good guide. It isn't always easy for a nooB to follow, but with a little effort this guide will help someone like me get the job done.

For my first time doing something like this, the complication of having two encrypted volumes made things a lot tougher. I still have not figured out the most elegant way to adapt the guide for use with two key files for two volumes.

Does any know how I can alter the script file to provide the correct key file for each of the two encrypted volumes? Thanks.

---

### Post by MountainX on 2008-03-23
deleted

---

### Post by MountainX on 2008-03-23
deleted

---

### Post by cdenley on 2008-03-24
> 
Oh... and yes this will work - letting you remotely reboot - and I do not believe it compromises your security and makes it "like you dont have any encryption at all" as someone suggested. The reason I say this is:
Whether you are present to type in a passphrase or not (using USB stick as key) at boot time - when the machine is running unattended (as a server 100feet away in a garage or server room is) then if ANYONE can get hands on access to it (running already) then they pwn it already.


I thought the only benefit of disk encryption was to protect your data from being read if someone had physical access. If your system is compromised remotely, whole disk encryption won't help you any. If someone has physical access, then they can only access the data if you give them the key. If you have the key on a usb drive, and leave it at the server, that would completely defeat the purpose of encryption. If someone gains physical access to the server while it is running, it would be possible to retrieve the key from memory, but very difficult.

---

### Post by MountainX on 2008-03-24
> **tact said:**
> a good guide is here....

[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

There is one small change required for this guide to work with Ubuntu.

I used modprobe In Ubuntu Hardy and I found these modules :
/lib/modules/2.6.24-12-server/kernel/fs/nls/nls_iso8859-1.ko
/lib/modules/2.6.24-12-server/kernel/fs/nls/nls_cp437.ko

Therefore, in /etc/initramfs-tools/modules  I used these modules:

vfat
fat
nls_cp437
nls_iso8859-1

(The only difference from the original guide being a dash in the last name instead of an underscore.)

Michal, thanks for the wonderful guide! I could never have accomplished this without the guide.

---

### Post by tact on 2008-03-25
> **cdenley said:**
> I thought the only benefit of disk encryption was to protect your data from being read if someone had physical access. If your system is compromised remotely, whole disk encryption won't help you any. If someone has physical access, then they can only access the data if you give them the key. If you have the key on a usb drive, and leave it at the server, that would completely defeat the purpose of encryption. If someone gains physical access to the server while it is running, it would be possible to retrieve the key from memory, but very difficult.

Whole disk encryption:   When the machine is running, i.e. you booted the machine and entered the encryption key (by typing passphrase or plugging in a usb key - doesn't matter)....the information on the disk is transparently decrypted.  Available.  There.  In the clear.  As if not encrypted at all.

No need to retrieve the key from memory or elsewhere.  Key was entered, disk decryption enabled, data now readable in the clear.  (While the machine is running).

Power off the machine....  then sure...  whole disk encryption protects you should someone get physical access to the disk.

---

### Post by hyper_ch on 2008-03-25
How about this kind of setup:

(1) encrypt your whole system
(2) add a key from a file on usb stick that's always plugged in
(3) after bootup delete that file on the usb stick (per script) while you carry that file with you on another stick or something
-------------
Now when you have to reboot then
(4) copy the file back onto your stick... as you can reboot your machine remotely you have somehow access to it
(5) for the bootup process it will use the file on the usb stick again to unlock
(6) once the bootup scripts run it will delete that file again
--------------

In this case the file isn't any longer on the stick and you just have to remember to add it before you reboot...

---

### Post by cdenley on 2008-03-25
> 
No need to retrieve the key from memory or elsewhere. Key was entered, disk decryption enabled, data now readable in the clear. (While the machine is running).

Readable to anyone who can log in. The only way they can bypass authentication would be to reboot into recovery mode, or boot to a livecd. Either one would require the encryption key to mount the encrypted partitions.

> 
In this case the file isn't any longer on the stick and you just have to remember to add it before you reboot...

You might want to zero out the USB drive at boot, otherwise the key is probably still on there. That may be a little paranoid, but so is using encryption on a server.  If you accidentally use your only remaining copy of your key, you won't be able to recover data from your server. If you make too many copies, you may leave one lying around where you shouldn't.

---

### Post by Chafnan on 2008-04-13
Just thought I would post a link to a good option.  The following link is to an article that explains how to enable ssh so that you can enter the password through it.

[HOWTO unlock LUKS encrypted root partition via ssh]("http://gpl.coulmann.de/ssh_luks_unlock.html")

---


---
title: "Recovering encrypted home folder"
date: 2010-07-19
forum: Security
---

### Post by fluffydanoob on 2010-07-19
Let's begin from the top. I have a relatively new laptop that I've been running Ubuntu on (along with a little-used Windows boot). Picked it up in November or so, installed the current "latest" version of Ubuntu at the time (9.10). I have been doing incremental upgrades, and it's been progressively breaking down more and more. Yes, this includes 10.04.

After GRUB stopped working, I decided it was time to try a reinstall from the top. I told it to leave all the other operating systems alone and do a full reinstall.

Fortunately, I had managed to stuff most of my current *work* in duplicate locations during this whole debacle, somehow. Don't ask me how I managed to do that when GRUB wasn't working. However, when I installed, I conscientiously said "Oh, yes, Ubuntu, encrypt my home folder! I love privacy!" As a result, about... 30 gigabytes of useful (but ultimately re-downloadable) material is rather inaccessible at the moment. When I try to boot the old system using the newly fixed GRUB, it goes into kernel panic. This seems like a no-go.

I have a saved hojillion-character long passphrase for decryption from my install back in November. Conscientiously saved in the case of just such an emergency.

I read [this how-to](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually) and followed it to the letter as far as I could tell, trying to mount with ecrytfs to recover my data.

[USERNAME] here is a proxy for my actual username. Yes, the location of my old home folder may seem a little bizarre. 
```
sudo mount -t ecryptfs /media/c82ca9fe-2b15-4aca-a98d-6482b1d80a32/home/[USERNAME]/ /home/[USERNAME]/oldhome
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9d2a064f5b06d4d0]: b1e63548e84d4ba2
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=b1e63548e84d4ba2
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9d2a064f5b06d4d0
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [9d2a064f5b06d4d0] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
```
I tried several variations on this theme, with the same result. Ubuntu is telling me that it's all there; I have a giant old Ubuntu operating system sitting on my desktop. Everything is clearly visible except the internal contents of the home/[USERNAME] folder within that old file system - which has those two little text files saying "NYAH NYAH NYAH YOU CAN'T GET IN!"

Now, the old system was already visible as "37 GB File System" on my desktop, so I decided to have a look-see there, as well. The home/[USERNAME] folder within contains a README.TXT file and an Access-your-private-data.desktop, neither of which Ubuntu wanted me to open. After copying it elsewhere and going through some hijinks to open the README, I read:
> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
Except, of course, trying to click the "Access your private data" file (the other file) gives the error: 
```
Untrusted application launcher 
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.
```
With no option other than to cancel, (and the contents of a copy just saying that it'll launch ecryptfs-mount-private), that's not too helpful.

The suggested command-line prompt, from within the directory, gives:
```
[USERNAME]@[COMPUTERNAME]:/media/c82ca9fe-2b15-4aca-a98d-6482b1d80a32/home/[USERNAME]$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```
Several variations later (again trying commands in numerous folders) the same error messages keep coming. I've managed to find a couple blog posts and forum threads that seem vaguely related, but that hasn't given me an understanding of what needs to be done in order to unlock a folder that doesn't seem to think it's there. So ... talk to me. How, *precisely*, can I get at this pile of useful data and save myself further headaches?

---

### Post by FuturePilot on 2010-07-19
Try this

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

---

### Post by fluffydanoob on 2010-07-20
I saw that before. It wasn't helpful.

On the off chance it might become helpful, I pulled out the live CD and waited forever for it to finish booting.
> ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - [USERNAME]
[b]keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'[/b]
[USERNAME]@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
Hm, think I, is it the wrapped or unwrapped passphrase? I had both, so I put in both. And then a few others, for good measure. No luck. Now I try what is suggested as an addendum in the event that you actually have the passphrase saved.
> [USERNAME]@ubuntu:~$ ecryptfs-add-passphrase --fnek
Passphrase: 
Error: Your kernel does not support filename encryption
... so the liveCD approach does not appear to be helpful here. Is this related to the mentioned 9.10 encryption bug mentioned in comments? The upgrade to 10.04 was rough and fraught with a number of bugs (persistent errors, particularly involving rtkit for whatever reason, dating back to the upgrade were one reason I decided I needed a fresh install; the installation process seemed to have gotten mangled). I don't know. What I do know is that it's not working.

---

### Post by fluffydanoob on 2010-07-20
Now, since it may be that the solution to this does not lie with wrangling through ecrypts manual recovery, here are the errors that I get at boot, paraphrased, in trying to boot to the /dev/sda6 operating system. If I were able to repair this, I could presumably boot into the system, log in using my regular user password, and be able to toss the odd 27 gigabytes of data into an unencrypted partition.

When trying to boot Ubuntu 10.04 LTS as seen on /dev/sda6, here are the messages leading up to kernel panic in the boot:
```
Autodetecting RAID arrays
Scanned 0 and added 0 devices
autorun...
autorun DONE.
VFS: Cannot open root device "sda6" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0.0)
```

---

### Post by COKEDUDE on 2010-09-22
I also have this same problem. I have not been able to figure out how to fix it.

---

### Post by COKEDUDE on 2010-09-22
This might do the trick. I haven't had time to test it out. 

[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

And incase you aren't familiar with terminal commands read that link. He is showing you a command here. 
```
root@ubuntu:/home/goshawk# adduser --no-create-home goshawk
```

[http://www.comptechdoc.org/os/linux/manual1/createuser.html](http://www.comptechdoc.org/os/linux/manual1/createuser.html)

---

### Post by billjoie on 2010-09-22
Hi Cokedude,

I too have had trouble with ecryptfs-mount-private, and the approach using chroot from a liveCD has always failed me.  This being said, I have been successful at manually mounting my private directories and partitions a certain number of times.  Basically, I have been following the approach in the help.ubuntu.com [howto]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually")

If this makes it a little clearer, here is a quick reminder I wrote for myself. The .Private folder will not be in the exact same location, but the procedure should still apply.  Hope this helps:


OBJECT:
	2010-08-24 -- How to manually mount an encrypted directory using ecryptfs
	 

INITIAL SITUATION:
	- Let us have Ubuntu 10.04 operation system
	- Let us have a user called /home/guest with ecrypt private directory
	- The encrypted data is in /home/guest/.Private
	- The normal mount point for the encrypted data is /home/guest/Private
	- The encryption properties and configurations are in /home/guest/.ecryptfs
	- I want to manually load the data inside the .Private folder from my /home/bill account
	- The login password for /home/guest is 'bienvenue'

1) Create mount point in your own directory:

	mkdir /home/bill/guest_private

2) Obtain the "mount passphrase" of the /home/guest/.Private

	$ sudo su
	# cd /home/bill/guest/.ecryptfs
	# ls
		auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase

	# ecryptfs-unwrap-passphrase wrapped-passphrase
		Passphrase:
			   <bienvenue>
		6a44be2be5dd9797c08e8af01451ed0a  

3) Add mount passphrase to kernel keyring

	$ $ sudo ecryptfs-add-passphrase --fnek
		Passphrase:
			<6a44be2be5dd9797c08e8af01451ed0a>
		Inserted auth tok with sig [c685836a2d202db0] into the user session keyring
		Inserted auth tok with sig [49a65b02b0ab37cb] into the user session keyring <==Use this second code for FNEK signature later
	
4) Mount: (The 1st line is somewhat different from the original tutorial, but it works I swear)
	$ sudo mount -t ecryptfs /home/guest/.Private/ /home/bill/guest_private/  
		Passphrase:
			<6a44be2be5dd9797c08e8af01451ed0a>

		Select cipher: 
		 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
		 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
		 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
		 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
		 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
		 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
		Selection [aes]: 
			<use default>

		Select key bytes: 
		 1) 16
		 2) 32
		 3) 24
		Selection [16]: 
			<use default>

		Enable plaintext passthrough (y/n) [n]: 
			<use default>

		Enable filename encryption (y/n) [n]: 
			<y>

		Filename Encryption Key (FNEK) Signature [c685836a2d202db0]: 
			<49a65b02b0ab37cb>

		Attempting to mount with the following options:
		  ecryptfs_unlink_sigs
		  ecryptfs_fnek_sig=49a65b02b0ab37cb
		  ecryptfs_key_bytes=16
		  ecryptfs_cipher=aes
		  ecryptfs_sig=c685836a2d202db0

		Mounted eCryptfs
5) That's it!

---

### Post by COKEDUDE on 2010-12-11
Has anyone had any luck?

---

### Post by DZ* on 2010-12-12
> **COKEDUDE said:**
> Has anyone had any luck?

I have Ubuntu installed on a stick where my home is encrypted. I use the following script to mount and access home on it when I put the stick into a computer that is already running linux. You'll need to type the unwrapped passphrase.

```
#!/bin/bash
##### EDIT [COLOR="Red"]PARTS IN RED[/COLOR] IN THE FOLLOWING 3 LINES
Dsk=[COLOR="Red"]/media/disk[/COLOR] # this is where the external disk is (already) mounted
Encrypted_Home=$Dsk/home/.ecryptfs/[COLOR="Red"]YourLoginDirectory[/COLOR]/.Private # location of enrypted home on the external disk
Decrypted_Home=[COLOR="Red"]/mnt/dsk[/COLOR] # this is where you will mount your Encrypted_Home (it has to exist)

echo "type your unwrapped passphrase as obtained by running ecryptfs-unwrap-passphrase"
read PassPhrase

Auth0=$(echo $PassPhrase | sudo ecryptfs-add-passphrase --fnek)
Auth=$(echo "$Auth0" | grep sig | awk '{print $6}' | sed -e 's/\[//g' -e 's/\]//g')

Sig1=$(echo $Auth | awk '{print $1}')
Sig2=$(echo $Auth | awk '{print $2}')

sudo mount -t ecryptfs $Encrypted_Home $Decrypted_Home \
-o key=passphrase:passwd=${PassPhrase},\
ecryptfs_cipher=aes,\
ecryptfs_key_bytes=16,\
ecryptfs_passthrough=no,\
no_sig_cache,\
ecryptfs_sig=$Sig1,\
ecryptfs_fnek_sig=$Sig2

```

---

### Post by Immahazmacookie on 2010-12-13
> **fluffydanoob said:**
> Let's begin from the top. I have a relatively new laptop that I've been running Ubuntu on (along with a little-used Windows boot). Picked it up in November or so, installed the current "latest" version of Ubuntu at the time (9.10). I have been doing incremental upgrades, and it's been progressively breaking down more and more. Yes, this includes 10.04.

After GRUB stopped working, I decided it was time to try a reinstall from the top. I told it to leave all the other operating systems alone and do a full reinstall.

Fortunately, I had managed to stuff most of my current *work* in duplicate locations during this whole debacle, somehow. Don't ask me how I managed to do that when GRUB wasn't working. However, when I installed, I conscientiously said "Oh, yes, Ubuntu, encrypt my home folder! I love privacy!" As a result, about... 30 gigabytes of useful (but ultimately re-downloadable) material is rather inaccessible at the moment. When I try to boot the old system using the newly fixed GRUB, it goes into kernel panic. This seems like a no-go.

I have a saved hojillion-character long passphrase for decryption from my install back in November. Conscientiously saved in the case of just such an emergency.

I read [this how-to](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually) and followed it to the letter as far as I could tell, trying to mount with ecrytfs to recover my data.

[USERNAME] here is a proxy for my actual username. Yes, the location of my old home folder may seem a little bizarre. 
```
sudo mount -t ecryptfs /media/c82ca9fe-2b15-4aca-a98d-6482b1d80a32/home/[USERNAME]/ /home/[USERNAME]/oldhome
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9d2a064f5b06d4d0]: b1e63548e84d4ba2
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=b1e63548e84d4ba2
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9d2a064f5b06d4d0
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [9d2a064f5b06d4d0] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
```
I tried several variations on this theme, with the same result. Ubuntu is telling me that it's all there; I have a giant old Ubuntu operating system sitting on my desktop. Everything is clearly visible except the internal contents of the home/[USERNAME] folder within that old file system - which has those two little text files saying "NYAH NYAH NYAH YOU CAN'T GET IN!"

Now, the old system was already visible as "37 GB File System" on my desktop, so I decided to have a look-see there, as well. The home/[USERNAME] folder within contains a README.TXT file and an Access-your-private-data.desktop, neither of which Ubuntu wanted me to open. After copying it elsewhere and going through some hijinks to open the README, I read:

Except, of course, trying to click the "Access your private data" file (the other file) gives the error: 
```
Untrusted application launcher 
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.
```
With no option other than to cancel, (and the contents of a copy just saying that it'll launch ecryptfs-mount-private), that's not too helpful.

The suggested command-line prompt, from within the directory, gives:
```
[USERNAME]@[COMPUTERNAME]:/media/c82ca9fe-2b15-4aca-a98d-6482b1d80a32/home/[USERNAME]$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```
Several variations later (again trying commands in numerous folders) the same error messages keep coming. I've managed to find a couple blog posts and forum threads that seem vaguely related, but that hasn't given me an understanding of what needs to be done in order to unlock a folder that doesn't seem to think it's there. So ... talk to me. How, *precisely*, can I get at this pile of useful data and save myself further headaches?
If you are trying to recover it, if you have the cash that is, take it into a professional and have them do it. It may cost, but it's better than you trying to do it and accidentally screwing it up even more.

---

### Post by COKEDUDE on 2010-12-16
> **DZ* said:**
> I have Ubuntu installed on a stick where my home is encrypted. I use the following script to mount and access home on it when I put the stick into a computer that is already running linux. You'll need to type the unwrapped passphrase.

```
#!/bin/bash
##### EDIT [COLOR="Red"]PARTS IN RED[/COLOR] IN THE FOLLOWING 3 LINES
Dsk=[COLOR="Red"]/media/disk[/COLOR] # this is where the external disk is (already) mounted
Encrypted_Home=$Dsk/home/.ecryptfs/[COLOR="Red"]YourLoginDirectory[/COLOR]/.Private # location of enrypted home on the external disk
Decrypted_Home=[COLOR="Red"]/mnt/dsk[/COLOR] # this is where you will mount your Encrypted_Home (it has to exist)

echo "type your unwrapped passphrase as obtained by running ecryptfs-unwrap-passphrase"
read PassPhrase

Auth0=$(echo $PassPhrase | sudo ecryptfs-add-passphrase --fnek)
Auth=$(echo "$Auth0" | grep sig | awk '{print $6}' | sed -e 's/\[//g' -e 's/\]//g')

Sig1=$(echo $Auth | awk '{print $1}')
Sig2=$(echo $Auth | awk '{print $2}')

sudo mount -t ecryptfs $Encrypted_Home $Decrypted_Home \
-o key=passphrase:passwd=${PassPhrase},\
ecryptfs_cipher=aes,\
ecryptfs_key_bytes=16,\
ecryptfs_passthrough=no,\
no_sig_cache,\
ecryptfs_sig=$Sig1,\
ecryptfs_fnek_sig=$Sig2

```

I'm not very good at writing shellscripts but I think you should add this line to your shellscript. This command will help you find the **.Private directory**. There is sometimes a broken symlink. 

```
sudo find / -type d -iname '.Private' 2>/dev/null
```

---


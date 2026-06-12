---
title: "Mount .ecryptfs file"
date: 2012-07-26
forum: Security
---

### Post by topher83 on 2012-07-26
Hi

I recently had a VHD file go corrupt on a VirtualBox VM running ubuntu
I have managed to run a recovery program and got a load of files from this however the home directory was encrypted
I have a few .ecryptfs files from the recovery and I know the password used however I am unable to recover the data (Not really sure if im doing it right)

-----------------

sudo mkdir /mnt/crypt
sudo mount -t ecryptfs b13600744.eCryptfs /mnt/crypt
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (loaded)
 2) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 3) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 4) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [fbc2d5c3151701c4]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=fbc2d5c3151701c4
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=fbc2d5c3151701c4
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [fbc2d5c3151701c4] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-20] Not a directory
Check your system logs; visit <http://launchpad.net/ecryptfs>

-----------------

Im either going the wrong way about mounting a .ecryptfs file given only the passphrase or somethings wrong with the way im mounting the file

Can anyone point me in the right direction

Thanks

---

### Post by topher83 on 2012-07-27
The syslog says
Jul 27 18:29:12 Topher-LI mount.ecryptfs: Failed to perform eCryptfs mount: [Not a directory]
Jul 27 18:29:12 Topher-LI kernel: [ 6847.640069] Reading sb failed; rc = [-20]

And the kern.log says
Jul 27 18:29:12 Topher-LI kernel: [ 6847.609883] ecryptfs_mount: kern_path() failed
Jul 27 18:29:12 Topher-LI kernel: [ 6847.640069] Reading sb failed; rc = [-20]

---


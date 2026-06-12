---
title: "Recovering Encrypted Home Partition"
date: 2010-05-03
forum: Security
---

### Post by 1awesomeguy on 2010-05-03
I had some major problems after the recent Ubuntu upgrade and had to boot from a live cd. I have a separate /home partition, but it was encrypted using the default install encryption in the 9.10 install cd. How can I get to my files so I can back them up?

I have tried this but it did not work: [http://ubuntuforums.org/showthread.php?t=1337693](http://ubuntuforums.org/showthread.php?t=1337693)

---

### Post by 1awesomeguy on 2010-05-04
I've tried this solution (from [this page]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")):

```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:~$ su - kirkland
kirkland@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Inserted auth tok with sig [xxx] into the user session keyring
kirkland@ubuntu:~$ cd $HOME
kirkland@ubuntu:~$ ls -alF
...
kirkland@ubuntu:~$ cat .profile
...
```

I get stuck on the second line:
```
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
```

My system says there is no directory called /mnt/dev. The same is true for /mnt/dev/shm, /mnt/proc, and /mnt/sys. If I continue further chroot does not work either:

```
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
```


My /home, /boot, /, and swap are all separate partitions if that makes any difference.

Any help would be really appreciated.

---

### Post by 1awesomeguy on 2010-05-04
I also tried what I found [here]("http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/"). Still no luck...

```
$ sudo aptitude install ecryptfs-utils
$ cd /mnt
$ sudo mkdir OldHome

$ sudo ln -s /media/3e8ea0ac-xxxx-xxxx-a35a-8ff17406fdb8/home/user/.Private OldPrivate

$ sudo ecryptfs-add-passphrase --fnek
Passphrase:
Inserted auth tok with sig [xxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring

$ sudo mount -t ecryptfs OldPrivate OldHome/
Passphrase:
Select cipher:
1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]:
Select key bytes:
1) 16
2) 32
3) 24
Selection [16]:
Enable plaintext passthrough (y/n) [n]:
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [xxxxxxxxxxxxxxx]: yyyyyyyyyyyyyyyy
Attempting to mount with the following options:
ecryptfs_unlink_sigs
ecryptfs_fnek_sig=yyyyyyyyyyyyyyyy
ecryptfs_key_bytes=16
ecryptfs_cipher=aes
ecryptfs_sig=xxxxxxxxxxxxxxx
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [zzzzzzzzzzzzzzzz] to
[/root/.ecryptfs/sig-cache.txt]
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
```

---

### Post by cariboo on 2010-05-04
Did you try creating the missing directories in /mnt?

---

### Post by 1awesomeguy on 2010-05-04
> **cariboo907 said:**
> Did you try creating the missing directories in /mnt?

Thanks. I figured out what was the error with the missing file names, but am still having problems. I did this because my /home partition is on a separate partition:

```
ubuntu@ubuntu$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu$ sudo mount /dev/sda4 /mnt/home
ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu$ sudo chroot /mnt
root@ubuntu$ su - kirkland
keyctl_searchL Required key not available
Perhaps try the interactive 'encryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" fr details.

kirkland@ubuntu$ ecryptfs-add-passphrase --fnek
Passphrase:
Error: Your kernel does not support filename encryption
kirkland@ubuntu$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [xxx] into the user session keyring
keyctl_search:Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
   cd /home/kirkland

kirkland@ubuntu$ cd /home/kirkland
kirkland@ubuntu$ ls -a
```

All files displayed start with "ECRYPTFS_FNEK_ENCRYPTED..."

I also tried doing this without the "ecryptfs-add-passphrase --fnek" command, but get the same problem.

Any suggestions would be very appreciated. I have been at this non-stop since yesterday...

---

### Post by DZ* on 2010-05-04
In your last post you omitted sudo. That's why you get "Your kernel does not support filename encryption"

Also, do you have the file /home/.ecryptfs/user/.ecryptfs/Private.sig ? Try both values from that file as "Sig=" (see below)

When experimenting with new values, do "sudo keyctl clear @u; sudo umount /path/to/Oldhome" prior to new attempts

You can put the mounting commands in a script and run that
```

Dsk=/media/ZZZZZZZ
PassPhrase=XXXXXXXXXXXXX
Sig=YYYYYYYYYYYYYY

echo $PassPhrase | sudo ecryptfs-add-passphrase --fnek

sudo mount -t ecryptfs $Dsk/home/.ecryptfs/dz/.Private /mnt/dsk \
-o key=passphrase:passwd=${PassPhrase},\
ecryptfs_cipher=aes,\
ecryptfs_key_bytes=16,\
ecryptfs_passthrough=no,\
no_sig_cache,\
ecryptfs_fnek_sig=$Sig

```

---

### Post by 1awesomeguy on 2010-05-04
Thanks DZ, but no luck using sudo. Same problem:

```
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - user
keyctl_searchL Required key not available
Perhaps try the interactive 'encryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" fr details.

user@ubuntu:~$ sudo ecryptfs-add-passphrase --fnek
sudo: unable to resolve host ubuntu
Passphrase:
Error: Your kernel does not support filename encryption
```

I do have the folder /home/.ecryptfs/user/.ecryptfs/ but it is locked. I have my phasephrase from when I wrote it down earlier. I also have the user's log in password. I am not sure how to use your script or if it applies in my situation. Any help would be appreciated. I'm just interested in getting to my information once so I can backup my data. I would feel a lot more comfortable working in terminal.

---

### Post by DZ* on 2010-05-04
But you were able to 'sudo ecryptfs-add-passphrase --fnek' before, and got
"Inserted auth tok with sig [xxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring"
What changed?

Nevermind my suggestion to look into '/home/.ecryptfs/user/.ecryptfs/Private.sig'. It has those two values from the output above, xxxxxxxxxxxxxxx, yyyyyyyyyyyyyyyy. The ecryptfs_fnek_sig value is the second one, yyyyyyyyyyyyyyyy.

As for the script, that's how I mount my encrypted accounts (save commands to a File, chmod +x File, run as ./File from terminal). Obviously, you'd need to change first 3 lines and 'dz/.Private /mnt/dsk' piece to your values.

---

### Post by 1awesomeguy on 2010-05-04
> **DZ* said:**
> But you were able to 'sudo ecryptfs-add-passphrase --fnek' before, and got
"Inserted auth tok with sig [xxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring"
What changed?

Nevermind my suggestion to look into '/home/.ecryptfs/user/.ecryptfs/Private.sig'. It has those two values from the output above, xxxxxxxxxxxxxxx, yyyyyyyyyyyyyyyy. The ecryptfs_fnek_sig value is the second one, yyyyyyyyyyyyyyyy.

As for the script, that's how I mount my encrypted accounts (save commands to a File, chmod +x File, run as ./File from terminal). Obviously, you'd need to change first 3 lines and 'dz/.Private /mnt/dsk' piece to your values.

Thanks for all your help DZ. I tried two completely different things above. The first from post 2 and 5 involved me mounting to /mnt. The second from post 3 involved me creating symbolic links. They are slightly different, but I am still a newbie at this so you probably can tell more from looking at the outputs.

I tried using your executable, but am having some problems also...

_My modifications of your file:_
```
Dsk=/media/12345abcd-1234-1234-1234-123456abcdefg
PassPhrase=123456abcdef
Sig=yyyyyyyyyyyyyyyy

echo $PassPhrase | sudo ecryptfs-add-passphrase --fnek

sudo mount -t ecryptfs $Dsk/home/.ecryptfs/chris/.Private /mnt \
-o key=passphrase:passwd=${PassPhrase},\
ecryptfs_cipher=aes,\
ecryptfs_key_bytes=16,\
ecryptfs_passthrough=no,\
no_sig_cache,\
ecryptfs_fnek_sig=$Sig
```

_Output from file:_
```
ubuntu@ubuntu:~/Desktop$ ./mounter
Passphrase: 
Inserted auth tok with sig [xxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=yyyyyyyyyyyyyyyy
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=xxxxxxxxxxxxxxx
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
```

EDIT: I get the same exact output when using 'sudo ./mounter'

---

### Post by DZ* on 2010-05-04
Can you access these locations prior to running 'mounter' (from the same terminal)?

sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg
sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private
sudo ls /mnt

I think the problem might be that you have 'chroot'-ed to /mnt .

---

### Post by 1awesomeguy on 2010-05-04
> **DZ* said:**
> Can you access these locations prior to running 'mounter' (from the same terminal)?

sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg
sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private
sudo ls /mnt

I think the problem might be that you have 'chroot'-ed to /mnt .

Thanks DZ for your continual assistance. I am not sure how to check if I have 'chroot'-ed to /mnt, but I did restart the computer just now to try it again. I am getting the same problem. Below is the output for the ls commands. It seems like the .Private directory cannot be accessed because it is a locked directory. I can navigate in Nautilus up until /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/  I can see the .Private directory, but it has an X on it.

_ls command output_
```
ubuntu@ubuntu:~/Desktop sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg
chris lost+found
ubuntu@ubuntu:~/Desktop sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private
ls: cannot access /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private: No such file or directory
ubuntu@ubuntu:~/Desktop sudo ls /mnt
ubuntu@ubuntu:~/Desktop 
```

EDIT: I am running all this from a live cd as I cannot boot up normally. I am afraid to install Ubuntu over my current install until I back up my data.

---

### Post by DZ* on 2010-05-04
> **1awesomeguy said:**
> 
```
ubuntu@ubuntu:~/Desktop sudo ls /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private
ls: cannot access /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris/.Private: No such file or directory
```

Well, this seems to be the problem. 
I'd try to ```
sudo -i
``` to switch to root and cd to /media/12345abcd-1234-1234-1234-123456abcdefg/home/.ecryptfs/chris

Then check (ls -la) permissions of .Private. Can you cd to it?

If it is something funny, change to, say 'chmod 755 .Private' and if you can cd to it now, try to run the script again.

---

### Post by 1awesomeguy on 2010-05-05
Thanks again DZ. I did what you said:
sudo -i, then cd to .../.ecryptfs/chris directory

Permisions
.Private: drwx--x--x
.ecryptfs:  drwx------

I first changed .Private to 755 and tried ./mounter. It failed. Same error. I then, changed .ecryptfs and again ./mounter failed... I also tried 'sudo ./mounter'.

I can now navigate in Nautilus inside the .Private directory though all files are encrypted.

_Output from ./mounter_
```
ubuntu@ubuntu:~/Desktop$ ./mounter
Passphrase: 
Inserted auth tok with sig [xxxxxxxxxxxxxxx] into the user session keyring
Inserted auth tok with sig [yyyyyyyyyyyyyyyy] into the user session keyring
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=yyyyyyyyyyyyyyyy
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=xxxxxxxxxxxxxxx
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
```

Anyone know what is going on here? I've been at this for two days already. Any help would be really appreciated! :(

---

### Post by 1awesomeguy on 2010-05-05
> **1awesomeguy said:**
> I've tried this solution (from [this page]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")):

```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:~$ su - kirkland
kirkland@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Inserted auth tok with sig [xxx] into the user session keyring
kirkland@ubuntu:~$ cd $HOME
kirkland@ubuntu:~$ ls -alF
```

My /home, /boot, /, and swap are all separate partitions if that makes any difference.

Any help would be really appreciated.


I completed these steps again and am able to mount my /home directory, but all files and directories begin with ECRYPTFS_FNEK_ENCRYPTED... and cannot be read.

I also tried adding in this before the ecryptfs-mount-private step:

```
ecryptfs-add-passphrase --fnek
Passphrase:
Error: Your kernel does not support filename encryption
```

Same error as when I started.

---

### Post by DZ* on 2010-05-05
See if this helps --
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709)

---

### Post by 1awesomeguy on 2010-05-05
> **DZ* said:**
> See if this helps --
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709)

Thanks a bunch DZ! After many many hours, I have solved my problem.

The exact solution that helped was [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709/comments/3](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709/comments/3)

_By Dustin Kirkland:_
> Martin-

Okay, try this ...

```
ecryptfs-unwrap-passphrase /home/.ecryptfs/kirkland/.ecryptfs/wrapped-passphrase
(record this as your MOUNTPW)

keyctl clear @u
keyctl list @u
(should be empty)
ecryptfs-insert-wrapped-passphrase-into-keyring /home/.ecryptfs/kirkland/.ecryptfs/wrapped-passphrase
keyctl list @u
(should see 2 sigs, one for file contents, one for filenames)
SIG1=$(head -n1 /home/.ecryptfs/kirkland/.ecryptfs/Private.sig)
SIG2=$(tail -n1 /home/.ecryptfs/kirkland/.ecryptfs/Private.sig)
mount -t ecryptfs -o rw,relatime,ecryptfs_fnek_sig=<SIG2>,ecryptfs_sig=<SIG1>,ecryptfs_cipher=aes,ecryptfs_key_bytes=16 /home/.ecryptfs/kirkland/.Private /mnt
ls /mnt
cat /mnt/.profile
```

This is working for me... Can you give this a shot?

Note that we're using mount -t ecryptfs here, rather than mount.ecryptfs.

:-Dustin

Note (this confused me):
When asked for a Passphrase from the ecryptfs-unwrap-passphrase command, enter your user account's password, but when asked for a Passphrase from the 'mount -t ecryptfs' command, enter the output from the ecryptfs-unwrap-passphrase command.

---

### Post by kylekobe on 2010-05-06
I, too, have been trying to recover my /home for the past two days after a failed upgrade. I tried most of the steps you did (except for all that mount -o sys /mount/sys and such, I went right to ecryptfs-unwrap-passphrase) and I had been getting the same error mounting eCryptfs. I'm not sure what's so different about this method (I didn't think putting options would make that much of a difference).

Thanks a lot for the repost 1awesomeguy!

---

### Post by 1awesomeguy on 2010-05-06
> **kylekobe said:**
> I, too, have been trying to recover my /home for the past two days after a failed upgrade. I tried most of the steps you did (except for all that mount -o sys /mount/sys and such, I went right to ecryptfs-unwrap-passphrase) and I had been getting the same error mounting eCryptfs. I'm not sure what's so different about this method (I didn't think putting options would make that much of a difference).

Thanks a lot for the repost 1awesomeguy!

Try running this command before:

```
sudo su
```

If I do that, it works every time. If I don't do that, it will only work sometimes. Not sure why...

---

### Post by progone on 2010-05-23
This link is helpful

[https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

---


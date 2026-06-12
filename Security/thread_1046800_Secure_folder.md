---
title: "Secure folder"
date: 2009-01-21
forum: Security
---

### Post by coiax on 2009-01-21
Back in the days when I was an Appleite, I never really liked using one of the password manager programs, so instead I wrote down all my password in plaintext files, and put them all in a disk image. I would then, using GnuPG, encrypt the disk image to myself, and shred/srm the original file.

I've written some simple little bash scripts to do this in Ubuntu (using tar/gzip, and piping it to gpg, and then extracting the contents of the folder into the /dev/shm ram disk), but I can't help feeling that I'm going the wrong way about it by using my GnuPG private key, and my constantly extracting the files from an encrypted archive seems a bit complicated.

Is there someway I can put my sensitive files inside some file/folder/partition/whatever, and mount and demount it on demand (with some form of GOOD security, preferably, and without having to overwrite the free space with endless amount of data from /dev/random)?

---

### Post by Dr Small on 2009-01-21
I can't say that I can help you, but I basically do the same thing; only I don't tar/untar the file. I wrote a little script called 'ged' (GnuPG EDitor) which allows me to decrypt a GPG file that has been encrypted with my public key, decrypts it to /tmp allows you to edit it with $EDITOR, saves it, encrypts it, and removes the temporary file.

I really never saw it as a hassle, as I don't like big bulky password managers, but to have my passwords easily accessible from the command line.

I've attached the script. I know that's not what you want, but maybe you'll find it useful ;) (Just remove .sh, drop it in your $PATH, and it should be ready to go :))

---

### Post by hyper_ch on 2009-01-22
problem is, if you first save the file and then encrypt it there are potential left-overs of it in your system. Shredding won't do much good here.

---

### Post by Tubes6al4v on 2009-01-22
Are you trying to protect the passwords from someone who has physical access to your computer?

I don't know, but I wonder if indexing filesystems could leave traces of the passwords around. Or perhaps in SWAP. hmm, just something to think about.


Edit: hyper_ch beat me to it.

---

### Post by amac777 on 2009-01-22
Here is a tutorial of how to make an encrypted directory using EncFS:

[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

If you don't like the command line, there is also a GUI based program to handle it as well called crypt-manager.

---

### Post by The Cog on 2009-01-22
That's a lot of messing around. I dropped these two script files in /usr/local/bin to make the encrypted directory easy to mount and unmount. The scripts have names that even a dummy like me can remember:

file /usr/local/bin/crypton:
> encfs ~/.crypt ~/crypt

file /usr/local/bin/cryptoff:
> fusermount -u ~/crypt

So the commands to mount/unmount are **crypton** and **cryptoff**. The files appear in ~/crypt, and the encrypted ones are in ~/.crypt. 

I use it to keep a spreadsheet of my usernames/passwords, and some VPN access key files.

---

### Post by coiax on 2009-01-22
> **amac777 said:**
> Here is a tutorial of how to make an encrypted directory using EncFS:

[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

If you don't like the command line, there is also a GUI based program to handle it as well called crypt-manager.
I'm assuming that this won't leave any traces of the unencrypted file on the hard drive itself?

Also, what about encrypted partitions? How do they work?

---

### Post by hyper_ch on 2009-01-22
if you want security from physical access and don't want to get invovled with where is what saved, are all traces deleted etc. then it's simplest to re-install a fully encrytped system.

However as soon as you start using an encrypted contair/partition/system then it's also mandatory have backups of your data. As you know, hardware migth fail and if the harddisk fails at a critical point then you could lose access to all your data.

---

### Post by amac777 on 2009-01-22
> **coiax said:**
> I'm assuming that this won't leave any traces of the unencrypted file on the hard drive itself?


That may not be a correct assumption. It is true that EncFS itself won't purposely write any copies of the unencrypted files on the hard drive. However, other programs might. For example, if you open the file in an application that makes backups of the files in another (non-encrypted) directory, or if you open the file and while it's in memory the file is saved to an (unencrypted) swap partition for some reason. So there are some potential holes.

That said, if you are not worried about these holes, EncFS does offer a very convenient way to have an encrypted directory. You can put as many files and other directories in the encrypted directory and it will all automatically encrypted as well. Also, you don't need to pre-reserve any space so it's very efficient in that regard as well.

---


---
title: "How to identify you have created an encrypted folder / home directory"
date: 2010-08-17
forum: Security
---

### Post by wacky_sung on 2010-08-17
Lately i just reformatted my laptop again and created a encrypted home drive using the default.It prompt for my password and then i key it into the terminal.Then the terminal closed it.How to justify that the home drive is encrypted and decrypted during login?Beside that,if it is encrypted and what kinda extension is drive gonna?

Apart from that,i used cryptkeeper to create a encrypted folder.How do i know if the folder is encrypted beside it prompt for me to enter my password?

Thank.

---

### Post by bodhi.zazen on 2010-08-17
for /home , boot to recovery mode and try to read the files in your users home.

for your other directory, try to read the data without entering your password for the encrypted directory.

---

### Post by wacky_sung on 2010-08-17
I have boot it into recovery and saw the home directory.The thing is that i cannot getting in nor prompt for a password to enter.Is that what you meant by encrypted home?Thank.

---

### Post by cariboo on 2010-08-17
That's exactly what bodhi.zazen meant. You should only be able to access an encrypted directory if you are logged as the owner.

---

### Post by bodhi.zazen on 2010-08-17
With ecryptfs, you can access the directory, but none of the data or sub directories.

There are 3 files, one is .Private, the others are text files giving instructions on how to decrypt your data.

---

### Post by wacky_sung on 2010-08-17
> **bodhi.zazen said:**
> With ecryptfs, you can access the directory, but none of the data or sub directories.

There are 3 files, one is .Private, the others are text files giving instructions on how to decrypt your data.

Can show me what is the command using ecryptfs or any tutorial to it?Thank.

---

### Post by bodhi.zazen on 2010-08-17
> **wacky_sung said:**
> Can show me what is the command using ecryptfs or any tutorial to it?Thank.

Here is the output of ssh into a server with an encrypted home :

```
bodhi@ufbt:~$ ls       
Access-Your-Private-Data.desktop  README.txt

bodhi@ufbt:~$ ls -la                                          
total 12
dr-x------ 3 bodhi bodhi 4096 2010-06-06 00:42 .
drwxr-xr-x 4 root  root  4096 2010-07-16 22:40 ..
lrwxrwxrwx 1 bodhi bodhi   56 2010-06-06 00:39 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 bodhi bodhi   31 2010-06-06 00:39 .ecryptfs -> /home/.ecryptfs/bodhi/.ecryptfs
lrwxrwxrwx 1 bodhi bodhi   30 2010-06-06 00:39 .Private -> /home/.ecryptfs/bodhi/.Private
lrwxrwxrwx 1 bodhi bodhi   52 2010-06-06 00:39 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

bodhi@ufbt:~$ ls .Private                                    
ECRYPTFS_FNEK_ENCRYPTED.FWZII07TnvX19-QHQQuRDp5.q42D3-MsCAY0gtyygNQloJ45xRXcNe0mqU--
ECRYPTFS_FNEK_ENCRYPTED.FWZII07TnvX19-QHQQuRDp5.q42D3-MsCAY0Tfv9CYjKT5YwthXOzYKS5---
ECRYPTFS_FNEK_ENCRYPTED.FWZII07TnvX19-QHQQuRDp5.q42D3-MsCAY0AVUI-OccGmdz153UD33ynU--
 <output truncated>
```

Your output would be the same if you boot to recovery mode or mount /home on a live CD.

Furthermore 

```
bodhi@ufbt:~$ cat README.txt                                                             

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

bodhi@ufbt:~$ ecryptfs-mount-private                                                     
Enter your login passphrase:

Inserted auth tok with sig [14d05245cb92d7d4] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/bodhi

bodhi@ufbt:~$ cd                                                                        
bodhi@ufbt:~$ ls                                                                         
Downloads  Public   Desktop    Music      Templates
Documents  Pictures   Videos
```

See also 

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by wacky_sung on 2010-08-17
I saw something similiar to what you got below.

```
bodhi@ufbt:~$ ls -la                                          
total 12
dr-x------ 3 bodhi bodhi 4096 2010-06-06 00:42 .
drwxr-xr-x 4 root  root  4096 2010-07-16 22:40 ..
lrwxrwxrwx 1 bodhi bodhi   56 2010-06-06 00:39 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 bodhi bodhi   31 2010-06-06 00:39 .ecryptfs -> /home/.ecryptfs/bodhi/.ecryptfs
lrwxrwxrwx 1 bodhi bodhi   30 2010-06-06 00:39 .Private -> /home/.ecryptfs/bodhi/.Private
lrwxrwxrwx 1 bodhi bodhi   52 2010-06-06 00:39 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

```

Thank i will read your tutorial.Appreciated for your help and attention.

---


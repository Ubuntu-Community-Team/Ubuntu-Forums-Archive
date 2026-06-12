---
title: "Cryptkeeper does not mount folder."
date: 2012-10-07
forum: Security
---

### Post by Cushie on 2012-10-07
I am using Ubuntu12.04 “cryptkeeper” package 0.9.5-5 AoA Model ZG5

I have set up an encrypted folder which shows in 'nautilus' but when I try to get access into it via the cryptkeeper icon all I get is 'the stash could not be mounted', my password is ok as cryptkeeper allowed me to change it. How do I 'mount' this folder? Any help would be appreciated.

---

### Post by BrandonIngalls on 2012-10-09
You should be able to mount the folder manually.
Open a Terminal
I normally create a folder called tmp

then use encfs to mount your stash folder to tmp...

```
cd ~/
mkdir tmp
encfs ~/StashFolder ~/tmp
```

replace the ~/StashFolder with the folder where your encrypted files are -- then replace the ~/tmp with the folder you want to to access your un-encrypted files from.

Once you no longer need to use the folder use...
```
fusermount -u ~/tmp
```

---

### Post by Cushie on 2012-10-10
Thanks for such a simple and concise procedure which Cryptkeeper could not solve.
The so called 'Stashfolder' is the hidden encrpted folder begining /. and ending _encfs  hence:-

cushie@Netbook-Precise:~$ encfs  ~/.Docs-crypt_encfs ~/Docs-crypt

EncFS Password: #enter password

#Decrypts the folder. Yes, the encrypted files are now available in file 'Docs-crypt'

cushie@Netbook-Precise:~$ fusermount -u ~/Docs-crypt

#this removes files in the unencrypted folder 'Docs-crypt' (and may be deleted)

Having sorted this and got it working I went back to Cryptkeeper which made the folders in the first instance and it would not recognise or import the _encfs file as an encrypted file.

If Cryptkeeper can not mount its own folders is there a simple way of having the encrypted folder mounted at boot time or is that not adviseable?

---

### Post by BrandonIngalls on 2012-10-10
> **Cushie said:**
> Thanks for such a simple and concise procedure which Cryptkeeper could not solve.
The so called 'Stashfolder' is the hidden encrpted folder begining /. and ending _encfs  hence:-

cushie@Netbook-Precise:~$ encfs  ~/.Docs-crypt_encfs ~/Docs-crypt

EncFS Password: #enter password

#Decrypts the folder. Yes, the encrypted files are now available in file 'Docs-crypt'

cushie@Netbook-Precise:~$ fusermount -u ~/Docs-crypt

#this removes files in the unencrypted folder 'Docs-crypt' (and may be deleted)

Having sorted this and got it working I went back to Cryptkeeper which made the folders in the first instance and it would not recognise or import the _encfs file as an encrypted file.

If Cryptkeeper can not mount its own folders is there a simple way of having the encrypted folder mounted at boot time or is that not adviseable?

Maybe try to rename the folder that holds the encrypted files to something like Docs-Encrypted and see if you can import it then.
Also are you trying to import the folder or the .encfs6.xml file? When you are chosing a file to import try to push Ctrl+H to show hidden files.

If that doesn't work you could make a script that will allow you to quickly mount the folder through a terminal...

```
mkdir ~/bin
cat << _END > ~/bin/mountDocs
encfs ~/StashFolder ~/mountPoint
 _END
nano ~/bin/mountDocs
```

If you do this, the next time you log in you can open a terminal(Ctrl+Alt+T Ubuntu default) and type in mountDocs then hit enter. It will then ask you for your password.

---


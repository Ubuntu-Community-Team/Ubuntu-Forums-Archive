---
title: "HOW TO: add passwords to, and encrypt, certain folders. (Easy step by step guide)"
date: 2008-12-08
forum: Security
---

### Post by pluckypigeon on 2008-12-08
Start by installing fuse-utils and encfs
in a terminal:
```
sudo apt-get install fuse-utils encfs
```



add your user to the fuse group (replacing USERNAME with your login name)
in a terminal:
```
sudo adduser USERNAME fuse
```



open /etc/modules with an editor and add the fuse module 
```
gksudo gedit /etc/modules
``` when it opens add the word:

fuse



then start fuse by typing
in a terminal:
```
sudo modprobe fuse
```



Create 2 directories, one hidden and one normal. The normal one will be the mountpoint and the hidden one will hold the encrypted files.
in a terminal:
```
mkdir ~/files
mkdir ~/.files
```
OR
right click in nautilus then "Create Folder" (The terminal option is quicker)




now mount ".files" at mountpoint "files" encfs
```
encfs ~/.files ~/files
``` (You'll be asked for a password)

Open the files folder and put your documents/vids/pics and other stuff in it. 

Then unmount it using fusermount. You will see your files are invisible. If you look in the '.files' folder you will see that they are also encrypted.

```
fusermount -u ~/files
```

..............................................................

Remember

To call up your files type 
```
encfs ~/.files ~/files
```

and to hide them again type
```
fusermount -u ~/files
```

..............................................................

What I did was create a simple bash script to open and close the files and placed it in /usr/bin and create a link in my menu with alacarte.

This is the script:
```
#! /bin/bash
read -p "Would you like to open your encrypted files (y/n)?"
[ "$REPLY" == "n" ] || encfs ~/.Files ~/Files
read -p "Would you like to unmount your encrypted files (y/n)?"
[ "$REPLY" == "n" ] || fusermount -u ~/Files
read -p "To open or close your encrypted files run this program again. Press Enter"
```

Paste it in to gedit and save it as encfsscript in your home directory

Make it executable

in a terminal:
```
chmod 755 ~/encfsscript
```



Open superuser nautilus and cut and paste the script in /usr/bin

in a terminal:
```
gksudo nautilus
```



Open alacarte and make a link in your menu

in a terminal:
```
alacarte
```

Go to the folder where you want to put the link and click "New Item"

Choose a nice icon by clicking on the picture.

Then add these details:

Type: Application in Terminal
Name: Encrypted Files
Command: encfsscript
Comment: Mounts and Unmounts Encrypted Files!!

I'd be very interested to hear how you got on, let me know!

Also let me know if you find any mistakes and typos!!

---

### Post by tubbygweilo on 2008-12-08
pluckypigeon, 
I could have done with this a few weeks ago but I settled for [Help EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") & [Wiki EncryptedPrivateDirectory]("https://wiki.ubuntu.com/EncryptedPrivateDirectory") and it seems to have worked for me. 

Keep up the good work.

---


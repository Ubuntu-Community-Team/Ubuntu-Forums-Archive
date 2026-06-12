---
title: "Urgent Wine Problem"
date: 2009-12-01
forum: Server Platforms
---

### Post by PinkyTr4ffic on 2009-12-01
I have ubuntu server running with ldap + samba for authentication purposes.
I can log in with my samba users on a client pc and their home directory is mounted from the server accordingly.

I installed wine with a local user on the client pc and wine is also installed on the server.

My problem is now that when i try to run a wine application i get an error saying that wine can't find the right folder. 

I know why this happens but i can't seem to fix it. 

The dosdevices folder contains a symlinks named c: which maps to the drive_c. I guess that this symlink is meant to emulate a real windows hard drive but the dosdevices folder does not contain the necessary symlinks to provide wine with the right pointer to the c drive, on the client. 

When i look in my wine folder, from that user, on the server i can clearly see that the c: symlink is present. 

When i run winecfg on the client pc and i click the drives tab a message box pops up with the error that i don't have a c: drive ( no ****) and i click on add then it adds the correct folder but when i quit the winecfg window it immediately deletes the symlink.

I have also tried mannually creating the symlinks with the following commando.

ln -s /home/user/.wine/drive_c c:

which presents me with a terrific error saying that c: doesn't exist, no **** i just tried to create it.

I also thought that the symbolic links wouldn't be mounted when i mounted the home drive so i added the following lines to my samba.

       follow symlinks = yes
       wide symlinks = yes
       unix extensions = no

I have absolutely tried everything i can and i'm at my wits end.
I've also profusely searched google to avoid comments lik "google it".
Can anyone PLEASE provide me with some useful information concerning this very urgent problematic issue?

---

### Post by PinkyTr4ffic on 2009-12-04
Ok, for all who cares, i've found an answer to my question but it didn't solve my problem.

Samba, well actually NTFS, has 7 special characters which cannot be used in a share,? " / \ < > * | :, and since
":" is one of these signs samba will refuse to mount folders who end with :.

And guess what, the dosdevices folder contains symlinks that represent hard drives in a manner very similar to windows --> C: D:

---


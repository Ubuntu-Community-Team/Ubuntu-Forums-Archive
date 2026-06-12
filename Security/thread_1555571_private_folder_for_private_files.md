---
title: "private folder for private files ?  ???"
date: 2010-08-18
forum: Security
---

### Post by softwarefreeze on 2010-08-18
i noticed that all files can be seen by another computer if the drive is accessed

can I stop this? can i set a private folder?

---

### Post by ronnielsen1 on 2010-08-18
Not really. You can rename a folder (from folder to .folder) and make it hidden but if someone clicks to show hidden folders, it will show. (For one folder I just put it in a hidden obscure part of the file system). You could also encrypt a folder but I've never done this

If you right click on the folder, you can go to properties and set permissions for other users to none. This would probably work

---

### Post by Morbius1 on 2010-08-18
> **softwarefreeze said:**
> i noticed that all files can be seen [COLOR=Blue]by another computer[/COLOR] if the drive is accessed

can I stop this? can i set a private folder?

By another computer?
If the "drive" is accessed?

Did you set up file sharing, like Samba, on this machine? How is the other computer accessing the "drive"?

---

### Post by Rumpletumbler on 2010-08-18
Take a look at this, it might help. I'm new as well so it might not be your best solution. 

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by endotherm on 2010-08-18
> **Morbius1 said:**
> By another computer?
If the "drive" is accessed?

Did you set up file sharing, like Samba, on this machine? How is the other computer accessing the "drive"?
my guess is that the Op means, when the drive is accessed from another os instance (dualboot, livecd, etc) or placed in another machine. may be wrong.

op, encryption is the only cure for this ailment, but be careful to use it sparingly as the cure can be worse than the disease. with unencrypted files, you can always retrieve them, no matter if your system dies, or you forget your password, as long as the disk is still functional. an encrypted file however will require you to keep archived the password or associated keys needed to open the file. if you lose them, your data is gone forever. 
I recommend Truecrypt. you create a "volume" (a file that acts like an encrypted folder), and mount/unmount the volume at will. as long as you don't lose the volume or your password, you can always be sure you can get at your data, and it's portable across win/lin/mac. built-in encryption systems like ubuntus home folder encryption however can become inaccessible if your OS takes a dive, and backing up the information to recover it is somewhat harder.  

on the logistical side, truecrypt is the better paradigm as well, since the volume is not automatically mounted. imagine you are crossing a border somewhere and a customs guy boots up your laptop. when they are asked for a password, they ask you for one. if you are not forthcoming, it could make for an uncomfortable afternoon, so you are left with the choice of rendering your encryption useless, or face in the best case an all expenses paid stay in the local hoosegow. it also underscores another concern with encryption: as innocuous as the usecase may be, lawenforcement will always see ciphered data as suspicious in and of itself. 
[http://xkcd.com/538/](http://xkcd.com/538/)

ultimately however, you are fighting a losing battle (not that i disagree with what you want to do). the first rule of computing security is simple: Physical access to a box is Root access to a box. theres just no getting around it.

---

### Post by Morbius1 on 2010-08-18
> **endotherm said:**
> my guess is that the Op means, when the drive is accessed from another os instance (dualboot, livecd, etc) or placed in another machine. may be wrong.

Ah, I do have a bad habit of taking things a little too literally ;)

---

### Post by alphaamanitin on 2010-08-18
> **endotherm said:**
> my guess is that the Op means, when the drive is accessed from another os instance (dualboot, livecd, etc) or placed in another machine. may be wrong.

op, encryption is the only cure for this ailment, but be careful to use it sparingly as the cure can be worse than the disease. with unencrypted files, you can always retrieve them, no matter if your system dies, or you forget your password, as long as the disk is still functional. an encrypted file however will require you to keep archived the password or associated keys needed to open the file. if you lose them, your data is gone forever. 
I recommend Truecrypt. [...].

It is important to note that with truecrypt [TC] you should also keep back up headers.  Headers are found at the beginning and end of a TC volume, the one in the back is a back up itself.  Anyway if those headers get damaged for any reason will NEVER recover your data even with a correct passphrase.  Read TC manual for why.  

And in response to the border crossing situation that endotherm mentioned the solution to this is a hidden volumes.  TC volumes look like psuedo random data.  It is possible to detect TC volumes-howerver, you can make a volume inside a different volume.  Due to all volumes looking like random data it is impossible (or nearly so) to detect how many volumes are on a drive.  You could therefor supply the passphrase for the outer volume while maintaining the security of the inner volume.  It is worth noting that any data written to the outer volume with enabling inner volume protection (which you do not want to do in front of some one as it lets them know there is an inner volume) can damage the inner volume-so back things up.

I recommend encryption on the basis of exercising your rights as a US citizen (at least for me as I am a US citizen, I cannot speak for other countries).  We have the right to encrypt whatever we want to and the government does not have the right to demand our encrypted data merely because it is encrypted.  For me it is a matter of principal.  
  
AlphaA

---

### Post by bodhi.zazen on 2010-08-18
> **softwarefreeze said:**
> i noticed that all files can be seen by another computer if the drive is accessed

can I stop this? can i set a private folder?

Yes you can change that behavior. What do you mean by "another computer if the drive is accessed" ?

Is this samba ? NFS ? ftp ? what type of access are we discussing here ?

---


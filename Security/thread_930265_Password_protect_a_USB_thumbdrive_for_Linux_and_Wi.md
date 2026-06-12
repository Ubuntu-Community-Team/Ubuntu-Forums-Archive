---
title: "Password protect a USB thumbdrive for Linux and Windows"
date: 2008-09-25
forum: Security
---

### Post by jimmy the saint on 2008-09-25
I need to password protect a usb thumbdrive that will be used on both linux and windows boxes.  Is there any software that is capable of doing this?  The one caveat is that I will not be able to install software on the windows machine, so it must be done from within the thumbdrive.

Thanks 

JTS

---

### Post by Dr Small on 2008-09-25
Truecrypt can probably do it. Have a truecrypt partition, with all of your encrypted data, and then have a small unencrypted partition that will hold the Windows Truecrypt executable. It should run from a USB, as I have seen USB sticks that come with Truecrypt installed right on them.

---

### Post by Trebaruna on 2008-09-26
Be advised that you'll need root on the windows machine to run TrueCrypt. [http://www.truecrypt.org/docs/?s=traveler-mode](http://www.truecrypt.org/docs/?s=traveler-mode)

---

### Post by jimmy the saint on 2008-09-26
Yeah, I kind of figured that.  So there is no multiplatform password protection that can just run from the drive?  It doesn't need to be super secure, hell it doesn't even need to be reasonably secure, it just needs to keep documents from being edited by others in the office.  More of a deterrent for computer illiterate.

---

### Post by doug-M on 2008-09-27
You could see if you can format it as NTFS and set the permission to read only. Not sure what will honor the permissions but you could try.

---

### Post by hyper_ch on 2008-09-27
use truecrypt for that... traveller mode only works on windows. It will create an autostart file that runs the tc binary. So no install of tc in windows is needed but you need to have the rights to mount the volume as drive.

---

### Post by kevdog on 2008-09-27
Can you describe your situation more thoroughly?  There are a lot of possible solutions (non ideal), however it depends on your current situation. 

Questions to ponder:
1. Can you boot from USB stick?
2. Are you able to run executables from USB stick?
3. Are executables located on host machine or must they be included on the USB stick?
4. Do you have root priviledges on windows machine?
5. Can you even mount the USB drive on the windows machine?  Some admins have locked this privilege.

---

### Post by jimmy the saint on 2008-09-27
Windows:
     I can
           Mount the USB stic
           Run executables
     I cannot
           Install anything
I simply need a drive in which I can store documents without worry of having them modified by anyone but me.  I think I am going to go the old fashioned physical security route.  In other words, the stick will stay in my bag!

Thanks for the suggestions.  I tried the TrueCrypt route yesterday but it could not run the drivers neccessary because I do not have sufficient privilages.  If I just keep the drive on me, no one can mess with it.

---

### Post by kevdog on 2008-09-27
You do have a tough situation.  I was thinking of using gpg symmetric file encryption for you, however it seems that might not work for you!

---

### Post by binbash on 2008-09-27
+1 for truecrypt

---


---
title: "Problem Running Starcraft"
date: 2010-08-28
forum: Wine
---

### Post by TwiztidJ on 2010-08-28
Hello everyone,
         I am having a bit of a problem running Starcraft in Ubuntu. Now, I know that this topic has come up a few times and has been solved but, unfortunately, I was not able to fix my problem using the solutions that have been given so far. My problem seems to be a common one but, as I stated, I can't seem to get through mine. The problem is the Data File Error. The error states that there is a file missing or the disk has not been placed in the drive properly. I have gone into WineCFG and the first thing I noticed is that the game is being picked up as a drive under the name "/media/SCdisk1". When I go and look at it, it is set up with the path as that and set to CD-Rom. Furthermore, when I add a drive, setting it to any random letter, and choose the path, for example "/dev/cdrom", with the CD-ROM setting, it still gives me the same error. I have tried to uninstall and reinstall wine multiple times and even updated to the most recent release but the outcome is still the same. Is there something else that could be wrong. If I remember correctly, don't I need to run python or something like that with Wine. Could it be that maybe the installation of this other program is the faulty portion of this situation? Your input is much appreciated.
Thank you for your time,
Twiztid J

---

### Post by TwiztidJ on 2010-09-01
Any help at all would be much appreciated. I have searched the web for the answer and all of them come up the same. I am going to try another search but, like I said, if someone knows how to assist me in my problem, it would be much appreciated.

---

### Post by bigboy_pdb on 2010-09-01
You might want to try creating an ISO image from the CD and running the game from that.

I haven't played Starcraft using WINE for some time, but that's how I've always done it.

Also, I haven't created any CD images in a while. The following link explains how to do it:
[http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/)

If that doesn't work you can always search for other ways to create the image based on what I've written.

To mount the image use:
```

sudo mount -o loop FILE.iso MOUNT_DIR

```

To unmount it use:
```

sudo umount MOUNT_DIR

```

FILE.iso is the CD image file and MOUNT_DIR is the directory you want to mount the contents into. For example, you can use /mnt as the MOUNT_DIR and when you enter the directory you'll see the CD contents listed there.

**EDIT**: I should also mention that you shouldn't have any browsers, terminals, or other programs within MOUNT_DIR or using files within it when you go to unmount the image.

---

### Post by TwiztidJ on 2010-09-02
> **bigboy_pdb said:**
> You might want to try creating an ISO image from the CD and running the game from that.

I haven't played Starcraft using WINE for some time, but that's how I've always done it.

Also, I haven't created any CD images in a while. The following link explains how to do it:
[http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/)

If that doesn't work you can always search for other ways to create the image based on what I've written.

To mount the image use:
```

sudo mount -o loop FILE.iso MOUNT_DIR

```To unmount it use:
```

sudo umount MOUNT_DIR

```FILE.iso is the CD image file and MOUNT_DIR is the directory you want to mount the contents into. For example, you can use /mnt as the MOUNT_DIR and when you enter the directory you'll see the CD contents listed there.

**EDIT**: I should also mention that you shouldn't have any browsers, terminals, or other programs within MOUNT_DIR or using files within it when you go to unmount the image.
Thank you for your reply. I tried it out and tried to run the image but I was getting the same problem with the image. When I went into where the files were kept, I noticed that there were actually  files missing. When I looked it up, there is supposed to be more than four file, yet that is all that I have. The four Files are: Autorun.inf, Installer.ico, Installer Tome.mpq, and StarCraft (Windows).exe. Is there, by any chance, that I can fix this?

**EDIT:** Also, I just tried to open the game through the terminal using the wine command and, in response, it did the same thing except this time it put, fixme:advapi:SetSecurityInfo stub, in the terminal code. I don't know if this means anything but I thought it might help.

Thanks

---

### Post by Dayofswords on 2010-09-02
if you want to skip the "need CD' stuff, blizzard made a patch a while back that made it so you no longer needed the CD if you do something:

[LIST]
[*]download the patch here
[http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21149](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21149)

[*]run through wine, there should be no issue
[*]"if you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to your StarCraft folder[in wine it's ~.wine/drive_c/Program Files/Starcraft/] and rename it to "StarCraft.mpq".
[/LIST]

---

### Post by TwiztidJ on 2010-09-02
> **Dayofswords said:**
> if you want to skip the "need CD' stuff, blizzard made a patch a while back that made it so you no longer needed the CD if you do something:

[LIST]
[*]download the patch here
[http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21149](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21149)
[*]run through wine, there should be no issue
[*]"if you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to your StarCraft folder[in wine it's ~.wine/drive_c/Program Files/Starcraft/] and rename it to "StarCraft.mpq".
[/LIST]

Yeah, I have actually tried that before but it give me an error to try it again and or uninstal and reinstall the game to run the patch but, for some reason, I can't even uninstall the game. Also, I am missing the install.exe and about three or four other files.

---

### Post by TwiztidJ on 2010-09-02
Okay, so I finally got the game to uninstall and I tried to reinstall it. Here is what I did:

```
joshua@joshua-laptop:/media/iso$ wine start Installer.ico
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Success
```

Unfortunately, it did not work and it gave me that error message. Does anyone know what I can do to fix this?

---

### Post by NightwishFan on 2010-09-04
When you use CD images in wine, mount them to a single directory called lets say.. /media/virtual. You can make the directory by running this command:
```
sudo mkdir /media/virtual
```

Add the /media/virtual as a drive under winecfg.

---

### Post by TwiztidJ on 2010-09-15
> **NightwishFan said:**
> When you use CD images in wine, mount them to a single directory called lets say.. /media/virtual. You can make the directory by running this command:
```
sudo mkdir /media/virtual
```Add the /media/virtual as a drive under winecfg.
Thank you for your post. Sorry that it took me so long to respond. I have actually setup the CD image mount. The wine cfg looks like this:

Drive letter- D:
Path- /media/iso
Type- CD-ROM
Device- Blank (Inaccessible)
Label- Blank (Inaccessible)
Serial- 0 (Inaccessible)

I have the image mounted to the folder that was created but I am still getting the same missing disk error for some reason. I have even tried installing the no CD patch, the patch successfully installed but the result was still the same. Would you happen to have any ideas as to why this might be? Another question, the actual CD is generated in the /media folder, would that conflict with the /iso Folder that is in there as well?

---

### Post by TwiztidJ on 2010-09-15
Question to all, I am trying to run the game in the Windows XP setup; would it be better to try running the game under Windows 98 setup for the wine cfg?

---

### Post by cwwilson721 on 2010-09-15
> **twiztidj said:**
> okay, so i finally got the game to uninstall and i tried to reinstall it. Here is what i did:

```
joshua@joshua-laptop:/media/iso$ wine start [COLOR=red]installer.ico[/COLOR]
fixme:exec:shell_execute flags ignored: 0x00000100
application could not be started, or no application associated with the specified file.
Shellexecuteex failed: Success
```unfortunately, it did not work and it gave me that error message. Does anyone know what i can do to fix this?[SIZE=6]You have to run the exe file!!!!!!!!!!!!
[/SIZE]

---

### Post by TwiztidJ on 2010-09-15
> **cwwilson721 said:**
> [SIZE=6]You have to run the exe file!!!!!!!!!!!!
[/SIZE]
I actually did that three times. I just tried it again and this time it worked. I think that the installer was stopping the installation during the installation. The game is actually running now.

---

### Post by TwiztidJ on 2010-09-15
Thank you everyone for your help. I found out what the problem was. I believe that the game was finishing the installation before the game could finish. The is finally working.

---


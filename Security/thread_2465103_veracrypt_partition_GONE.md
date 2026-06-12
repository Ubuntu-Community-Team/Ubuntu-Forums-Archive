---
title: "veracrypt partition GONE"
date: 2021-07-22
forum: Security
---

### Post by Unguidedone on 2021-07-22
ok lets just point out i understand how powerful aes-256 is: its unbreakable... with 3x symmetric crypto algorithms in a cascade it provides stupid amounts of security.  im totally aware of this fact, if a single byte of off of my keyfiles (i have copies) and a single bit of my password is off come hell or high water or the universe cooling that drive will not be decrypted ever.....

I have used truecrypt for the better part of 10 years and never had this issue before.  I fear the data is cryptoshredded aka really really gone.

so here is the trouble:

i wrote a 8 tb veracrypt volume its a seagate external desktop drive.  Uses it for years works fine its reliable no issues.  In the process of security upgrades of upgrading my system from truecrypt into veracrypt.
make a veracrypt full disk image(temp storage): done
mount truecrypt and copy files to temp storage in veracrypt: done
deleted truecrypt volume and written over with veracrypt volume: done
unmounted disk and remounted disk to validate the password works / keyfiles work: success
copied files from veracrypt temp to seagate veracrypt: done
unmounted disk and remounted disk to validate the password works / keyfiles work: success
moved files from temp storage into new veracrypt full disk image: done
unmounted veracrypt image and tested if i could remount: failure

veracrypt only sees /dev/sde while the image is written to /dev/sde1  where did it go?


[LEFT] **Problem: **[/LEFT]
 [LEFT] *VeraCrypt volume cannot be mounted; VeraCrypt reports "*Incorrect password or not a VeraCrypt volume*".*[/LEFT]
 [LEFT] **Possible Cause: **[/LEFT]
 [LEFT] The volume header may have been damaged by a third-party application or malfunctioning hardware component.[/LEFT]
 [LEFT] **Possible Solutions: **[/LEFT]
 
[LIST]
[*=left] You can try to restore the volume header from the backup embedded in the volume by following these steps:
[LIST=1]
[*=left] Run VeraCrypt.
[*=left] Click *Select Device* or * Select File* to select your volume.
[*=left] Select *[Tools > Restore Volume Header]("https://www.veracrypt.fr/en/Program%20Menu.html#tools-restore-volume-header")*.
[/LIST]
 
[/LIST]

gave error was not a valid volume so i can assume this means its hardware that is failing????  the data was really slow writing but thats normal.



i triple checked password its correct / i checked hash auto detection and set to manual it was correct / i triple checked keyfiles for any issues and it was correct

to attempt to debug i tried to backup the volume headers and got the bad password or not a valid volume error.  The volume is encrypted but is missing sde1 partition mounting point.    

so i ruled out passwords and keyfiles it is correct.  i then checked on another computer and got all identical behavior.



veracrypt cant mount what does not exist.  so where did /dev/sde1 go? 

to add insult to injury i was in the process of making a backup of the data.

---

### Post by TheFu on 2021-07-22
If using encryption, having excellent backups is mandatory, not optional.

Not veracrypt, but LUKS encryption how-tos: 
[LIST]
[*]Creating Part1: [https://youtu.be/vk9Z2_rEUak](https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
[*]Accessing Part2: [https://youtu.be/ELEVo6SbYl0](https://youtu.be/ELEVo6SbYl0) seems to be it.  
[*]Text version: baldnerd.com/add-a-drive-to-linux-and-encrypt-it
[/LIST]

Native is best. Stick with native Linux file systems and native linux encryption to avoid performance penalties and problems with permissions.

---

### Post by Unguidedone on 2021-07-22
all very valid :(

seems the data is lost

---


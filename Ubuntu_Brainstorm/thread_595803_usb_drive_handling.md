---
title: "usb drive handling"
date: 2007-10-29
forum: Ubuntu Brainstorm
---

### Post by oliviacond on 2007-10-29
when i want to delete some files in the usb drive, it will not completely delete the files, instead, the files will be sent to trash folder of the usb drive.

to completely remove the files, i have to select "Show hidden files" and remove them from the trash. beginners may feel weird why the drive is full although they have deleted the files.

my idea is when i delete particular file in the usb drive, the file will be completely deleted.

---

### Post by Zackariah on 2007-10-29
> **oliviacond said:**
> when i want to delete some files in the usb drive, it will not completely delete the files, instead, the files will be sent to trash folder of the usb drive.

to completely remove the files, i have to select "Show hidden files" and remove them from the trash. beginners may feel weird why the drive is full although they have deleted the files.

my idea is when i delete particular file in the usb drive, the file will be completely deleted.

I may be wrong, but I believe all files are moved to the trash folder, so if you empty the trash with the icon on the bottom right bar of the desktop it will removed them from the .trash-whoever folder.

Hope this helps,
Zackariah

---

### Post by chrisccoulson on 2007-10-29
Since Gutsy, when you eject or unomount a removable drive, a prompt appears asking if you want to delete the trash on the drive to free up space

---

### Post by osx424242 on 2007-10-30
As a philosophical discussion, I believe that beginners would rather have "Undo" work than have deleted files disappear completely.  (Yes, this is a security issue, but if you are in an environment where security is an issue than either hire a competent IT/IS department or learn a lot... I learned with little effort to do a 'sudo rm -rf /Volumes/USB/.Trashes; touch /Volumes/USB/.Trashes; chmod 000 /Volumes/USB/.Trashes' on my Mac OS X system.)  Also, removable drives keep getting bigger and bigger: a cheap drive at Staples / Office Depot / Dunder Mifflin is now 256MB, not 32MB like it was a couple years ago, so "running out of room" is becoming less and less of an issue.  

Finally (and, hopefully, somewhat humorously)... would you rather deal with
> "w00t why won't my LINUX UBUNTU FEISTY GUSTY delete f1l3z for REAL, I have to delete them myself"
or
> "MY COMPUTER DELETED MY TERM PAPER AND WONT BRING IT BACK BUT MY MICROSOFT DID WHY DID MY B/F TELL ME TO MOVE HE WONT FIX IT AND SAYS HE CANT FIX IT WILL YOU FIX IT!!! MY LIFE IS OVER IF THIS DOESNT WORK?! BRING MY PAPER BACK OR ILLL GO BACK TO THE OFFICE FOREVER?!!!"
: )

---


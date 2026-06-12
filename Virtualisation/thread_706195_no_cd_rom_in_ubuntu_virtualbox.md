---
title: "no cd rom in ubuntu virtualbox"
date: 2008-02-24
forum: Virtualisation
---

### Post by Tucatts on 2008-02-24
I have Gutsy running as a guest in virtualbox. The cd rom drive is not showing up and can't add any media to Gutsy with either a cd or a flash drive. Not sure how to proceed at present so any thoiughts on this would be appreciated. Thanks!

---

### Post by LarryJ2 on 2008-02-24
In the VBox ubuntu Settings,  click on CD/DVD-ROM then  make sure you have an X by Mount CD/DVD Drive and that your CD/DVD drive shows as /dev/something in the drop down selection.  For example,  my laptop cd drive shows as TSSTcopr DVD  (/dev/scd0)   Also click the radio button to the left of the  Host CD/DVD Drive.  Insert your install CD and power up the virtual machine again.    If the vm doesn't read from the CD, then   change the boot order in General Advanced   so the CDROM is the first to be queried for bootable programs.

Meow to your cats.

---

### Post by bmc3 on 2008-04-27
I got the same problem, but the drop down list is empty.
I used the current OSE and non-OSE editions and installes libhal-dev (even it is not necessary anymore).

What can I do?

---

### Post by bmc3 on 2008-09-25
Just stumbled over this again ... if I remember correctly any user who should be able to use the hosts cdrom drive has to be member of the cdrom group.
Then the cdrom drive is displayed and the user can use it.

(Remember to log out & back in after adding a user to the cdrom group. Check group memberships with "groups user_name" on the terminal.)

---


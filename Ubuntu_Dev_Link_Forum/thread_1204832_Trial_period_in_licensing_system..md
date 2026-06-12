---
title: "Trial period in licensing system."
date: 2009-07-05
forum: Ubuntu Dev Link Forum
---

### Post by SERGYI on 2009-07-05
[FONT=Calibri][SIZE=3]Hail! We have successfully ported 3d-coat editor to Linux using &#8220;gtk+&#8221; ([/SIZE][/FONT][[FONT=Calibri][SIZE=3]http://3d-coat.com[/SIZE][/FONT]]("http://3d-coat.com/")[SIZE=3][FONT=Calibri]). One last thing remains unresolved &#8211; licensing system. Our editor has trial period of one month with almost full functionality. The first start date and time of the program we save within several files in different locations, such as &#8220;c:\Windows\System32&#8221;, &#8220;/Library&#8221;, etc. But in Linux with default user rights the only folder you can store to is the user home folder. Please advice, where can we store information about the first start date and time of the program to provide cheat-resistant trial period?[/FONT][/SIZE]

---

### Post by WRDN on 2009-07-05
Storing data in plain text files in various locations doesn't make it "cheat-resistant". If you really want to do it this way, then, create a hidden folder/file within the home folder, by prefixing the name with ".". E,g, to create a hidden folder, create a folder with the name ".folderName". The same applies to files.
You could also use [gconf]("http://projects.gnome.org/gconf/"), the configuration system for the GNOME environment.

---

### Post by prshah on 2009-07-05
> **SERGYI said:**
> Please advice, where can we store information about the first start date and time of the program to provide cheat-resistant trial period?

When the program is being installed, it is being done so with "sudo"; this essentially means that you can store your file anywhere you want. Just make sure that the file and the store location has +r (read) access for (o)thers group.

To make it cheat-resistant, I'd suggest: 

a) When installing, check if the date is correct with an Internet timeserver. If you are offering an offline installation, store the date of installation of the program; then run a sanity check when the program is being used. Otherwise, there's nothing to stop a person from setting a future date (eg, a year in advance), then being given a month's trial, and then going back to the correct date, so that he/she gets a 13 month trial.

b) Before storing the file, encrypt it to prevent tampering. Use a public/private key. Also, store the hash (md5) of the file in another location, for performing a sanity check there as well.

c) These suggestions will make the program cheat-resistant; not cheat-proof.

---

### Post by lavinog on 2009-07-06
Storing the time file in the user home folder seems like all a user would have to do is create a new user every month to reset the time?

---

### Post by SERGYI on 2009-07-12
[SIZE=3][FONT=Calibri]Thanks for your advices! It seems, like encrypted hidden files in user home folder are enough. You know, any system can be cracked today (even PS3 someday :-), so licensing system should be considered more like reminder for the user “maybe it’s time to pay?”. And of course, it should be resistant to trivial actions from the user, like reinstalling application, or date and time change.[/FONT][/SIZE]

---


---
title: "Decent FTP app?"
date: 2006-05-30
forum: The Cafe
---

### Post by _simon_ on 2006-05-30
gFTP is really annoying me by not having any option to save the password.

Can anyone recommend one that DOES remember the login details?

---

### Post by SeanTater on 2006-05-30
KIO in kde does -- with kwallet

other than that -- don't know -- only know kde

---

### Post by aysiu on 2006-05-30
If you're using Firefox, I'd highly recommend the FireFTP extension.

---

### Post by _simon_ on 2006-05-30
for some reason fireFTP (which i've already tried) doesn't display all of the directories available to me with my online host which renders is useless :(

I just tried Kasablanca and that's worse than gFTP, never mind the password it doesn't remember the host or username!

---

### Post by arendm on 2006-05-30
Connect to your ftp-site and then press Ctrl-A. There's an option to save your password. It works for me anyway :)

---

### Post by aysiu on 2006-05-30
KFTPGrabber is pretty good.

---

### Post by _simon_ on 2006-05-30
[QUOTE=arendm]Connect to your ftp-site and then press Ctrl-A. There's an option to save your password. It works for me anyway :)[/QUOTE]

Thank you!!! That's worked a treat.

Thanks for everyones suggestions, now that I've managed to save the password I'll stick with gFTP. :)

---

### Post by Rackerz on 2006-05-30
Linux has a lack of GUI ftp programs. That's when I start to miss my FlashFXP in Windows, it's doesn't work emulated through Wine either :(.

---

### Post by dcraven on 2006-05-30
You could try ncftp as well. It saves locations as bookmarks and it looks the same on all desktops.

Cheers,
~djc

---

### Post by aysiu on 2006-05-30
[QUOTE=Rackerz]Linux has a lack of GUI ftp programs.[/QUOTE] Have you even read the rest of this thread?

gFTP is GUI.
KFTPGrabber is GUI.
You can also use Nautilus and Konqueror for FTP--both of those are GUI.

---

### Post by siimo on 2006-05-30
why not **Nautilus**? it even supports gnome keyring functionality for remembering passwords.  simply open a Nautilus window (ctrl+L) for location bar and type: [ftp://username@server.address.com](ftp://username@server.address.com)  and it will prompt you for a password.  Then simply use it as any other folder on your hard drive.. copy paste cut etc to move files around :mrgreen:

---

### Post by aysiu on 2006-05-30
[QUOTE=siimo]why not **Nautilus**? it even supports gnome keyring functionality for remembering passwords.  simply open a Nautilus window (ctrl+L) for location bar and type: [ftp://username@server.address.com](ftp://username@server.address.com)  and it will prompt you for a password.  Then simply use it as any other folder on your hard drive.. copy paste cut etc to move files around :mrgreen:[/QUOTE] I like it in theory, but am I the only one who's experienced [this bug](https://launchpad.net/malone/bugs/39239) when trying to use Nautilus for FTP (and bookmarking the FTP sites)?

---

### Post by toorima on 2006-05-30
[QUOTE=Rackerz]Linux has a lack of GUI ftp programs. That's when I start to miss my FlashFXP in Windows, it's doesn't work emulated through Wine either :(.[/QUOTE]

The 2.x version works fine with wine.

---

### Post by ampicillin on 2006-06-07
I have used nautilus so far and all other ftp's works ok.. exept my ISP ftp..

When i try to connect it i get result...

The folder contents could not be displayed.
Sorry, couldn't display all the contents of "ftp: ftp.xxxxxxxxxxxx.fi".

So i tried access it thru Firefox and all went ok.. i tried also gFTP and it worked also ok.

So, am i doing something wrong.. i just cant figure out what's wrong... ](*,) 
If someone could help me, i would be really happy. Thank's in advance..

---

### Post by aeidman on 2006-06-07
[QUOTE=ampicillin]I have used nautilus so far and all other ftp's works ok.. exept my ISP ftp..

When i try to connect it i get result...

The folder contents could not be displayed.
Sorry, couldn't display all the contents of "ftp: ftp.xxxxxxxxxxxx.fi".

So i tried access it thru Firefox and all went ok.. i tried also gFTP and it worked also ok.

So, am i doing something wrong.. i just cant figure out what's wrong... ](*,) 
If someone could help me, i would be really happy. Thank's in advance..[/QUOTE]

I am having the same problem. Perhaps it needs to be set to passive mode?

---

### Post by curuxz on 2006-06-07
Konqueror is the best linux ftp client I have used, all the others crash on me continualy or time out on big upload/download operations Gftp is a total waste of time in frequent use because its about as stable as a drunk one legged pig on crack. I mean seriously every single time you use it, it dies.

---


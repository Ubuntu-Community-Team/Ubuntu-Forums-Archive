---
title: "E-sword installer"
date: 2007-07-28
forum: Ubuntu Christian Edition
---

### Post by rahhot on 2007-07-28
Ok I downloaded the e-sword installer from ubuntu CE edition. The installer for normal ubuntu feisty users. I ran the package and it worked fine but when I go to applications ---> accesories ----> e-sword installer it comes up with the dialogue:

Ubuntu CE Users:

You MUST disable dansguardian before running the e-Sword Installer. You can do this using the built in dansguardian GUI(System>Administration>Configure Parental Controls).

Once the e-Sword Installer has successfully completed you can re-enable dansguardian.

Click OK to continue with the e-Sword Installer.

Then I click ok and nothing happens. The dialogue box dissapears and nothing happened. The e-sword module manager still wants me to run the installer...

Please help, my bible study group uses e-sword as one of their main tools.

---

### Post by tak1150 on 2007-07-28
You must temporarily disable Dansguardian (internet filtering program) to install e-sword.

Click on the start button - looking button, then choose "system" --> "Administration",

After that point, refer to the guide below to enable e-sword installation.

[CLICK HERE]("http://ubuntuforums.org/showpost.php?p=2929617&postcount=10")

Then go back to the e-sword installer again and try installing.

Let us know how that goes.

Tak

---

### Post by rahhot on 2007-07-30
I run the normal version of ubuntu and don't have dansguardian...

---

### Post by tak1150 on 2007-07-30
> I run the normal version of ubuntu and don't have dansguardian...

Oh I didn't know that.
Ok, then you can ignore everything about Dansguardian; ie just click on E-sword Installer and hit OK when the message about Dansguardian comes up.

---

### Post by rahhot on 2007-08-03
I run the installer but nothign happens after I click ok

---

### Post by rahhot on 2007-08-03
i tried it in terminal and this is what I get:
$ sudo /usr/local/apps/esword4linux/./dg_question
LiveCD check complete...
Syntax error in project file.
Cannot preload libraries: Success
sizeof(CLASS) = 256 !
gbx: Swapping archive
ERROR: #1: Out of memory
/usr/local/apps/esword4linux/./dg_question: line 15:  9425 Segmentation fault      (core dumped) /usr/local/apps/esword4linux/esword4linux/esword4linux

---

### Post by tak1150 on 2007-08-03
All right  then,

you can install e-sword without the installer.
Follow [this how-to]("http://ubuntuforums.org/showpost.php?p=2418830&postcount=1").

---


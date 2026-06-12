---
title: "Apache prevents login"
date: 2007-06-03
forum: Server Platforms
---

### Post by Citizen Nate on 2007-06-03
I recently installed apache with mod_ssl on with ubuntu. Some files used in ssl (Certificates or keys) are password-protected. In order to start up apache, I need to type in my passphrase for these files. On startup, it appears that I'm typing in my username and password, apache attempting to prompt for the passphrase appears to screw things up. After typing my name and password, the prompt freezes with the cursor still appearing after the password: line. a minute later I get the message  "Login timed out after 60 seconds." and another login prompt. This time nothing I type actually appears, as if something is prompting for a password. My current work-around is to move /etc/init.d/apache to ~/ and then logging in and calling sudo apache after every boot. Does anyone have any suggestions for making apache boot automatically?

---

### Post by kidders on 2007-06-04
Hi there,

Ubuntu's boot process is really designed to be non-interactive. If you really want to use encrypted SSL keys, the most straightforward thing to do is start Apache manually after each boot, as you've been doing ... although moving /etc/init.d/apache is _not_ a good idea.

The only satisfactory way (in security terms) of having Apache pull in SSL key passphrases automatically (off the top of my head) would probably involve storing them on a CD or USB key that you could insert in during boot ... a technique often used to handle things like filesystem encryption, where people are similarly paranoid about security.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Mr. C. on 2007-06-07
You can remove the passphrase from your key if that is an acceptable solution for you.  See the EXAMPLEs at the end of the rsa man page.

MrC

---

### Post by Citizen Nate on 2007-06-07
I set up some scripts to read the passphrase from my usb drive. (I suspect the passphrase isn't useful to anyone without access to my server) Thanks for the help.

---


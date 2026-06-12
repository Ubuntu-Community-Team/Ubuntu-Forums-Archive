---
title: "I am developing an Ubuntu Server Remote Control Panel"
date: 2009-09-21
forum: The Cafe
---

### Post by GreenDance on 2009-09-21
Hi Everyone, I am busy developing an Ubuntu Server Remote Control Panel and I would like to know what features people would want so I can incorporate them into Release 1 of the Control Panel.  :)

---

### Post by ChrT on 2009-09-21
> **GreenDance said:**
> Hi Everyone, I am busy developing an Ubuntu Server Remote Control Panel and I would like to know what features people would want so I can incorporate them into Release 1 of the Control Panel.  :)

There already is a server remote control panel in ubanto, you can acces it through "applications->accesories->terminal" menu, or by pressing alt+F2 and typing in "gnome-terminal", without the quotes.

Thank you for your interest in ubanto kind sir.

(captcha: anyone who wants to host stuff on the internet should first prove sufficient intelligence by learning bash)

---

### Post by Deamos on 2009-09-21
Wow, the previous poster seems to be a terminal only kind of person. 

Honestly, as for Ubuntu Server control, I do favor the way Webmin works.  It allows for control of just about ever service, including LVM and Disk/Drive support.

If you are thinking of doing a web based control panel, take a look at what Webmin does and try to make it better :)

Best of Luck!

---

### Post by Bachstelze on 2009-09-21
Webmin much?

---

### Post by lespaul_rentals on 2009-09-21
> **GreenDance said:**
> Hi Everyone, I am busy developing an Ubuntu Server Remote Control Panel and I would like to know what features people would want so I can incorporate them into Release 1 of the Control Panel.  :)

Hmm...

The possibilities really are endless.  Some ideas that come to mind:

Bring Apache websites up or down.

View FTP server information, such as currently connected clients.  Add options to kick or ban, add/remove users, etc.

SSH control.

By the way, if you're going to post with a jerk attitude, why post at all?  This is someone with coding knowledge who is willing to contribute to the community.

---

### Post by kevdog on 2009-09-21
Some attitudes in this thread were uncalled for.  I believe the OP intent was genuine.

---

### Post by Exodist on 2009-09-22
> **kevdog said:**
> Some attitudes in this thread were uncalled for.  I believe the OP intent was genuine.

No pun on the OP at all, but I feel the other posters where not being harsh at all but more confused at why there must be more server config applications when good ones already exist.

My question to the OP is tho are you wanting a application that runs on X/Gnome/KDE?  Reason I ask is no one runs a GUI on a server as it eats system resources. So you will find more applications that are CLI or remote web based.

---

### Post by Viva on 2009-09-22
> **Exodist said:**
> No pun on the OP at all, but I feel the other posters where not being harsh at all but more confused at why there must be more server config applications when good ones already exist.

My question to the OP is tho are you wanting a application that runs on X/Gnome/KDE?  Reason I ask is no one runs a GUI on a server as it eats system resources. So you will find more applications that are CLI or remote web based.

If the OP is willing to put the effort, I don't see any problem with his intention to create a control panel. It really doesn't matter if a similar software exists.

---

### Post by Exodist on 2009-09-22
> **Viva said:**
> If the OP is willing to put the effort, I don't see any problem with his intention to create a control panel. It really doesn't matter if a similar software exists.
I don't either. I was just making an analogy.

---

### Post by j7%&lt;RmUg on 2009-09-22
Correct me if im wrong but i think the OP wants to create a control panel (GUI) that runs in gnome or KDE or whichever he is developing for, that you can use to remotely access a server. I dont think the OP intends to have the control panel on the server at all.

@OP: Correct me if im wrong.

---

### Post by GreenDance on 2009-09-22
> **Exodist said:**
> My question to the OP is tho are you wanting a application that runs on X/Gnome/KDE?  Reason I ask is no one runs a GUI on a server as it eats system resources. So you will find more applications that are CLI or remote web based.

Hi, the control panel will run from within a web-browser of choice to the ubuntu server administrator.

Thanks to everyone else for the suggestions and support, ubuntu has given alot to me, and i feel it's time i gave something back and this is what i can/will do :).

---

### Post by jaxxstorm on 2009-09-22
> **GreenDance said:**
> Hi, the control panel will run from within a web-browser of choice to the ubuntu server administrator.

Thanks to everyone else for the suggestions and support, ubuntu has given alot to me, and i feel it's time i gave something back and this is what i can/will do :).

What language(s) are you writing it in, just out of interest?

Is it going to support just apache as a webserver? I really like lighttpd, but webmin's support for it at the moment isn't fantastic.

An LDAP, kerberos and Samba control panel would be just fine as far as I'm concerned, good luck!

---

### Post by amlucent23 on 2009-09-22
If you could make the LDAP options close to that of fedora directory server.. Particularly the user management options,  I would love you forever.

[http://directory.fedoraproject.org/wiki/Screenshots](http://directory.fedoraproject.org/wiki/Screenshots)

---


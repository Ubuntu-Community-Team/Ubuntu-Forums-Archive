---
title: "Using nokia 5800 to access server"
date: 2009-09-17
forum: Server Platforms
---

### Post by dink1000 on 2009-09-17
i was wondering if someone could help me out.

what i'm trying to do is access my server from my nokia 5800 so i can download music files off the server.

i only want to access it from home via wi-fi.

i think i got apache to work as if i type the server ip into my phones web browsr i get the "it works" page but that's as far as i got.

ideally what i want is for me to put the ip addy into my phone and just see a list of the samba shares? is this possible?

---

### Post by samosamo on 2009-09-17
I did this for my iPhone with an ubuntu LAMP, mt-daapd, and web front end to it called "Crossfire."

You could also do it using an ubuntu LAMP with ampache + a theme for mobile devices.

---

### Post by volkswagner on 2009-09-17
If you want to download files, set ftp server and install sic!ftp or similar on your phone.

EDIT:  I'm not sure if your Symbian device/OS supports WebDav, may be an option.  It is available on feature pack 2.

---

### Post by rebegin on 2010-01-17
i use program called symsmb on my phone to share any folder on my phone/microsd so i can access my files easily from my pc...

---

### Post by volkswagner on 2010-01-17
> **rebegin said:**
> i use program called symsmb on my phone to share any folder on my phone/microsd so i can access my files easily from my pc...

Seems symsmb is not free (free trial?).  I have used smb4s60 after installing the required python....pretty cool, but for some reason I have not been able to connect to samba shares with password protection.  I can connect to windows and my linkstation.

I use sic!ftp, and putty also for my server.  It is nice to be able to ssh into the server in a pinch...it is for quick stuff with t9 input!

MicroWow is great for wake on lan commands.

---

### Post by rebegin on 2010-01-18
> **volkswagner said:**
> ...
I use sic!ftp, and putty also for my server.  It is nice to be able to ssh into the server in a pinch...it is for quick stuff with t9 input!

MicroWow is great for wake on lan commands.

i also read about an other program with samba shares but can't remember the name. haven't tried that though.

putty is great :)

i'll check this microwow, sounds interesting.

---

### Post by gobbledigook on 2010-01-18
Hi! 

I have a 5800 and have been trying to use it to queue up files for the server to download rather than get files from the server. 

> putty is great 
 I couldn't get putty to work well with the 5800 because its touch-screen input didn't seem to be supported.

Samba onteh 5800 is interesting at best ;)

I would go with an ftp solution personally, simplicity is always best especially when the phones browser can be sooo slow!! set up an ftp server, i use vsftpd, and i would also suggest using something like [**_opera mini_**]("http://www.opera.com/mini/") as an alternative web-browser, because it supports a lot more than the inbuilt browser.

good luck!

---


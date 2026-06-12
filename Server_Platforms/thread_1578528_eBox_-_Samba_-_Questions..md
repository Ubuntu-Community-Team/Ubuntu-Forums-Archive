---
title: "eBox - Samba - Questions."
date: 2010-09-20
forum: Server Platforms
---

### Post by Roasted on 2010-09-20
In my ongoing hunt for a Samba GUI that is feature packed, well supported, easy to use, yet doesn't suck, I found myself tinkering with eBox. I have it installed and fired up but I'm a little confused. I can add a Samba share - okay great. But I sorta need to add users. Where on earth can I add users? The users and group section of eBox doesn't appear to be related to what I need, and I also cannot get into the access control section of the very share I just created.

Any thoughts?

---

### Post by windependence on 2010-09-20
Maybe.......learn a little tiny bit of <horror> command line?
 
There are two steps to creating a user. First we’ll run the smbpasswd utility to create a samba password for the user.
[INDENT]```
 
sudo smbpasswd -a <username>

```Next, we’ll add that username to the smbusers file.
[/INDENT][INDENT]```
sudo gedit /etc/samba/smbusers
```
[/INDENT]Add in the following line, substituting the username with the one you want to give access to. The format is <ubuntuusername> = “<samba username>”. You can use a different samba user name to map to an ubuntu account, but that’s not really necessary right now.
[INDENT]```
 
<username> = “<username>”

```
 
Now you can create samba shares and give access to the users that you listed here.
[/INDENT]

---

### Post by Roasted on 2010-09-20
Ha - I'm actually quite comfortable with the command line. As I was reading about eBox, I was reading that the newer version doesn't utilize the smbpasswd command. But then again, maybe that was gadmin-samba. Geez... I kind of forget now.

---

### Post by CharlesA on 2010-09-20
> **windependence said:**
> 
There are two steps to creating a user. First we’ll run the smbpasswd utility to create a samba password for the user.
[INDENT]```
 
sudo smbpasswd -a <username>

```Next, we’ll add that username to the smbusers file.
[/INDENT][INDENT]```
sudo gedit /etc/samba/smbusers
```
[/INDENT]Add in the following line, substituting the username with the one you want to give access to. The format is <ubuntuusername> = “<samba username>”. You can use a different samba user name to map to an ubuntu account, but that’s not really necessary right now.
[INDENT]```
 
<username> = “<username>”

```
[/INDENT]

Maybe I'm a bit daft, but I've only ever needed to use smbpasswd -a <username> to allow the users access thru samba. Then again, those users have unix accounts already. *shrug*

---


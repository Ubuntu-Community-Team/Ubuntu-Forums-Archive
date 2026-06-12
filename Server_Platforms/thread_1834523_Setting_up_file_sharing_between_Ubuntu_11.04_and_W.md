---
title: "Setting up file sharing between Ubuntu 11.04 and Windows XP (Samba)"
date: 2011-08-27
forum: Server Platforms
---

### Post by CrimsonTurkey on 2011-08-27
Hello everybody, im new at the fourm but ive been using Linux for a few years now and im trying to make a server to share files via Samba but alas i have hit a wall it wont let me edit the smb.conf file i have found a few things about this problem on the forum but none of them seem to work could someone please advise me on what I should do.

Terminal:
sudo gedit /ect/samba/smb.conf

It then opens an empty smb.conf and gives this error in the terminal:

(gedit:3872): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.RUD00V': No such file or directory

(gedit:3872): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

The location of the smb.conf is /etc/samba
Its set to read only.

---

### Post by sangsterthegangster on 2011-08-27
lol I do this all the time...

you typed in
```
sudo gedit /ect/samba/smb.conf
```

when its really
```
sudo gedit /etc/samba/smb.conf
```

you got the 't' and 'c' mixed up in "/etc"

---

### Post by CrimsonTurkey on 2011-08-27
:lolflag: Yup thanks :D that was it but I have another problem now when I try to restart samba it gives me this error:

```
chris@BlueTouch:~$ sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found
```:/

---

### Post by Morbius1 on 2011-08-27
First, never run a gui with sudo it's
```
gksu gedit /etc/samba/smb.conf
```Second, there is no "samba" daemon any more and the new one isn't in init.d so try this instead:
```
sudo service smbd restart
```

---

### Post by CrimsonTurkey on 2011-08-27
Yeah that was it. :KS My File sharing systems up and running now the files are copying over to my system now thanks all :D

---


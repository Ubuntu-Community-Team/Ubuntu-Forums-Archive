---
title: "Local file server, help me setup!"
date: 2010-06-06
forum: Server Platforms
---

### Post by Alseimik on 2010-06-06
Hi guys.

I recently tried to set up a local server, by following a apparently out off date manual and a xubuntu. Didn't work at all, and i had a lot of problems setting it up.

I would like to set up a local file server, with should be able to access from any computer on the local network (I don't know anything about the Internet protocols 'n' stuff, so you just got it in plain English).

I'm not an veteran Linux user, but if anything is explained, i would be able to do it.

Can you help me guys? Also with connecting from other machines (both linux and windows, the windows ones i would like to have a really easy to use interface, maybe integrated into explore or something)

Hope you can help me out of this mess:)

---

### Post by gobbledigook on 2010-06-06
hey there!

to share files you simply need to install [_**samba**_]("https://help.ubuntu.com/community/SettingUpSamba") you can administer from the cli using termial or putty from anywhere... but from the sound of your post, you are more comfortable with a gui. 

So in addition to samba you could install xbuuntu as a minimal desktop and use vncserver to share it to any other pc by using a vnc client. 

see  [**_here_**]("https://help.ubuntu.com/community/VNC") for more info on that :)

---

### Post by Alseimik on 2010-06-07
thanks gobbledigook.

I got a reply on another forum, where one told me that Samba could use the same protocol as windows, and therefore it would be able to just use the windows lan connector. Is the guy right?:confused: i didn't found it anywhere i looked!

---

### Post by clrg on 2010-06-07
Hello Alseimik

I really can't believe you didn't find the answer to that.

The answer is yes. Samba uses the CIFS (Common Internet File System, sometimes also called SMB, Server Message Block), which can be accessed by Linux, Solaris, Windows, HP-UX, VMS, AIX and others.

---


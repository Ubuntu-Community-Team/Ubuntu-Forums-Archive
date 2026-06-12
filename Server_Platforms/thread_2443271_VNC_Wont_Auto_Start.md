---
title: "VNC Wont Auto Start"
date: 2020-05-13
forum: Server Platforms
---

### Post by jonesy112233 on 2020-05-13
Hi Ubuntu Guru's!

I need some assistance if you would be so kind. 
I have been given the task of setting up TightVNC on a new server. Server OS Ubunutu 16.04
I have installed the app and it loads if i complete the standard command in terminal

# vncserver :1 

I then went further and setup a systemd service. 
The server is registered and enable and attempts to start as it should but instantly moves into a "Dead" status. 
Looking at the journalctl I can see 

pam_systemd(login:session): Failed to release session: Access Denied 
Rejected send message, 2 matched rules; type="method_call", sender="x.xxx" (uid=xxxx pid=xxxx comm="(sd-                                 ") interface"org.freedesk

When looking at the vnc log I see the following detail:
Listening for VNC Connections on TCP Port 5901
/usr/bin/startxfce4: X Server already running on display :1

This error occurs even if I try to change the display to :2 :3 :4 etc. 

I am almost certain this is a permission issue but I have no clue where to go to resolve from here. 
Help please !!!

Thanks

---


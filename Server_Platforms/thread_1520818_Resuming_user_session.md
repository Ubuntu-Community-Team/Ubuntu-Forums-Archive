---
title: "Resuming user session"
date: 2010-06-30
forum: Server Platforms
---

### Post by gtirtha on 2010-06-30
Hi all,

I am currently in a project to set up an LTSP server with 10 thin clients. I am using Ubuntu 9.10 (Karmic).

Installing server and booting clients are working fine.

Now, according to the need, I have to restrict user session numbers and allow resuming previous user session.

I have achieved to do the first one, but still could not able to setup the second one. As per requirement, if some thin can have power failure, the same session should be restored back.

I am confused here, if I need to focus on saving xsessions or saving gnome sessions.

Any one has any idea on this. I am looking for a concrete solution as I am running out of time.

Thanks in advance.
regards,

---

### Post by gtirtha on 2010-07-06
Ok after waiting a lot :( for any reply, I tried myself and found that if I can wrap gnome session through VNC or NX or Citrix like stuff, and then I can achieve a resumable session.

I followed some ideas, got in Internet and finally able to show up gnome login through VNC at thin clients booting.:D

I have added only one service of VNC on port 5901 on server and passed SecurityTypes=None in VNC parameter assuming GNOME login will check for authorization.

Now, if one user logs in using a thin client, others are unable to log in to server. I guess, as each thin client will try to log in to server using "vncviewer server.name:1" (this I placed in .xinitrc file in an infinite loop) and if one has occupied others will be refused. :mad:

But my intention is to allow all users to go through this and allow to have their independent sessions. 

I am really lost here, couldn't understand how to do the same :confused:. I understand that I can use different port for different users, but this is not a generic idea as users can keep growing. 

I can provide the steps to  what I did if required.
Any single idea will be highly appreciated. Any solution other than VNC will work for me too.
This time I am really expecting some response at least. :frown:
Thanks in advance.

---


---
title: "Ubuntu Terminal Server like Windows 2003 Server"
date: 2010-02-15
forum: Server Platforms
---

### Post by tam3105 on 2010-02-15
Hi,

I have installed *ubuntu*-*9.10*-*alternate*-*amd64 (Karmic Koala)* on DELL server. I want to access this server from more than one windows xp and puppy linux systems through terminal services at a time.

Is it possible to configure Ubuntu terminal server like windows 2003 server in the above mentioned OS?

Could anyone help me to configure Ubuntu Terminal server?

Thanks in Advance...

---

### Post by kiranmurari on 2010-02-16
Hi,

You can use LTSP (Linux Terminal Server Project)

Please find below the link on community documentation regarding LTSP.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Let me know if you face any issues during setup.

---

### Post by tam3105 on 2010-02-20
Hi,
Thanks for your reply. Now i have configured LTSP server on DELL system and came to know that it is a diskless booting of client systems.
We know that from any client (wind.XP-remote desktop connection, puppy linux & GOS-terminal server client), we can connect windows 2003 server after enabling terminal services. is it possible in Ubuntu to connect from various types of client systems at a time?

Using VNC, only one user can use the server at a time. 

for example **XMING**, link is given for your reference.

[http://ajopaul.com/2007/11/23/remote-login-to-linux-from-windows-non-vnc](http://ajopaul.com/2007/11/23/remote-login-to-linux-from-windows-non-vnc)

---

### Post by cariboo on 2010-02-20
The Ubuntu server doesn't have a gui, so all you need is ssh, there are clients for Windows and OSX. If you have a gui installed, use vnc which is installed by default on Ubuntu systems, free clients are available for other operating systems.

---

### Post by tam3105 on 2010-02-21
You meant that there is no option to take a remote connection from more than client systems at a time except VNC.

It would great support, if you suggest the OS type and version to make linux terminal server (like windows 2003 terminal server). 
Please help for the above. Thanks in advance.

---

### Post by redmk2 on 2010-02-22
> **tam3105 said:**
> ...
It would great support, if you suggest the OS type and version to make linux terminal server (like windows 2003 terminal server). 
Please help for the above. Thanks in advance.

I think what you want is to run X-server apps remotely.This would be the ability to run GUI apps from a server on remote hosts.

For basic information see [**_[COLOR="Navy"]here[/COLOR]_**]("http://tldp.org/HOWTO/Remote-X-Apps-9.html").

The basic Google search would be [**_[COLOR="Navy"]remote + x-server[/COLOR]_**]("http://www.google.com/search?q=remote+x-server&btnG=Go!.").

You would need something like [**_[COLOR="Navy"]X-ming[/COLOR]_**]("http://www.straightrunning.com/XmingNotes/") if you want to run Linux X apps on a Windows XP/Vista host.

---

### Post by tam3105 on 2010-03-12
Yes. I have installed and used XMING for both of ubuntu and XP systems. But XMING allows only two users can login at a time from XP system.
And now I can able to login in Ubuntu using XDMCP from other linux systems only. From XP systems any other possibilities to use XDMCP? or any other way?

---


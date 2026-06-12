---
title: "Make a Login Server (Like Windows Server 2008)"
date: 2013-09-29
forum: Server Platforms
---

### Post by computawhizze39 on 2013-09-29
Hi i was wandering how do i make a server I could login to using a different computer with a GUI interface!

Please HELP!

---

### Post by nerdtron on 2013-10-01
What would you do with the GUI of the Server? I can't of any setting you can change from that GUI that you can't change on the command line, unless you are going to write long documents and reports using the server.

Anyway, have you tried using your ubuntu desktop to navigate the file system of the server?
You can use nautilus/file manager to browse the file heirarchy of the server. It may almost feel like you are browsing a local directory.
In the location bar of the file manager, type sftp://username@IPaddress:/home/username 
Enter your password and you're good to go. Be sure that the ssh service on the server is running and you can ssh to it in the terminal.

---

### Post by CharlesA on 2013-10-01
Another option is Samba for file sharing, but it's a bit more.. complicated to set up than ssh/sftp.

---

### Post by 1clue on 2013-10-01
I'm not exactly sure what you're talking about.

Do you mean something like remote desktop, where you get a desktop on a remote server?  If so, then you might try [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp)

Or do you mean a central login server like a Windows domain controller?  If that's the case, then you might try [https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

If you're talking about getting a remote desktop type of session, then strictly speaking nerdtron is right.  That said, the Windows/Mac people at my office can't seem to figure it out.  You would want to use something like this:

ssh -X 192.168.1.100 
<password> 
Xnest :1 -geometry 1920x1050 -query localhost

---

### Post by computawhizze39 on 2013-10-21
Thanks for all your help

---


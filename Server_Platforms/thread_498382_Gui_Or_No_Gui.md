---
title: "Gui Or No Gui"
date: 2007-07-11
forum: Server Platforms
---

### Post by guilly on 2007-07-11
Hey guys. 

Heres my situation i'm not that familiar when it comes to linux but I've managed to create an FTP server out of my Old PIII. My future plans are to also make a Print server, my question is now that i've created teh ftp server which i did thru proftp and not gproftp, should i unistall GNOME completly and then attempt to install CUPS and any necessary drivers? Or install all of that and then Uninstall GNOME. 

I would liek to do it without the GUI at all but i find that sometimes i need to resort to the GUI for assistance since i am quite the newbie at this


thanks for any advice

---

### Post by stalker145 on 2007-07-11
> **guilly said:**
> Hey guys. 

Heres my situation i'm not that familiar when it comes to linux but I've managed to create an FTP server out of my Old PIII. My future plans are to also make a Print server, my question is now that i've created teh ftp server which i did thru proftp and not gproftp, should i unistall GNOME completly and then attempt to install CUPS and any necessary drivers? Or install all of that and then Uninstall GNOME. 

I would liek to do it without the GUI at all but i find that sometimes i need to resort to the GUI for assistance since i am quite the newbie at this


thanks for any advice

Personally, I would say to leave the GUI for now - you can always remove it later. Of course, I'm the type that tests the water before I jump in. 
You can always pull the monitor from the server and VNC, RDP, SSH, etc into the box to do any administration. Also, you shouldn't even need to log in to get the desired services running (from my experience with Apache) and that would mean that your desktop wouldn't even load into RAM. Best of both worlds in my opinion.

---

### Post by guilly on 2007-07-11
Alright thanks for the prompt reply. 

I'm actually already using VNC to log in. Which brings up another good point. When i boot up the server for me to be able to VNC into the system i need to be logged in, is there a way to remove the log on prompt to allow Ubuntu to log me in automatically ??? I'm not worried about security too much, the server is in my appartment right beside me

---

### Post by stalker145 on 2007-07-11
> **guilly said:**
> is there a way to remove the log on prompt to allow Ubuntu to log me in automatically ???

Yes, this is possible. Just go to the same place you change the login screen (I believe it is Preferences~>Login) and click the security tab. You should find options for immediate and timed automatic logins.

---

### Post by guilly on 2007-07-11
> **stalker145 said:**
> Yes, this is possible. Just go to the same place you change the login screen (I believe it is Preferences~>Login) and click the security tab. You should find options for immediate and timed automatic logins.

Alright thanks for the help!!!

---


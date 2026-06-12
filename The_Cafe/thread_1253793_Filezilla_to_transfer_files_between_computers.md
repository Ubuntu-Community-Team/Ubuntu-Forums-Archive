---
title: "Filezilla to transfer files between computers?"
date: 2009-08-30
forum: The Cafe
---

### Post by cody7002002 on 2009-08-30
Is this possible? So that I can access files on my desktop computer from my laptop computer?

---

### Post by Kingsley on 2009-08-30
Sure. Set up an FTP server on either computer.

---

### Post by cody7002002 on 2009-08-30
How do I do that? Does it make a difference if one computer is running windows and the other ubuntu?

---

### Post by Kingsley on 2009-08-30
On Ubuntu, I would use vsftpd to set up an FTP server. Search the forum for a good guide. I'm not sure of what to use on Windows. But it doesn't matter which OS you use to connect to the FTP server.

---

### Post by cariboo on 2009-08-30
I use filezilla and sftp. If you have openssh-server installed you don't need anything else. Filezilla is in the repositories, and there is a free windows client available.

You can use sftp with nautilus too.

---

### Post by madjr on 2009-08-30
am also interested in this since network sharing windows (vista, win7, not xp) + linux = Fail

---

### Post by cody7002002 on 2009-08-30
so what program is recommended to set up a file server on my windows desktop?

---

### Post by madjr on 2009-08-30
> **cariboo907 said:**
> I use filezilla and sftp. If you have openssh-server installed you don't need anything else. Filezilla is in the repositories, and there is a free windows client available.

You can use sftp with nautilus too.

how would you connect and browse?

how is the speed?

---

### Post by Frak on 2009-08-30
> **cody7002002 said:**
> so what program is recommended to set up a file server on my windows desktop?
Filezilla

---

### Post by chris4585 on 2009-08-30
> **madjr said:**
> how would you connect and browse?

how is the speed?

If you have openssh-server installed on Ubuntu for the computer you want to serve files, then on another computer go to Places > Connect To Server > and select SSH etc.. with filezilla on windows just connect via sftp

---

### Post by madjr on 2009-08-30
> He was trollin'! Trolls, trolls. I'm not trollin'! He was trollin'! Trooools. I'm not trollin'!

who is boxxy and why she got so many views =o

---

### Post by Frak on 2009-08-30
> **madjr said:**
> who is boxxy and why she got so many views =o
A girl and why not?

---

### Post by cody7002002 on 2009-08-30
Alright, I think I have everything set up properly. I set up everything on filezilla on windows with a tutorial then I connected to the server on my ubuntu laptop and I was able to access all the folders like I specified. Is there anything else I need to know about maintaining/accessing the server?

How do I unmount the server?

---

### Post by madjr on 2009-08-30
> **Frak said:**
> A girl and why not?

this one is nUtz

---

### Post by Frak on 2009-08-30
> **cody7002002 said:**
> Alright, I think I have everything set up properly. I set up everything on filezilla on windows with a tutorial then I connected to the server on my ubuntu laptop and I was able to access all the folders like I specified. Is there anything else I need to know about maintaining/accessing the server?

How do I unmount the server?
It should auto-unmount when you are done. It is only active when a file query or transfer is active.

---

### Post by cody7002002 on 2009-08-30
ah, well I just tried to copy a file from my fileserver to my laptop and the file operation seems to be stuck... It says 1.7KB of 1.75KB have been copied but the file operations box is still up. I clicked on the red X to cancel it but now its just stuck. What do I do?

---

### Post by cody7002002 on 2009-08-30
I think that something is going wrong somewhere along the line. I connect to the server then I go in and copy a file from the server to my laptop. The copying file dialog box comes up and shows the progress of the copying. It went to 100% but the box doesn't close. I press the x and nothing happens. It seems to be hung up on it. Then I notice that after a few minutes on my filezilla server it says the connection has timed out.

What's going on here?

---

### Post by madjr on 2009-08-30
> **cody7002002 said:**
> I think that something is going wrong somewhere along the line. I connect to the server then I go in and copy a file from the server to my laptop. The copying file dialog box comes up and shows the progress of the copying. It went to 100% but the box doesn't close. I press the x and nothing happens. It seems to be hung up on it. Then I notice that after a few minutes on my filezilla server it says the connection has timed out.

What's going on here?

time to hack in

---

### Post by chris4585 on 2009-08-30
> **madjr said:**
> who is boxxy and why she got so many views =o

boxxy is awesome

---

### Post by cody7002002 on 2009-08-30
After it says the connection timed out and on my laptop I try to connect back to the server  I get the error

Could not open location "*server address here*"
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by madjr on 2009-08-30
> **cody7002002 said:**
> After it says the connection timed out and on my laptop I try to connect back to the server  I get the error

Could not open location "*server address here*"
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

this is from windows to linux; linux to windows; linux to linux ; other?

---

### Post by cody7002002 on 2009-08-30
Windows computer has filezilla server installed on it.

On my ubuntu computer I go to places>connect to server then put in the proper information and it connects. I'm noticing that after a few minutes the server times out leaving me to have to restart the computer

---

### Post by DigitalDuality on 2009-08-30
> **cody7002002 said:**
> Is this possible? So that I can access files on my desktop computer from my laptop computer?

this is much easier with ssh, that way you have ssh, sftp and scp options open to you and never have to fire up a graphical client.

putty, filezilla, and/or winscp though would be good options on windows

---

### Post by FuturePilot on 2009-08-30
> **cody7002002 said:**
> Windows computer has filezilla server installed on it.

On my ubuntu computer I go to places>connect to server then put in the proper information and it connects. I'm noticing that after a few minutes the server times out leaving me to have to restart the computer

Might be this bug [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/366073]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/366073")

---

### Post by madjr on 2009-08-30
the latest (today) full circle mag has some nice articles on networking, servers, lamp and sshfs and the 1 before talks about home servers :)

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by cody7002002 on 2009-08-31
Futurepilot that is exactly the problem I am having. Appears there's no fix in jaunty =/

---

### Post by cariboo on 2009-08-31
Your problem is not related to the bug quoted above. The bug report is for ftp, not sftp, as they are two different processes.

Have a look in /var/log/auth.log to see if there is any indication of what is happening.

---

### Post by cody7002002 on 2009-08-31
I'm looking in the log file but I really don't know what I'm supposed to be looking for

---

### Post by gn2 on 2009-08-31
Cheat, use [Adrive]("http://www.adrive.com").

---

### Post by FuturePilot on 2009-08-31
> **cariboo907 said:**
> Your problem is not related to the bug quoted above. The bug report is for ftp, not sftp, as they are two different processes.

Have a look in /var/log/auth.log to see if there is any indication of what is happening.

I'm pretty sure the OP is using FTP and not SFTP.
AFAIK Filezilla server does not provide SFTP on Windows.

---

### Post by madjr on 2009-08-31
> **cody7002002 said:**
> Windows computer has filezilla server installed on it.

On my ubuntu computer I go to places>connect to server then put in the proper information and it connects. I'm noticing that after a few minutes the server times out leaving me to have to restart the computer

have you tried in kde/dolphin?

seems that [bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/366073") is linked to gvfs (gnome/nautilus)

install kubuntu-desktop

else you may want to do normal [networking]("http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/")

---


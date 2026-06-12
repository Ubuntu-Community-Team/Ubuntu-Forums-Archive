---
title: "Installing Linux on a Dell 725N NAS Device"
date: 2010-05-17
forum: Server Platforms
---

### Post by uknowho008 on 2010-05-17
I have a Dell Powervault 725N NAS Server and I would very much like to install Linux on it. It currently has Windows 2000 Server, thats gotta go. How can I do this? I'm unsure about whether it will boot from a usb or not... :( but I'm afraid it's not going to be that easy? Any ideas? or should I just forget it? I would like VMware ESXI except it doesn't support USB :(

Thanks guys, just wondering what you think or if anybody has any ideas.

---

### Post by creamers on 2010-05-17
Here is a thread that will help.

[http://ubuntuforums.org/showthread.php?t=690483](http://ubuntuforums.org/showthread.php?t=690483)

You need to have anouther Mac or Linux box with tftpboot and a dhcp server on it. You then use Pxe boot on the server to install ubtunu.

---

### Post by uknowho008 on 2010-05-18
Oh that's perfect, I figured a netboot was going to be the only way, but I was dreading getting that involved in something I wasn't even sure was going to work. But he's using the same exact system so I guess I'll dive ride in now. Thanks a ton.

---

### Post by uknowho008 on 2010-07-20
Where can I find the netboot files for 10.04 server?

---


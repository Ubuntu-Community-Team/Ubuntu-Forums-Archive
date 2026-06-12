---
title: "Need Suggestions on Server Setup"
date: 2011-03-28
forum: Server Platforms
---

### Post by _joecrawford on 2011-03-28
I bought a solid Dell from work when we upgraded to new machines.  The box has been sitting mostly unused for a long time and I would like to make a home server on it.  I have no idea how to this and what distro to use.  I could use some serious help!  Anything would be appreciated.  I honestly don't even know what I am looking for in a server.  Thank you for helping out!

---

### Post by wojox on 2011-03-28
Install 10.04 on it. [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

---

### Post by papibe on 2011-03-28
I installed Ubuntu Server 10.04 on a refurbish PC, and works fantastic as a home server (although I added more disks over time).

These are some things you can use your home server for:
[LIST]
[*]File Server. You can share files between computers easily. Use it to back up your desktop/laptop files on it. Store you media on it so it could be available from any computer/devices on your house.
[*]Download server. So you can turn off your desktop/laptop at night and leave the work for the server. For direct downloads you can use something like wget or curl. For bittorrent you can install transmission-daemon and control it remotely using your firefox.
[*]Stream media. If you have restricted devices that can play media but don't use network shares (like PS3, Xbox, etc.), you can stream the media to them. MediaTomb could a a simple solution to do that.
[/LIST]

I hope this helps. You would have to be prepared to learn new things, because most of the config/admin is done by using the terminal.

Good Luck!

---

### Post by Z.K. on 2011-03-29
> **_joecrawford said:**
> I bought a solid Dell from work when we upgraded to new machines.  The box has been sitting mostly unused for a long time and I would like to make a home server on it.  I have no idea how to this and what distro to use.  I could use some serious help!  Anything would be appreciated.  I honestly don't even know what I am looking for in a server.  Thank you for helping out!

I used 10.04 and it was fairly easy to set up with some excellent guides on the Internet.  I used Samba to share my files with other machines both Linux and Windows.  I also have a DHCP server on it though it is not necessary with modern routers.  At one time I even had a tftp boot server for imaging other machines with various operating systems, but when I reimaged I did not install tftp.  There are many things it can be use for though file sharing, multmedia such as video and audio, seems to be the most of what a home server is used for.  You could also use cups for your printers.  I have a usb printer attached to my server.

Oh, if you only use the server with a command line like I do, you might want to install a way to automount your USB devices.  I used autofs though there are other ways to do it.  If you installed the desktop, it is probably not necessary.

Good luck and have fun  :)

---

### Post by _joecrawford on 2011-03-29
Thank you for the help everyone.  I will have a new weekend project now!  I will post when I am stuck, or hopefully, done!

---


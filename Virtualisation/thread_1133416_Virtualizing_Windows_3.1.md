---
title: "Virtualizing Windows 3.1"
date: 2009-04-22
forum: Virtualisation
---

### Post by RealG187 on 2009-04-22
I have Windows 3.1 running in a VM. It's something I always wanted to do. I remembered my days using it and wanted to return to the past. Seeing it now I was like how could I use to use this? Maybe having running in a window isn't good and fullsize full screen would help (this possible).

But anyways how can I exchange files between host and guest. This OS is so old I doubt samba is an option ([I can hardly do that with Windows 98 which is like 6 years newer)]("http://ubuntuforums.org/showthread.php?t=1131486"). Could access the virtual hard drive in Ubuntu or have a folder on the host mounted as a harddrive in the VM (this would also help for the Windows 98 problem I am having too).

I wonder also is there a web broswer that would work? I always wanted to try surfing the net in 3.1!

---

### Post by parkland on 2009-04-22
netscape navigator, i remember using 3.1 wfw and netscape.

---

### Post by jflaker on 2009-04-22
> **RealG187 said:**
> I have Windows 3.1 running in a VM. It's something I always wanted to do. I remembered my days using it and wanted to return to the past. Seeing it now I was like how could I use to use this? Maybe having running in a window isn't good and fullsize full screen would help (this possible).

But anyways how can I exchange files between host and guest. This OS is so old I doubt samba is an option ([I can hardly do that with Windows 98 which is like 6 years newer)]("http://ubuntuforums.org/showthread.php?t=1131486"). Could access the virtual hard drive in Ubuntu or have a folder on the host mounted as a harddrive in the VM (this would also help for the Windows 98 problem I am having too).

I wonder also is there a web broswer that would work? I always wanted to try surfing the net in 3.1!

Use FTP to get and put the files as needed.  Though I doubt there would be anything useful you could create in Win3.1 and conversely, anything that you could create in current apps that would be readable by Win3.1

---

### Post by aesis05401 on 2009-04-22
Navigator came out towards the end of 3.1 distribution time-frame.  The original Mosaic base was around in 92 when 3.1 made its debut, but I have no idea how well it worked.

IE came out in '95, but I don't recall  if it ran on 3.1.

---

### Post by RealG187 on 2009-04-23
Can you do FTP on Windows 3.1? Does Windows 3.1 support LAN or only dialup? Would I have to create a virtual dialiup connectio that connects lets say [ftp://host.com](ftp://host.com) to the folder on the host and all other sites to the internet using my Laptop's Wifi.

---

### Post by jflaker on 2009-04-26
> **RealG187 said:**
> Can you do FTP on Windows 3.1? Does Windows 3.1 support LAN or only dialup? Would I have to create a virtual dialiup connectio that connects lets say [ftp://host.com](ftp://host.com) to the folder on the host and all other sites to the internet using my Laptop's Wifi.

There was a whole add on to DOS to get a TCP/IP stack....with that, I believe, was a command line FTP client.  If I remember right, there wasn't anything really useful as far as networking until Windows for Workgroups (Windows 3.11) unless you were using Novell Netware and IPX network protocol.

---

### Post by HermanAB on 2009-04-26
Hmm, you need the old Trumpet TCP/IP network stack.  It took Microsoft some time to copy a network stack from FreeBSD and drive Trumpet out of business, so Win3.1 doen't do TCP/IP out of the box.  Maybe you can bum something off the FreeDOS distribution.

---

### Post by RealG187 on 2009-04-28
What's the trumpet TCP/IP network stack?

---


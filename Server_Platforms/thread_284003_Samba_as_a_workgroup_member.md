---
title: "Samba as a workgroup member?"
date: 2006-10-25
forum: Server Platforms
---

### Post by Kensey on 2006-10-25
This is not strictly an Ubuntu question, but Ubuntu comes into it since I want my Ubuntu laptop to be able to connect to this as well.

I have a Debian server (crowley) on my LAN.  I want it to provide file shares for users with accounts, but I don't want it to create any kind of domain or be any kind of domain controller.  Basically I just want it to be a member of the workgroup MORNINGSTAR and serve files (and maybe, later on, a printer or two) so my wife can use my Linux server (which has the biggest disks in the house) for file storage.

I did a default install of samba 3.0.14a-Debian (the version in sarge).  I have an entry in /etc/smbpasswd for myself:

kensey = kensey

and I set the smbpasswd for kensey as root, so I know I've got that right.

When I browse to the server IP from a Windows XP box that's also a member of MORNINGSTAR, I get prompted for my username and password.  If I fill the username in as kensey and give the password, the prompt returns with MANSON\kensey (the XP box is named manson).  Trying as crowley\kensey or 192.168.1.2\kensey fail as well.

I don't know if it has any bearing, but when I try to change my smbpasswd on crowley as user kensey (rather than doing it for kensey as root) I get the following error:

cli_nt_session_open: cli_open failed on pipe \PIPE\samr to machine 127.0.0.1.  Error was ERRSRV - ERRaccess (The requester does not have  the  necessary  access  rights  within  the specified  context for the requested function. The context is defined by the TID or the UID.)
machine 127.0.0.1 rejected the password change: Error was : RAP86: The specified password is invalid.
Failed to change password for kensey

Is there something simple I'm missing to get this to work?

---


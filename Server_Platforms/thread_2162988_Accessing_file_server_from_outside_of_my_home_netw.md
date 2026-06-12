---
title: "Accessing file server from outside of my home network."
date: 2013-07-16
forum: Server Platforms
---

### Post by TheInfamousAlk on 2013-07-16
I have a samba file server that I set up at my house. I am able to access it from my internal network, and it works fine. I have ports 139 and 445 forwarding to my server, and *everything* has a static ip address. I am using the newest version of lubuntu, and I am also using webmin to manage my server because it's easier than the actual lubuntu UI. I need to be able to access this file server from outside my network; from anywhere over the internet. I do not want it password protected, (It wouldn't be a problem if it has to be) and I want anyone anywhere to be able to access it. I am not very experienced in linux at *all*. I managed to set up the samba server using webmin and lots and lots of forums, but now I'm stuck.


Any ideas on how I could get it working, or any alternatives that would achieve the same desired result?



(Edit: I am at work right now, so I will reply later.)

---

### Post by newbie-user on 2013-07-16
FTP is easy for anonymous downloads: [https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)

---

### Post by SeijiSensei on 2013-07-16
Forget samba over the Internet.  It's way too insecure.

Install **openssh-server** on your server, then [forward](http://portforward.com/) some arbitrary high port (>1023) on your router back to port 22 (SSH) on your server.  Suppose the port is 22222.  Now you have a number of options available to you.

On Windows machines, use [WinSCP]("http://winscp.net/eng/index.php").

On Linux machines, use the "fish" protocol.  Enter a URL like "fish://username@server.example.com:22222/" in a file manager like Nautilus or Dolphin.  You should see the remote's directory appear after you enter username's password.  You will then have all the rights available to "username".  Alternatively, you can permanently mount the remote to the list in /etc/fstab using the [sshfs]("https://help.ubuntu.com/community/SSHFS") protocol.

Android phones have SSH, SFTP and SCP clients as well.  Some of them like AndFTP require you spend $2-5 to buy the "pro" versions to use SCP.

If you let everyone and his brother upload and download files from your server like you suggested, it will eventually be discovered and turned into a site to share illicit files.  You don't want to see the FBI at your door asking about those pictures of children engaged in indecent acts that they discovered on your server.

If you want to distribute files to the public, use a web server.

---

### Post by SchnappiJedi on 2013-07-16
> **TheInfamousAlk said:**
> I have a samba file server that I set up at my house. I am able to access it from my internal network, and it works fine. I have ports 139 and 445 forwarding to my server, and *everything* has a static ip address. I am using the newest version of lubuntu, and I am also using webmin to manage my server because it's easier than the actual lubuntu UI. I need to be able to access this file server from outside my network; from anywhere over the internet. I do not want it password protected, (It wouldn't be a problem if it has to be) and I want anyone anywhere to be able to access it. I am not very experienced in linux at *all*. I managed to set up the samba server using webmin and lots and lots of forums, but now I'm stuck.


Any ideas on how I could get it working, or any alternatives that would achieve the same desired result?



(Edit: I am at work right now, so I will reply later.)

You have two options:

1.) Access your files via SFTP (using Filezilla, [https://filezilla-project.org/](https://filezilla-project.org/),  or other FTP client reference above)
2.) Access your files via SSHFS ([http://code.google.com/p/win-sshfs/](http://code.google.com/p/win-sshfs/))

Both of these options will require a password. I think option two will work better for you as it will show up as a "drive" like you are used to. All of this is assuming that you have a SSH server set up. If you would like any clarification on anything that I have said please do let me know. I know that it is hard to take in everything that people are suggesting.

Bottom line, SSHFS is the way to go (short of setting up a VPN server).

---

### Post by TheInfamousAlk on 2013-07-17
Thanks! I will try setting up an ssh server when I get home.

---

### Post by SchnappiJedi on 2013-07-17
Good luck. Ubuntu makes it really easy to build a ssh server. The hard part is figuring out permissions once you gain access via SSH.

---

### Post by CharlesA on 2013-07-17
> **TheInfamousAlk said:**
> Thanks! I will try setting up an ssh server when I get home.

Check out this page: [https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)

There are also links that give information on how to secure it.

> **schnappi2 said:**
> Good luck. Ubuntu makes it really easy to build a ssh server. The hard part is figuring out permissions once you gain access via SSH.

Agreed. It's one of those services that is pretty much dead simple to install/setup on any flavor of *nix.

---

### Post by nerdtron on 2013-07-18
Install open-ssh-server on the server machine.
And then you can use FileZilla anywhere on the internet to access your file server.
All done.

Security, firewall, etc. that's another problem :)

---


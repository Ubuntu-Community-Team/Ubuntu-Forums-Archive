---
title: "File server"
date: 2011-03-11
forum: Server Platforms
---

### Post by 4eva on 2011-03-11
Hey,

I am new to ubuntu and I have an old laptop (Intel core duo T2250 1.73Ghz, 2Gb ram and 160Gb harddisk) want to use it as a file server for windows 7 and windows xp (maybe ubuntu in next few months) via lan. Preferably to work with Ubuntu desktop 10.10 as I am also using dropbox and wireless network along with it.

I tried the following guide [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) but did not work.

Is there newer guide for ubuntu 10.10 or a newbie friendly guide ? Do share it with me.

Thanks ! ;)

---

### Post by HermanAB on 2011-03-11
Howdy,

There are many ways to share files with Windows.  In order of increasing difficulty:
1. FTP
2. SSH/SFTP
3. NFS
4. Samba

For FTP, install any FTP server on Linux and install FileZilla on Windows.  It should work out of the box with zero extra configuration.

For SSH/SFTP, install ssh-server on Linux and install FileZilla on Windows.   It should work out of the box with zero extra configuration.

For NFS, install nfs server on Linux and install UNIX Services for Windows on Windows (Free download from Microsoft).  Unlike the previous two, NFS requires one line of configuration, so it is almost trivial to set up.

For Samba, go to the Samba web site and read the manual.  Getting Samba to work is about 100 times more difficult than NFS. The whole Samba book is about 2 inches thick, so good luck with that one...

---

### Post by 4eva on 2011-03-11
> **HermanAB said:**
> Howdy,

There are many ways to share files with Windows.  In order of increasing difficulty:
1. FTP
2. SSH/SFTP
3. NFS
4. Samba

For FTP, install any FTP server on Linux and install FileZilla on Windows.  It should work out of the box with zero extra configuration.

For SSH/SFTP, install ssh-server on Linux and install FileZilla on Windows.   It should work out of the box with zero extra configuration.

For NFS, install nfs server on Linux and install UNIX Services for Windows on Windows (Free download from Microsoft).  Unlike the previous two, NFS requires one line of configuration, so it is almost trivial to set up.

For Samba, go to the Samba web site and read the manual.  Getting Samba to work is about 100 times more difficult than NFS. The whole Samba book is about 2 inches thick, so good luck with that one...

Oh.. do you have any guide/how to link for NFS ? :popcorn:

---

### Post by Lars Noodén on 2011-03-11
> **HermanAB said:**
> Howdy,

There are many ways to share files with Windows.  In order of increasing difficulty:
***1. SSH/SFTP***
2. FTP
3. NFS
4. Samba
...

HermanAB, SFTP is built in as part of SSH, so on the set up, it is worlds easier than setting up FTP.  As a bonus, SSH is probably already on the server, so in that case no extra server software is needed.  There are also [more built-in SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) around these days than you can shake a stick at.  SSHFS is one of the cooler options.

---

### Post by Lars Noodén on 2011-03-11
> **4eva said:**
> Oh.. do you have any guide/how to link for NFS ? :popcorn:

When I last set up [Samba](https://help.ubuntu.com/community/Samba), which was a while ago now, it was not that difficult.  So my vote is for Samba rather than NFS. YMMV

---

### Post by 4eva on 2011-03-11
Oh thanks I would give everything a try. Which ever work for me I would just go along with it first. Just curious, which of these setup would appear as a drive on another pc ? :popcorn:

---

### Post by volkswagner on 2011-03-11
If you want to map a network drive in Windows, SAMBA would be my choice.

Howtoforge.com has many tutorials.  [Here is one for SAMBA]("http://www.howtoforge.com/ubuntu-10.10-samba-standalone-server-with-tdbsam-backend") and a [second with SAMBA using SWAT]("http://www.howtoforge.com/how-to-set-up-a-webgui-based-print-server-on-ubuntu-server-using--swat-cups-and-samba") plus CUPS for sharing printers.

Enjoy!

---

### Post by 4eva on 2011-03-11
> **volkswagner said:**
> If you want to map a network drive in Windows, SAMBA would be my choice.

Howtoforge.com has many tutorials.  [Here is one for SAMBA]("http://www.howtoforge.com/ubuntu-10.10-samba-standalone-server-with-tdbsam-backend") and a [second with SAMBA using SWAT]("http://www.howtoforge.com/how-to-set-up-a-webgui-based-print-server-on-ubuntu-server-using--swat-cups-and-samba") plus CUPS for sharing printers.

Enjoy!

I tried the first guide but I could not connect to the ubuntu pc using windows pc through \\192.168.0.102\home :confused:

Where have I done wrong ? I am using a d-link router and have set DHCP / fixed ip address (192.168.0.102) to the ubuntu pc.

---

### Post by Lars Noodén on 2011-03-12
> **4eva said:**
> Just curious, which of these setup would appear as a drive on another pc ? 

Any of them except FTP.

If you go with SFTP, then if you connect using SSHFS the remote machine will look like another folder on the drive.  

I'd try SFTP first, then Samba.  However, Samba will make the machine just like any other SMB/CIFS server, if that's what you want.

---

### Post by 4eva on 2011-03-12
> **Lars Noodén said:**
> Any of them except FTP.

If you go with SFTP, then if you connect using SSHFS the remote machine will look like another folder on the drive.  

I'd try SFTP first, then Samba.  However, Samba will make the machine just like any other SMB/CIFS server, if that's what you want.

A special thanks to all for the help and tips !... I will mess with the machine until it works ! :KS

---

### Post by HermanAB on 2011-03-13
Howdy,

NFS only requires ONE line of configuration.  Samba has hundreds of line of configuration that can go wrong.

[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by 4eva on 2011-03-14
> **HermanAB said:**
> Howdy,

NFS only requires ONE line of configuration.  Samba has hundreds of line of configuration that can go wrong.

[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

Hi,

I mounted the file on ubuntu but I can't seem to map the network drive when using windows 7. Do you have any idea how to solve this ? :confused:

---

### Post by uRock on 2011-03-14
To mark as solved, please click on **[COLOR="Red"]Thread Tools[/COLOR]** at the top of the page and select to **Mark thread as solved**.

---

### Post by 4eva on 2011-03-14
> **uRock said:**
> To mark as solved, please click on **[COLOR=Red]Thread Tools[/COLOR]** at the top of the page and select to **Mark thread as solved**.

Opps sorry ! :(

---

### Post by uRock on 2011-03-15
> **4eva said:**
> Opps sorry ! :(

No need to apologize!:P

---


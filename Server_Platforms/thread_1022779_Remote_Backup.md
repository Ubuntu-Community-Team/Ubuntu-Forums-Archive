---
title: "Remote Backup"
date: 2008-12-27
forum: Server Platforms
---

### Post by raleysm on 2008-12-27
Is there any remote backup scripts that I can backup other share drives, servers or desktops to my ubuntu server drive?  I know that there are ftp scripts to do this but it would need to be something I can run on windows 2000/2003 servers, xp, etc as a scheduled task to send specified folders to my ubuntu server. Thanks

---

### Post by networkjedi on 2008-12-27
You could setup Samba on your Ubuntu server and create a share for your windows based servers to backup to.  The windows backup utility will allow you to backup files to a network share, just run the backup wizard, set what you want to backup and when in windows and away you go.

---

### Post by raleysm on 2008-12-27
Yes but I'm going to backup remotely so the ubuntu server is not on the same network as the machines I'm backing up. By remote I mean off-site.

---

### Post by hictio on 2008-12-27
Does it have to be transmitted over an encrypted channel? Or are you connected thru a VPN to the off-site server?
If encryption is not critical, you can use [Rsync for Windows](http://www.google.com/search?client=safari&rls=en&q=Rsync+for+Windows&ie=UTF-8&oe=UTF-8) on the Windows boxes, and setup an rsync server on the Ubuntu one.

If you have to encrypt the traffic, you can setup Cygwin or similar on the Window boxes, to tunnel the rsync traffic thru SSH, using public key authentication, ironically, doing that from Linux to Linux is trivial...

---

### Post by freebeer on 2008-12-27
I use DeltaCopy on the windows clients to backup to my ubuntu server, then rsync the Ubuntu server to my home server (Ubuntu, too).  It works well.

---

### Post by HermanAB on 2008-12-28
I install Cygwin on my Windows boxes and then use rsync over ssh, same as on a Unix machine.

Cheers,

Herman

---

### Post by windependence on 2008-12-28
You don't need any if this stuff. Both Amanda and Bacula can back up Windows boxes without SAMBA.

[http://wiki.zmanda.com/index.php/Zmanda_Windows_Client](http://wiki.zmanda.com/index.php/Zmanda_Windows_Client)

Here's what the Bacula page says:


[LIST]
[*]> Multi-Operating System Support
[*]Programmed to handle arbitrarily long filenames and messages.
[*]GZIP compression on a file by file basis done by the Client program  if       requested before network transit.
[*]Saves and restores POSIX ACLs on most OSes if enabled.
[*]Access control lists for Consoles that permit restricting user access       to only their data.
[*]Support for save/restore of files larger than 2GB.
[*]Support for 64 bit machines, e.g. amd64, Sparc.
[*]Support ANSI and IBM tape labels.
[*]Support for Unicode filenames (e.g. Chinese) on Win32 machines on          version 1.37.28 and greater.
[*]Consistent backup of open files on Win32 systems (WinXP, Win2003,           and Vista)          but not Win2000, using Volume Shadow Copy (VSS).
[*]Support for path/filename lengths of up to 64K on Win32 machines          (unlimited on Unix/Linux machines).
[/LIST]
 
[LIST]
[*]  
[/LIST]
 Also:

[http://www.bacula.org/en/dev-manual/Supported_Operating_Systems.html](http://www.bacula.org/en/dev-manual/Supported_Operating_Systems.html)


I personally like Amanda or Zmanda, but Bacula is fine too.

-Tim

---


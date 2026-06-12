---
title: "Samba Share between Ubuntu 18.04 Server &amp; Windows 10"
date: 2018-10-01
forum: Server Platforms
---

### Post by yuggniiks on 2018-10-01
I recently started over with my server, and installed 18.04.1 LTS.  I'm having trouble getting the Samba share with Windows 10 working.   I have tried both the steps shown in [COLOR=#000000][FONT=arial]**Ubuntu 18.04 LTS Server: Administration and Reference**[/FONT][/COLOR][COLOR=#999999][FONT=arial] – [/FONT][/COLOR][COLOR=#999999][FONT=arial]Richard Petersen [/FONT][/COLOR]as well as this post:  [http://www.ubuntuboss.com/how-to-set-up-windows-file-shares-in-ubuntu-18-04-with-samba/](http://www.ubuntuboss.com/how-to-set-up-windows-file-shares-in-ubuntu-18-04-with-samba/)  .

here is the bottom of my smb.conf file:

[ubuntu_windows_share]
  path = /mnt/share
  valid users = nala
  read only = no
  browsable = yes
  writeable = yes
  guest ok = no

When I try to connect from windows:  Using add network location and this format:

\\192.xxx.x.xx\share   

it gives "The folder you entered does not appear to be valid.  Please choose another.

Thanks in advance for any suggestions, or other sources :)

---

### Post by SeijiSensei on 2018-10-01
The share name is what you entered in brackets, "ubuntu_windows_share".  Try that instead of "share" or change the name in smb.conf.

If you install the smbclient package, you can use the command "smbclient -L 192..." to list the shares available to you on the server.

---

### Post by yuggniiks on 2018-10-01
Thanks SeijiSensei.

I tried "[COLOR=#000000]ubuntu_windows_share[/COLOR]" also, as well as changing the smb.conf name and trying that :(

I installed smbclient as you suggested (but gives a warning that the syslog option is deprecated) and it shows the share I have in smb.conf.

---

### Post by HermanAB on 2018-10-01
Ayup - if it doesn't work with smbclient, then it won't work with the target machine either.  Smbclient is a very valuable debug tool.  Look very carefully at the error messages and google them if you don't understand them.

---

### Post by SeijiSensei on 2018-10-03
I'm not sure underscores are supported in "UNC" share names.  Have you tried renaming "ubuntu_windows_share" to something shorter without underscores?

Have you looked at the samba logs?  I don't use Ubuntu on servers, but I believe the logs are in /var/log/samba.

---

### Post by yuggniiks on 2018-10-03
I've tried the share name without underscores, same outcome.

I'm finding that Windows 10 (i think fall creator edition) disabled SMBv1 due to security issues and they don't recommend using it (heartbeat bug i think??)

From Ubuntu 18.04 LTS Server by Richard Petersen:
> Accessing Samba Shares from Windows Accessing Samba shares from Windows is an issue for Windows 10 . Upgrades to Windows 10 has disabled the SMBv1 network browsing capabilities of Windows, as it transitions to SMBv3 from SMBv1. You could try to manually re-enable SMBv1 browsing, but SMBv1 is being disabled due to security issues. It is not advisable to re-enable it. This means you cannot simply browse a Linux host currently, but you can still easily set up access to each Samba shared folder on that Linux host. It is still easy to access your Samba Linux shares from Windows 10. You can simply add a new network location for it, that will be accessible from a shortcut you can set up for it on your Windows file manager "This PC" folder. To set up the shortcut, open the Windows file manager to any folder and right-click on the "This PC" entry in the sidebar to display a menu. Click on the "Add a network location" entry to open the "Add Network Location Wizard" and click Next. Click on the "Choose a custom network location" entry and click Next. In the text box labelled "Internet or network address:" enter the host name of your Linux system that holds the shares you want to access, beginning with the two backward slashes and followed by a backward slash (you may have to also enter the name of one of the shared folders on that system).

---

### Post by yuggniiks on 2018-10-04
Got it working.   
Not sure if I had my permissions wrong but got it working by mapping drives vs. right click on mycomputer and clicking 'add network location'


Followed this: [https://www.technig.com/share-file-between-ubuntu-and-windows/](https://www.technig.com/share-file-between-ubuntu-and-windows/)

---

### Post by slickymaster on 2018-10-04
*Thread moved to **Server Platforms**.*

@yuggniiks: Please mark your thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---


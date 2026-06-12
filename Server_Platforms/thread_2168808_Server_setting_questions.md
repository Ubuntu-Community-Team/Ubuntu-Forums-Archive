---
title: "Server setting questions"
date: 2013-08-19
forum: Server Platforms
---

### Post by enigmaingr on 2013-08-19
I'm setting up a home server using Samba and Ubuntu Server 12.04. I thought I added users correctly, but when I went to check the set up on both my Windows 7 and Windows XP machines, it appears that something is amiss. On both machines, I am able to navigate and find the server. When it asks for login credentials, I enter them but it automatically changes my username from "john" (the user name I entered in Samba's settings) to "[name of windows PC]/john" - essentially, the setup doesn't recognize my credentials so I can't access anything. I've tried doing the same login procedure using both what should be my root credentials, and another client's username / password. 

Here's what I'm trying to do:

-I have an ubuntu server in my home office connected by wire to a wireless router that is behind my DHCP main router.
-I'd like for this server to have all my media (install Plex), and serve as a print server as the network printer is wired to the same wireless router in the same room.
-I'd like to be able to access the server via my other ubuntu desktop when I need to change settings.
-I need to serve files to a windows 7 machine acting as my HTPC (wired), a Windows Vista laptop (wireless), a windows XP netbook (wireless), and I'd also like the ability for guest access to the media files via wireless

Any suggestions on how or where to start?

---

### Post by papibe on 2013-08-19
Hi enigmaingr.

A few thoughts:[LIST]
[*]
[*]Make sure that all Windows machine are set in the same workgroup (some of them may be in MSHOME).
[*]All authentication has to be mapped to a Linux user, so if you have the same username, but different passwords on the Windwos machines, then the automatic login won't work.
[*]You can use the command tool 'smbpasswd' to set a different password for samba access (so it is different from the login one).
[*]Windows saves the credentials, so it frequently creates problems when change the server side. To clean your Windows credentials in Windows 7 try going to: ```
Start > Credential Manager > Windows Credentials > Remove from vault
```.
[*]The easiest way that I connect from several Windows machine (with different users and passwords) to the same samba share is to use the server credentials: ```
SERVERNAME\actual_linux_username
``` and using the current Linux password.
[/LIST]
On the other hand. if this is your own network and you feel comfortable about its security, you may want to switch samba to "share" mode. That way you won't have any problems with usernames and passwords.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sandyd on 2013-08-19
> **enigmaingr said:**
> I'm setting up a home server using Samba and Ubuntu Server 12.04. I thought I added users correctly, but when I went to check the set up on both my Windows 7 and Windows XP machines, it appears that something is amiss. On both machines, I am able to navigate and find the server. When it asks for login credentials, I enter them but it automatically changes my username from "john" (the user name I entered in Samba's settings) to "[name of windows PC]/john" - essentially, the setup doesn't recognize my credentials so I can't access anything. I've tried doing the same login procedure using both what should be my root credentials, and another client's username / password. 

Here's what I'm trying to do:

-I have an ubuntu server in my home office connected by wire to a wireless router that is behind my DHCP main router.
-I'd like for this server to have all my media (install Plex), and serve as a print server as the network printer is wired to the same wireless router in the same room.
-I'd like to be able to access the server via my other ubuntu desktop when I need to change settings.
-I need to serve files to a windows 7 machine acting as my HTPC (wired), a Windows Vista laptop (wireless), a windows XP netbook (wireless), and I'd also like the ability for guest access to the media files via wireless

Any suggestions on how or where to start?
In Addition, make sure you have homegroups disabled.

---

### Post by enigmaingr on 2013-09-10
Hello,

I successfully got my server up and running on everything except my new desktop running Ubuntu 13.10. All the computers are wired into the network. For some reason, when I try to login to the Samba share using my Ubuntu desktop, it doesn't accept my credentials. Any suggestions?

---


---
title: "Samba configuration"
date: 2014-12-19
forum: Server Platforms
---

### Post by Micha_Sabat on 2014-12-19
Good morning.

I installed Samba on my server but I need some help in consfiguratin:

1. Access only for users from my network
2. Create catalog for all users, users not login - only read, users log in - all(read, create, write)
3. Create catalog for users group. If we create some group users from that group have access to that catalog (read, create, write)
4. All users have acces to their home catalog.
5. No time synchronization with server

Thank You very much.

---

### Post by bab1 on 2014-12-19
> **Micha_Sabat said:**
> [COLOR=#000000][FONT=verdana]Good morning.

I installed Samba on my server but I need some help in consfiguratin:

1. Access only for users from my network
2. Create catalog for all users, users not login - only read, users log in - all(read, create, write)
3. Create catalog for users group. If we create some group users from that group have access to that catalog (read, create, write)
4. All users have acces to their home catalog.
5. No time synchronization with server

Thank You very much.[/FONT][/COLOR]

[LIST=1]
[*]All network users are both Linux users and Samba users that you configure -- The server is configured to respond to all requests in the local LAN 
[*]Samba login is for access not for read write permissions - RW is file system attribute
[*]This is combination of Samba access and file system permissions
[*]This is set with a single [homes] share (catalog?)
[*]I don't know what this means
[*]
[/LIST]

Assuming that this is a standalone Samba server (no AD-DC services); the basic steps are:
[LIST]
[*]Add the users to the server as: Linux (adduser) and Samba (smbpasswd -a)
[*]Add users to a common user group for public Samba shares (adduser user group)
[*]Configure the file system's root directory of each share (chown and chmod)
[*]Configure each share by editing the share parameters (/etc/samba/smb.conf)
[*]
[/LIST]
Do you have any computer background?  Have you read or done anything about Samba configuration for this server?  What type of network are you using Samba in: home or business?  How many users are there on this network?

---


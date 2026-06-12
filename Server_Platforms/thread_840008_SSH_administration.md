---
title: "SSH administration?"
date: 2008-06-25
forum: Server Platforms
---

### Post by robbrandt on 2008-06-25
I have a functioning 8.04 server, new installation, new to Ubuntu.

I've getting used to logging in as non-root and sudo-ing everything at the command line.  However I am longing to do file management visually, as on my other servers I use WinSCP to do file management.  But how to do this conveniently?  Sometimes I'm moving stuff permissioned to different users, changing users/groups, chmod, etc.  I see no equivalent to sudo there, and so I'm limited to files owned by the admin user I logged in as.

Suggestions?

---

### Post by firecat53 on 2008-06-25
You can run a Nautilus window as root. I think there may even be a plugin to add a right click option to open a root file browser. And you can create an ssh session in Nautilus as well using the File -> Connect to Server option.

I think that answers your questions :)

Scott

---

### Post by molotov00 on 2008-06-25
If you've already got SSH set up then SFTP is supported:

[http://en.wikipedia.org/wiki/SSH_file_transfer_protocol](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol)

It's a secure FTP protocol similar to what you were using before (WinSCP). I don't know of any GUI clients but that's only because I haven't looked. They are out there.

I'm assuming you are using SSH and logging in remotely b/c of the title.

---

### Post by forger on 2008-06-25
> **molotov00 said:**
>  I don't know of any GUI clients but that's only because I haven't looked.

I use **nautilus** using menu File > Connect to server for ftp / sftp, but the program gftp is a gui that supports sftp as well!

---

### Post by robbrandt on 2008-06-25
Yes, I am remote.  I had a hard time wrapping my mind around the nautilus suggestions until I realized they were talking about non-remote, sitting at the terminal.  Or sitting at a remote Linux workstation(?).

I'll look at the sftp stuff.

---

### Post by robbrandt on 2008-06-25
Actually, WinSCP supports SFTP (I can set each connection as either SFTP, SFTP (Allow SCP fallback), or SCP.  But even when I switch to SFTP, I can log in as my admin account but have no ability to do something like sudo, and root login is disallowed.  Am I missing something?

---

### Post by cariboo on 2008-06-25
Install mc on your server, It's just like the old Norton Commander. No mouse needed everything works with keyboard commands. mc is available in the respositories:

```
sudo apt-get install mc
```

Use mc to start, the program can be run as root too.

Jim

---

### Post by windependence on 2008-06-25
> **cariboo907 said:**
> Install mc on your server, It's just like the old Norton Commander. No mouse needed everything works with keyboard commands. mc is available in the respositories:

```
sudo apt-get install mc
```

Use mc to start, the program can be run as root too.

Jim

Just FYI, there IS mouse support in the mc window too, even in an ssh session - pretty cool.

For WinSCP, I don't see to many alternatives to enabling the root account. Fact is, most other distros have it enabled, and in my mind, if they compromise the user account, with sudo, they have root also.

You <could> set up a group for your user that would have the power you need without being full root, but that almost defeats the purpose.

-Tim

---


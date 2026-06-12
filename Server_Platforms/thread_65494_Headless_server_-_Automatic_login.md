---
title: "Headless server - Automatic login"
date: 2005-09-14
forum: Server Platforms
---

### Post by Moonshine on 2005-09-14
I am using Ubuntu as a server and would like on bootup to have an automatic login so I can simply press the button, and away we go. I know what settings to change, I'd just like to check that this wouldn't comprimise any of the security. If SSHing people would still have to provide a username and password, right?

Thanks! :)

---

### Post by lao_V on 2005-09-14
By definition (and by default in Ubuntu) a server doesn't/shouldn't have X. As such there is no need for the system to "log in" as you will be administering it remotely (ssh or otherwise) and this will require you to log in.

---

### Post by Moonshine on 2005-09-15
It's just desktop Ubuntu with a few server things like SSH that I use occassionally. When I need to use this I would start it at the start of the day and turn it off at the end. So what I'd ideally like to do is have it so I can simply press the on button and it logs in by itself but without losing the security of SSH or anything. 

Thanks.

---

### Post by lao_V on 2005-09-15
[QUOTE=Moonshine]It's just desktop Ubuntu with a few server things like SSH that I use occassionally. When I need to use this I would start it at the start of the day and turn it off at the end. So what I'd ideally like to do is have it so I can simply press the on button and it logs in by itself but without losing the security of SSH or anything. 

Thanks.[/QUOTE]

Even if you have the X (desktop) installed on your server you still don't want it to log in automatically because you will be logging in remotely! :-)

Furthermore, I'm not sure what the purpose of the server is or where it is located but you don't really want your server to log in automatically because anyone with the physical access to it could pose a security threat.

---

### Post by Moonshine on 2005-09-15
The physical security isn't really an issue because of it's location. But you're saying that if I automatically log in then it will be remotely logged in as well, thus reducing remote connection security? I think I'm making this a bit confusing. Will automatically logging in back it easier for people who don't have physical access to the server (eg via SSH) easier to connect?

Thanks for your previous replies.  :)

---

### Post by lao_V on 2005-09-15
[QUOTE=Moonshine]The physical security isn't really an issue because of it's location. But you're saying that if I automatically log in then it will be remotely logged in as well, thus reducing remote connection security? I think I'm making this a bit confusing. Will automatically logging in back it easier for people who don't have physical access to the server (eg via SSH) easier to connect?

Thanks for your previous replies.  :)[/QUOTE]

Right, regardless of whether you are logged into your server or not you **will** need to log in when you are connecting to your server remotely through SSH. Does that make it clearer? :-)

---

### Post by Moonshine on 2005-09-16
[QUOTE=lao_V]Right, regardless of whether you are logged into your server or not you **will** need to log in when you are connecting to your server remotely through SSH. Does that make it clearer? :-)[/QUOTE]

Great, thanks!  \\:D/

---

### Post by LordHunter317 on 2005-09-16
[QUOTE=lao_V]By definition (and by default in Ubuntu) a server doesn't/shouldn't have X.[/quote]Simply wrong.  You've obviously never worked with Oracle before.  Oracle requires X to complete it's installation (ignoring unattended installs).  Even if you don't install the X server, you will have all the libraries.  A crapload of the admin tools require a GUI, as well.

Also, for various reasons, a print server will have most of a X11 install (though not enough to run many apps) as a matter of consequence for fonts.

---

### Post by jimcooncat on 2005-09-16
[QUOTE=Moonshine] If SSHing people would still have to provide a username and password, right?[/QUOTE]

You can set up your sshd to use public key authentication. Your users SSHing in can use an agent to hold their keys. If they're coming in from a Windows client, they can use PuTTy and Pageant. Works great for me, and I only need to enter a passphrase when I reboot or log out of Windows. (Ok, that's still often enough.)

---

### Post by jworr on 2005-09-19
If you want to enable automatic X login goto start => System => Administration => Login Screen Setup

In the middle of the Login Setup Screen there should be an option for auto-login

remote users still have to login with their username and password

---

### Post by venzen on 2005-09-20
If I understand you correctly your server is headless, so you ONLY want to log in via SSH right? In this case you do not want to automatically login upon startup. If you have a user logged in to a running headless server, then anyone can gain access to that server by simply rebooting and attaching a monitor and keyboard...

My advice is not to automatically logon a user to a running headless server. If you or someone else you trust want to logon to the host then use SSH to login remotely. Perhaps you have another reason for wanting to this?

---


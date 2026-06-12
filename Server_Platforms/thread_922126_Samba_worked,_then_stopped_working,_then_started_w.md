---
title: "Samba worked, then stopped working, then started working, then stopped again."
date: 2008-09-17
forum: Server Platforms
---

### Post by jacensolo on 2008-09-17
I have no idea what is going on. I had samba working with different shares and users. Then, after a reboot (for ftp reasons, not touching samba at all) when I tried to log on from xp the log on window just flashed. I tried it four times with different user names. I tried rebooting all the clients. Then I rebooted the server, restarted samba and it worked. After about an hour it started doing the same thing. FTP and SSH are still working fine. I also tried rebooting the samba service many times too.

Here is the smb.conf even though there is nothing on it.
```
[global]
workgroup = STONE
netbios name = Server
encrypt passwords = yes
security = user
wins support = yes

[homes]
read only = no
browseable = no

```

Also, "browseable" = no never did work. I had to change the directory permissions via chmod. I'm running the latest ubuntu server release.

---

### Post by cariboo on 2008-09-17
You're wasting a lot of time rebooting, most of the services are located in /etc/init.d to restart a service for example samba in a terminal type:

```
sudo /etc/init.d/samba restart
```

This is especially helpful if you make changes to the network configuration when you are access the server through ssh.

As for your Samba problem do run **testparm** after making changes to /etc/samba/smb.conf, testparm will show you if there are any mistakes in your configuration file.

---

### Post by jacensolo on 2008-09-17
> **cariboo907 said:**
> You're wasting a lot of time rebooting, most of the services are located in /etc/init.d to restart a service for example samba in a terminal type:

```
sudo /etc/init.d/samba restart
```

This is especially helpful if you make changes to the network configuration when you are access the server through ssh.

As for your Samba problem do run **testparm** after making changes to /etc/samba/smb.conf, testparm will show you if there are any mistakes in your configuration file.

But it originally stopped working when I didn't make any changes. I had made changes to the proftpd.conf and didn't know how to restart it like samba so I rebooted. Now Samba doesn't work.

I ran testparm and it said it was ok.

Any other clue?

---

### Post by jacensolo on 2008-09-18
It was working last night, but I don't know why it stopped. 

If I can get to it by going \\servername\share and it connects, it works. But most of the time I can't connect and I have to put the /share at the end. But that never works because the login windows just reappears after typing in the password. I've made sure it is the right one. Does anyone else have an idea?

Right before it stopped working I restarted /etc/init.d, then it quit working.

---

### Post by jacensolo on 2008-09-19
Nobody has an idea?

---

### Post by Ripfox on 2008-09-19
Have you tried Lanshark on getdeb website? It can share any folder with windows, linux or mac and it actually works very well. Not to hijack the thread just an idea.

---

### Post by warchief_ryan on 2008-09-19
Maybe you should try adding "valid user = "your username"".

Also make sure the usernames and passwords are the same on both box's.

---

### Post by jacensolo on 2008-09-19
> **warchief_ryan said:**
> Maybe you should try adding "valid user = "your username"".

Also make sure the usernames and passwords are the same on both box's.

I reformatted and it did the same thing! This is annoying.

---

### Post by jacensolo on 2008-09-20
Got it to work again :D. I don't know what was wrong, but I installed samba-common along with samba and it worked. I'm going to save this configuration.

Does anyone know the difference in between the two?

---

### Post by jacensolo on 2008-09-20
Err. Without changing anything, from my windows media center pc, it is doing the same thing. But I can access public shares, I just can't login.

---

### Post by warchief_ryan on 2008-09-21
I think samba-common is required for samba and is installed when samba is.

You must have changed something, samba doesn't change its configuration by itself. Maybe you should post your smb.conf again if its different from the one you already posted. Perhaps a forgotten samba service restart.

I found SWAT a good tool to use when I was first using samba, because it shows basic options and links to the help file that explains the various options.

---

### Post by jacensolo on 2008-09-21
Alright. I think I figured it out. I just can't get it to work.

On the computers that are working, the username (xp's user name) is the same as the one I'm trying to login with. So maybe samba is checking to see if the user name's are the same?

I don't know how to turn this off. Is there a way?

Edit: Scratch that. It checks to see if the username is any one of the usernames on the server, then I can login to samba with any username.

---


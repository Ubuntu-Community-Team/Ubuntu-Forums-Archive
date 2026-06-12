---
title: "SSH Transfering Files Remotely."
date: 2011-05-09
forum: Server Platforms
---

### Post by Sirkyuubi on 2011-05-09
Hello. I seem to be having an issue with ssh.

So I have setup my ssh server, and it works great. I can connect remotely. The issue I am having is finding a way to get files from it.

If I log in through filezilla I notice that it uses the commands get and put, but these commands don't work if I'm on windows using putty. Is there a way for me to transfer files when I'm ssh'd into the server? I don't like using multiple programs.

---

### Post by msandoy on 2011-05-09
Try man scp and man sftp.
There is also something called SSHFS. 
Google is your friend.

Also, try open nautilus, dig up the addressbar from your menus, enter:
```

fish:ipaddress

```

---

### Post by Sirkyuubi on 2011-05-09
I looked at them. They don't seem like they are what I'm looking for.

---

### Post by dargaud on 2011-05-09
I second scp and sftp. And also the very powerful rsync (if you regularly transfer the same things, put an rsync command into a script). What's wrong with them ? If you are looking for a Windows solution you can use WinScp/WinScp2 which shows you a nice Explorer-like shell.

---

### Post by Lateralis on 2011-05-09
Are you connecting through Windows or through a Linux distro?  If Linux, then use scp.  It is a commandline program and works great.  I in fact used to use scp all the time, until I discovered how to mount the remote directory on my local tree hierarchy using sshfs, so +1 to that solution.  

If you're not using Linux but Putty in Windows then I don't know what you can do.  I never did find a way of using scp through Putty to get remote files on my local machine, although I didn't try very hard.  There may be options in Putty to do this, but I can't be certain.

---

### Post by msandoy on 2011-05-09
I did not know about WinSCP, thanks for the tip dargaud.

---

### Post by Sirkyuubi on 2011-05-09
I have setup a LAMP box with SSH. It will depend on the client I'm connecting with, but lets assume putty is the only thing available client side unless the client is linux box then ssh is avai, but I need to be able to connect remotely through ssh and do file transfers too in one program. I was assuming there was a way to do it if I putty into the server I could download from the server or upload to the server from the client while connected through putty via command line.

---

### Post by spynappels on 2011-05-09
There is no way to do this using PuTTY. You will have to use WinSCP for this. WinSCP and PuTTY are both available as executable binaries which do not require installation, so putting them on a USB stick should mean you can use them from any Windows client.

Or look at portableapps.com for a whole bunch of programs and utilities which can be run from a USB stick. I have a USB stick with portable apps on it which includes everything I need to access any of my servers from any Internet connected Windows machine without requiring any special privileges or installation on the client machines.

In short, you will have to use another program, WinSCP is easiest.

---

### Post by SecretCode on 2011-05-09
Simon Tatham, the author of PuTTY, also has some windows command line scp and sftp programs ... called pscp.exe and psftp.exe. See [PuTTY Download Page](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

However, if you don't need command line, WinSCP is great.

---

### Post by hawkmage on 2011-05-11
I use putty from windows all the time, the full installer has a command pscp which is basically PuTTY scp.  It has the same syntax and options as the regular linux scp.

---


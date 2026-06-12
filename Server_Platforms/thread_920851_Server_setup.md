---
title: "Server setup"
date: 2008-09-15
forum: Server Platforms
---

### Post by SqueakyDK on 2008-09-15
Hey,

I usually ran my server on an old windows machine. Ran fine though a bit choppy. It got 3 hdd's. 1 with the OS and 2 for data. I used it with bittorrent and a ftpserver. I remotecontrolled it with pcanywhere. It all worked great.

Now, with a new server up i wanted to try ubuntu. I want the same features i got with windows.

I allready got the VNC server up and running fine. That's one problem down.

So now i have to configure the ftpserver. Im using vsftpd. I want to make an admin user and a guest user with a password. 

My 2 hdd's are ntfs drives (should i change that?) and the DO NOT automount. I can't figure out how to make them. Does that pose a problem if i reboot the server without accessing them? (Which seems to mount them).

Well back to the ftp problem. I want both accounts to access both of the datadrives. The admin has to be able to write also. How do i do that?

I haven't installed the BT client yet. I'll see if i can manage that. Otherwise you'll know :-)

Samba shouldn't be a problem either.

If you have trouble understanding what im trying to say here please ask :-)

Btw im using Hardy Heron Desktop Version due to the fact that a GUI is provided.

Cheers!

---

### Post by jamesrfla on 2008-09-15
For the FTP stuff you can use SSH. If you are on windows you can get a client so you can SSH and another one for the FTP stuff.

---

### Post by Dr Small on 2008-09-15
My personal choice of an FTP server is proFTPd. You can get a GUI utility to work with it, called gProFTPd. Works great. The drives can stay NTFS if you choose, but ext3 is the prefered filesystem of linux.

To remotely control the system, I would recommend installing openssh-server. You can connect to the system from a command line across the network/internet, as long as you have a client, such as openssh-client, PuTTy or cgywin.

The drives don't automount because you probably don't have an entry in /etc/fstab for them to mount at bootup.

---

### Post by SqueakyDK on 2008-09-16
> **Dr Small said:**
> My personal choice of an FTP server is proFTPd. You can get a GUI utility to work with it, called gProFTPd. Works great. The drives can stay NTFS if you choose, but ext3 is the prefered filesystem of linux.

Maybe i should try proFTPd then.

Can i reformat them without losing my data?

> **Dr Small said:**
> 
To remotely control the system, I would recommend installing openssh-server. You can connect to the system from a command line across the network/internet, as long as you have a client, such as openssh-client, PuTTy or cgywin.

I am using VNC at the moment because i prefer a GUI. Isn't that good enough?

> **Dr Small said:**
> 
The drives don't automount because you probably don't have an entry in /etc/fstab for them to mount at bootup.

How would i do that? I know where fstab is but i can't seem to find the right information to put in there. But if i make my drives ext3 then it wouldn't be a problem

---

### Post by maxwellcom on 2008-09-16
> **SqueakyDK said:**
> Maybe i should try proFTPd then.

I am using VNC at the moment because i prefer a GUI. Isn't that good enough?

How would i do that? I know where fstab is but i can't seem to find the right information to put in there. But if i make my drives ext3 then it wouldn't be a problem

Like you Squeaky I'm much more comfortable with a GUI.  But I have recently set up an Ubuntu server box and found that with Webmin and openSSH installed, you really don't need a GUI on the box.  

For example, you can format drives and set them up as permanent mount points in your filesystem (i.e., edit fstab) in just a few clicks with Webmin.  You can even use it to upload files, although if you have lots of files (like for a webserver) it might not be that efficient.  Webmin will upload a .tar/.zip file, unpack it, and then delete the archive, but that seems a little cumbersome...

Anyway, openSSH can be installed via aptitude

```
sudo apt-get install openssh-server
```

and Webmin has a Debian package complied on their [website]("http://www.webmin.com/") that you can download and run on the server.  You can use [Putty ]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")to access the server console from a Windows box.  The Webmin config can be accessed with any browser.

---

### Post by SqueakyDK on 2008-09-17
So with Webmin i can access my files through any browser? Because a got some problems with closed ports at my college which blocks my access to VNC.

Webmin sounds like a good solution. Maybe i'll install the server edition of ubuntu along with Webmin.

I'll keep you updated :)

---


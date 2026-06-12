---
title: "Need suggestions to choose cloud software"
date: 2017-02-19
forum: Server Platforms
---

### Post by simonlap on 2017-02-19
Hi Guys! 
  I was wondering if any of you would have some suggestions for me. I  have been looking at couple options and I can't figure out what would be  the best solution. I looked at Syncthing, Bit Torrent Sync, Syncany,  Seafile, OpenVPN. 
  Here's what I am trying to achieve. I have an ubuntu server with a  shared disk in which I have 4 folders. Each folder is for a different  user and is only accessible by the user. 

  Each user would need to have remote connection to his folder only  (like a cloud). Im trying to find a solution that would be as much as  possible like a cloud, so that we can edit save and open file easily on  our computer and have them back easily on the server!

I have heard about SSH and SSHFS but I would prefer something with synchronization options, etc...!

Thanks for the help :)

---

### Post by howefield on 2017-02-19
[Owncloud]("https://owncloud.org/") or the "fork" [Nextcloud]("https://nextcloud.com/") ?

---

### Post by simonlap on 2017-02-19
> **howefield said:**
> [Owncloud]("https://owncloud.org/") or the "fork" [Nextcloud]("https://nextcloud.com/") ?

I tried owncloud but did not really like it! 

Is nextcloud really great? Did you try it?

---

### Post by howefield on 2017-02-19
> **simonlap said:**
> Is nextcloud really great? Did you try it?

I use ownCloud and do like it, however if you don't then it is probable that you won't like Nextcloud either.

---

### Post by simonlap on 2017-02-19
> **howefield said:**
> I use ownCloud and do like it, however if you don't then it is probable that you won't like Nextcloud either.

Confirmed, just tried it! hahaha! Probably going to try seafile...!

---

### Post by damo12 on 2017-02-20
I have a similar configuration at work.  I run OpenVPN on the server with a separate connection profile for each user.  Once they have logged in, they can only access their folder.  The folder access is configured through Samba (each user has their own account).

To install and configure OpenVPN I use PiVPN ([http://www.pivpn.io/]("http://www.pivpn.io/")).  Running the installation script installs and configures everything you need for OpenVPN and you simply create user connection profiles using the command:```
pivpn -a
```

Using this method, the files the user works on is located on the server eliminating the concern about synchronisation etc.  Should users require access to other user's folders, you just need to change the Samba configuration file.

The only thing to remember is that Samba can be a bit memory intensive and the connection speed will depend on your internet connection however if you have managed to run Owncloud you shouldn't have any issues with this.

---

### Post by simonlap on 2017-02-20
> **damo12 said:**
> I have a similar configuration at work.  I run OpenVPN on the server with a separate connection profile for each user.  Once they have logged in, they can only access their folder.  The folder access is configured through Samba (each user has their own account).

To install and configure OpenVPN I use PiVPN ([http://www.pivpn.io/](http://www.pivpn.io/)).  Running the installation script installs and configures everything you need for OpenVPN and you simply create user connection profiles using the command:```
pivpn -a
```

Using this method, the files the user works on is located on the server eliminating the concern about synchronisation etc.  Should users require access to other user's folders, you just need to change the Samba configuration file.

The only thing to remember is that Samba can be a bit memory intensive and the connection speed will depend on your internet connection however if you have managed to run Owncloud you shouldn't have any issues with this.

Is there any guide on how to set this up? I already have my samba shared folder setup, and I installed PiVPN, I installed the windows GUI and I am connected to the VPN, but I can't figure out how to access my data as I never worked with OpenVPN. This will sound really bad, but I can't figure out how this works...

---

### Post by damo12 on 2017-02-21
Once the remote machine has connected to the server through the VPN, you need to map a network drive to the server share in pretty much the same way that you would if it was on the same physical network.  The only issue is that you cannot use UNC but need to use the IP address of the server instead.

Usually, you would map the drive using the command:```
net use z: \\servername\share
```

When you are connected using a VPN you have to change this to:```
net use z: \\192.168.0.1\share
```replacing 192.168.0.1 with the IP address of the server.

---

### Post by simonlap on 2017-02-21
> **damo12 said:**
> Once the remote machine has connected to the server through the VPN, you need to map a network drive to the server share in pretty much the same way that you would if it was on the same physical network.  The only issue is that you cannot use UNC but need to use the IP address of the server instead.

Usually, you would map the drive using the command:```
net use z: \\servername\share
```

When you are connected using a VPN you have to change this to:```
net use z: \\192.168.0.1\share
```replacing 192.168.0.1 with the IP address of the server.

It's working mate! Thanks a lot for this :D

---


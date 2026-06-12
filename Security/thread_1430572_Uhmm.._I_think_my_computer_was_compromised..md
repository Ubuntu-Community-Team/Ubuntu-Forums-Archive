---
title: "Uhmm.. I think my computer was compromised."
date: 2010-03-15
forum: Security
---

### Post by Saidear on 2010-03-15
I went to go about setting up a share on my Ubuntu file server (running 9.10 desktop edition) and I log in to see a weird series of BASH commands on my desktop:

"~/vnc$ ./go 84.231"
[+] Real VNC by Slick
[+] Scanning for servers
[+] Scanning: 84.231.255.* (total: 14) (100.0% done)
[+] Pscan complete in 477 seconds. (found 14 ips)
[+] Now scanning for the vulnerable servers
-
-
and so on, time and time again the with IP range changing.  

I immediately removed the physical ethernet connection from the tower and am using a different computer on a different connection to make this post.   I have a few concerns:

1) what can I do to re-secure this installation again without losing data already on.
2) what steps can be taken to prevent this happening again?
3) I had Firestarter installed, but for some reason it doesn't like my sharing and blocks all connections (even if I have them permitted ie: Hostname.local) so had it disabled at the time. How can I make this work with my file shares to allow only my local computers access to the shared media? 

Any help would be appreciated!

---

### Post by gnupipe on 2010-03-15
> **Saidear said:**
> 
1) what can I do to re-secure this installation again without losing data already on.
2) what steps can be taken to prevent this happening again?
3) I had Firestarter installed, but for some reason it doesn't like my sharing and blocks all connections (even if I have them permitted ie: Hostname.local) so had it disabled at the time. How can I make this work with my file shares to allow only my local computers access to the shared media? 

Any help would be appreciated!

Please make a complete re-install (remember to back up important files) and make sure you use *STRONG* passwords for *EVERYTHING* and don't install un-needed services. Was openssh or VNC installed?

---

### Post by Saidear on 2010-03-16
Yes, so I can control it remotely.  It's sitting in a closet in our basement typically so having it do things otherwise is pretty difficult.

---

### Post by ndefontenay on 2010-03-16
You'll have to do a complete re-install. You won't be able to know what files have been compromised.

---

### Post by HermanAB on 2010-03-16
Hmm, VNC is the favourite way to get your machine hacked.  There are many tales of woe on these forums.

You should remove the VNC server and install the ssh-server package.  SSH can do everything VNC does and more and it is secure.  You really don't need VNC.  If you don't agree, then you just don't know SSH properly...

---

### Post by gnupipe on 2010-03-16
> **HermanAB said:**
> 
You should remove the VNC server and install the ssh-server package.  SSH can do everything VNC does and more and it is secure.  You really don't need VNC.  If you don't agree, then you just don't know SSH properly...

Yes SSH is secure but even with SSH you must remember to use strong passwords or use public key authentication because there are a lot of password guessing bots out there. :)

---

### Post by Saidear on 2010-03-16
> **HermanAB said:**
> Hmm, VNC is the favourite way to get your machine hacked.  There are many tales of woe on these forums.

You should remove the VNC server and install the ssh-server package.  SSH can do everything VNC does and more and it is secure.  You really don't need VNC.  If you don't agree, then you just don't know SSH properly...
I likely don't, tho I am learning relatively quickly. I have a full install running as we speak, I'm assuming that if I don't do a format, I am not going to lose the files on the system (ie: the ones being shared)

---

### Post by CharlesA on 2010-03-16
> **Saidear said:**
> I likely don't, tho I am learning relatively quickly. I have a full install running as we speak, I'm assuming that if I don't do a format, I am not going to lose the files on the system (ie: the ones being shared)

There are a few good guides in the security sticky.

If yer machine was compromised, backup your data and reinstall, that is the only way to be sure you won't have problems in the future.

Are you sharing files with Samba or some other means?

---

### Post by amac777 on 2010-03-16
> **Saidear said:**
> I have a full install running as we speak, I'm assuming that if I don't do a format, I am not going to lose the files on the system (ie: the ones being shared)

That might not be a good assumption. You should backup your files first.

---

### Post by Saidear on 2010-03-16
> **CharlesA said:**
> There are a few good guides in the security sticky.

If yer machine was compromised, backup your data and reinstall, that is the only way to be sure you won't have problems in the future.

Are you sharing files with Samba or some other means?
Samba via Nautilus' GUI.

Install completed, reinstalled Mediatomb with no issues, and that is running fine now.  I have my media stored on a separate partition (Media), which is a larger partition than where Ubuntu is installed (60GB vs 400GB)

I installed Firestarter and set it to allow only local connections (192.168.1.1/24) and to the SMB service (Allow Samba Service, port 137-139, 445, everyone).  I can connect to the server, I can see the shared folders on my Windows machine, but trying to connect prompts me for username and password.  I enter the user/pass of the only account on the machine, and it rejects it.  If I disable Firestarter, I can access the share without any problem.  

I can still VNC into the machine regardless.  I will likely disable VNC in the near future once I have it comfortably setup and resort to SSH only.

---

### Post by noway2 on 2010-03-16
First off, learn from your mistake and dump the VNC.  You can run a remote desktop without it using SSH alone, OR if you really want remote desktop capability try FreeNX instead: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).

It sounds like there is a conflict between your firestarter and Samba.  Doing a quick google search for "ubuntu firestarter samba" gave me this as the first link:[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542).

I didn't read it to see if there were any resolutions suggested, but if you continue to have problems consider using IPtables directly or the UCFW (uncomplicated firewalls), which is a front end for IPTables.

If you don't currently have one, you should also consider putting a router in between your public connection and your server and only enable/forward the ports you need to use.

---

### Post by Saidear on 2010-03-16
> **noway2 said:**
> First off, learn from your mistake and dump the VNC.  You can run a remote desktop without it using SSH alone, OR if you really want remote desktop capability try FreeNX instead: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).
FreeNX with NoMachine's Window's client does the trick, I disabled the built in VNC (Vino I think it is?) option under System > Preferences > Remote Desktop

> It sounds like there is a conflict between your firestarter and Samba.  Doing a quick google search for "ubuntu firestarter samba" gave me this as the first link:[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542).

I didn't read it to see if there were any resolutions suggested, but if you continue to have problems consider using IPtables directly or the UCFW (uncomplicated firewalls), which is a front end for IPTables.
I thought Firestarter was also a GUI for IPTables as well, I picked it because (supposedly) it was simpler to use.  But that fix definitely resolved it, thank you!

> If you don't currently have one, you should also consider putting a router in between your public connection and your server and only enable/forward the ports you need to use.
I do, which is part of my mistake before since I enabled some port-forwarding to see my bittorent status while away from the house.

---

### Post by gordintoronto on 2010-03-16
If you're going to run bittorent, you can't expect to have any security...

---

### Post by rookcifer on 2010-03-17
> **gordintoronto said:**
> If you're going to run bittorent, you can't expect to have any security...

I wouldn't say that.

---

### Post by Saidear on 2010-03-17
If you connect to the internet, you can't expect any security would be equally true.  I understand that there is no panacea to make every computer completely invulnerable, the goal is merely to make the risks as minimal as possible.

---

### Post by Grenage on 2010-03-17
> **gordintoronto said:**
> If you're going to run bittorent, you can't expect to have any security...

Oh, tosh!

NX is great; if you aren't using a hardcore password or cert, you might also consider something like fail2ban.  It automatically blocks an IP address after X amount of incorrect logins.

---

### Post by gordintoronto on 2010-03-17
[QUOTE=Grenage;8981445]Oh, tosh!

I'm suitably chastised.

---

### Post by gnupipe on 2010-03-18
> **gordintoronto said:**
> If you're going to run bittorent, you can't expect to have any security...

Why?

---


---
title: "Cannot connect to repository"
date: 2007-03-11
forum: Repositories &amp; Backports
---

### Post by bikuta on 2007-03-11
Hi I just installed Ubuntu Dapper and none of the repositories seem to be working, is there something that I need to setup?

This is what I get when I run "sudo aptitude update"

> 
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used


---

### Post by Kateikyoushi on 2007-03-11
When you click on those links in your post you can open them in the browser right ?

---

### Post by bikuta on 2007-03-12
I just did a re-install of Ubuntu because for some reason the HD got corrupted, Ubuntu was complaining about inode errors and after going through all that I couldn't boot into Ubuntu anymore because the /sbin/init file was missing.

Well long story short, it seems to be working now and updates are working. Now I will endeavour to perform the upgrade to 6.10.

Thanks for the reply though, I appreciate it.

---

### Post by grazhoppa on 2007-03-12
I cannot connect to archive.ubuntu.com or us.archive.ubuntu.com on this Ubuntu computer - through any *apt* program or webbrowser. Using Ubuntu 6.10/Edgy
Other computers in my house can connect... they are running Windows though.

The Ubuntu computer** can** connect to ca.archive.ubuntu.com, gb.archive.ubuntu.com, and au.archive.ubuntu.com!
Even when sources.list explicitly says to use gb.archive.ubuntu.com... all the *apt*  programs still try and fail to connect to archive.ubuntu.com towards the end of the update process.


I'm behind a router, and the Ubuntu computer is using the DHCP address given to it by the router.  The Windows computers are using DHCP as well.

The DNS servers the Ubuntu computer uses are the same as the Windows computers.
I've tried changing the DNS servers to OpenDNS and also a couple SpeakEasy ones, and neither worked.

What is weird, is that archive.ubuntu.com and us.archive.ubuntu.com are the only sites I have trouble with.

Am I inflicted with some sort of malware/spyware of the Linux variety here? 
The /etc/hosts file has only this, so it doesn't look like the hosts file is misdirecting the connection:
```

127.0.0.1 localhost
127.0.1.1 Ubuntu6-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I am a linux newb and would love some enlightenment on this...

---

### Post by Kateikyoushi on 2007-03-13
Recently many reporeted problems connecting to both to the main and the us server.
Sticking with .ca won't hurt.

Are you sure that you modify the whole sources.list and the right sources.list ? Strange that it tries to connect to the main server.

---

### Post by rabid emu on 2007-03-15
I have exactly the same problems connecting to the main and us server.  Made a thread about it [http://www.ubuntuforums.org/showthread.php?t=383191]("http://www.ubuntuforums.org/showthread.php?t=383191")

I'm trying the gb server now though, the ca one doesn't work for me.

---

### Post by X-626 on 2007-03-16
If any of you have Firestarter installed, it may be restricting your connections.  I mad a reply to a topic with problems connecting to both archive.ubuntu.com and us.archive.ubuntu.com.  If you do have Firestarter installed, try opening it, and going to Preferences, Advanced Options, then uncheck "Block traffic from reserved addresses on public interfaces".  If that doesn't work, try stopping Firestarter with the command:
```
sudo /etc/init.d/firestarter stop
```After it is stopped, try connecting to those repositories.  If you connected, then Firestarter *did* stop it, but it may have been something else.  If not, I don't know  what else would cause it.
It seems that both of those repositories make a connection back to you, which Firestarter drops and that prevents you from making a connection.

---

### Post by grazhoppa on 2007-03-18
X-626 had the solution, thank you.
I was running Firestarter and it was restricting the connection to us.archive.ubuntu.com and archive.ubuntu.com. Exiting or stopping the firewall solved the problem.

A couple months ago this quirk wasn't present. I guess archive.ubuntu.com or the apt programs changed the way they do things...


Funny thing, after grabbing/installing the updates I ran into a bug with the graphical version of "sudo" not acceptnig a correct root password.  I put up with it for a few days by running things that needed root privileges from the "sudo" command line which still worked.  But for whatever reason it "fixed itself" and the normal GUI sudo thing came back... Beta testers with Fiesty version were experiencing this same bug on this forum :( .

---

### Post by rabid emu on 2007-03-19
Stopping firestarter while using apt did fix the problem.  I just wish I didn't have to do that every time though.  I even reinstalled firestarter to see if that would fix it, no dice.

---

### Post by tuga on 2007-03-20
I had the same issue. Connection to repos is only possible after stop firestarter.

---


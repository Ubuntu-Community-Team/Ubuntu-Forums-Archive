---
title: "Terminal Server or equivalent"
date: 2007-12-20
forum: Virtualisation
---

### Post by tjpren on 2007-12-20
Hi, 
I hope this is the correct forum - apologies if its the wrong one.

I'm investigating whether Linux-Ubuntu has an equivalent to Windows Terminal Services.

I'm looking at running windows apps in a VMware server environment in a Ubuntu OS.  I'd like other windows PC's to be able to connect to the linux server via TS or equivalent and run a session of the windows app.

Does anyone know if this is possible ?

Can rdesktop make multiple client connections (i think windows can use some variant of this).

I'm not sure if VMware server can run multiple sessions

Anyway - any help gratefully appreciated.

---

### Post by toobuntu on 2007-12-20
Sounds like you might need a Windows version that can handle multiple concurrent Remote Desktop Connection or rdesktop (both use RDP as the protocol) users, such as Windows 2000 Advanced Server or Windows Server 2003 in Terminal Services/Application Server mode; these are multi-user flavors of Windows.  Windows 2000/XP Pro cannot accept so many concurrent RDP connections; these are single-user flavors of Windows.

If all you need is capability for one Windows user at a time, then your plan should work.  Just make sure that you set up the Windows VM to allow remote desktop connections, and specify the allowed users under the system properties control panel.  Windows 2000/XP Pro will accept connections from multiple devices via RDP, but only one user at a time.

You could, however, run Win XP Pro as a VM - locally on each machine - and have your users rdesktop into their locally-hosted machine.

As for an rdesktop equivalent to access Ubuntu remotely with a GUI, the classic answer is VNC, but many people find it slow.  NX Free is free, as in beer, but is proprietary software.  It works faster than VNC does.  The open source FreeNX is based on old code and is hard to recommend at this point.

[http://www.nomachine.com/download-package.php?Prod_Id=5]("http://www.nomachine.com/download-package.php?Prod_Id=5")

Because Ubuntu GNU/Linux is a true multi-user OS, you could have multiple concurrent NX Free connections.  However, if each of those users tries to access the same VM running under VMware, they will compete for access to that machine.  In other words, each logged on user would be accessing the same running VM, so you may need to go with a multi-user Windows flavor as mentioned above.

---

### Post by daflame on 2007-12-20
> **toobuntu said:**
> 
As for an rdesktop equivalent to access Ubuntu remotely with a GUI, the classic answer is VNC, but many people find it slow.  NX Free is free, as in beer, but is proprietary software.  It works faster than VNC does.  The open source FreeNX is based on old code and is hard to recommend at this point.

[http://www.nomachine.com/download-package.php?Prod_Id=5]("http://www.nomachine.com/download-package.php?Prod_Id=5")

Because Ubuntu GNU/Linux is a true multi-user OS, you could have multiple concurrent NX Free connections.  However, if each of those users tries to access the same VM running under VMware, they will compete for access to that machine.  In other words, each logged on user would be accessing the same running VM, so you may need to go with a multi-user Windows flavor as mentioned above.

toobuntu is right for mostly all of what he said.  However, there is an updated FreeNX that is being maintained:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

However, from my experience it is difficult to see any windows screen using vmware in an NX environment unless you use RDP proxy, but you will still need a Windows TS for multiple users (which defeats the purpose).

Also, there is an option to use wine as the Windows layer to run programs as long as those programs are supported.

Finally with NX you have the freedom to make the programs rootless so they look like they are running on the client machine.

I have done all of the above.

---

### Post by freesbee on 2012-09-15
Concurrent RDP sessions were allowed in WinXP until the RC1. Then they suddenly disappeared. There is a very simple trick to enable it, works perfectly on WinXP and Win7 (any version).

The mod for Win7 can be found with all documentation at [www.missingremote.com]("http://www.missingremote.com")

If you need the mod for WinXP, I still have it, I'll be glad to send it to you.

I read any kind of comment about enabling concurrent RDP sessions on Windows OSs that are NOT "Terminal Server" editions (safety of the file system, bla bla bla...). My personal experience using this mod on more than 40 machines since several years is: no problems encountered, even when I did relatively deep installations (adobe reader for example) while the user was logged on.

Now back to Ubuntu, that's why I'm writing here.
I am quite new to the linux world.

I am trying to set up the same kind of environment based on Ubuntu and NXserver with the NX client from nomachine.com
My test machines have both a fresh installation of Ubuntu Desktop 12.04 x86
I installed KDE via:
```
$ sudo apt-get install kubuntu-desktop
```From the machine I can login perfectly with Unity, GNOME and KDE, no problems at all.

Via NX client I can login only with GNOME.

I have found on the web several topics about problems with the remote sessions, but nothing similar to my problem, where only GNOME seems to work from the remote client, while from the computer itself all of them work.

I am not sure that this is the correct forum for this topic. If it isn't I would kindly ask somebody to indicate me which is the right one.

Thank you in advance.

---


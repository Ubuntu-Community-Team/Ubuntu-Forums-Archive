---
title: "Migration to Ubunu Linux Server!?"
date: 2006-08-21
forum: Server Platforms
---

### Post by truth on 2006-08-21
What if you were a system administrator of a Windows Network with 100+ thinclient end-users working in  Windows 2003 Terminal Servers 100% of the time.

You have 2 developers/programers writing custom applications(and other stuff) for Window Based Software that meet the Companies Needs Perfectly, All end-users depend on these custom apps that once again are windows based. 

Thats ok, but whats not ok is when the Server goes down because a program Crashes/Hangs and brings the whole server down with it. Now we are talkin downtime, which various depending on the scope of the promblem.  

Now ive been thinking about a Linux Solution but i dont know where to start. . .

could any of you help. . .keep in mind the Custom Apps, & Developers who code in a Windows Enviroment using .NET,VB and FoxPro, this is probably the only thing holding back a Linux Migration.    

And ofcourse im talking about a possible Migration to Ubunu Linux Server

---

### Post by lamego on 2006-08-21
truth,
first as an introduction, I am an experienced System Administrator and Application Developer both with Windows and Linux but I am not currently working with Linux, my suggestions are based on techical know-how and readings. I don't have test cases for this particular suggestions.

Server Side / Thin Client Services

You can use the "standard" Ubuntu Thin Client Server (LTC), you can read a proper description here:
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

Or you could use Diskless Remote Boot in Linux (DRBL), [http://drbl.sf.net/](http://drbl.sf.net/)
The major advantages from drbl should be the "pure" thin client function by having all the system/data stored on the server, and the performance gain from having the data distributed using broadcast.


Client Side
About the applications migration and not knowing the ammount and complexity of your applications I would guess you can't afford the resources to migrate them to a Linux environment, so let's start with the ability to run the existing applications on a Linux client.

Wine
----
Wine as a compatibility layer for running Windows programs, this could allow you to run the native windows applications from Linux. The bad news is that it doesn't seem to support .NET based apps yet, you would need to check this.
VMWare - You could run the vmware player with a VM installed window systems, I am not sure your thin clients have enough processing power for this...

Porting
-------
The perfect solution would be to port those .NET/FoxPro apps to Linux, as for the .NET, there is a .NET compatible implementation for Linux (the name is Mono) however there are still missing pieces like the Windows Forms, anyway it should allow you to port at least the application functional code without much problems.

As for any other reimplemenation you have a lot of options, I have learn Python 2 months ago and I would recommend it.

---


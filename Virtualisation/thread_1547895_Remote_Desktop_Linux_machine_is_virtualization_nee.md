---
title: "Remote Desktop Linux machine: is virtualization needed?"
date: 2010-08-07
forum: Virtualisation
---

### Post by UranUtan on 2010-08-07
Hi,

Can you please show me how to do this with Linux. I am not sure if it's a virtualization technique, if I am in the wrong forum section, please redirect me to the right place.

I have a Linux machine running upstairs (Lucid Desktop, 10.04 x64).

Let says, I am downstairs and I would like to use my Upstairs machine remotely. Which means I have a GUI that allows me to log in and then I would have exactly the same desktop than if I was sitting upstairs. In other words, I am using the upstairs machine remotely. The downstairs machine (could be Ubuntu or Windows 7) just allows to display the desktop GUI of the upstairs machine.

In the Windows world, I can do that using Remote Desktop. There is actually no need of any virtualization. Better yet, two users can remote desktop simultaneously (max allowed = 2, however).

Is there anyway to do the same than Windows Remote Desktop with Linux?

Thanks in advance for any help.

---

### Post by sh1ny on 2010-08-07
In linux it's called VNC ( actually it's crossplatform :P ).
You can enable remote connections from :

System -> Preferences -> Remote Desktop

On the other machine, you need to install a vnc client ( if it's windows ) or if it is ubuntu -> Applications -> Internet -> Remote Desktop Viewer ( i think it's called that way, speaking on memory from my windows 7 boot :F ).

This has nothing to do with virtualization :)

---

### Post by UranUtan on 2010-08-09
Oh that's cool, thanks for putting me on the right track. Does VNC Server has any limit in simultaneous users?

The idea is to allow to better use the resource of a powerful machine which idles most of the time.

**Question 1**: 3 remotes users use VNC Client to remote control the same computer. Each user logs in with their own login. Each user work on their own desktop and doesn't interact with other users.

**Question 2**: On the big machine, there is user1 who is using it (physically, no VNC). Is it possible for User2 to log in remotely using VNC?

---

### Post by JustinR on 2010-08-09
> **UranUtan said:**
> Oh that's cool, thanks for putting me on the right track. Does VNC Server has any limit in simultaneous users?

The idea is to allow to better use the resource of a powerful machine which idles most of the time.

**Question 1**: 3 remotes users use VNC Client to remote control the same computer. Each user logs in with their own login. Each user work on their own desktop and doesn't interact with other users.

**Question 2**: On the big machine, there is user1 who is using it (physically, no VNC). Is it possible for User2 to log in remotely using VNC?

VNC is just taking what the upstairs computer is sending to its own monitor. So if another person logs into the VNC server (upstairs computer) then they will be seeing what is going on on the upstairs computer. Makes sense?

Edit: If you want multiple users to use the computer like you put in your first question - you will have to look into PXE booting on each of the remote computers.

---

### Post by dtfinch on 2010-08-09
If I just want to run a single Linux gui app and have it appear locally on Windows, I use Xming (X11 server for Windows) and Putty (ssh client for Windows), enable X11 forwarding in Putty, and then with Xming running I just run the app over ssh.

There's also FreeNX but I have no experience with it.

---

### Post by UranUtan on 2010-08-09
> **JustinR said:**
> VNC is just taking what the upstairs computer is sending to its own monitor. So if another person logs into the VNC server (upstairs computer) then they will be seeing what is going on on the upstairs computer. Makes sense?

Edit: If you want multiple users to use the computer like you put in your first question - you will have to look into PXE booting on each of the remote computers.

No it doesn't make sense at all. If I use a VNC Client to connect to the Upstairs computer, I expect to see a login screen where I can choose my own login and then after a successful log in, I will see my own desktop. Like the ways Windows Remote Desktop works.

If VNC just relays the same screen content without allowing simultaneous multiple users, then it won't fit the scenario I am looking for. I would like to replicate a concept of "thin" clients where each user doesn't need a powerful computer but is able to run their Linux session off a central server. Let me look at this PXE concept.

---

### Post by JustinR on 2010-08-09
> **UranUtan said:**
> No it doesn't make sense at all. If I use a VNC Client to connect to the Upstairs computer, I expect to see a login screen where I can choose my own login and then after a successful log in, I will see my own desktop. Like the ways Windows Remote Desktop works.

If VNC just relays the same screen content without allowing simultaneous multiple users, then it won't fit the scenario I am looking for. I would like to replicate a concept of "thin" clients where each user doesn't need a powerful computer but is able to run their Linux session off a central server. Let me look at this PXE concept.

VNC is just that.

And what you described at the end is exactly PXE Net booting - using thin clients as the remote computer and a server (upstairs computer) as the remote computers source!

---

### Post by sh1ny on 2010-08-09
> **UranUtan said:**
> No it doesn't make sense at all. If I use a VNC Client to connect to the Upstairs computer, I expect to see a login screen where I can choose my own login and then after a successful log in, I will see my own desktop. Like the ways Windows Remote Desktop works.

If VNC just relays the same screen content without allowing simultaneous multiple users, then it won't fit the scenario I am looking for. I would like to replicate a concept of "thin" clients where each user doesn't need a powerful computer but is able to run their Linux session off a central server. Let me look at this PXE concept.

You can't have remote desktop "like"-ish functionality with VNC.
If you want a thin client functionality, use the ltsp-server that comes with ubuntu - Download the advanced ubuntu desktop cd and on the install menu ( first screen ) press F4 and select "Install LTSP Server".

---

### Post by UranUtan on 2010-08-09
Hum ... Now VNC is out. But two new concepts: LTSP Server, PXE Net booting. Sounds like I am going to have some learning to do for a while. Thanks gentlemen. Let's hope that's not too complicate.

---


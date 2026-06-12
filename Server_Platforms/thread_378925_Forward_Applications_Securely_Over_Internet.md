---
title: "Forward Applications Securely Over Internet?"
date: 2007-03-07
forum: Server Platforms
---

### Post by iXneonXi on 2007-03-07
Hello, I currently forward applications from my desktop running Xubuntu over to my laptop running DSL using ssh and my home network.  Is it possible to securely forward applications to my portable DSL system (PVPM running DSL Linux through Qemu from a USB key) over the Internet?
I am aware standalone application forwarding is very insecure and should not be used online, since keypresses may be intercepted making passwords vulnerable. Is there a way to secure the connection so I can forward my desktop apps to wherever I am, or should I take another approach, and if so I'm trying to get a secure application forwarding solution or I may give in and choose remote desktop approaches.  For what it sounds like I'm trying to accomplish, what are some good ways of going about it?
Sorry if I'm sounding a bit cryptic, it's hard to describe my situation and what I want to do.

---

### Post by Mr. C. on 2007-03-07
Are you saying you have a USB device, that you want to connect to insecure or public computers  and connect to some remote site securely?

If so, you have no control over these insecure systems, and therefore have no ability to necessarily detect or avoid keylogging software, or other malware / spyware.

If you are booting from your own USB device, then you will likely be secure (but no guarantees).

MrC

---

### Post by iXneonXi on 2007-03-07
I have something called the PVPM.  It's essentially DSL that runs inside QEMU when you launch a startup script. Since PVPM/DSL is a full linux installation, it has ssh support.

I am not necessarily worried about the local network (my work place) grabbing my input (they easily could since I'm running PVPM inside of Windows which even though input is transferred to QEMU a keylogger should still be able to intercept.

Using the portable DSL I wish to connect to the computer I'm posting from securely from anywhere, with the ability to forward apps to whatever computer I'm using to run DSL.

---

### Post by Mr. C. on 2007-03-07
Ok, I'm getting a better picture.

I'll still unclear about your concept of "forwarding apps".  One doesn't forward applications.  You can make an SSH connection, and tunnel TCP ports, thereby allowing you to securely connect to various services.

This would allow you to, for example, connect to your remote desktop session at, say home, from anywhere.  All you need is to tunnel, for example, VNC over SSH connected to your server.

Whenever I travel (with laptop, but your device will work too), I always have remote access to my desktops, mail server, ftp server, etc.

Is this what you're looking for?
MrC

---

### Post by iXneonXi on 2007-03-07
I'm looking for something similar. VNC as far as I know shares the entire desktop, and can be secure (however I have heard it has security flaws). By "forwarding apps" I mean something like "ssh -X user@address" which gives you a prompt wher one may type "gaim &" which will launch Gaim on the computer you are currently at (forwarded from the host computer like when using thin X clients).

However, if you have a guide to do what you have set up, I can at least give it a try, I just prefer to remotely use single applications as opposed to the entire desktop.

---

### Post by Mr. C. on 2007-03-07
Ah, got it.

Ok, VNC over and SSH tunnel is perfectly secure.  Until SSH's cryptographic is cracked, you have *nothing* to worry about.

SSH has two types of forwarding.  Standard TCP forwarding (tunneling) and X Window tunneling (this is just another form of the former).

Answer: yes you can do this.

Everything that passes through the tunnel is secure, and you should configure everything you use remotely to be tunneled.

To tunnel VNC to access your remote VNC server, you simply configure a localhost:5900 forward tunnel.

X11 forwarding is the same type of config. 

The SSH server must have these configured in sshd_config:

 AllowTcpForwarding  yes
 X11Forwarding  yes

if you want both.

Start with a single tunnel; for example, a remote VNC desktop connection.  To connectto your remote desktop, telll VNC to connect to locahost:5900 (after your SSH connection, and tunnel is up, this will forward port 5900 to your remote system, where the SSH server will redirect to port 5900 on that remote system).

Hope this helps,
MrC

---


---
title: "Using Ubuntu Server as a vpn server w/ SBS2003?"
date: 2010-04-21
forum: Server Platforms
---

### Post by gamnoparts on 2010-04-21
I have searched and found nothing, but that is probably b/c I'm not sure exactly what terms to search for. . .

We currently have an all Windows environment (7 xp/1 win7 workstations & 1 sbs2003 domain server) We have 3 users that access their workstations remotely thru rdp.  I would like to setup an ubuntu terminal(or vpn) server for remote access. I'm a little confused as to the best way to do that (or even what it is I should be researching).

Any ideas or at least which direction to look are greatly appreciated.

---

### Post by cdenley on 2010-04-21
What exactly are you trying to accomplish? Do you want secure access to a (text) terminal on your ubuntu server? Do you want to remotely establish a graphical desktop session on your ubuntu server (VNC, X11 tunneling, FreeNX)? Do you want to have access to the server's entire network by connecting to your ubuntu server (VPN)?

---

### Post by gamnoparts on 2010-04-21
Mostly I need access to the shared/mapped network drives that are on the server now.  I've already got access w/ remote desktop but it is slow & not really worth using. But w/ SBS I (believe) need to purchase terminal server & set that up, so I figured if I could do it w/ ubuntu, it would be 1-cheaper, and 2- help me in trying to convert the "conventional wisdom" of windows only around our office.

---

### Post by cdenley on 2010-04-21
These shares are being served from the ubuntu server with samba? I guess the simplest way to mount/map the shares remotely and securely would be to tunnel TCP port 139 through SSH. However, if you're working with large files, limited bandwidth could make this unusable. What kind of access to the files do they need? Do they need to use particular applications to access the files? If so, are the applications installed on their local computer and/or the windows server and/or the ubuntu server? Do they need to access them directly, or can they simply download a copy to work with?

---

### Post by spynappels on 2010-04-21
I guess the shared drives are on the Windows server? You can set up the Windows server as the OpenVPN server, or else a new Ubuntu server as the OpenVPN server, and map the Shared folders on client machines by LAN IP rather than by hostname. Then you just need to push routes to your clients that will allow them to use your office LAN IPs to connect to these shares through their VPN tunnels.

The only thing to watch is to keep the office LAN on a seldom used subnet such as 192.168.98.x or similar to avoid routing conflicts with clients on remote LANs with the same subnet.

---

### Post by gamnoparts on 2010-04-21
The shared drives are on the windows server. Most of the files would be typ office files (docs, xls) except for our accting program that is installed on the server & has it's database accessed from the server (if that makes sense).

And they would need to access what's on the server so that if anybody needs to view the same file, they can, but w/ read-only access and the knowledge that someone else is editing it.

My limited (and maybe flawed) thought process is that (hopefully) I could use a remote workstation to connect to the ubuntu server through vpn, which connects & authenticates users to the windows server, allowing access to the shared files. I think that's what I want to do, just not sure how to go about it.

Does/will it work that way or am I way off base?

One of the reasons I'm thinking in that line is if something happens to the ubuntu server & it takes me a little time to figure it out, it won't mess w/ the rest of the network.

THANK YOU guys very much, for helping w/ this.

---

### Post by cdenley on 2010-04-21
> **gamnoparts said:**
> 
My limited (and maybe flawed) thought process is that (hopefully) I could use a remote workstation to **connect to the ubuntu server** through vpn, which connects & authenticates users to the windows server, allowing access to the shared files. I think that's what I want to do, just not sure how to go about it.


What do you mean connect? Do you want remote users to have a grahpical destkop environment running on the ubuntu server? Which system do you want to actually open the file, the user's local system or the ubuntu server? You're accounting software is installed on the server? Does it execute on the server, or the user's local system? Does it have to be run on windows?

---

### Post by gamnoparts on 2010-04-21
I would prefer it to be as seamless as possible to what they're used to. I don't think I would need a graphical desktop on the ubuntu server. Right now, when they log into their pc it automatically reconnects the mapped drives. When they need to access a file for a specific job they go to that drive and find their folder.

I would like the users local system to open the file.

The accounting software, is installed on the server and the workstation. It has its own server/client versions. It looks like it does need to be run on a windows system.

---

### Post by cdenley on 2010-04-21
So you just need users to connect your the file shares on the windows server remotely. All they need is access to TCP port 139. Obviously, you don't want to make this open to the internet, so any type of encrypted tunneling should work. VPN or SSH. Using the ubuntu server to establish the tunnel wouldn't be difficult. However, if your bandwidth is so limited that an RDP session is unusable, I doubt remote file access will be any better.

Your accounting software sounds similar to ours. The database is accessed through a windows file share. Horribly inefficient. Running the software on the remote user's local system wouldn't work at all. It would take too long to read the database files over the internet. We had to resort to using terminal services so the accounting software can be executed on the server. 100 times faster.

---

### Post by stefan73 on 2010-04-21
At work, we run a Windows network and we use IPCOP boxes to handle our VPN needs (OpenVPN). OpenVPN has a nice and easy VPN client for Windows which works really well. IPCOP is not Ubuntu, but IPCOP is very easy to setup and administer.

---

### Post by cdenley on 2010-04-21
> **stefan73 said:**
> At work, we run a Windows network and we use IPCOP boxes to handle our VPN needs (OpenVPN). OpenVPN has a nice and easy VPN client for Windows which works really well. IPCOP is not Ubuntu, but IPCOP is very easy to setup and administer.

Never tried IPCOP, but I use and like pfsense.
[http://www.pfsense.com/](http://www.pfsense.com/)

---

### Post by gamnoparts on 2010-04-22
Thanks guys. If there isn't going to be much improvement I may just abandon the idea and stick w/ what we've got. I will definitely look into IPCOP and openVPN further, and maybe even try it just for me to test.  At least I know now that I'm on the right track - that's the hardest part. ;)

Again, thank you all for your help.

---


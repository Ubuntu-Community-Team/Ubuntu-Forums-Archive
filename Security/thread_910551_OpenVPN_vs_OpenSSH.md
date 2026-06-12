---
title: "OpenVPN vs OpenSSH"
date: 2008-09-04
forum: Security
---

### Post by Zakhafr on 2008-09-04
Hello forumers,

it's not a help question, it's interrogations :confused:

I read a little bit about SSH, and don't understand totally the pro/cons of it compared to OpenVPN I have been using for quite a while, both with Windows and Linux.

So correct me if I'm wrong.

OpenVPN:
-Pro:
 can tunnel(/bridge) almost every protocol whatsoever
 can connect clients to clients (if option selected)
 can connect LAN behind a client (if option selected)
 very high security : asymetric key + static key
 works very well in Linux AND Windows
 works through UDP or TCP (useful for proxying for example)
-Cons :
 adds a pseudo network-interface
 no direct integration with Linux systems

SSH (OpenSSH or others)
-Pro:
 integrated to Linux Systems
-Cons:
 works only with protocols adapted to SSH
 Windows support ?


OpenVPN looks superior to me, despite its not directly integrated by Linux tools.
I do plenty of things through it, totally seemlessly:
- HTTP
- FTP
- WebDAV (which is basically HTTP extended)
- VLC streaming (port 1234)
- VNC
- X11 remote connection.
The only port I need to open on the router is the UDP port of OpenVPN, and it makes the local network secure from outside attacks.

Do I get it right, or could some one explain the fundamentals differences with the two systems?

---

### Post by rogeriopvl on 2008-09-05
In most cases, SSH suits just fine for home computers. VPN is most suited for companies to provide external access to their intranet.

---

### Post by HermanAB on 2008-09-05
The fundamental difference is that SSH provides an on demand VPN which you establish whenever you need it, for the duration of the need only.  SSH connections can be set up and torn down in seconds.  One would frequently use SSH just to transfer a single file or execute a single command on a distant system.

OpenVPN connections are usually static and more permanent in nature.

Hope that helps!

Herman

---

### Post by Biochem on 2008-09-05
With SSH you can also take control of the remote computer.

Paersonnally I consider them as 2 different tools used for diferent purpose. OpenSSH for remote control and openVPN for remote network access. IMHO, samba and NFS over openVPN are so much more stable than sshfs

---

### Post by Zakhafr on 2008-09-05
Thanks for your inputs, I'm understanding a little bit better the differences now !

> **rogeriopvl said:**
> In most cases, SSH suits just fine for home computers. VPN is most suited for companies to provide external access to their intranet.
Ok, so as I manage a bunch of PC (association) I'm in the right path with VPN.


> **HermanAB said:**
> The fundamental difference is that SSH provides an on demand VPN which you establish whenever you need it, for the duration of the need only.  SSH connections can be set up and torn down in seconds.  One would frequently use SSH just to transfer a single file or execute a single command on a distant system.

OpenVPN connections are usually static and more permanent in nature.

Hope that helps!

Herman
Fantastic explaination!
And you are very right. When I look at the log of OpenVPN, it does quite a lot of things when connection opens. So it would not be efficient to start and stop it every time you need and. So SSH does that "light-VPN" for occasional use. 


> **Biochem said:**
> With SSH you can also take control of the remote computer.

Paersonnally I consider them as 2 different tools used for diferent purpose. OpenSSH for remote control and openVPN for remote network access. IMHO, samba and NFS over openVPN are so much more stable than sshfs
So SSH has a sort of bundled VNC in it? Or is it remote login (equivalent to remote X11 or telnet)?
True you can do it also with VPN, but then you will need an additional tool for VNC.
And I didn't yet do Samba & NFS over OpenVPN, but WebDAV over it was very reliable. I'll defintely try Samba now that I switched to Ubuntu (with windows, opening "shares" over a VPN, means that if the client is infected, it can easily bring viruses inside your secure VPN!)

Thanks again for your enlightenments.

---

### Post by Biochem on 2008-09-05
> **Zakhafr said:**
> 
So SSH has a sort of bundled VNC in it? Or is it remote login (equivalent to remote X11 or telnet)?
True you can do it also with VPN, but then you will need an additional tool for VNC.
And I didn't yet do Samba & NFS over OpenVPN, but WebDAV over it was very reliable. I'll defintely try Samba now that I switched to Ubuntu (with windows, opening "shares" over a VPN, means that if the client is infected, it can easily bring viruses inside your secure VPN!)

Thanks again for your enlightenments.

SSH actually stand for Secure SHell, so in it's most basic form it's like telnet with strong encryption. I often used it to launch session on remote computer somtimes with a complete DE like XFCE. You can also use is to transfer files (via scp, sftp, sshfs or rsync) or configure it to act as a small vpn. Honestly I never managed to get a ssh vpn going, but I didn't try for long.

As for the virus thing, any infected computer that sends files to any computer on your network can bring virus into your system, even via email... But if your computer is running any flavour of Linux than it is secure. If you are sharing files with windows computers it might be a good idea to install a virus scanner to scan your share as a courtesy toward the sensitive OS user. But, other consider that it's their problem.

---

### Post by kevdog on 2008-09-06
You can tunnel application over ssh similar to openvpn.  SSH is kind of like "VPN-light".  Its not as full featured as a full blown vpn, but because of the lack of overhead, it should run faster and consume less resources then openvpn.  Additionally setting up openssh is far easier than openvpn (which is kind of a pain).  HTTP can in fact be tunneled through openssh (with any computer, or through a router running ddwrt where openssh forwarding is built-into the router software).  

Both tools work well, it just really depends on what you want to do.

---

### Post by hyper_ch on 2008-09-06
well, IMHO

SSH --> taking remote control of another computer through a secured line
VPN --> attaching yourself to a remote (internal) network through a secured line

I know, it's a very broad description but I think it's not too bad.

---

### Post by kevdog on 2008-09-06
> **hyper_ch said:**
> well, IMHO

SSH --> taking remote control of another computer through a secured line
VPN --> attaching yourself to a remote (internal) network through a secured line

I know, it's a very broad description but I think it's not too bad.

Not a bad two line description, but with the use of tunneling applications through ssh, couldn't #1 also imply #2 in certain cases?  But overall I agree with your description.  If only there was such an easy process to get the openvpn server and client running as there is with openssh.

---


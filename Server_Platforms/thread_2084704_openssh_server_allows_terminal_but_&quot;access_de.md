---
title: "openssh server allows terminal but &quot;access denied&quot; when trying remote desktop"
date: 2012-11-16
forum: Server Platforms
---

### Post by hawaiiman on 2012-11-16
I'm using Bitvice to ssh on port 22 to Ubuntu 10.04 server with openssh installed. xrdp is also installed on server. Terminal opens fine, but I can't get a remote desktop to open. I've added and removed several programs to alleviate, but all more or less with the same result. 
" Attempting password authentication.
Authentication complested.
Auto opening SFTP session.
Auto opening xterm terminal session.
Opening new Remote Desktop session.
Listening for Remote Desktop client-2-server connection on 127.0.0.1:18380
suceeeded.
Remoter Desktop Connection launched successfully.
Accepted Remote Desktop client-2-server connection from 127.0.0.1:52601 to
127.0.0.1:3389
Server rejected our attempt to open a Remote Desktop client-2-server connection
-reason: SSH_OPEN_CONNECT_FAILED, description: connection refused.
Closing Remote Desktop client-2-server connection from 127.0.0.1:52601 to
127.0.0.1:3389, sent: 0, received: 0. "
Most of the time I try this when I'm far away from the server, But today I tried it close by. I was hoping I could quickly find a working setting, but so far no luck.

---

### Post by hawaiiman on 2012-11-29
"bump" anybody??

---

### Post by steeldriver on 2012-11-29
Can you explain a bit more what exactly you are doing? Is the RDP being tunneled over SSH or is it just being compressed? sorry I don't know what Bitvice is exactly

And by 'close by' do you mean on the same LAN or is NAT involved?

---

### Post by darkod on 2012-11-29
As an alternative, have you tried VNC? I think it's included in the desktop version, not sure are you running a desktop OS as server, or the server OS with added GUI.

Otherwise, if you don't have GUI, why would you try RDP when SSH is enough. And if you do have GUI, why not VNC access that it supports more or less by default?

---

### Post by itpro007ca on 2012-12-02
I'm running Ubuntu Server 12.04.

That's what I'm doing.

I can SSH to the Server to run text commands,and since VNC installed by default(I had to go in and under "Desktop Sharing",share the desktop),have TightVNC on the Windows XP PC(in the same room) and the Laptop (at the Dining Room Table)and it's great that I can save myself a trip upstairs!

---

### Post by darkod on 2012-12-02
> **itpro007ca said:**
> I'm running Ubuntu Server 12.04.

That's what I'm doing.

I can SSH to the Server to run text commands,and since VNC installed by default(I had to go in and under "Desktop Sharing",share the desktop),have TightVNC on the Windows XP PC(in the same room) and the Laptop (at the Dining Room Table)and it's great that I can save myself a trip upstairs!

Desktop Sharing, share the desktop, on Ubuntu Server release? Without installing a desktop environment?

I don't think it's possible.

---

### Post by hawaiiman on 2012-12-02
Bitvise is a free client which uses ssh to tunnel xterm, SFTP, and remote desktop (x11).
By close by I meant in the same room and connected through the LAN.
I read that tunneling an rdp through ssh was a secure method. This is why I chose it.
The server O/S is 10.01 server version with gnome desktop added.
I get the same results whether connecting from a LAN connection or from the internet.
Funny thing, when I first tried it, I had to install xrdp package on the server and was able to open an rdp from the internet. I was working on permissions for folders on the samba file server when the desktop locked up. I had to re-boot, but after that access denied and haven't had it working since. The xterm and SFTP sessions work just fine.

---

### Post by darkod on 2012-12-03
It seems that the change in permissions have something to do with it, if it was working before that. Try undoing those changes temporarily, and if it works you will know where the problem is.

Then look more carefully into the permissions you want to change to find out what you can or can not change.

I don't know how to help more, I have never used a GUI RDP to access a server.

---

### Post by hawaiiman on 2012-12-03
Yes I have been curious as to the "coincidence". Problem is, the permissions I was working with were in samba. There are now 38 users , each with group and individual folders all with permissions. I'm taking it as a forest and trees concept. I suspect that there is a fundamental conflict between samba and openssh at the root of this. I've noticed that in a .conf file, for example, that the order in which commands are entered changes the way the file as a whole operates. It could well be just a matter of cutting and pasting a few lines lower or higher on the page.

---


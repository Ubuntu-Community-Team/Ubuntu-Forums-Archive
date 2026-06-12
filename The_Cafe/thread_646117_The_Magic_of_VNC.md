---
title: "The Magic of VNC"
date: 2007-12-20
forum: The Cafe
---

### Post by Nekiruhs on 2007-12-20
Wow. I just discovered how wonderful VNC is. After installing UltraVNC Server and Viewer on my home comp, setting up port forwarding on port 5900, getting a DynDNS account to point to my IP, setting up encryption, and installing Portable UltraVNC Viewer on my flash drive I am amazed. At school I can now use all my apps, access all my documents and do more hardware intensive tasks *cough*COMPILING*cough*. VNC is amazing, why didn't I use it sooner? Anyone else use VNC?

---

### Post by kool_kat_os on 2007-12-20
Me does

---

### Post by a12ctic on 2007-12-20
ssh > *

---

### Post by LookTJ on 2007-12-20
> **a12ctic said:**
> ssh > *
I use ssh instead of VNC :D.

---

### Post by Nekiruhs on 2007-12-20
I never really understood SSH, but then again I never really understood VNC either till today. What are the benefits over VNC?

---

### Post by Depressed Man on 2007-12-20
SSH is more secure.

---

### Post by beercz on 2007-12-20
ssh is the way to go :-)  (Although I do use vnc on my LAN)

---

### Post by finferflu on 2007-12-20
I never managed to run X apps through SSH, so I always use VNC to help my friends (and my mother) over the net.

---

### Post by kevdog on 2007-12-20
How can you say SSH is more secure when you can tunnel VNC through SSH??  That statement makes no sense!

---

### Post by Sami_Sdata on 2007-12-20
I use x11vnc as a server then tightvnc as the client.  I connect with ssh and forward vnc through the encrypted ssh session.  I think it uses less bandwidth as well but haven't done much testing on that.

start the sever with 
x11vnc -display :0

connect with 
vncviewer -via [email]sami@my_ip.com[/email] 127.0.0.1


You need to have your VNC_VIA_CMD variable set on the client for this to work.
VNC_VIA_CMD=/usr/local/bin/ssh -f -L %L:%H:%R %G sleep 20

Might be a more elegant solution around.  I've been using this for years to connect from Solaris boxes at work back to my house.

---

### Post by Depressed Man on 2007-12-20
> **kevdog said:**
> How can you say SSH is more secure when you can tunnel VNC through SSH??  That statement makes no sense!

Aren't you then using SSH's security with VNC? Dunno, whenever I've seen this pop up, people say to do this for extra security.

---

### Post by got awesome? on 2007-12-20
I use NX on recommendation from this forum. It's far, far faster than VNC and works over SSH by default (and you only need your SSH port open).

It really is fast, I used VNC and liked it, but NX waaaaay better! Linux Server only, but you can get a Linux or Windows client (and maybe Mac too?), super easy to install and use (I also use a no-ip account for my dynamically assigned router).

[www.nomachine.com](www.nomachine.com)

---

### Post by popch on 2007-12-21
SSH (secure shell) lets you use the CLI from a remote location. VNC lets you access the GUI from a remote location. SSH is secure (because of encryption) and VNC is not. 

You can use VNC 'through' SSH. This adds encryption to VNC in a very robust and economical manner and makes it secure.

I have used VNC occasionally to remote control the Windows PC of my mother in law. I did this both from a Linux desktop and from Mac OS X. I did not even use dynamic DNS for that purpose. I wrapped the VNC server in Windows into a simple batch file which displayed the current IP address and some simple instructions for my mother in lawin a command window.

---

### Post by atomkarinca on 2007-12-21
> **got awesome? said:**
> I use NX on recommendation from this forum. It's far, far faster than VNC and works over SSH by default (and you only need your SSH port open).

It really is fast, I used VNC and liked it, but NX waaaaay better! Linux Server only, but you can get a Linux or Windows client (and maybe Mac too?), super easy to install and use (I also use a no-ip account for my dynamically assigned router).

[www.nomachine.com](www.nomachine.com)

Yes, NX is faster but it has a major disadvantage: it cannot log into an existing session. Until it can, VNC is the way to go for X applications for me. Other than that SSH is faster and smoother than any alternative.

---

### Post by toupeiro on 2007-12-21
[http://sourceforge.net/projects/securevnc/](http://sourceforge.net/projects/securevnc/)

ftw!

---

### Post by stalker145 on 2007-12-21
NoMachine FTW!!

CLI through SSH, remote login to new session through SSH, VNC through SSH. Heinously easy to install and no configuration required. 3 simple debs to run on the server side and one deb on the client side and you're ready to go :D

---


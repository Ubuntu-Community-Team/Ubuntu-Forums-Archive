---
title: "Should I get ubuntu server?"
date: 2009-08-04
forum: Server Platforms
---

### Post by pcarlos853 on 2009-08-04
Hello, I have some mild experience with ubuntu, I had it on my desktop for about a year. Anyway now I am using that computer as a server. It is running windows xp pro it has WAMP, Srcds (Counter Strike Source Game Server), RealVNC Server, Filezilla Server, a Ventrilo server (Voice game server), A mail server (Doesnt really work:(), and a DynDns updater (Because my external IP address changes this tool updates my hostname with the current ip address). I know everything that I have listed is compatatable with linux (I dont know if DynDns updater is or if there is a linux equlivant). I installed Ubuntu server on a virtual box just to try it out, but I had no idea what to do after I logged in. I read how to get a gui, but It just looked like a regular ubuntu desktop. In the install I slected LAMP and every program that they give you the option of installing (ex. mail server, mySoq). So my question is should I swich to Ubuntu server or stay with windows xp. 

Thanks alot!

---

### Post by slakkie on 2009-08-04
You could try it, although I don't like Ventrillo (since the server has only Linux binaries but the client doesn't). You could try Mumble an open source voice server (which has clients for all major playforms).

I once had a DynDns updater script, but it got lost a couple of years ago, but you can create such a script pretty easy.

A Linux server usually has no GUI, and is administered remotely via ssh. 

Set on up via virtualbox (you did that already) and download putty to login from your Windows desktop. You need to install the openssh-server package to do so:

aptitude install openssh-server

Then you can connect to that box via putty. If you have a Linux desktop you can use ssh for it.

---

### Post by pcarlos853 on 2009-08-04
Thanks for the fast reply!

Unfortunately, I think that Ubuntu server is to complicated for me so I will just keep running in on a virtual machine and trying different things with it until more comfortable.

---

### Post by hetx on 2009-08-04
Since an Ubuntu server is basically a desktop without the desktop, trying out regular Ubuntu will help you in case you decide to make the transition in the future! Wubi is a great way of trying Ubuntu with as little risk and work as possible.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by slakkie on 2009-08-04
> **pcarlos853 said:**
> Thanks for the fast reply!

Unfortunately, I think that Ubuntu server is to complicated for me so I will just keep running in on a virtual machine and trying different things with it until more comfortable.

Don't be scared :) But like hext said, maybe give Wubi a try and go from there (or not). Best of luck with whatever your choice may be!

---

### Post by pcarlos853 on 2009-08-04
I did have Ubuntu on my desktop for about a year and really liked it, but my printer was not compatible so I had to switch back to windows:(. Slakkie I didnt know mumble existed until you told me about it. I have downloaded it (server & client) and have recomended it to all of my friends:D

Thanks for all the advice everyone.

---

### Post by adrian-g on 2009-08-04
There is a DynDNS client for Ubuntu, it's called ddclient.

I used [this]("http://mexpolk.wordpress.com/2008/01/29/ubuntu-gutsy-dyndns-client-setup/") tutorial to get it set up on my web server.

It works flawlessy :)

---

### Post by juancarlospaco on 2009-08-04
install Gnome-core and you don't need VNC if you have SSH, 
disable automatic GDM, so it stay in CLI mode, and you can use a GUI to managment tasks.
iIn example:

ssh -X remote-user@servers-ip nautilus

ssh -X remote-user@servers-ip firefox

:)

---


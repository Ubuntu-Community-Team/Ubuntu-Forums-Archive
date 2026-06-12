---
title: "A few questions about Ubuntu Server"
date: 2008-06-20
forum: Server Platforms
---

### Post by mmad on 2008-06-20
I wanted to make sure of a few things before I actually install the Ubuntu Server. I currently have Windows XP but I want to dual boot it with the server which is going to be be on a seperate HDD. 

1) Will that actually be okay to run? (A friend told me that his Windows server 2008 wont dual boot because it encrypts the files on the other partition aswell)

2) How long does it take to turn on and off? (I ask because my friends server takes about 40 mins to turn on - and I dont think I can be bothered to wait that long)

3) Will I be able to configure the server so i can view it in a web browser on a computer that is not connected to my own network, i.e. over the internet?

Sorry about the long post, I just wanted to make sure that I know what I am getting myself into before I begin :p

---

### Post by tgrimley on 2008-06-20
1) I'm not sure about 2008, but Ubuntu will have it's own partition and hopefully windows won't touch it.. so it should be fine to run.

2) If you have hardware newer than 5 years old it shouldn't take you more than about 3 minutes to boot.

3) Of course, how you do it depends on what you mean by "view it in a web browser" as well as your network configuration.  Maybe you could tell us what you plan on doing with it? just hosting a http server like apache?

---

### Post by molotov00 on 2008-06-20
1) I've installed the server alongside WinXP without problems.
2) Less than 2 mins
3) I don't know what you mean by "view it". The server will only be serving when you've booted it. So either XP or Ubuntu, you can't run both at the same time. Unless, you go the route of vmware and run Ubuntu inside Windows or Windows inside Ubuntu. But this is a not a dual boot. If you just want to experiment I'd go the virtualization route.

Edit: apparently I wasn't fast enough w/ the reply.

---

### Post by mmad on 2008-06-20
Ah im sorry I didnt make my third question clear. Basically I want to be able to view the desktop and view the files/use the software on the server from another computer e.g. at a friends house or at school. Also this server is basically for learning purposes at the moment, I just want to experiment with file/print/webhosting servers :p

Thanks for the responses :)

---

### Post by molotov00 on 2008-06-20
If that's the case then I'd install vmware server, then create a new virtual machine that runs Ubuntu. Read up about vmware. Basically, this will allow you to have Ubuntu running inside of Windows. You'd want to use 'bridged networking' so that to all other computers on your network it will look as if there are two physical computers -- one with ubuntu and one with xp, each with their own IP.

Or, if you still want to dual boot... There are several ways to remotely control the server. There are apps such as webmin; there's connecting via ssh; there's 'remote desktop' which you can set up any number of ways (depending on whether you install Ubuntu, Kubuntu, or Xubuntu). All of these remote connection features will only work when you've booted the server. So again, only XP or Ubuntu, not both at the same time if you dual boot.

Also note that the server distribution does not include a desktop, only the command line. If it's just a hobby server, go with Ubuntu Desktop, which is very close to a Ubuntu server installation with a Gnome desktop.

[http://www.google.com/search?q=ubuntu%20vmware%20windows%20xp](http://www.google.com/search?q=ubuntu%20vmware%20windows%20xp)
[http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server](http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server)

---

### Post by mmad on 2008-06-20
> **molotov00 said:**
> If that's the case then I'd install vmware server, then create a new virtual machine that runs Ubuntu. Read up about vmware. Basically, this will allow you to have Ubuntu running inside of Windows. You'd want to use 'bridged networking' so that to all other computers on your network it will look as if there are two physical computers -- one with ubuntu and one with xp, each with their own IP.

Or, if you still want to dual boot... There are several ways to remotely control the server. There are apps such as webmin; there's connecting via ssh; there's 'remote desktop' which you can set up any number of ways (depending on whether you install Ubuntu, Kubuntu, or Xubuntu). All of these remote connection features will only work when you've booted the server. So again, only XP or Ubuntu, not both at the same time if you dual boot.

Also note that the server distribution does not include a desktop, only the command line. If it's just a hobby server, go with Ubuntu Desktop, which is very close to a Ubuntu server installation with a Gnome desktop.

[http://www.google.com/search?q=ubuntu%20vmware%20windows%20xp](http://www.google.com/search?q=ubuntu%20vmware%20windows%20xp)
[http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server](http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server)

Okay I'll try it in VMware, but I intended to install the server version because it already contains everything I might need, and the GUI is not going to be hard to install :). Thanks for your reply :mrgreen:

---

### Post by tgrimley on 2008-06-20
I'll add that if you're doing any remote desktop sort of thing, I have had the most success with nx desktop from nomachine.  You need a client, but there is one for Windows and Linux and there are debs on the site to install on your Ubuntu machine.  It's very fast for me over slow connections.

---

### Post by mmad on 2008-06-20
> **tgrimley said:**
> I'll add that if you're doing any remote desktop sort of thing, I have had the most success with nx desktop from nomachine.  You need a client, but there is one for Windows and Linux and there are debs on the site to install on your Ubuntu machine.  It's very fast for me over slow connections.

I know of a few client based remote control services, but I was going for a browser version so Im not restricted on networks where certain file types cannot be executed, e.g. at school I cannot run .exe files because a standard user does not have the permissions to do so. I figured that If i used a java based system within a browser, then at least I could access it.

EDIT: I just came across this: [http://www.microsoft.com/windowsxp/using/networking/expert/northrup_03may16.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/northrup_03may16.mspx) - Would this be ok to do if I was running ubuntu within VMware?

---

### Post by molotov00 on 2008-06-20
vncserver serves an html page with a java applet. i'd prefer to connect directly to the virtual machine than through xp->vm. but there's nothing stopping you from using an xp-based remote desktop, as you've linked to.

---


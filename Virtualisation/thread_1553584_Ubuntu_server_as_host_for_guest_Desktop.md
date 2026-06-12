---
title: "Ubuntu server as host for guest Desktop"
date: 2010-08-15
forum: Virtualisation
---

### Post by joerg_ac on 2010-08-15
Hi,

I am going to set up an Ubuntu 10.04 server mainly to get a clean  file-server with a big raid array. It is supposed to run without a  desktop for most of the time. On top of this I would like to use KVM in  order to use guests, which are desktops. So if I attach a monitor to my  server I want it to serve me with a (virtualized) desktop system.

Questions:
- Can a desktop with GUI run in a VM on a server/host which does not have a GUI? 
More specifically: Will the Desktop guest be able to get the screen for graphical output? If yes, would this be hard to achieve?

- If this works, will I still get direct access to the server's console.  I mean, by switching full-screen between the server console and the  guest desktop's GUI. 

- In this setup, it would also be possible to run two desktop guests in  parallel. Probably Windows and Ubuntu Desktop. Could I simply switch  in-between them and the host's console for example by using a Keyboard  shortcut.


Of course I could use Ubuntu desktop as the host, but the server is most  of the time running standalone. I want a clean server and separate the  desktop as much as possible. For remote server configuration I also plan  to use eBox. Thus, I do not need to sit in font of the server except if  I want it to provide a desktop to me. 

Does this plan sound very weird to you. To me it makes perfect sense,  because the box the server is running on is much too powerful to be only  a home-fileserver. Also, having the desktop in a VM allows playing with  it without risking the well configured server. I like this way of  getting a desktop much more than installing the Ubuntu-desktop package  directly on top of the server as it is discussed often in this forum. 
I am a little bit worried that my plan does not work, because I read  somewhere that KVM on top of Ubuntu server is mainly made for  virtualized server guests. 

I did also put this request in the Server section. I am not sure if it belongs here ore there.

Many thanks in advance for your opinion and advice, Joerg

---

### Post by joerg_ac on 2010-08-15
Hi,

Let me rephrase my question:

Is it possible to run a guest system with GUI on a host (KVM,  VirtualBox) without a GUI? Can the guest GUI be visible on a screen  attached to this server box although the host system is only running a  CLI?

I want to use Ubuntu server with eBox. Occasionally I want to be able to  start a desktop (or even many desktops like a linux and a Windows one)  on this same machine and work with it locally (not remotely) sitting in  front of this server box. 

If this does not work well: should I better install Ubuntu desktop as  host and use it as server (mainly file server). I would then have no  problems running further desktops using Virtual Box. Does eBox support  Ubuntu Desktop?

Another alternative might also be installing Ubuntu Server and adding a  GUI to it. Then use Virtual Box or KVM to get the other VMs.

What do you think? What will be the best way to go? The central Idea is  having a lightweight and remotely (eBox) managed server by default  (Monitor stays off) and if I need a desktop of any type, I want this  server to provide it to me locally. I also want  server as separated  from the desktops as possible and to be flexible to run different  desktop systems is needed.

best regards, Joerg

---

### Post by TheFu on 2010-08-16
Yes. Check out **vboxheadless** (OSE version) and you'll need to configure some kind of remote access to the client OS.  Remote access can be as simple as ssh or you can load VNC (or any variant) inside the client OS. If your client OS is Windows, you can use RDP, provided you set that up inside the client and have the appropriate version of Windows. I know you didn't ask this, but lurkers may be interested.

If you selected the non-OSE version of VirtualBox, I suppose you can use RDP from the OS server side, but I don't use that and don't know about that. The theory is that you won't need to install anything inside the client OS, I believe.

I see from your second post that you really just want a server OS that normally doesn't include a GUI (X/Windows), but still be able to access client OSes with GUIs locally.  I run Ubuntu Server, but added LXDE (which includes X-Windows in the dependencies), so you can use the normal VirtualBox GUI and access your client OS VMs just like any other desktop user does.  If you use the ebox version on Ubuntu, it is fairly easy to add the GUI of your choice to is. There are lots of articles on which packages to install out "there."  I may even have written a blog article on it too. ;)

Anyway, either method will work.  Remote access or just loading a DE locally.

---

### Post by joerg_ac on 2010-08-16
Hi TheFu,

Thank you very much for you help. This confirms somehow what I did suspect from reading in this forum and elsewhere. So I can either use remote access to the guest GUI or I need an X-server in the host for local access. I did somehow hope, that the local screen control can be assigned to the x-server in the guest, so that the host can live without X for a local screen. I wanted a clean separation of server and desktop, but maybe I am overdoing here for a home server. Also, the GUI tools of Virtual Box seem to be that convenient that a lightweight GUI on the server is anyway the best option for me. So the host GUI is only used for managing and starting the VMs. 

I think I can live with it. I guess, I can also boot the server GUI-less and start the host GUI on demand with startx. 

As these are my first practical experiences with virtualization I have another question. What would give me the best overall experiance in terms of performance, stability and convenient tools in a use case like mine: KVM, Virtual Box or even VMware? I was planning to use Virtual Box, because it is said to be easy to use, but I am not religious about it. 

I guess I simply start experimenting. I am looking forward to it.

I highly appreciate your help, thanks again, Joerg

---


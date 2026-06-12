---
title: "Headless GUI admin Server 10.04"
date: 2011-05-04
forum: Server Platforms
---

### Post by drexlock on 2011-05-04
Hello Awesome Ubuntu Community.

I have been having some trouble configuring a means to remotely administer an Ubuntu Sever 10.04 machine i recently built and am hoping for some guidance. I'm sorta new to linux so please forgive my ignorance of conf files and the command line :). 

I am looking to have this server serve as...
VPN Server, Minecraft Server, KVM Server, Torrent and Dyn-DNS box.

I have managed to install all the KVM settings including bridged networking running (Personal victory there) and sorta have Minecraft running (only need to figure out how to make it launch on boot). Torrents already taken care of since Transmission came along with the ubuntu desktop install :).

The big thing that is slowing me down is remote management. I installed ubuntu desktop (thankfully its Gnome 2), i know that most people don't like it but its what i'm most familiar with. I tried running VNC but always needed to login on the physical machine before I could use that which defeats the purpose. I am now using xrdp which frankly the performance is terrible compared to what i was getting with the built in VNC server and still needed the monitor on and active to connect.  

Is there a way to use either of these (VNC preferably) using a headless system without the need to login prior to attempting to connect?

---

### Post by HermanAB on 2011-05-05
Howdy,

VNC is mostly a Windows thing and is almost always the wrong solution on Linux.

Install ssh-server and use ssh from Linux or Cygwin and ssh or Putty on Windows:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

---

### Post by Lars Noodén on 2011-05-05
HermanAB describes how you can tunnel clients to the X server on your desktop.  It's worth knowing how. The program is then running on the remote machine but its window is interacted with on your desktop.  Any graphical program can run that way.

---

### Post by drexlock on 2011-05-05
Thank you for the help. I'll have to try that method out when i get home. I've been looking  for a solution for a few days now and was getting incredibly frustrated cause nothing i tried seemed to work exactly right :(

---

### Post by CharlesA on 2011-05-05
> **drexlock said:**
> Thank you for the help. I'll have to try that method out when i get home. I've been looking  for a solution for a few days now and was getting incredibly frustrated cause nothing i tried seemed to work exactly right :(
You'll need an Xserver running if you are using Putty on Windows - I use XMing.

On Linux, you are fine, as it's already running X.

I think Cygwin has an xserver, but I am not sure.

---

### Post by drexlock on 2011-05-05
XMing works like a charm :) but when i connect i get a terminal, so i type gnome-panel and the toolbars appear and i get this message "** (gnome-panel): WARNING **: Could not connect to session manager: Could not get owner of name org.gnome.SessionManager': no such name". 

Also, when I start Minecraft_Server.jar as soon as i close my ssh session the Minecaft server shuts down also :(. Is there a way to keep any programs running after disconnecting like when using RDP to a windows server? I hate to use the MS word here buts its what I am most familiar with :(

EDIT: Also about 50% of the time I get "Network error: Connection refused" when trying to connect

---

### Post by CharlesA on 2011-05-05
Start the minescript server in a screen session:

```
screen
```

Do you have a firewall in place?

---

### Post by drexlock on 2011-05-05
I do have a firewall on my Win7 desktop but i made an exception to allow XMing. 

When I coonect it seems like gnome is almost half loading. My background is a a black to white gradiant and my cursor is a black X. But when i move the cursor over a window (like the mincraft server window) or a menu bar it becomes the normal cursor again.

EDIT: I did try connecting from a test machine i have running 11.04 and still recieved the org.gnome.Sessionmanager error.

---

### Post by CharlesA on 2011-05-06
Interesting. not sure why that's happening. Can you launch something like gedit?

---

### Post by drexlock on 2011-05-06
I can launch programs from the taskbar like gedit and terminal and such, but things like trying to shutdown or restart the server does not work. The buttons appear but nothing happens once you click them.

---

### Post by arrrghhh on 2011-05-06
> **drexlock said:**
> I can launch programs from the taskbar like gedit and terminal and such, but things like trying to shutdown or restart the server does not work. The buttons appear but nothing happens once you click them.

I'd say you're trying to fit a square peg into a round hole...

If you want Ubuntu Desktop, install Ubuntu Desktop.  If you want Ubuntu Server, install Ubuntu Server - but don't go installing a DE on the Server edition, you're asking for pain (and it's completely unnecessary pain!)

---

### Post by drexlock on 2011-05-06
> **arrrghhh said:**
> I'd say you're trying to fit a square peg into a round hole...

If you want Ubuntu Desktop, install Ubuntu Desktop.  If you want Ubuntu Server, install Ubuntu Server - but don't go installing a DE on the Server edition, you're asking for pain (and it's completely unnecessary pain!)

Its not that i want to use this machine as my daily driver im just used to a gui for administration. Plus for a LTS server the extend support is important to me. 5 years for server really makes the difference for me especially because this is going to be a headless machine.

---

### Post by arrrghhh on 2011-05-06
> **drexlock said:**
> Its not that i want to use this machine as my daily driver im just used to a gui for administration. Plus for a LTS server the extend support is important to me. 5 years for server really makes the difference for me especially because this is going to be a headless machine.

Well you're mixing things here.  LTS Server and GUI's don't mix - one or the other I say!

---

### Post by moe19790 on 2011-05-06
Well, if u want an ubuntu LTS + GUI why don`t you try [http://www.zentyal.org/](http://www.zentyal.org/) "formally E-box"

MOe!

---

### Post by arrrghhh on 2011-05-06
> **moe19790 said:**
> Well, if u want an ubuntu LTS + GUI why don`t you try [http://www.zentyal.org/](http://www.zentyal.org/) "formally E-box"

MOe!

Ubuntu Desktop is also LTS, it's just 3 years support instead of 5.

---

### Post by moe19790 on 2011-05-06
thats also a 5 years, its Ubuntu server LTS + GUI :)

---

### Post by moe19790 on 2011-05-06
To make it clear its a light weight customized GUI for servers for easy admiistrationsad installation

MOe!

---

### Post by arrrghhh on 2011-05-06
> **moe19790 said:**
> thats also a 5 years, its Ubuntu server LTS + GUI :)

Yea, but it's a webUI, not a full blown DE... I would definitely encourage the use of a webUI over a full blown DE any day.

Webmin isn't bad either, although I think it's not 'officially' supported by Ubuntu.

---

### Post by moe19790 on 2011-05-06
yep u got that right :) i thought he was asking for that not a real full DE. mmmmmmmm, i might be wrong lol :D. both those WebUI made my life way easier :D

---

### Post by CharlesA on 2011-05-06
I'd rather run something like Openbox on a server if I really needed a GUI.

Or in my case, I have a VM on my server that is running Ubuntu desktop. I use it for for web development, but I don't know how well that would work for a minecraft server.

---

### Post by drexlock on 2011-05-06
I managed to correct the connection issue i was having with SSH by uncommenting port 22 under ssh_config and moved my minecraft server back to the VM I had installed it on originally in KVM.

My whole reason for first trying the RDP/VNC route was because I like the option of working at the machine, walking away, and from another machine resuming what i was doing. Given I know that this is a server and is not something that happens often but its a feature i found very handy when this was a Server 2008 machine running Hyper-V. 

This is what my SSH X11 session looks like when i connect....

[IMG]https://lh5.googleusercontent.com/_PJtC-nyhMrI/TcSi_jN6wBI/AAAAAAAAABY/b_jmiG4YQs0/s1024/SSH%20X11.jpg[/IMG]

---

### Post by arrrghhh on 2011-05-06
> **drexlock said:**
> I managed to correct the connection issue i was having with SSH by uncommenting port 22 under ssh_config and moved my minecraft server back to the VM I had installed it on originally in KVM.

**My whole reason for first trying the RDP/VNC route was because I like the option of working at the machine, walking away, and from another machine resuming what i was doing.** Given I know that this is a server and is not something that happens often but its a feature i found very handy when this was a Server 2008 machine running Hyper-V. 


What, you never heard of screen?  :p

---

### Post by drexlock on 2011-05-06
> **arrrghhh said:**
> What, you never heard of screen?  :p

Not really no. This is my first serious linux machine. Ive "played" with a variety of linux disros in virtualbox but never ran it as a production machine. This is in a way my first step in my jump to linux.

---

### Post by arrrghhh on 2011-05-07
> **drexlock said:**
> Not really no. This is my first serious linux machine. Ive "played" with a variety of linux disros in virtualbox but never ran it as a production machine. This is in a way my first step in my jump to linux.

Screen allows you to do just what you describe - you can have many, many things open even - you can have as many instances of screen running as you could possibly want.  Check it out, there's no need for a full blown DE on Linux - one of the main reasons I think it's way ahead of Windows Servers...

---

### Post by drexlock on 2011-05-08
Thank you all for all the help. Using Webmin screen and xrdp I now have a successfully manageable  headless ubuntu server :) I was getting tempted to go back to server2008 over this but now that its up and running I'm beyond happy that i did not. Thank you all again for all the help :)

---


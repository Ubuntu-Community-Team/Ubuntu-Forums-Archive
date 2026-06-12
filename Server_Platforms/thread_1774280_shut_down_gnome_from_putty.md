---
title: "shut down gnome from putty"
date: 2011-06-03
forum: Server Platforms
---

### Post by Fodox on 2011-06-03
Hello

I have ubuntu 10.4 lts server and I want to use it only via putty and vnc.
This server have gnome and gdm installed without autostart.
When I need, I start gnome with putty and I use vnc client to use the graphical interface.
When I have finished I close vnc and I want to shut down gnome, but here I have problems.
I don't know how to do it: I tried to kill everything, but I have not found the correct way to make a clean operation.

Please help! Thank you.


   Fodox

---

### Post by Lars Noodén on 2011-06-03
Wouldn't this do it for you?

```

sudo /etc/init.d/gdm stop

```

---

### Post by egpetrich on 2011-06-05
If I understood your original post correctly, you're logging in with Putty and then launching the Gnome desktop (which appears on the workstation display). You then use a VNC viewer to connect to that desktop.

Two thoughts come to mind:
[LIST=1]
[*]Can you just select the "logout" option from the Gnome desktop through VNC? This should at least log you out, which would then either disconnect the VNC session or return you to the GDM login screen. You could then disconnect from VNC without leaving yourself logged in.
[*]Or, you could install the "vnc4server" package (assuming it isn't already installed). Once everything is set up correctly, you can start a virtual Gnome desktop from Putty using the command "vncserver". This won't show on the workstation display, but you can connect to it using your client VNC viewer. When you're all done, you can either disconnect and leave the VNC server running, or you can shut it down with "vncserver -kill".
[/LIST]Hope this makes sense.

---

### Post by Fodox on 2011-06-06
```
sudo /etc/init.d/gdm stop
```
this command can't work: I am in ubuntu 10.4 and some things are changed.

Here are the steps I follows in details:

[LIST]
[*]login with putty from a client pc in my home network, physically near the server pc
[*]type in putty "sudo gdm start" (I can see in the server monitor gnome starting)
[*]type in putty "CTRL-Z", I return to prompt
[*]type in putty "sudo x11vnc -usepw -bg -forever"
[*]now I can connect with vnc clients, I can use the server as a desktop
[*]when I have finished, I try to click on "system -> logout...." through vnc connection but nothing appens. I remain logged in: FIRST PROBLEM!
[*]type in putty "sudo x11vnc -r stop". the vnc server stop and from now I can't login with client.
[*]now I want to shuth down gdm and gnome but I don't know hot to do. If I type "sudo gdm stop" I can see following messages and nothing happens:
```
WARNING ***: Failed to acquire org.gnome.DisplayManager
WARNING ***: Could not acquire name; bailing out
```
If I type "sudo ps -a" I can see: **gdm-binary**, **gdm-simple-slav**, **gdm-sesion-wor**. Googling I have found this command: "sudo init 1". This stop gnome and close my putty connection, but after few seconds I can see in server monitor a text-based window called "resume menu" with some choices. I can't login with putty, I have to reboot the server directly from the pc.
[/LIST]

Please help in my steps, I can't believe it is impossible to kick out gdm once started :-P

I will try also "vnc4server", it could be the solution. Thank you.

ah, please also excuse my english errors ^_^

---

### Post by krunge on 2011-06-06
Do I understand correctly that you suspend something via 'Ctrl-Z' to get a prompt back, but you do not subsequently put the thing you suspended into the background via 'bg'?

What programs(s) and process(es) are you suspending? I'm not familar with 'gdm start'. I'm guessing if a gdm process is suspended there will be problems for the next X session login...

---

### Post by collisionystm on 2011-06-06
> **Fodox said:**
> Hello

I have ubuntu 10.4 lts server and I want to use it only via putty and vnc.
This server have gnome and gdm installed without autostart.
When I need, I start gnome with putty and I use vnc client to use the graphical interface.
When I have finished I close vnc and I want to shut down gnome, but here I have problems.
I don't know how to do it: I tried to kill everything, but I have not found the correct way to make a clean operation.

Please help! Thank you.


   Fodox


```
sudo bash

service gdm stop
```

---

### Post by Fodox on 2011-06-07
> **krunge said:**
> Do I understand correctly that you suspend something via 'Ctrl-Z' to get a prompt back, but you do not subsequently put the thing you suspended into the background via 'bg'?

What programs(s) and process(es) are you suspending? I'm not familar with 'gdm start'. I'm guessing if a gdm process is suspended there will be problems for the next X session login...

I press ctrl-z becouse after typing "sudo gdm start" I have no more prompt command, but I need it to start x11vnc. Apparently nothing is stopped, looking at server's monitor nothing is changed.
After googling right now, maybe I can use the "&" to send the command directly in background:

```
sudo gdm start &
```

---

### Post by collisionystm on 2011-06-07
> **Fodox said:**
> I press ctrl-z becouse after typing "sudo gdm start" I have no more prompt command, but I need it to start x11vnc. Apparently nothing is stopped, looking at server's monitor nothing is changed.
After googling right now, maybe I can use the "&" to send the command directly in background:

```
sudo gdm start &
```



On the server monitor you need to hit CTRL ALT F7 or F8

---

### Post by Fodox on 2011-06-07
> **collisionystm said:**
> ```
sudo bash

service gdm stop
```

doesn't work, this is the output:

```
Rather than invoking init scripts through /etc/init.d, 
use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted 
to an Upstart job, you may also use the stop(8) utility, 
e.g. stop gdm
```

this command also doesn't work:

```
stop gdm
```

output:

```
Unknown job: gdm
```

---

### Post by tseb on 2011-06-07
Hi,

In the past when I wanted to do exactly this, instead of the gdm command to start gnome, I used sudo nohup startx and then could disconnect my session and the gnome session would keep running, then I would close by using the logout on the VNC desktop. 

I don't know if using nohup made this possible, but it worked OK for me!

Hope it is some help...

tseb.

---

### Post by arrrghhh on 2011-06-07
Don't use GNOME on a server... Seriously.

It's not only a waste of resources, but it's a big security risk and adds a ton of packages that need updating.  Plus, it seems to add a lot of silly headaches!

---

### Post by Fodox on 2011-06-14
> **arrrghhh said:**
> Don't use GNOME on a server... Seriously.

It's not only a waste of resources, but it's a big security risk and adds a ton of packages that need updating.  Plus, it seems to add a lot of silly headaches!

I installed gnome-core. I need this to use nautilus or to launch graphical packages, like transmission.
Gnome doesn't start automatically, I use it only when I need. The server is a home server and not a work server.

---

### Post by Fodox on 2011-06-14
It's time to close this topic, I have found 3 solutions!

Step by step, the dirty one:

[LIST]
[*]login with putty
[*]type "sudo gdm start"
[*]type "CTRL-Z" then "bg"
[*]type "sudo x11vnc -usepw -bg -forever"
[*]Now vnc and gnome are ready: I do my things, when I have finished I close the vnc client without gnome logout
[*]type "sudo killall gdm-binary" to shut down gnome
[/LIST]

The clean one, thanks to tseb:

[LIST]
[*]login with putty
[*]type "sudo nohup startx"
[*]type "CTRL-Z" then "bg"
[*]type "sudo x11vnc -usepw -bg -forever"
[*]Now vnc and gnome are ready: I do my things, when I have finished I do logout from gnome. Graphical session closes automatically.
[/LIST]


The alternate way, my preferred, thanks to egpetrich:

[LIST]
[*]login with putty
[*]type "sudo vnc4server"
[*]Now vnc and gnome are ready: I do my things, when I have finished I close the vnc client without gnome logout
[*]type "sudo vnc4server -kill :1" to close vnc and gnome together
[/LIST]


bye
  Fodox

---

### Post by arrrghhh on 2011-06-14
> **Fodox said:**
> I installed gnome-core. I need this to use nautilus or to launch graphical packages, like transmission.
Gnome doesn't start automatically, I use it only when I need. The server is a home server and not a work server.

Just forward X over SSH.  No need for GNOME or VNC.  I do this with Dolphin all the time...

To each their own, you just seem to be doing a lot of extra work for nothing.  Just trying to provide alternatives to your setup, which from my angle looks a little silly ;).

---

### Post by Fodox on 2011-06-15
> **arrrghhh said:**
> Just forward X over SSH.  No need for GNOME or VNC.  I do this with Dolphin all the time...


Sorry, but I dont't understand your tip; can you explain more?
I forgot to mention that I connect to the server with a windows client.

Thanks :D

---

### Post by Lars Noodén on 2011-06-15
> **Fodox said:**
> 
I forgot to mention that I connect to the server with a windows client.


That's too bad.  Sorry to hear it's still a problem.

Windows does not come with a X server.  Your choices are limited.  There's [Xming](http://sourceforge.net/projects/xming/), [Cygwin/X](http://x.cygwin.com/) and maybe a few others. 

Once you have a X server on your desktop, your programs can be run on the server, but displayed on your desktop.  That method is known as X11 Forwarding or Tunneling X11.  There are tons of short guides on how to do it the first time.

---

### Post by arrrghhh on 2011-06-15
> **Fodox said:**
> Sorry, but I dont't understand your tip; can you explain more?
I forgot to mention that I connect to the server with a windows client.

Thanks :D

Lars beat me to it ;).

His explanation was probably vastly better than mine - all I can add is that I use Xming @ work (WinXP only here...) and it works pretty well.  Obviously if you're on a Linux box it's easy since X is already there & ready to go... but the process to get it working on Windows isn't bad.  Putty+Xming, little bit of config and you're good to go.

---

### Post by Fodox on 2011-06-15
I searched the solution for months and now... a new challenge with xming. My brain is burning away ](*,)

Maybe i will try, I like to learn new things expecially in linux world.
However, probably xming is not the right solution for me. For example, if I need to download something with transmission I need desktop session remains open even if I logout and disconnect. Also, with my method I need only two executables: putty.exe and vncviewer.exe. I can upload those in my web site and quickly download if I need.

Security implications... yes, vnc is not the best, and password is only 8 characters. But in my case there is no sensible data in the server pc and I have a dynamic IP connection. I can accept the compromise :D

---

### Post by arrrghhh on 2011-06-15
> **Fodox said:**
> I searched the solution for months and now... a new challenge with xming. My brain is burning away ](*,)

Maybe i will try, I like to learn new things expecially in linux world.
However, probably xming is not the right solution for me. For example, if I need to download something with transmission I need desktop session remains open even if I logout and disconnect. Also, with my method I need only two executables: putty.exe and vncviewer.exe. I can upload those in my web site and quickly download if I need.

Security implications... yes, vnc is not the best, and password is only 8 characters. But in my case there is no sensible data in the server pc and I have a dynamic IP connection. I can accept the compromise :D

Well honestly then it seems like you want Ubuntu Desktop **not** Ubuntu Server...

Don't try to fit a square peg in a round hole.

---

### Post by Fodox on 2011-06-16
> **arrrghhh said:**
> Well honestly then it seems like you want Ubuntu Desktop **not** Ubuntu Server...

Don't try to fit a square peg in a round hole.

I don't think so. I use the server as file server with my mp3 and videos (my home is cabled), ftp server, web server for sharing my photos with my relatives and to test some works...

Right now I have a P3 1Ghz with ubuntu desktop 9.10, with installed all the server features and removed some unused apps. Now I want to change my "point of view" with the server version :D

I think ubuntu server (with graphic session off) consumes less power.

Thank you anyway for your precious advices!

---

### Post by arrrghhh on 2011-06-16
> **Fodox said:**
> I don't think so. I use the server as file server with my mp3 and videos (my home is cabled), ftp server, web server for sharing my photos with my relatives and to test some works...

Right now I have a P3 1Ghz with ubuntu desktop 9.10, with installed all the server features and removed some unused apps. Now I want to change my "point of view" with the server version :D

I think ubuntu server (with graphic session off) consumes less power.

Thank you anyway for your precious advices!

I think if you're going to go the server edition, go all out... no DE ;).  It's just a crutch, and it probably does consume more power.

There are CLI tools for downloading torrents (I like rtorrent), there's tools like screen, there are many many ways of making the terminal work for you - no need for a DE at all.

I know at first it can be hard, but honestly I learned a lot about how Linux (and Ubuntu) work underneath when I went full server.  I was definitely a little intimidated, but after a lot of reading and some help on here I have a really solid server, and I never ever need to access any sort of a desktop interface on it.  I very rarely ever forward X over ssh as we talked about earlier, cli is all I need!

Especially when you have older hardware that runs a little slow... remove that DE!

---


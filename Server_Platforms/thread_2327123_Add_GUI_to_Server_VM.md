---
title: "Add GUI to Server VM"
date: 2016-06-07
forum: Server Platforms
---

### Post by Sxcd1 on 2016-06-07
I have installled 14.04 Ubuntu and choose VM option.  Is there any disadvantage to installing a GUI ?  Which one is recommended?
I'm thinking of installing a screen capture program to capture video from firefox.  Will that run with a server running in the backround?

---

### Post by DuckHook on 2016-06-07
There's nothing inherently "special" about Ubuntu Server. It's just a command line interface with some configuration files optimized for server usage (example: swappiness). However, it assumes that the user is worried about security so its default is command line only. This exposes as few surfaces as possible to potential attackers. Most Linux server administrators will run their servers only with the command line. However, many desktop users install the server version and then add the desktop of their choice. This converts the install from a server into a desktop, but it's not really a big deal. You will just have certain configurations and parameters optimized for a server instead of a typical desktop. You can choose to use *any* machine as a server, a desktop, or both. There is no special ingredient that magically makes one machine a server and another machine a desktop.

The real issue with GUIs is security. Security-conscious administrators will not allow GUIs on their server for the same reason that they won't allow browsers, office apps or any typical desktop app: these are all invitations to have your security breached. And if apps are not permitted, then there is no point in just having the GUI, which is itself a security hole. For example, xorg, the graphics server for all 'buntu desktops, directly accesses main memory and is not sandboxed. Therefore, theoretically, the mere act of running a desktop GUI creates a security hole that doesn't need to be there. GUIs also need lots of processes running to make all of those pretty pictures. The more processes, the more attack surfaces, things that can go wrong, app maintenance and resources eaten up for no good reason.

Reading between the lines of your post, I am assuming that you are just exploring and discovering. If so, I don't see what harm a GUI will do in your case. I would definitely not recommend installing a GUI if this was a critical production server. However, if you wish to learn good server habits (for example, if you are studying to become a server admin), then you definitely do not want to be running Firefox on your server.

---

### Post by Bucky Ball on 2016-06-07
A very lightweight desktop is lxde. xfce4, also lightweight, is my preference.

Installing 

```
sudo apt-get install xfce4
```

or 

```
sudo apt-get install lxde
```

Reboot and you should get a login screen.

---

### Post by HermanAB on 2016-06-08
Normally, a server is installed in a rack, together with a hundred others and resides in a dark corner of a dank data centre, with not a living soul about, except maybe a mouse (the biological kind), with no screen, keyboard or mouse (the mechanical kind) attached to it.  

In this case, installing a point and click GUI is rather pointless, since the machine will be operated remotely over SSH from a rather more airy environment, where the machines do have all the necessary pointy-clicky attachments with GUIs to support SSH for remote administration of the above mentioned poor neglected servers.

Therefore, if you are on a LSD trip (Look See and Discover), then there is no good reason why not to install a GUI on your server, since it will have all the necessary attachments, or even install regular Ubuntu/Kubuntu/Xubuntu or whatever else tickles your fancy, since Linux, is Linux, is Linux - it is all the same difference...

---

### Post by howefield on 2016-06-08
Moved to the "*Server Platforms*" forum.

---

### Post by raja.genupula on 2016-06-08
> **Bucky Ball said:**
> A very lightweight desktop is lxde. xfce4, also lightweight, is my preference.

Installing 

```
sudo apt-get install xfce4
```

or 

```
sudo apt-get install lxde
```

Reboot and you should get a login screen.

Run levels will change automatically to GUI [5] ? 

Just asking...

---

### Post by DuckHook on 2016-06-08
> **HermanAB said:**
> Normally, a server is installed in a rack, together with a hundred others and resides in a dark corner of a dank data centre, with not a living soul about, except maybe a mouse (the biological kind), with no screen, keyboard or mouse (the mechanical kind) attached to it.  

In this case, installing a point and click GUI is rather pointless, since the machine will be operated remotely over SSH from a rather more airy environment, where the machines do have all the necessary pointy-clicky attachments with GUIs to support SSH for remote administration of the above mentioned poor neglected servers.

Therefore, if you are on a LSD trip (Look See and Discover), then there is no good reason why not to install a GUI on your server, since it will have all the necessary attachments, or even install regular Ubuntu/Kubuntu/Xubuntu or whatever else tickles your fancy, since Linux, is Linux, is Linux - it is all the same difference...A very atmospheric description of the life of a typical server. :) Needs moody music to complete the effect.

But there is another kind. Servers aren't just high-tech machines installed in massive server farms. I run four servers on my laughably insignificant small-office-home-office network on old salvaged retreads. They are all command-line-only and headless, just like the morose victims so colourfully described by HermanAB above. In my case, they are sans-GUI not because they are remote and inaccessible, but because GUIs are superfluous, maintenance headaches, resource-intensive and compromise my security. When it comes to proper servers, it's always best to use the KISS (Keep It Stupidly Simple) principle. Less is more.

P.S. It turns out that I've been tripping on LSD all along. Who'd a thunk?

---

### Post by Bucky Ball on 2016-06-08
> **raja.genupula said:**
> Run levels will change automatically to GUI [5] ? 

Should do, yes, as you've just installed a desktop environment and a desktop manager if you install xfce4 or lxde. Has always been the case in the past.

---

### Post by sudodus on 2016-06-08
An alternative is to install only a window manager, for example fluxbox or openbox, and start it with startx only when necessary. Normally the computer should run with a text user interface. I think it is enough to install the following three packages (and what they pull into the system)

```
sudo apt-get install fluxbox xinit xterm
```

This is described at this link [Mini-system_Installer sub-menu](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative). I am re-using a screenshot from that link, so ignore the hight-light, look at the first item of the list instead:

'01 Install fluxbox xinit and xterm'

---

### Post by Sxcd1 on 2016-06-10
Wow, lots of great advice, thanks for the suggestions.

---

### Post by DuckHook on 2016-06-10
If you are happy with the answers given:

...*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by bab1 on 2016-06-10
> **DuckHook said:**
> A very atmospheric description of the life of a typical server. :) Needs moody music to complete the effect.

Yes indeed.  The machine room is not a fit place for humans.  I always wear a jacket and carry a flashlight.  Every time I need to check something there is never enough light.  I'm not so sure my office is much better, except for the temperature.  I leave the lights low so I can see the monitors better. 
> 
But there is another kind. Servers aren't just high-tech machines installed in massive server farms. I run four servers on my laughably insignificant small-office-home-office network on old salvaged retreads. They are all command-line-only and headless, just like the morose victims so colourfully described by HermanAB above. In my case, they are sans-GUI not because they are remote and inaccessible, but because GUIs are superfluous, maintenance headaches, resource-intensive and compromise my security. When it comes to proper servers, it's always best to use the KISS (Keep It Stupidly Simple) principle. Less is more.

It might be less confusing if we dissect this statement a bit.  This is not a situation where the server is a monolithic entity.  From a CS (computer science) point of view, the hardware (be it high-tech or not) is just that hardware.  Yes there is "server grade" hardware, but it is still just hardware.  The OS is also server agnostic if you think about it.  It is the distro that starts to point to  whether the install is for servers (daemons) or not.

The server is a process that is continuously running waiting for a client request for services; a daemon.  Some examples are (sshd SSH), httpd (Web Server) , smbd (SMB File Shares), NFS (Network File Sharing, etc).

So the "server" is the daemon.  Looking at the system this way makes questions like "Can I have a host that is both a client and a server" easily explained.

I have machines that are dedicated to server only activity at home too.  They are managed via ssh also.  I'm not sure what you mean by headless.  The traditional term means the host has no dedicated keyboard or monitor (no console).  My hosts at home are not headless as the monitor/keyboard (KVM) is connected to them.  Only rarely do I need direct console access.  Most of the time I use SSH for everything.  If you think about it, remote control re-defines where *there* is.  On more than one occasion I have spent a frantic 15 minutes looking for missing files only to realize that I'm looking on the wrong host for the files.  A quick look at the prompt (you@**there **) in the beginning would have saved time and energy.  ;-)
> 


P.S. It turns out that I've been tripping on LSD all along. Who'd a thunk?
This has been a lifetime journey for me also

---

### Post by DuckHook on 2016-06-10
> **bab1 said:**
> It might be less confusing if we dissect this statement a bit.  This is not a situation where the server is a monolithic entity.  From a CS (computer science) point of view, the hardware (be it high-tech or not) is just that hardware.  Yes there is "server grade" hardware, but it is still just hardware.  The OS is also server agnostic if you think about it.  It is the distro that starts to point to  whether the install is for servers (daemons) or not.

The server is a process that is continuously running waiting for a client request for services; a daemon.  Some examples are (sshd SSH), httpd (Web Server) , smbd (SMB File Shares), NFS (Network File Sharing, etc).

So the "server" is the daemon.  Looking at the system this way makes questions like "Can I have a host that is both a client and a server" easily explained.

I have machines that are dedicated to server only activity at home too.  They are managed via ssh also.  I'm not sure what you mean by headless.  The traditional term means the host has no dedicated keyboard or monitor (no console).  My hosts at home are not headless as the monitor/keyboard (KVM) is connected to them.  Only rarely do I need direct console access.  Most of the time I use SSH for everything.  If you think about it, remote control re-defines where *there* is.  On more than one occasion I have spent a frantic 15 minutes looking for missing files only to realize that I'm looking on the wrong host for the files.  A quick look at the prompt (you@**there **) in the beginning would have saved time and energy.  ;-)...well stated. And by headless, I mean without keyboard or monitor. All done through ssh.

I like to run my "dedicated" servers with a minimum of electricity. It's almost a fetish with me, but since they are running 24/7, every watt counts and I get a kick out of squeezing the last nickle of savings out of them. This means that a monitor is a no-go. Even HDDs are put to sleep when not in use. A silly obsession, I suppose, but it's all part of that LSD thing. :mrgreen:

---

### Post by bab1 on 2016-06-10
> **DuckHook said:**
> ...well stated. And by headless, I mean without keyboard or monitor. All done through ssh.

I like to run my "dedicated" servers with a minimum of electricity. It's almost a fetish with me, but since they are running 24/7, every watt counts and I get a kick out of squeezing the last nickle of savings out of them. This means that a monitor is a no-go. Even HDDs are put to sleep when not in use. A silly obsession, I suppose, but it's all part of that LSD thing. :mrgreen:
I can agree to that, but only if you have a monitor and keyboard (MK) nearby.  When you need direct access (console) then then a MK is required.  If you look at racks in a machine room there is a 1 or 2 U space for a MK setup.  I don't have the monitor on unless I need console access or I am at the machine and need to do something without going back to my desk in the den.  The server room at home is a room I built in my garage.  :D

[COLOR="#0000CD"]Edit:  The headless question comes from some younger users thinking that *non-gui=headless*.  It does not.  [/COLOR]

---


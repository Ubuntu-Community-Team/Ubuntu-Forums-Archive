---
title: "X11 not forwarding audio consistantly"
date: 2018-02-01
forum: Virtualisation
---

### Post by shave999-w on 2018-02-01
Hi all,

Having trouble to get audio forwarded though X11 consistently. I have done my due diligence research/testing and have come here for the experts help. I have included relevant code at the bottom for clarity. Let me explain my setup.

I am running Ubuntu 17.10 x64 on VMWare Workstation 14. I did the basic install then installed synaptic, x2go, ssh, vmware tools, and all the stable desktop environments (code below.) I ran dpkg-reconfigure sddm and chose sddm. I get the KDE login. All the desktops load fine. I configured paprefs for everything "on" including simultaneous output. I switch "simultaneous output" to the default device. I configured ( /etc/X11/Xwrapper.config  /etc/ssh/ssh_config  /etc/ssh/sshd_config ) as you see below. I verified the ownership and permissions as you see below.

On my Windows 10 x64 (host) I then installed Bitvise-7.39, VcXsrv, and later Xming out of desperation. I configured Bitvise to connect to the hostname "ubuntu" on port 22, saved user/pass, protocol "xterm" (default), and checked the block for "X11 Forwarding" enabled and "Enable authentication agent forwarding. I ran VcXsrv (and later Xming) with multi-window and left it in my windows systray.

I then login login through ssh with Bitvise, I get a terminal. I can "sudo nano", browse files, etc. I can launch "synaptic", "kate", and "firefox", etc. It all loads in it's own window, I can move it around, minimize, close, etc. 
Everything is great.... Except one thing. NO AUDIO. I run Firefox, go to YouTube, no audio. I get "X11 authentication failed for X11 forwarding from 127.0.0.1:34490 to :6000" as a notification from Bitwise in the bottom corner of windows. Here's what's funny though, if I log into the desktop with VMWare, X11 apps running through ssh audio works! If I log back out of the desktop through VMware while a video is playing, firefox frezes. I tried adding the following to the "display" box in the terminal tab of Bitwise ("blank", localhost,localhost:0.0, localhost:10.0, 127.0.0.1, 127.0.0.1:0.0, 127.0.0.1:10.0). I have tried multiple configurations with VcXsrv and Ming.

I found out "localhost" was resolving with an IPv6 address so I put the below registry hack in to prefer IPv4 over IPv6 (a handy one to keep and an adventure in itself.) That fixed localhost resolving to 127.0.0.1 but did not fix the audio. Additionally in desperation, I formatted and reinstalled Windows 10 and all my apps just to make sure there wasn't something borky on my PC that no one on here would be able to know. All Win apps installed from scratch and no luck.

I feel like I should be able to Fire up my windows PC, fire up the VMWare Ubuntu machine, SSH in, Run Firefox, and watch/listen to a video. It's supposed to work. I'm at a loss. Please help.

Initial Install Stuff
```
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install synaptic paprefs ssh open-vm-tools x2goserver x2goserver-xsession ubuntu-mate-desktop cinnamon-desktop-environment budgie-desktop lubuntu-desktop xubuntu-desktop kubuntu-desktop

```

/etc/X11/
-rw-r--r--   1 root root   630 Jan 31 19:14 Xwrapper.config
```
allowed_users=anybody

```

/etc/ssh/
-rw-r--r--   1 root root   1722 Jan 31 19:16 ssh_config
```
Host *
   ForwardAgent yes
   ForwardX11 yes
   ForwardX11Trusted yes

```

-rw-r--r--   1 root root   3260 Jan 31 23:55 sshd_config
```
AllowAgentForwarding yes
AllowTcpForwarding yes
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
```

/home/shave999/
-rw-------  1 shave999 shave999    155 Feb  1 01:23 .Xauthority

# Make Windows prefer IPv4 over IPv6 on all adapters without disabling IPv6
```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip6\Parameters] "DisabledComponents"=dword:00000020

```

---

### Post by shave999-w on 2018-02-05
As it turns out, the audio I did hear came from the VM console, not the SSH session. This completely changes the issue to a pulseaudio server on windows issue which I think merits a new thread. Marking this as solved. Feel free to delete thread.

---


---
title: "Tunneling X through SSH - WIndows to Linux Box"
date: 2012-02-02
forum: Server Platforms
---

### Post by kevdog on 2012-02-02
Excuse me if this is the wrong subforum to post this.

I'm wanting to tunnel a graphical X connection over SSH.  I know there are many ways to accomplish this, but I'd like to avoid any VNC or FreeNx solution.  I'd like to go with the tried and true if possible -- the X windowing system.

My problem is program stability.  I'm currently attempting to tunnel from windows box to linux box using the cygwin X server implementation.  Once logged in through ssh, I'm a little in a loss what to do.  The only way I can seem to get things working, is launch xnest followed by either a xfce4-session or openbox or fluxbox session.  Things work great for about 2 minutes, and then the connection suddenly just konks out.  I've attempted to look up the error codes that immediately proceed the disconnect, however this attempt seems futile.  So many discordant pieces of information with different software, linux installs, setups, etc.  

I guess I'm looking for the best way to proceed at this point, possibly from someone who has a working setup.

Thanks.

---

### Post by TheFu on 2012-02-02
You asked for the "best way" ... remember that.

Some will probably disagree, but I found the Cygwin X server to be too buggy for use 5 yrs ago and I switched to running a virtual Linux machine instead. If all you want is a solid X/Server (the client runs on the remote system), then 
a) download and install a copy of virtualbox on your Windows hostOS.
b) download the smallest GUI linux you can be happy with - probably PuppyLinux or TinyCore-GUI. Get the ISO.
c) Inside virtualbox, setup a new VM that has 256MB of RAM, 1 CPU, no HDD, and connect the ISO you just downloaded to the CDROM - set the CDROM to boot.
d) Boot the new VM and use X like you know on any Linux/UNIX system.  "ssh -X  userid@server" will work.

VirtualBox is very stable.  Linux running inside virtualbox is very stable.
There are many, many other ways to get an X/Server running on your PC, but this is "the best" way, IMHO.

I would point out that X/Windows doesn't work very well over WAN connections, but it works fine over LAN connections 100-base-tx or better.  For slow WAN connections, NX is definitely the best choice followed by VNC.  NX has ssh tunneling built-in and the GUI protocol is much, much, much more efficient than VNC.  With VNC, you still need an encrypted channel - like ssh or a VPN - to be secure over the internet.

Good luck. I hope I didn't scare you off.

---

### Post by Jive Turkey on 2012-02-02
I use a program (on windows) called Xming in conjunction with PuTTY.  I can use it to open gui apps on my headless server on my win 7 desktop screen.  I feel this is superior to a vnc/whole desktop type of option.  The Xming website has pretty good documentation.  The latest version is donationware.  I donated and got a password for the latest releases and it works fantastic once you get it going and learn your way around the config.

---

### Post by kevdog on 2012-02-02
Great suggestion guys.  Totally forgot about the vmware approach.  As far as Xming -- I think that's built on the same source code as the cygwin Xserver.  Could it really be that different?

---

### Post by kevdog on 2012-03-05
Just to update the thread I started, I started using Xming and its a lot more stable than the built-in cygwin X server.  It works really well, seems very light, and easily hands either xcfe4 desktop or xcfe4-panel.  Highly recommended for those not wanted to install a vm.

---

### Post by hawkmage on 2012-03-05
I use putty and X-Ming and it works just fine.

---


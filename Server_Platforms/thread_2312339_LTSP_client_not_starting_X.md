---
title: "LTSP client not starting X"
date: 2016-02-03
forum: Server Platforms
---

### Post by le_jawa on 2016-02-03
I just started working with LTSP today to replace an older LTSP 5 (Fedora 10) installation. I set the server up, ran the client build, and generated the new client image.   However, in the environment where the LTSP clients will be running, we don't have any Linux servers, just UNIX.  So, DHCP, TFTP and NFS are setup to boot the clients, which works fine... to a point.  The client boots fine to the CLI environment , but X won't start.  Here are the specifics:

[LIST]
[*]The NFS export is read-only.  The LTSP client won't run otherwise (server permission denied).
[*]I created /tmp and /var/log as tmpfs filesystems to allow the necessary writes.
[*]I've placed "startx" in rc.local to manually get X going.  (Cheap hack, I know, but it's been forever since I worked with manual X configurations, so I'm feeling lost at this point.  A lot has changed.)
[*]I have the config files from the old FC10 install, but I'm not sure of how many of them (if any) are being used but the Ubuntu
[/LIST]

EDIT:  Since I am booting from NFS, I am bypassing grub, and I know that grub plays its part in loading the GUI.  If that's what's keeping X from loading, how do I get around that?

Any thoughts on why X isn't starting?  I expected that to work out of the box, based on the doc, but I realize that since I'm not using an LTSP server (other than to build the client).  The existing (again, very old) FC10 boot works fine in this environment, so I'm not sure why the new Ubuntu install isn't working.

Thanks!

---

### Post by MAFoElffen on 2016-02-03
In the details (fine print) of the Ubuntu LTSP client doc's, this seems to fit what you are describing to a "T":
> 
**This workstation isn't authorized to connect to server**[COLOR=#333333][FONT=Ubuntu] error message on client, please run commands [/FONT][/COLOR]**sudo ltsp-update-sshkeys**[COLOR=#333333][FONT=Ubuntu] and[/FONT][/COLOR]**sudo ltsp-update-image**[COLOR=#333333][FONT=Ubuntu] (in this order) [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]reference: [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296)


---

### Post by le_jawa on 2016-02-03
MAFoElffen, thanks for the reply, but I'm not getting that message( that I've seen). Since I'm not using the LTSP server, I doubt SSH is the issue.  I'll put the logs on a rw export tomorrow and se if that message or something else useful shows up.

---

### Post by MAFoElffen on 2016-02-03
So if you are "not using LTSP server"... but you say you are using LTSP clients?
> 
What is LTSP?
&#8226; LTSP is a software add-on to Linux to create about server:
&#8211; Boot desktop computers over the network; and
&#8211; Run them in a stateless fashion (requiring no storage)
&#8226; By default, LTSP is configured to:
&#8211; Run as both boot server AND application server
&#8211; Present a login screen through which users can connect to the LTSP server and run the entire desk top on the LTSP server.

What is LTSP not?
&#8226; LTSP is not an application server
&#8211; Applications that users use are not dictated
&#8211; The server that users log into need not be the same as the one that booted the thin client
&#8226; LTSP is not a protocol
&#8211; Booting uses standard protocols, like DHCP, TFTP, etc.
 &#8211; By default, LTSP uses X11-over-ssh to connect to the application server, but other protocols may be used,such as RDP, ICA, NX, etc with proper scripting 

So with LSTP Server, it generates the LTSP client configuration. If you are not using LSTP Server, then are you doing something along the lines of LTSP, manually? Like PXE booting a thin skeleton Linux core client from you NTF share as it's root drive, and a min XServer Clients through a remoted basic XDM session? Which in the old days, we used to just do as is... but in recent times, we now use ssh to tunnel the XSession through... so now a glimpse of security.

LSTP Server does this as a package kind of affair, that takes care of the pieces and automates some of the wiring between them. (much more simplified installation, and administration.

So please explain what your setup is and what you are trying to do.

---

### Post by le_jawa on 2016-02-04
You've got most of it, it sounds like.   We have Unix servers at our remote locations, but no Linux.  In the past, my predecessors (who are no longer here) used DHCP/TFTP/NFS to provide a thin-client boot to our Wyse (and other) PC terminals.  The previous build was done with K12Linux on Fedora 10, using LTSP to build the client.  As you pointed out, using LTSP to build the client simplified setup and administration.  The boot however, was done from the Unix server, not a Linux LTSP server.  Now, that setup needs to be replaced with one that can be patched, as FC10 quit receiving updates quite some time ago (to say the least).

Once the terminal starts up, the system loads X with their application loaded full screen.  No window manager or anything.  (The terminals are dedicated devices.)  On the old FC10 boot, XClients loaded /etc/sysconfig/desktop, which then set the startup script for the app as the display manager, using the DISPLAYMANAGER variable. (DISPLAYMANAGER=/usr/sbin/ltsp-client-launch).

---

### Post by MAFoElffen on 2016-02-04
Oh man... Just had a flashback to about 1989: Unix XDMCP, XWindows, VT-220 terminals! So you were gen'ing your LTSP clients  on a Fedora LTSP server from the client configs, but instead of your Xaccess script being named as lstp-client-launch...

I think I have a link that might provide you some info, albiet you will have to translate from XDM to what you are using... 
[http://www.bodenstab.org/xdm.html](http://www.bodenstab.org/xdm.html)
[http://www.tldp.org/HowTo/XDM=Xterm/config.html](http://www.tldp.org/HowTo/XDM=Xterm/config.html)

---

### Post by le_jawa on 2016-02-15
MAFoElffen,
Thanks for all the effort to try to understand the convoluted mess here.  After I got my other solution working, this became unnecessary, and given how much of a hack the old LTSP solution was, I'm actually glad to have LTSP out of the equation.  Now on to documenting and automating the replacement solution...

Thank you!

Jason

---

### Post by MAFoElffen on 2016-02-15
You are welcome. I would be curious to hear more about your solution. (On what worked for you.)

---


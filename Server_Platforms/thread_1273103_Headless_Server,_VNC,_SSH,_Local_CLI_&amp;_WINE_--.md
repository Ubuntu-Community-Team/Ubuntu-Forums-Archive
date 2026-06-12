---
title: "Headless Server, VNC, SSH, Local CLI &amp; WINE -- Is It Possible?"
date: 2009-09-23
forum: Server Platforms
---

### Post by KiLaHuRtZ on 2009-09-23
OK, so this is what I need to accomplish.  I have some Windows only software that relies on a GUI.  Said software, however, is server based.  Set it up in a GUI and minimize, etc...  What I want to do is setup a secure VNC server using GDM/Gnome without having GDM on the local VGA port (I want this to be CLI only!).  From there I want to be able to log in to the GUI via VNC, open up WINE and start my Windows software.  Then, either suspend or log out of the VNC/Gnome session, but keeping WINE running with the Windows software inside.  All while keeping my nice BASH CLI on my local VGA port.  Also, this box uses SSH for remote CLI connections so I need password authentication so public key is out for the VNC portion.  Has anyone ever done something like this before?  If you have, please share your 2 cents worth...:-k:-k:-k:-k

Oh, and I'm running Hardy server edition.  And also have the option of setting up another network interface bound only to my local "trusted" network.

EDIT: I suppose I could run GDM on the VGA, if I must, as I have a Getty login on a serial interface.

---

### Post by trundlenut on 2009-09-23
What about running windows in a virtual machine on the server and running your windows program in that?

---

### Post by ukripper on 2009-09-23
> **KiLaHuRtZ said:**
> OK, so this is what I need to accomplish.  I have some Windows only software that relies on a GUI.  Said software, however, is server based.  Set it up in a GUI and minimize, etc...  What I want to do is setup a secure VNC server using GDM/Gnome without having GDM on the local VGA port (I want this to be CLI only!).  From there I want to be able to log in to the GUI via VNC, open up WINE and start my Windows software.  Then, either suspend or log out of the VNC/Gnome session, but keeping WINE running with the Windows software inside.  All while keeping my nice BASH CLI on my local VGA port.  Also, this box uses SSH for remote CLI connections so I need password authentication so public key is out for the VNC portion.  Has anyone ever done something like this before?  If you have, please share your 2 cents worth...:-k:-k:-k:-k

Oh, and I'm running Hardy server edition.  And also have the option of setting up another network interface bound only to my local "trusted" network.

EDIT: I suppose I could run GDM on the VGA, if I must, as I have a Getty login on a serial interface.

What you are trying to achieve can also be achieved easily by using X forwarding on SSH and forward wine on X. For more info check this link - [url]http://www.techotopia.com/index.php
/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29[/url]

And instead of VNC i'd rather use FreeNX - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) which is easy, secure and takes less bandwidth.

---

### Post by KiLaHuRtZ on 2009-09-23
> **ukripper said:**
> What you are trying to achieve can also be achieved easily by using X forwarding on SSH and forward wine on X. For more info check this link - [http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29)

Yeah, I can do this, the only thing is, how can I run wine and then exit the system leaving wine still running.  Then at a later time, SSH back to the server and recall my previous wine session (i.e. suspend the session, etc...).  And I'm also going to guess that I will not need to install GDM/Gnome with this method, just wine?  Thanks.

---

### Post by openfly on 2009-09-23
Seems to me like a VM is the way to go.

---

### Post by ukripper on 2009-09-23
Not sure wine will run in X only without GNOME. But you can give it a try with GNOME first and then try without GNOME, X only.

If all is working well  and wine is configured to your liking then just write a shell/bash script for wine to run certain program you are required to run within wine and put the script in rc.local for it to start after every reboot.

---

### Post by KiLaHuRtZ on 2009-09-23
A VM cannot be accomplished because I do not want to run Windows at all.  So that option is out.  However, this might work...

> **ukripper said:**
> If all is working well  and wine is configured to your liking then just write a shell/bash script for wine to run certain program you are required to run within wine and put the script in rc.local for it to start after every reboot.

I may just install GDM/Gnome anyway, seeing as I have the Getty login on the serial port, so remote maintenance can be accomplished anyhow.

---

### Post by hessiess on 2009-09-23
> **KiLaHuRtZ said:**
> A VM cannot be accomplished because I do not want to run Windows at all.  So that option is out.  However, this might work...



I may just install GDM/Gnome anyway, seeing as I have the Getty login on the serial port, so remote maintenance can be accomplished anyhow.

No need to use Gnome, just install a lightwaight WM like openbox or DWM.

---

### Post by KiLaHuRtZ on 2009-09-24
Ok, so I've made some progress.  I have installed GDM/Gnome, Xvnc and Wine.  I have setup XDMCP and also setup 16 VNC sessions via inetd.  1-15 are called with a 'nowait' so if you close the window it will kill the Xvnc session.  The 16th, however, is called with 'wait' so if you close the window, the session is still open on the server.  This is where Wine is and will run my Windows software.  And before you ask...all 16 VNC sessions are protected by 'VncAuth'.  So the 16th session is safe!  all I have left to do is secure VNC and XDMCP as they listen on all interfaces.  I only wait them to listen on localhost and thus I will provide an SSH encrypted tunnel.  So...any ideas on binding VNC & XDMCP to localhost?  I couldn't find any so I am thinking 'iptables'...???  Everything else id public, so I was thinking or 18 rules; 1-16 deny all my VNC sessions, 17 deny XDMCP, and 18 permit everything else.  What does the Ubuntu community think?

---

### Post by KiLaHuRtZ on 2009-09-24
Well, I solved my last issue with iptables..  Everything is working how I need it now.  Thanks to everyone for all your insight :P:P:P:P

---

### Post by ukripper on 2009-09-24
That's great. Now you can mark this thread as solved in case someone is looking for this, may help them.

---

### Post by KiLaHuRtZ on 2009-09-24
If anyone else needs assistance with setting this up, PM me.  I will be glad to assist.  There is just to much private data in the configs to post the procedure here. :)

---


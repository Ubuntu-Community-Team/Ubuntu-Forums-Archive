---
title: "Remote Desktop Provisioning Performance"
date: 2018-08-22
forum: Virtualisation
---

### Post by zexelon2 on 2018-08-22
I have a potentially unique usage scenario here. I am provisioning remote desktop environments to provide an always online development environment. The current setup is as follows:

Server:          Xubuntu 17.10 
VM Software: Virtual Box
Guest OS:      Windows Server 2012
Remote Prot.: RDP current
Network:       1Gbs ethernet

Currently the development environments are hosted from Windows Server 2012 via Microsoft's RDP terminal service. Performance wise this setup works very well however the application we are working on has reached a point where a Linux dev environment would be much more suitable to work in (the application runs only on Linux anyway). 

The problem is after much testing and experimenting I can not for the life of me find a workable solution to provision remote desktops in Linux that perform at the level of the Windows RDP desktops. My test setup is a dual monitor system with one 2k and one 4k monitor. I have tested, XRDP, TigerVNC and VRDP (the virtualbox version). The issue is latency, no matter what remote desktop software I run on Linux there is a latency issue that makes the desktops unusable for anything other than remote admin work. I have also tried adjusting the quality settings, and both XFCE and Mint desktop environments. They all have the same latency issues. 

I have also maxed out the video memory for the Linux machine, this made no difference. 

The latency issues dramatically improve if I limit the remote desktop to just one of the two monitors (specifically the 2k one) and the desktop largely becomes usable, however not really useful for development work. This leads me to believe that the state of Linux remote desktop provisioning is just not optimized for my usage scenario. 

If anyone has any ideas on other possible solutions to remotely provision Linux desktops to a dual monitor 2k/4k client I would really like to hear it! 

I have not tried Spice/Virt-Viewer yet, does anyone have any high resolution experience with the performance of this protocol? I have some new server hardware to spool up soon and will likely be switching to virt-manager/kvm for the virtualization solution.

Sadly as I write this post now it is being done in the Windows environment :(

---

### Post by wyliecoyoteuk on 2018-08-22
I think the problem is that you are using a microsoft protocol (RDP) on a Linux solution.
Running multiple Xservers is supported in Linux, in fact I wrote an article about it a few years ago, and managed to run 3 desktops (3 graphics outputs, 3 screens, keyboards,mice, usb sound) on the same machine simultaneously with no noticeable lag while using libreoffice, browsing, playing youtube videos, etc.
I have also run multiple X sessions over SSH, even on Windows using Xming.
You could look at using multiple sessions with X forwarding over SSH, 
Of course, any lag will be dependent on the network bandwidth available, so desktop provisioning over a slow connection will always be slow.

Nomachine offers this, but I have no experience of how well it runs.
[https://www.nomachine.com/](https://www.nomachine.com/)

there are also FreeNX and OpenNX (windows client)

Some more info:
[https://kb.iu.edu/d/bdnt](https://kb.iu.edu/d/bdnt)

---

### Post by zexelon2 on 2018-08-22
Thank you very much for the response. The actual client machine is running windows 10. I was going to test a direct X11 forward to it using X-ming. After doing some research though it was looking like the X protocol would likely still suffer the lag issue at the high resolutions that the client machine runs at (i.e. the 2k + 4k dual monitors). 

The network is a 1Gbs Ethernet LAN connection and as mentioned the Microsoft RDP solution works flawlessly so I am not inclined to believe it is a network infrastructure issue. 

I have used X-ming before but not at these resolutions and typically only on a per-app basis never a whole desktop. I will also look into the NX possible solution. Have you ever used a SPICE solution before?

---

### Post by wyliecoyoteuk on 2018-08-22
NoMachine is probably your best bet.
A single client connection is free (for any OS), and multiple connections are a low annual fee.
The NX protocol uses UDP  and is apparently very quick.
I haven't dabbled in multi session for a few years, as the application I used it for is no longer in use.
Userful multi session used to use it for up to 16 sessions, but that company now has moved to selling video wall apps.
And no, I have never used SPICE, but I now understand why you need the resolution.
Another option is Apache Guacamole, but being browser based, it might be too slow.

---

### Post by zexelon2 on 2018-08-22
Actually I use Apache Guacamole for external access to the desktops and it works very well. It is extremely fast and versatile. Unfortunately it has no support for multiple monitors. This is typically not an issue externally as usually such a user is on the move and doesnt have multiple monitors on hand anyway. So yes Apache Guacamole is very good... just not in this situation. 

I did a test tonight with Nomachine and unfortunately it simply would not work across the two different monitors. The client window would maximize across all the monitors but unfortunately would only display the remote machine in a small area centered between the monitors (ie. it could not re-size the remote display). I could not figure out a way to make it work so I moved on. 

I am now using Xming and forwarding the individual windows to the client. This is so far working surprisingly well! Its ugly as the theming isn't coming through so its just default GTK skin but who cares... it works. Lag is effectively non-existent. I am very pleased with this possible solution. I will continue testing it to verify but so far it looks to be the most effective way of provisioning most of the remote system.

---

### Post by wyliecoyoteuk on 2018-08-23
glad you found a solution

---

### Post by zexelon2 on 2018-08-26
Okay... so here is a synopsis of the state of hi-resolution multi-monitor desktop provisioning in Linux: It SUCKS! In this instance the Linux community as a whole is dramatically far behind other solutions (ex. Citrix and Windows RDP). 

My experience with Microsoft Windows RDP running on Server 2012 is that it simply works out of the box in pretty much every scenario, even the uncommon ones. I can spool up a Windows Server 2012 instance in any virtualization solution I want and within minutes enable RDP connections and instantly have remote access to the desktop over a 1Gbs LAN connection with no further issues regardless of the topology or layout of the screens and rendering system on my client box. Even though I have dual monitors running at significantly different resolutions it just works. There is also no lag running on a 1Gbs LAN connection and the experience is as if it was a local console. 

Now moving on to Linux. I have now tried pretty much every available solution in the Linux ecosystem: 
**1) XRDP**
This Open Source implementation of the Microsoft RDP protocol probably holds the most promise. 
_Pro's_
Really easy to set-up, simply ```
#apt install xrdp
``` and start using your desktop from any RDP client including with windows one.
Screen resolutions and topology automatically scale to the client
Sessions are preserved across connection and disconnection
[U]
Con's[/U]
Performance sucks... a lot, on a single monitor running at lower resolution (i.e. 1080p) performance is quite passable, add in a second monitor or higher resolutions and it falls off
Rumor has it that this software is no longer supported (a really bad side effect of the Linux ecosystem) 

[B]2) TigerVNC
[/B][U]Pro's
[/U]Mostly easy to set-up
Similar to XRDP

_Con's_
Requires separate client to be installed on client machines (ex. Windows)
Suffers the same high resolution performance issues
[B]
3) X2Go[/B]
_Pro's_
Relatively easy to set-up
Performance is generally good on a single high resolution display (ex. 4k)

_Con's_
No support for multi-monitor (claims to have support, could not get it to work, may have been a side effect of multiple monitors running at different resolutions) 
Requires client to be installed

**4) Xpra**
_Pro's_
Allows for session suspend and restore across connections
Allows for seamless apps to be provisioned
Good multi-monitor support for provisioned apps
[U]
Con's[/U]
Requires separate client 
Appears to have major issues with keyboard mappings... could not figure that out
Not all apps work (ex. Postman) on seamless provisioning
[B]
5) Good old X11 forwarding[/B]
_Pro's_
Minor configuration works generally out of the box on Linux systems using Xorg
Good multi-monitor support for provisioned apps
Good performance on a 1Gbs LAN connection 

_Con's_
Same issues as Xpra
No session suspend or resort

---

### Post by wyliecoyoteuk on 2018-08-26
Rather unfair, as you are using Windows clients, which are not part of the Linux ecosystem.
Translating between an Xserver  and Windows GDI is never going to be straightforward, mainly because the Windows GDI is not open-source, so all solutions are reverse engineered.
Citrix and RDP are not Linux systems, nor are they open source, maintained by volunteers or free.
If you are prepared to pay for it, Microsoft Terminal server may solve your problem, (or using Linux clients with a Linux server may do it for free).
Nomachine also offers a (paid for) enterprise terminal server edition, but you only tested the free home user version, which is limited to a single session.
I use VNC and RDP on both platforms with no issues, but I am not trying to run circuit design software at high resolutions, and I would be surprised if any of the developers of the various softwares you tried would even consider it for that purpose.

---

### Post by zexelon2 on 2018-08-26
Sadly the issue is not one of money. The development we are doing requires Linux. Linux has come a phenomenal distance from the first days that I used it back when Mandrake was the distro you had to buy in a box. However when it comes to desktop usage over the years my experience has always been that Linux has lagged behind. Especially if you wanted "cutting edge" desktop features in this case like desktop provisioning at high resolution. 

I have no doubt Linux will have a solution eventually.

Thank you very much for the feedback and suggestions though! They were very helpful in finding a workable solution to the problem.

---

### Post by wyliecoyoteuk on 2018-08-26
Perhaps you should try x forwarding with a linux desktop client. 
Windows has, and always will, present problems for integration, simply because Microsoft has no incentive to provide it.
Even within the Microsoft ecosystem they have repeatedly tried to dislodge competitors such as Adobe for example, simply by repeatedly breaking or blocking postscript implementations.
I have used Windows, Linux and Mac for over 20 years, and don't expect this to change.

---

### Post by TheFu on 2018-08-31
I didn't read all the posts.

BTW, support for 17.10 ended last month.  Today you should deploy on either 18.04 or 16.04.

I use x2go daily, constantly, both on the same LAN and from 5 continents. Audio and video playback are poor.   In a business, if I needed more performance, I'd deploy a Citrix VDI solution.

---


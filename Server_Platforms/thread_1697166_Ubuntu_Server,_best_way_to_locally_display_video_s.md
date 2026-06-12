---
title: "Ubuntu Server, best way to locally display video stream from IP camera."
date: 2011-02-28
forum: Server Platforms
---

### Post by jweb on 2011-02-28
I'm deploying an Ubuntu server running on an industrial Kontron SBC to provide OpenVPN services and a ZoneMinder (DVR) for 4 IP-based cameras (Axis 219FD) for a remote (geographically speaking) installation of a recycling technology (many IP devices on the subnet, OpenVPN required to talk to all of them securely.  The cameras are for quality control and process feedback).  On the prototype I currently have in the field, I built an Intel-based server using desktop components purchased from NewEgg; it is running Ubuntu 8.10 desktop (Gnome).  This box has a locally-connected monitor that displays the video streams from the 4 IP-based cameras using Firefox (a simple webpage pointed at localhost that displays the mpeg video streams).  This has worked reasonably well, but we are having intermittent hardware lock-ups that require reboot.  The processors are full throttle running the ZoneMinder application, resolving and recording 4 high-res video streams.  I haven't been able to nail down the cause of hard lockups other than general hardware incompatibility.     

Regardless, my current plan is to install Ubuntu 10.04LTS server on the Kontron.  This should provide a stable platform for me to build on.  I planned on installing Fluxbox to provide for the local display of the video streams, but I'm wondering if there is a better way.  Unfortunately, I have to use this box for both serving the ZoneMinder application and providing local video display.  There will be little interaction by the operators other than viewing these video streams.  I could just install Desktop, but then have to deal with the overhead of everything that comes with it; minimizing RAM and processor usage is a priority.  Also, I'd prefer not to permit the operators access to the PC, anyway.  Although I haven't used it much, I presume there are ways to lock down Fluxbox a little better (at least against the casual user).

Is there a better way other than 10.04LTS server + Fluxbox?  With just 10.04LTS server, I can't envision any way to display graphical information on the local display (i.e., video) without an X-windows manager.  Am I correct?

Thanks in advance,

Jeff

ps. I posted in the server sub-forum.  I hope this isn't too far off normal topic.  If so, please advise and I will repost elsewhere.

---


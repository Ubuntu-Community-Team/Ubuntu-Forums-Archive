---
title: "Dell PowerEdge 2650"
date: 2007-04-02
forum: Server Platforms
---

### Post by silurius on 2007-04-02
I have aims to run a production web server on Ubuntu.  Because I'm a web developer first and sysadmin second, and my OS expertise is still much stronger in Windows, my backend knowledge is still sorely lacking at this point.  I'm very grateful that I have some time flexibility as I continue to learn my way around this new OS -- otherwise it'd have to be an entirely different platform.

That said, I want to have a stable test environment up and running fairly soon.  So I have two basic questions today:

1.  Does anyone else have experience running Ubuntu Server on the Dell PowerEdge 2650 or a similar box?  Any general or specific guidelines or warnings?

I plan to rack it in the next day or two.  So far it's running pretty well for me and seems like it shouldn't be a problem, although there is one potential issue where whenever I install a package I get warnings about the APM (Advanced Power Management) with no other consequences -- packages still seem to install & run just fine.

2. Does anyone have experience with the **Remote Access Controller**?  I've read a few manuals and guides on the Dell site, but I'm still unclear on what this tool can do for me beyond manage the core server stuff.  [One of the guides]("http://bcr2.uwaterloo.ca/~brecht/servers/docs/PowerEdge-2600/en/ERA/rac34c1.htm#26644") seems to imply that it can do much more than that, but it's a little vague (I'm not even sure if Dell wrote this).

I colorized the statements which got my hopes up about RAC's capabilities:

> **Firmware** - Executes on the RAC independently of the managed system's operating system. [COLOR="Red"]It includes networking utilities, an embedded Web server, and an embedded file system[/COLOR]. It provides software interfaces to all the embedded systems management functions provided by the BMC.

**Managed system software** - [COLOR="Red"]Executes on the managed system under supported operating systems[/COLOR] and interfaces RAC firmware with other Dell systems management software. The RAC managed system software includes device drivers, agents, and services that provide a communications path for Server Administrator to configure the RAC and provides graphical console redirection screens when the system is running.

**Management station software** - Provides discovery of all RACs on the network and correlates all RACs with managed system addresses. It also provides a launching point for the Web-based interface, reception of RAC-generated asynchronous events, and the dial-up connection to a DRAC III.

**RAC Web-based interface** - Communicates with the RAC firmware using Java applets that execute in a remote Web browser. The Java applets are loaded into the browser from the embedded Web server in the RAC firmware. The browser connects directly to the RAC when you enter the RAC IP address.

The first red section clearly states network tools & file system access, which alone is very useful for certain sysadmin scenarios.  The second is extremely confusing to me, and seems to suggest that RAC can actually provide a view of some sort into an existing operating system.  This server officially supports Windows and Red Hat, so I think it's a safe bet that any OS-related features would include Ubuntu as well.

My hope when discovering Dell's RAC was that it might be similar to [HP's Integrated Lights Out]("http://en.wikipedia.org/wiki/Integrated_Lights-Out"), which is a great little RC tool that has saved me time and hassle at previous jobs (all Windows environments).  You get a full-blown view of the server session that is in progress (comparible to Dameware, pcA or VNC except over a web browser).

---

### Post by silurius on 2007-04-02
Dell Support has verified that the DRAC4 (and I suspect the DRAC3 also) would probably work just fine with Ubuntu:

> The DRAC4 does support Linux GUI - Red Hat Enterprise Linux version 3 update 3 or greater and Red Hat Enterprise Linux version 2.1 update 5 or greater already have suitable video drivers. On other versions you can verify the video driver update with the command:

rpm -qa | grep radeon_7000m_dell_server 
The RPM rhel**_radeon_7000m_dell_server-0.4-1 or later should be installed. This RPM is available at [www.dell.com](www.dell.com)


The DRAC5 is better due to how it handles screen resolution, but that would require a newer Dell server.

Unfortunately, I had to abort this effort due to project funding priorities, but at least I know my options.

*edited to remove incorrect info*

---


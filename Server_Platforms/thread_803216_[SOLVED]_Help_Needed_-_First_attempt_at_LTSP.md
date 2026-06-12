---
title: "[SOLVED] Help Needed - First attempt at LTSP"
date: 2008-05-22
forum: Server Platforms
---

### Post by mel_phil@flashmail.com on 2008-05-22
Hi,

Hope I am in the right place. I want to build a LTSP Server. I wish to connect to it through my LAN & remotely with windows XP machines running an RDP client of sorts.

I used Xubuntu CD and chose LTSP option. The installation worked fine. I saw all the LTSP components install during setup. There were no errors during the installation & the machine boots nicely to a xfce desktop without a problem. In the etc folder there is folder called LTSP with the config file in it. I created a user account on the Linux box & after this is where I come unstuck. I installed VNC viewer on my XP machine & tried to connect and could not "failed to connect to server" error is displayed. 

I need to know if there is some sort of setting or proceedure to enable to make this work. 

From the documentation I read prior to install it was an "Out of the Box" solution that should just work.

Also is there a program to create a client software to run on Windows?


I run a Netgear Router acting as a DHCP Server. 

Any help would be appreciated I have built & run 6 Windoze Terminal Servers that are still in production but want to get the Microsux Monkey off my back & not be so dependent on them & offer an alternative to my customers.

Please excuse any ignorances & many thanks in advance for any help offered

Humbly

PS:)

---

### Post by bluefrog on 2008-05-22
from what you describe, it will not work.
to connect to a vnc session you need to log in ubuntu and enable remote desktop.
You could also install xvncserver (or something so) which allows you to connect via vnc at the linux login screen. But both those methods defeats the capability of LTSP which is a terminal server supposed to run with thin clients.

As LTSP is already installed, you could PXE boot your "windows" machine (so you use those machines as thin clients) and log in. Those client will be running linux then.

Now it all depends why you want a linux server and why you need to keep windows machines.

James Dupin

---

### Post by mel_phil@flashmail.com on 2008-05-22
Hi James 

Many thanks for the reply.

I think you have helped me get a step further. 

I have built Windows TS Servers as Database & document servers for my customers. I was just using RDP on their XP Systems to connect to these Severs either from the office or from home, all was working well. One day I got a call from one of these customers. They had a power problem (caused by their own factory equipment...the Servers are on UPS)that wiped out one of their workstations & needed this workstation back online fast. When I arrived I saw they had an old P3 933 128 meg of RAM with no OS just sitting there & decided to pull out my faithful Damn Small Linux CD & install it to the hard disk. Problem solved within 15 minutes of being on site. The Manager was so impressed at the speed at which this installed, the performance was no different to their Windows P4 computers & it cost nothing for the licence. I have since configured them two other P3 workstations they had lying around with DSL installed as backup terminals in case it happens again.

Then I had the bright idea, what if I could do the reverse, have the Windows "Fat Clients" (which customers have already paid for or have in their homes)connect to a Linux Server with some sort of RDP Software and run Open Office or custom apps etc on server in the same way I have Linux "Fat clients" connect to a Windows Server to create licence free servers to reduce TCO etc etc. 

This is where I think you have helped me. I think I may have misunderstood the concept of LTSP. Correct me if I am wrong but it would appear that LTSP only support diskless, fanless etc "Thin Clients" that boot from the Network card and retrieve a config file from the server to run?. To achieve what I wanted to do above I should just run a standard install of XUbuntu and install one of the many "VNC Server" component on the Linux Server & viewer component on the Windows client & not worry about LTSP unless implementing the type of thin Client mentioned above?

I'm really sorry at the long essay but it seemed the best way to explain my thought process.

Your help is very much appreciated

Cheers

PS:):):)

---

### Post by bluefrog on 2008-05-23
I still have some problems understanding where you're getting at :-).

You can run thin and fat clients (thin could be an existing PC with an existing OS which will not be used during the "thin client session")

So, you have
1 server (eventually under linux)
x pc (under windows)

You want your windows machine to use openoffice on the server. Is that all?

Install openoffice directly on windows machine.

Use your linux server as a DRP server with tools such as clonezilla, OSCAR or partimage to be able to put a faulty pc online in 2 minutes (assuming you have all hardware ruuning correctly).

If you want a trouble free (or so) network, use linux ltsp and use the existing pc (so they will not use windows but linux directly from the server, you can leave windows on their machines, just set up PXE boot as primary boot device). Ok they have paid for their windows but if there is no more use for windows, who cares?

---

### Post by mel_phil@flashmail.com on 2008-05-23
Many thanks for your reply :)

Sorry I did not explain myself better. 

I think you are onto what I need to know. Yes the idea is to have a Linux Server & yes to have Windows Clients connect to it.

Your Comments:

*** .... thin could be an existing PC with an existing OS which will not be used during the "thin client session".... ***

&

*** .... use linux ltsp and use the existing pc (so they will not use windows but linux directly from the server)....***

In the above you state *"which will not be used during the "thin client session" & [I]"Will not use Windows"*. [/I]I need to know can Windows OS installed on the local client PC's hard drive _be_ used while running a client session to the Linux Server at the same time?

An example in the "Windows client to Windows Server" environment would be the user boots their PC using the Windows OS installed on their local hard disk & runs the MS windows remote desktop program to connect to the Windows Server (either on their LAN or through the Internet). The user can then minimize that Server session window & work on their local PC OS (e.g browse etc). They can then go back to the remote session window at anytime by using ALT-TAB. _Can this be replicated using Linux as the Server running LTSP?_ or do I need third party Open Source Software?

I do understand the flaws in the above but it is only part of the overall project & meant as an another connection option. After more reading I would want other PC's connecting to the Linux Server as true thin clients by PXE & not even have a "Spinning Disk" installed as another connection option but that's the next step in the project. I do have full project notes for how I want this server to function, be configured & the "Why's" but they are rather long, boring and probably not relevant to getting the right answers I need at this stage, but I can post them it if you like. I do like the idea of a Open Source DRP Server in my arsenal - Maybe that's the next project.

Once again your help & advice is very much appreciated

Cheers

PS  :):)

---

### Post by bluefrog on 2008-05-24
I see what you would like but I do not know if it is possible the way windows does it.

What you could do, to mimic that, is install virtualbox (virtualbox.org, owned by sun now) on your windows machines, set up the host network interfaces so that when you launch a virtual machine it will use PXE boot and run a linux session.

---

### Post by mel_phil@flashmail.com on 2008-05-25
Thanks for the patience & advice on the DRP server stuff. What I want to do is possible. I found this link

[http://www.linuxtsc.org/home ]("http://www.linuxtsc.org/home")

It is a Linux RDP Client for Windows & even looks a bit like the Windows one. Just gotta get it to work now. But I am a step further.

Hope this helps you & anyone else looking for info

Cheers :):):):):)

---

### Post by mel_phil@flashmail.com on 2008-05-26
Linux TSC works a treat - Solved

:guitar::)

---


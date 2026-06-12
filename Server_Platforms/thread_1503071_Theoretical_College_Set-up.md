---
title: "Theoretical College Set-up"
date: 2010-06-06
forum: Server Platforms
---

### Post by HTML-insane on 2010-06-06
So in College, I'm doing an I.T course that encompasses a few different areas of work in I.T and computing. In most of the courses, they've taught the use of various (often inferior) proprietary packages on Windows and Mac OS, but I've often used open-source alternatives on my Kubuntu laptop.

The last course, however, manages a theoretical college network set-up with Windows Server and Active Directory. I imagine that something similar, or even superior, is possible given Linux's flexibility, but so far I've not found *quite* the right solution.

Here are the requirements:
1. The users, groups, documents and settings have to be managed on the server.
2. Applications also have to be managed on the server. Though the set-up with Windows has server-installed applications automatically pushed to the clients when they're restarted, I expect X can do some sweet kind of magic here instead.
3. (This one's been the hold-up for me) If I have 3 average desktop machines, then I need to be able to install the server on any of them and be able to set-up the remaining two as clients. No specialised hardware. Therefore, specialised thin-clients or specialised network cards are a no-go.

Having done a great deal of research, Googling and playing with virtual machines, I'm interested and curious in the best way to manage this.

Considerations I've already had:
1. Using an NFS server for /usr, /etc and /home and having these mounted on boot-up. This was shot down pretty quickly, as every machine would need all users to be set up on them individually.
2. Setting up the machine to boot into a minimalistic local user in a virtual terminal, connect to the server via SSH with X forwarding and creating a new X session/Display Manager across the network. I seemed to be doing something wrong, because this didn't work.
3. Setting up XDMCP and having the local log-in screen automatically ask for a username and password, which would allow for logging-in to the server. This is another thing that I struggled with, since GDM's configuration has changed dramatically recently and most guides to this are out-of-date.
4. Having the client start up an X server to act as a server for the server's log-in screen or display manager. I've not tried this one out, 'cause I've no idea how to go about it.

Discuss!

---

### Post by scorp123 on 2010-06-06
> **HTML-insane said:**
>  The last course, however, manages a theoretical college network set-up with Windows Server and Active Directory. I imagine that something similar, or even superior, is possible given Linux's flexibility, but so far I've not found *quite* the right solution.  VDI + thin client computing. There are various vendors for that stuff. I personally prefer Sun/Oracle's solutions because they offer the biggest flexibility.

> **HTML-insane said:**
>  Here are the requirements:
1. The users, groups, documents and settings have to be managed on the server. You put all user $HOME directories on the central storage. Done. If done right it will work tip top even across OS boundaries, e.g. it doesn't matter if a user is working with Windows or Linux, his documents are always there.

> **HTML-insane said:**
>  2. Applications also have to be managed on the server. [http://en.wikipedia.org/wiki/Sun_Secure_Global_Desktop](http://en.wikipedia.org/wiki/Sun_Secure_Global_Desktop)

Users only get the applications the administrator has published for them. Works tip top. On the client side only a web browser (pretty much any web browser will work) and the Sun Java plugin are needed, that's it.

With this I can give users access to whatever software they require without having to bother about uploading or downloading packages around. All software remains on the application servers. I'm merely exporting the graphical output.

The other positive effect is that I can decrease the number of people with VPN access ... they don't need it anymore.

> **HTML-insane said:**
>  If I have 3 average desktop machines  ... then you can't do anything. Server-based computing like this needs decent server hardware. A quad-core CPU and at least 8 GB RAM. The more CPU and RAM the better, even in a demo setup.

> **HTML-insane said:**
>  specialised thin-clients  SGD only needs a browser and Sun's Java plugin on the client side. And there is a soft-client that 100% emulates their "Sun Ray" thin-clients. It's a Windows program but it will work 100% tip top under WINE on Mac OS X and Linux too. I have built thin-clients like that: have them auto-boot into a minimal Linux desktop and then auto-start the soft-client and connect to the server setup. Taddaaaa, my own "specialised" thin-client built out of 100% standard PC components.

> **HTML-insane said:**
>  I'm interested and curious in the best way to manage this.

Reading material for you:

**_Commercial solutions $$$$$$$:_**

[LIST][http://www.oracle.com/us/products/servers-storage/desktop-workstations/030738.htm](http://www.oracle.com/us/products/servers-storage/desktop-workstations/030738.htm)[/LIST]
[LIST][http://wikis.sun.com/display/VDI3dot1/Home](http://wikis.sun.com/display/VDI3dot1/Home)[/LIST]

Sun/Oracle's solutions are the only ones that I know of that can handle Windows and Linux equally well. Actually you can probably use any OS you like with their solution. In my experiments I even got various BSD's and Mac OS X to work with their stuff.

The rest is mainly focussed on Windows and Windows only:

[LIST][http://www.vmware.com/products/view/](http://www.vmware.com/products/view/)[/LIST]
[LIST][http://www.citrix.com/English/ps2/products/product.asp?contentID=163057](http://www.citrix.com/English/ps2/products/product.asp?contentID=163057)[/LIST]
[LIST][http://www.panologic.com](http://www.panologic.com)[/LIST]


**_Free & open source solutions:_**

This is the only free & open source solution that even remotely comes close to the commercial offerings as far as features are concerned. But they still have a long way to go:

[LIST][http://www.ulteo.com](http://www.ulteo.com)[/LIST]

---

### Post by HTML-insane on 2010-06-06
When I said, "3 average desktops", I meant it had to be technically possible, as opposed to feasible or desirable.

Anyway, I'll be having a good read-up on this stuff. Thanks. :)

---

### Post by scorp123 on 2010-06-06
Real-world picture of a university where Sun Rays were deployed:

[IMG]http://dl.dropbox.com/u/1614648/tmp/SunRay_Classroom_640x480.jpg[/IMG]


(But as I said above ... you could use standard PC's too. Just make sure they auto-launch the software client upon boot.)


Each student is authenticated vs. Microsoft AD (any LDAP server such as OpenLDAP or Novell eDirectory or Sun DSEE would work too) and upon login can then choose the OS they want to work with, e.g. usually there is a choice between Windows XP, Windows 7 or Ubuntu Linux.

Because all data is on the storage the students always have access to all their files, no matter what OS they work with.

---

### Post by scorp123 on 2010-06-06
> **HTML-insane said:**
> When I said, "3 average desktops", I meant it had to be technically possible 

Are you sure you're an IT student and not already some sort of "suit" somewhere somehow? :D  You sure sound like some managers I regularly have to deal with. :D

Just kidding.

But seriously: Can you give me an overview of that hardware? How much RAM, CPU's and disks are we talking about?

---

### Post by HTML-insane on 2010-06-06
The point of the statement wasn't to give an impression of the kind of hardware used, it was just to point out that we couldn't use e.g. specialised network cards or adaptors, nor could we use specially-built client computers such as thin clients.

What I'm interested in the most is the software set-up. Of COURSE it would be practical to use a powerful, full-fledged server machine, and that's not what I'm asking about.

P.S. I've also been looking into the possibility of using VNC. Any comments on it?

---

### Post by scorp123 on 2010-06-06
> **HTML-insane said:**
>  What I'm interested in the most is the software set-up. Of COURSE it would be practical to use a powerful, full-fledged server machine, and that's not what I'm asking about.

So I assume you do have access to reasonable hardware then? Ulteo and Oracle's stuff will work with pretty much "normal" PC hardware if only you have enough CPU's and RAM in the machine. For example: a system with a quad-core AMD or Intel CPU and 12 GB RAM is enough to build a "VDI Evaluation Single Host" setup and then serve 5-6 virtual OS instances (Linux or Windows). Such a setup is described here:

[http://wikis.sun.com/display/VDI3dot1/VDI+Demo+%28Featuring+Sun+VirtualBox%29](http://wikis.sun.com/display/VDI3dot1/VDI+Demo+%28Featuring+Sun+VirtualBox%29)

The basics:
[LIST]
[*]find a system with reasonable amounts of CPU and RAM (e.g. 1 x quad-core + 12 GB RAM)
[*]having additional disks in the system would be a bonus (e.g. one disk for the OS, one disk for VDI's ZFS pools)
[*]before you install anything, please make sure the PC is even compatible with Solaris 10, e.g. you can use this Java applet to determine this: [http://www.sun.com/bigadmin/hcl/hcts/device_detect.jsp](http://www.sun.com/bigadmin/hcl/hcts/device_detect.jsp) (read the instructions there)
[*]if that Java applet says that everything works, get the Solaris 10 DVD from here: [http://www.oracle.com/us/products/servers-storage/solaris/index.html](http://www.oracle.com/us/products/servers-storage/solaris/index.html)
[*]install Solaris 10 ... make sure you use a Console-based setup from the GRUB screen and that you pick ZFS as the file system
[*]make sure that the swap space is at least twice the RAM (or VDI's setup will complain later!)
[*]you will only be asked to define the "root" account. This is normal. Because Solaris 10 is supposed to be used by professionals only it is assumed that you yourself will create additional users later if needed.
[*]for VDI you will need some form of LDAP server ... follow the instructions here to get one quickly without too much hassles: [http://blogs.sun.com/whitemencantjump/entry/why_does_sun_vdi3_mandates](http://blogs.sun.com/whitemencantjump/entry/why_does_sun_vdi3_mandates)
[*]if you got that far: follow the instructions for a single-host "Evaluation" setup for VDI from the link above this list ... 
[/LIST]

Such a VDI setup is intended for use with Oracle's proprietary "Sun Ray" thin clients ... but normal PC's will work as clients too. You can either take the soft-client from here (requires that you create a free account):

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=SDAC-1.0-W-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=SDAC-1.0-W-G-F@CDS-CDS_SMI)

Or you follow the instructions here -- in that case any ordinary RDP client will be sufficient and there would be no need for special thin clients or special client software at all -- any plain normal Atom netbook would then be sufficient as client if only it can fire up a RDP client of any sorts:

[http://wikis.sun.com/display/VDI3dot1/Remote+Desktop+Client+Access+%28RDC%29+%28All+Topics%29](http://wikis.sun.com/display/VDI3dot1/Remote+Desktop+Client+Access+%28RDC%29+%28All+Topics%29)

With this setup you'd then be able to serve virtual Windows and Ubuntu Linux clients, and your users would only have the applications you gave them via the master-image. If you define their virtual instances as being "dynamic" then you can even give them the administrator / root password for their virtual instance ... whatever they do to their image doesn't matter: as soon as they logout of it their OS is reset to the state you defined previously. ("reset to snapshot")

Where I work we keep a few "Experimental" desktop pools just for that, so my users can do all sorts of BS and experiments ... if anything goes wrong: no problem, simply logout and the hosed OS is reset back to a working default state. :)

---

### Post by scorp123 on 2010-06-06
> **HTML-insane said:**
>  I've also been looking into the possibility of using VNC. Any comments on it? LOL.

Better use NX. ;)  But even for this kind of "terminal server" you'd still need decent hardware. You'd have to calculate around 256 MB RAM per concurrent user if you plan to serve out GNOME sessions. 128 MB or less per concurrent user if you use any of the smaller desktop sessions such as OpenBox, LXDE, FluxBox, etc.

NX tutorial:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Why NX and not VNC: NX is SSH based, so it does a way better job at identifying the user who wants to connect and it's safer too.

With VNC there is only a session password and a port number, no user authentication worthy of being called that. And VNC isn't exactly fast. The more users connect to it, the slower the overall performance and the worse the experience gets for everyone. In other words: VNC is OK for a single user accessing his own system ... but I definitely wouldn't use it in a multi-user setup and as "Terminal Server" replacement. It definitely wasn't built for that.

BTW, in another thread some time ago someone brought this to my attention:

LTSP -- Linux Terminal Server Project
[http://www.ltsp.org/](http://www.ltsp.org/)

... maybe this is more suitable for you? I never used it so I have no idea how good (or bad?) it is.


EDIT:

There are some nice instructions right here:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by HTML-insane on 2010-06-06
Thanks everyone - I'll have a thorough look through all this and see what I find that's most suitable. :)

---


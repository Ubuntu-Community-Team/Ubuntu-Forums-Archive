---
title: "Completely unsure"
date: 2013-09-17
forum: Server Platforms
---

### Post by brent4 on 2013-09-17
I didn't see a post quite like this anywhere in the forums but my search wasn't super exhaustive.  Please forgive if I'm reposting or something along those lines.

My questions are as follows:

Can ubuntu be used to host windows programs for a small business?
Is it relatively easy to configure?
Can it handle the routing or would I need another program like pfSense?
Does it autodetect most configurations like win server or is it all hand set?
Are remote connections easy with pure windows PCs?
And last, but certainly not least, is it a viable solution for a small business?

Some details about the business:

Small "mom and pop" computer repair business.
5-6 perm PCs in place on wifi, various repairs going on daily (upwards of 9-15 PCs can be on at once)
Web hosting for 8 or so web pages

I want to store our POS and diagnostic software on the central server location to use between two sites.  The PC shop and the glass company I own next door.  I am very green when it comes to the server side of things, my primary experience has been in windows environments.  A friend turned me on to Ubuntu for desktop and I fell in love with it so now I'm looking into the server side of things because I really hate having down time to fix security patches in windows.  Any information (including newbie setup/ configuration/ admin posts) would be much appreciated.  Treat me as a total noob and I'll love you for it.  Any help/ info at all goes a long way.

---

### Post by ian-weisser on 2013-09-17
> **brent4 said:**
> Can ubuntu be used to host windows programs for a small business?
Yes, if you expect the server to merely host.
Maybe (not), if you expect the server to run windows executables. Additional software (wine or a VM) may be needed.


> **brent4 said:**
> Is it relatively easy to configure?
Yes, if you understand a bit about Linux.
If your entire experience is Windows server, your previous experience may cause you a bit of frustration on the learning curve.


> **brent4 said:**
> Can it handle the routing or would I need another program like pfSense?
Yes, but it's generally unwise to mix routing with more complex services on the same machine.
A failure in a complex non-network service could crash your network. And take much longer to recover from.
With your network down, it may be difficult to look up how to troubleshoot the problem.
pfSense is not an application. It's a different linux-based OS. You can boot into either Ubuntu or pfsense, but not both at the same time on the same machine.


> **brent4 said:**
> Are remote connections easy with pure windows PCs?
I think so.

> **brent4 said:**
> And last, but certainly not least, is it a viable solution for a small business? 
For my (non-computer-related) business, yes.
For your business, much depends upon the services you sell, and your skill sets. Only one way to really find out....

---

### Post by pbpersson on 2013-09-17
Here are my thoughts.  I will just ramble and hopefully there will be something useful here.

First of all, some people will tell you that a server should not have a GUI (xServer) component.  I disagree, especially if you are new to Linux.  If you have at least 2GB of RAM I would suggest that you use the desktop version.  The only difference is that on the desktop version you will have graphical tools to edit files, install software, setup partitions, and do other things on the server.

I used to have an Ubuntu machine that I configured as my main file server for all my Windows machines.  You setup the desktop/server as a regular Linux machine and you can share a large partition out on the network using Samba.  The Windows machines will **think** it is another Windows machine - you can map network drives and run Windows applications right from the Linux shared drive.  If you want a graphical tool to setup the Samba environment on the server I highly recommend WebMin.  Please keep in mind I just configured a workgroup, I did not deal with a domain model.

Regarding your question about using the Linux server to host web pages.....If the web pages you are hosting are just home made collections of files and data created with something like SeaMonkey (think of FrontPage in Windows) then it is easy to do.  If they are web pages that access data in a database that would be more involved.

Regarding having the Windows machines accessing the Linux server over wireless, that is no problem.  You just need to have a wireless access point on the subnet.

I did not understand your question about routing on the network.

---

### Post by cariboo on 2013-09-17
> **pbpersson said:**
> Here are my thoughts.  I will just ramble and hopefully there will be something useful here.

First of all, some people will tell you that a server should not have a GUI (xServer) component.  I disagree, especially if you are new to Linux.  If you have at least 2GB of RAM I would suggest that you use the desktop version.  The only difference is that on the desktop version you will have graphical tools to edit files, install software, setup partitions, and do other things on the server.

I used to have an Ubuntu machine that I configured as my main file server for all my Windows machines.  You setup the desktop/server as a regular Linux machine and you can share a large partition out on the network using Samba.  The Windows machines will **think** it is another Windows machine - you can map network drives and run Windows applications right from the Linux shared drive.  If you want a graphical tool to setup the Samba environment on the server I highly recommend WebMin.  Please keep in mind I just configured a workgroup, I did not deal with a domain model.

Regarding your question about using the Linux server to host web pages.....If the web pages you are hosting are just home made collections of files and data created with something like SeaMonkey (think of FrontPage in Windows) then it is easy to do.  If they are web pages that access data in a database that would be more involved.

Regarding having the Windows machines accessing the Linux server over wireless, that is no problem.  You just need to have a wireless access point on the subnet.

I did not understand your question about routing on the network.

There are several things I disagree with here, firstly, Ubuntu server is meant to sit under a desk, or in a closet, with no keyboard and monitor connected. All administration should be done remotely. Once setup properly, there isn't a need for a gui. File management can be done using sftp and a file manager, and if there is a gui app that you need, X-forwarding, is a much better way of doing things, rather than running a desktop full time.

Purchase as much ram as possible, so that if you do need to run Windows applications, you can run them on Windows in virtualbox, and any of the other virtualization applications available.

Consider paying someone to set up your server, as it takes quite a bit of time to rid yourself of old Windows habits, and learn the Linux way of doing things.

I'd also suggest staying away from Webmin, if your system is internet facing, as there have been some security problems over the past couple of years.

---

### Post by brent4 on 2013-09-18
Thanks for the heads up and the options guys.  It's not imperative to get it set up quickly but I'm wanting to do it asap regardless.  The server setup I have right now should be more than enough to handle the physical requirements, more than enough RAM and roughly 30TB worth of memory storage.  Since there was such a fast and well diversified response I'll ask if anyone has a few favorite programs I should be looking into to have the system work the way I want it to?

I'd already figured I may need WINE or something like it to host the windows apps and to make things like remoting a bit easier with win 7 PCs.  My main concerns are serviceability and reliability.  Like I said in the original posting, my linux experience is limited to Ubuntu desktop version but I love it and I really want to have more in depth experience with it.  Any advice as to what I should be looking at or looking into?  Is there any kind of automation like with windows server?  Those types of things are what I need to know and research before I go this route.  Thanks again for any info.

---

### Post by TheFu on 2013-09-18
> **brent4 said:**
> Thanks for the heads up and the options guys.  It's not imperative to get it set up quickly but I'm wanting to do it asap regardless.  The server setup I have right now should be more than enough to handle the physical requirements, more than enough RAM and roughly 30TB worth of memory storage.  Since there was such a fast and well diversified response I'll ask if anyone has a few favorite programs I should be looking into to have the system work the way I want it to?

I'd already figured I may need WINE or something like it to host the windows apps and to make things like remoting a bit easier with win 7 PCs.  My main concerns are serviceability and reliability.  Like I said in the original posting, my linux experience is limited to Ubuntu desktop version but I love it and I really want to have more in depth experience with it.  Any advice as to what I should be looking at or looking into?  Is there any kind of automation like with windows server?  Those types of things are what I need to know and research before I go this route.  Thanks again for any info.

I'll chime in.  I've been running Linux and UNIX servers for over 20 yrs.
Don't expect things to work like they do on Windows. You will be frustrated.  Learning Linux is like learning a foreign language. Some things are similar, but many things are completely different.  The UNIX way of thinking is to make small programs that do 1 thing extremely well.  Then we can put those programs together using a pipe to make some amazing tools.

WINE doesn't work as well as people will have you believe.  Don't expect it to be useful most of the time.  Even if you get it working for 1 program, an update will break that.  Remote computing was invented on UNIX. It is Windows that lags behind.

Automation on Linux makes Windows look like a toy. Learn to script and you can make almost anything work. Forget using GUIs for this. There are CLI programs that are much more powerful.  PowerShell was modeled after UNIX-based scripting.

Don't lock for programs to load outside the package manager. Avoid using any programs directly from .deb or .tgz files. You'll screw up the ease of maintenance that Linux package managers bring to the entire OS.  THIS is the main reason I;ve preferred Linux over other OSes the last 15+ yrs.  If you absolutely need a newer version, use a trusted PPA - NEVER the source or .deb package from somewhere.

There aren't really any programs. No need to pay for any software to manage a Linux system, server, desktops.  It is almost as easy to manage 1 box as to manage 50. Just the hardware issues make it more complex, not the installation/management of programs and settings.  Those are easily managed from anywhere in the world, securely.

So, like learning a foreign language, expect the first 6 months to be hardest.  Then something will "click" and you'll never want to go back to limited computing.

BTW, my businesses use Linux for everything except 1 box runs Quickbooks. That is the only Windows in our company ... besides desktops which are owned by each employee. Fighting with an accountant isn't worth their or my time. ;)

Like others have said, running most services directly on the internet is a bad security practice, regardless of the OS.
Also pfSense is most definitely NOT linux. It is freebsd-based. Both are UNIX-like, but have a different feel for an administrator.  I prefer pfsense over any Linux-based router/firewall/proxy ... Definitely run this on a dedicated machine - a i386 is fine.  Just deployed an Alix.2d13 for a client with 50 end-nodes. They didn't have the technical savvy for a server, but we could have done so much more if they did.

If your "server" hardware is sufficient, definitely deploy virtualization. On Linux, there are different virtualization choices - most people need to use VirtualBox for the GUI performance, but KVM is rock solid for server-on-server needs and can handle lite desktop VMs too. I prefer that KVM is built-into the Linux kernel and not some 3rd party add-on that has to muck with the kernel.

To get started with linux servers, the best places are file/print. Those have worked very well since the mid-90s. Add a proxy to filter and speed up internet connections, then a wiki to capture workplace knowledge.  For remote access, learn with ssh (use keys and follow best-practices for securing it), then only if you need it, setup remote desktop access using FreeNX server and NoMachineNX clients. This works fine for small companies. If you use rdp or vnc, a real VPN is mandatory - openvpn. Do not use pptp it has been hacked for years.  For internet facing services, put them on different VMs. For internal things, putting them on a single VM can make sense as long as the setup doesn't become too complex and hard to reproduce.

Remember, you aren't having to track license keys or license costs with Linux, so having 2 or 20 VMs really comes down to complexity needs.  When you get about 5 VMs, it is time to look at config management tools. I'm loving Ansible.

The basics of backups are the same, but there are many more fantastic, free options for Linux. No need to do highly inefficient, image-based backups with Linux either.  

Asking broad questions returns broad answers here.  To get the best answers, 
* do your homework. google, RTFM, search the distro-related forums, help, and how-tos. Prefer the help.ubuntu.com over other website how-tos.
* try to make it work. The attempt is critical.
* if it doesn't, explain what the end-goal was and the software/hw used
* be open to different ways of accomplishing the goal - the UNIX way is almost always VERY different from the Windows way.
* don't fear the shell/cli interface. That is where all the power lies.

I wrote a lifehacker article on system maintenance for Debian/Ubuntu systems a few years ago. Here's the [updated version]("http://www.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs").
Check my signature for more Linux stuff that is important to know.

---

### Post by brent4 on 2013-09-18
That....is the most in depth and flat out awesome answer I've received in all my years on forums.  I want to take the time to thank you TheFu for the information.  I'm certain it will go a long way when I really start getting into this beast.  The problem I'm really facing is that I hired a gent to set up the server after I got so fed up with windows that I couldn't stand it anymore.  He put that pfSense thing on there.  2 days ago, we had a small power outage and when the server booted back (my dumb fault for no UPS online) it was pulling the DHCP WAN IP instead of the static block I pay for.  So I reset the WAN to the static and while my server can talk to the internet (can ping anything and all websites available) I cannot however route the internet to my router and to my wifi PCs.  PCs see router, router sees server, server doesn't talk to router.  This has been an ongoing nightmare and is costing me money, the guy who set it up won't return my calls and I'm not savvy enough to figure out where it went wrong.  So I'm weighing my options and like I said in previous posts, I fell in love with Ubuntu desktop.

By the way, I have a full service server rig, not an adapted PC.  I run Dell PowerEdge 2950s and while I am of course worried about security, I'm more worried about functionality at this point.  Does that make sense?

---


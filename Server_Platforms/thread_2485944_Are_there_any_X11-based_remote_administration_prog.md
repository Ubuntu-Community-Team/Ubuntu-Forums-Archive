---
title: "Are there any X11-based remote administration programs?"
date: 2023-04-14
forum: Server Platforms
---

### Post by papriak on 2023-04-14
I'm currently using Webmin to access and check the stats of my Ubuntu installation, but I would like to use a more "native" method if there are any available.

The main features I seek are a file manager and hardware usage stats, in addition to Terminal access.

---

### Post by TheFu on 2023-04-15
Er ... is this a trick question?  You can run local admin tools on any system over X11-forwarded connections.

Most enterprises would use a DevOPS tool like **ansible** to manage more than 20 systems.  For less than 5 systems, ssh is the normal method.  There are a number of tools to make ssh use easier (in theory). Check out **ClusterSSH**.

"hardware usage stats" is called "monitoring".  There are lots of tools for that, but all the enterprise versions have an agent that reports stats to a centralized server.  Check out **glances** for 1 system, live, monitoring.  ssh into a system and run it. The defaults are fine, but it can be highly customized.

Check out Cacti, **Munin**, or 50 others for centralized monitoring.  I think Munin is the easiest.  **SysUsage** used to be pretty easy to setup, but it was mainly for single-system networks. These all generate webpages. [https://sysusage.darold.net/](https://sysusage.darold.net/)

**Cockpit** is a popular admin tool these days. Seems like a replacement for webmin in many respects. It is a webapp.

If you are looking for something like the MSFT Performance Monitor, someone else will need to answer.  I've seen something like that on desktops, but since servers don't use GUI programs, they are of limited use.

I find the lack of historical data makes tools like that nearly useless.  When trying to figure out performance issues with 1 or 50 systems, having data for the last 2 months really is important. Munin can provide that in addition to data from the last 10 minutes. [http://guide.munin-monitoring.org/en/latest/preface/whatis.html](http://guide.munin-monitoring.org/en/latest/preface/whatis.html)

---

### Post by papriak on 2023-04-15
> **TheFu said:**
> Er ... is this a trick question?  You can run local admin tools on any system over X11-forwarded connections.

Most enterprises would use a DevOPS tool like **ansible** to manage more than 20 systems.  For less than 5 systems, ssh is the normal method.  There are a number of tools to make ssh use easier (in theory). Check out **ClusterSSH**.

"hardware usage stats" is called "monitoring".  There are lots of tools for that, but all the enterprise versions have an agent that reports stats to a centralized server.  Check out **glances** for 1 system, live, monitoring.  ssh into a system and run it. The defaults are fine, but it can be highly customized.

Check out Cacti, **Munin**, or 50 others for centralized monitoring.  I think Munin is the easiest.  **SysUsage** used to be pretty easy to setup, but it was mainly for single-system networks. These all generate webpages. [https://sysusage.darold.net/](https://sysusage.darold.net/)

**Cockpit** is a popular admin tool these days. Seems like a replacement for webmin in many respects. It is a webapp.

If you are looking for something like the MSFT Performance Monitor, someone else will need to answer.  I've seen something like that on desktops, but since servers don't use GUI programs, they are of limited use.

I find the lack of historical data makes tools like that nearly useless.  When trying to figure out performance issues with 1 or 50 systems, having data for the last 2 months really is important. Munin can provide that in addition to data from the last 10 minutes. [http://guide.munin-monitoring.org/en/latest/preface/whatis.html](http://guide.munin-monitoring.org/en/latest/preface/whatis.html)

Thank you for your detailed response.

It's not a trick question, I'm fairly new to linux and don't know all the terms.

There's only one machine on my network that I want to monitor, and possibly a second in the future.

The reason I asked was because I was told X11 is more stable than Wayland.

---

### Post by TheFu on 2023-04-15
> **papriak said:**
>  The reason I asked was because I was told X11 is more stable than Wayland.

For some things, that is true. For other things, it isn't true.  I use X11 because of some workflows that Wayland doesn't support and there isn't any reasonable workaround to solve.

X11 is a client/server display system. The server is on the machine we are sitting at and clients are either on the same machine or anywhere on any network.  This is backwards from what most client/server architectures use.  The terms
 X11 == X/Windows == X
 X/Server is the X/Windows server. There are a number of them, but on Linux is it usually xorg.  Not all platforms include an X/Server, but there are paid and F/LOSS options.
 X/Client is what the normal program we would run is called.  

So, if I run an xterm on a remote system, but have the DISPLAY environment variable setup correctly (and a few other things set correctly), then that program, xterm, will show up on a window on my local machine. The xterm (X/Client) is communicating with my local X/Server. 
There are specific X libraries for clients and specific libraries for servers.  They always communicate over network UDP sockets.  This is a security issue, since UDP is a stateless network packet and the "FROM" information in the UDP header doesn't need to be correct.
When ssh was first created, they added something called X11Forwarding.  This is usually enabled in Ubuntu, but often not enabled in Unix platforms to prevent end users from running GUI programs remotely, draining server resources.  Imagine a server with 6000 concurrent end users and they all want 2 xterms running all day?  That's a bunch of wasted resources which I've seen bring a $5M server to its knees.  We disabled X11forwarding and there were lots of complaints, but everyone learned to do the same work using straight ssh ... and actually became more efficient because the server to handle more tasks, faster, with the drastically reduced load.

Wayland seems to have 2 modes with the default mode assuming no networking between the client and server. This assumption means those 2 halves communicate using local IPC, not over network IPC.  I think there's something called XWayland that is supposed to provide the same network agnostic capabilities that normal X11 clients and servers have. XWayland really wasn't usable until around 2015, so it has come a long way in a short time.  Many of the people maintaining the Xorg software are also on the Wayland team.  X11 has code from the mid-1980s, so there is a much of cruft AND a bunch of already solved, complex solutions.

Wayland closed a number of security holes, some really big, with X/Windows.  Perhaps in another 5-10 yrs the things that it cannot do that Xorg does today will be possible. I'm hopeful.

Right now, I have 15 windows open on my workstation.  Of those 15, 5 are running programs locally and the other 10 are running stuff on other systems.  I run my browser and email client on remote systems, for example.  This is a security technique.  Running remotely just keeps potential malware off my workstation.  In addition, I run all high-risk programs inside sandboxes that I control.  I find the control and other issues provided by snap packaged programs to be too limiting, in general, with a few exception. Snaps are a completely different topic.

So, back to Xorg vs Wayland stability.  The answer is "it depends".  OTOH, stability between webapps and local apps is a completely different issue.  I'm less worries about stability of webapps, but really concerned about doing any administrations using any webapps.  Seems like a really good way to get a system cracked.  Attackers are professional webapp attackers - much better than the average admin is at security.

If you care about security, learn to do things from a shell, over ssh and stop there. If you need to manage more systems, learn scripting and a devops tool.  DevOPS is something real admins have been doing 40+ yrs, well before someone got a marketing team to push Ansible or Salt or Puppet or Chef or CFEngine or Rexify.  I've looked at them all and attended training on 3 of them. Most of those tools caused more problems than they solved, unfortunately.  I think the only one that didn't was ansible.  Ansible is far from perfect, but the least suckage for all those types of tools.  So many of them have "magic file locations" that don't make sense. Ansible has just a few, but they are expected and easily overridden in expected ways.

It is always best to start managing systems using your own scripts first, so you understand what really needs to happen.  I still do weekly patching using my own scripts, though if I need to install a package on all my web servers, I'll use ansible to accomplish that. Once setup (which doesn't require any "magic" either, Ansible "feels" like a normal Unix tool, unlike many of the other options.  I was able to learn to manage the /etc/hosts file for every system here in about 20 minutes. Each is slightly different, so it wasn't just a trivial "copy" using the tool, but a templated solution that used ansible "facts" (those are known system things) to filling specific parts of the /etc/hosts file for each system.

Sorry for going on. I had a few minutes.

---

### Post by papriak on 2023-04-15
> **TheFu said:**
> Sorry for going on. I had a few minutes.

Don't worry about typing long posts in my case, I have the time and much to learn.

The  server(s) I'm building are for personal backups and shared file  storage, probably not of interest to anyone on the outside.  (Though I  might be wrong)

I've only tried Webmin for accessing a headless server.  I'll try SSH-ing and maybe give Cockpit and Glances a try too.


Thanks!

---

### Post by TheFu on 2023-04-15
> **papriak said:**
>  
The  server(s) I'm building are for personal backups and shared file  storage, probably not of interest to anyone on the outside.  (Though I  might be wrong) 

Any hardware connected to any network is a juicy target for crackers.  Don't think you are uninteresting.  Keep your router patched and current with firmware.  When no new firmware is release for a quarter, it is time to get a new router with better/longer support.

Look at your router logs and see who's actually attacking, constantly. I think you'll be surprised.  I see hundreds of thousands of attempts every day.  Usually about 150 IPs get blocked automatically because they do stupid things.  The gangs running all these attack servers keep going, day after day after day, seeking weak security and pouncing when any tiny flaw is found in our defenses.

This article: [https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/) is worth a read to understand that **any** computer device that can be accessed over the internet can be used by others to make money, somehow.  Even if you block all inbound attempts, but still allow webpages to run javascript, you've provided an attack and reconnaissance platform to run the code the remote guys want.

---

### Post by MAFoElffen on 2023-04-20
I think for remote admin for Linux Servers... I don't trust or like many of them. webmin and nagios are liked by many. Sometimes those bring in their own problems.

Some use Console and some others... I was excited by the promises of Console, but then found it was very limited by what was actually GUI, and the wrapper centered back to a GUI terminal console to do most of what you needed to really do.

Which brings it back to just using ssh for admin tasks...

I haven't really found anything that I have fell in love with or trusted. I have, in the past loved and recommended Zentyal as a Small business type server platform or home server, but that is a local "https" wrapper for a local GUI built on an Ubuntu Server base. But their release versions lag too far for my liking, behind Ubuntu releases. I think they are now almost ready to release 22.04...

Sidenote to others- His server is a home server providing Samba File shares, with nothing public facing.

---


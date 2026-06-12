---
title: "Is my thinking all wrong on Ubuntu Desktop vs. Server"
date: 2015-01-12
forum: Server Platforms
---

### Post by jfaberna on 2015-01-12
my application is a simple java server application that communicates with external hardware via Ethernet and WiFi to PCs logging into java server app.  I've tested it on a very small PC (NUC) running Standard Ubuntu 14.04 LTS Desktop.  I thought that once I figured it out. I'd just change to Ubuntu Server, no GUI,  and auto start the java server app.

However, without changing any hardware or network connections, when I install Ubuntu Server 14.04 LTS, I can't get the network to find the DHCP server during install.  At this point I'm questioning What's wrong with just running Ubuntu Desktop and change grub to boot into text mode.  If that eliminates Unity and X, them maybe that's all I need for a stable Server.  I can manage it via openSSH.

Thoughts?

---

### Post by TheFu on 2015-01-12
You can to that and if you are self-hosting, fine. It is just a waste of 5G of storage.
The reason to run server is to remove unstable (relatively) GUI libraries from the system. This means the uptime won't be 2 months, but 2+ yrs, if you like.

Why not just fix the DHCP issue? You'd learn something and end up with a leaner, more stable server.

---

### Post by tgalati4 on 2015-01-12
Servers typically have manual IP addresses so unless you need to assign IP addresses to other machines on your network, you would normally let the router do that.  You don't need DHCP, unless you really need it.

---

### Post by Bucky Ball on 2015-01-12
*Thread moved to **Server Platforms**.*

You should have more luck here.

---

### Post by jfaberna on 2015-01-13
>  Why not just fix the DHCP issue? You'd learn something and end up with a leaner, more stable server.

For me as a hobbyist, the step down in ease of use from a desktop environment to a server command line is a huge step.  I find I keep a browser open and cut and paste commands from websites/forums all the time.  Also the GUI setup apps do work and are easy to use without remembering the syntax of the CLI.

Now that I have everything working on my project using a desktop Ubuntu release, I'll parallel what I did on a Ubuntu server setup and hopefully find the right files for configuring the network and just copy them over.

I probably should just stay with Desktop because if my embedded application is stable for 2 days, then it's stable for infinity.  The application is powered up, run for 16 hours, then shut down, till next time.

---

### Post by TheFu on 2015-01-13
"Server" uses DHCP by default, so switching to desktop won't fix that if you keep using DHCP expecting it to work.  The issue is likely at your router.

However, if you want to run a server, then it needs a static IP.  That is just a few lines in 1 config file and you never have to worry about it again. The same lines work in desktops too.  This is about the easiest thing to correct there is.

If you learn the CLI methods (or know where to look them up), that knowledge works for 30+ yrs.  If you learn the GUI way, that knowledge lasts 2-3 years until a new GUI is forced onto you. 

Still - it is your decision.

---

### Post by jfaberna on 2015-01-14
Just as a learning process I did get Ubuntu Server 14.04 LTS installed  and got my WiFi port configured at a static IP and my enet port static on another subnet to talk to my external device.  I now have a USB drive with the /etc/interfaces file on it so I won't have to do this again.:p

However, for development I like a GUI and maybe just put lubuntu-core on and a browser.

---

### Post by TheFu on 2015-01-14
Wifi and a server are a less-than-good idea.  Servers usually need to provide great connectivity and that isn't wifi. After doing 1200+ wifi deployments around the world, I completely avoid it whenever possible.  For example, I'm using a chromebook now - no wired ethernet port - but I've connected a GigE USB3 port to it.  Wifi has so many issues and is not a stable connection in reality. To humans, it may seem stable, but computers know the difference.

---

### Post by jfaberna on 2015-01-14
It's really application dependent.  I should have given more detail, but didn't think it relevant at the time.  My Server is an Intel Core i3 NUC ~4"x4"x1". It sits on top of the External device which is a Stoker charcoal grill controller and is connected to the Server with a 3" enet cable.  The WiFi port allows the Server to host a webapp that can be view by any PC in my house with a web browser.  So the Server and Stoker sit outside by the BBQ smoker with only 110v connection to the world.  So on an 16 hour smoke run, I sit inside watching TV and glancing at a browser.

There is no problem that can't be solved by applying an excessive amount of technology.

[IMG]http://i61.tinypic.com/2gspj85.jpg[/IMG]

---

### Post by TheFu on 2015-01-14
**YOU SIR ARE THE MAN!!!!!**

I used to work at a Central Tx BBQ joint.  I must say, you need to patent this ASAP!  1,000s of BBQ competition teams will pay handsomely for this. Especially as an all-in-one purchase.  Be sure to demo it using a tablet/smartphone.

So now that I'm really engaged - what was the issue again? ;)  If solve, please mark the thread as solved!
You wouldn't live near ATL?  My LUG would love to see this both at a meeting and "in action".

---

### Post by jfaberna on 2015-01-14
This is not an unique solution.  The Stoker-web app is at [https://code.google.com/p/stoker-web/](https://code.google.com/p/stoker-web/) and the Android app for smart phone are available at Google play.  Other apps that work with the Stoker grill controller are linked to on the Rocks BBQ Stoker site ([https://www.rocksbarbque.com/Applications.html](https://www.rocksbarbque.com/Applications.html)).

Lot's of competition BBQ teams use the stoker.  You don't need to connect to the Stoker with a computer to use it, but you can and like I said, no problem can't be solved with the application of excessive technology. I just had this NUC laying around and it's too cold to go play golf and I need a project.

---

### Post by TheFu on 2015-01-14
NUCs should be great as Plex servers or XBMC devices.

I'm using a AMD E350 APU for Plex, XBMC and NFS.  Wish I would have bought 3 more of these for $99 complete. The stopped selling them 2 yrs ago. Handles 1080p content perfectly (thanks to the GPU). Had to add some leftover RAM and a HDD then swap the jet-engine PSU for a PicoPSU (100% silent) to be used in the projector room.

Wish I would have switched to Plex server years ago.  Now I'm thinking it will be a Calibre ebook server for the LAN.

BTW, if you need a good remote desktop into a headless device, **x2go** clients/servers work great. My primary desktop is running in a VM of a private cloud only accessible through ssh (x2go uses NX, which is based on ssh).

---

### Post by jfaberna on 2015-01-14
thanks, and BTW in NC not ATL.

---

### Post by lukeiamyourfather on 2015-01-15
> **jfaberna said:**
> For me as a hobbyist, the step down in ease of use from a desktop environment to a server command line is a huge step.  I find I keep a browser open and cut and paste commands from websites/forums all the time.  Also the GUI setup apps do work and are easy to use without remembering the syntax of the CLI.

I was quite annoyed with the command line interface as well until I figured out SSH. That way you can copy and paste things or use a web browser on whatever machine you want but still be able to control the Linux machine remotely. In this case I'm sure Ubuntu Desktop will be fine. It looks like a fun project!

---

### Post by MAFoElffen on 2015-01-16
> **jfaberna said:**
> There is no problem that can't be solved by applying an excessive amount of technology.

Ingenious! I have to tell you, I fell out of my chair laughing with your reference (quoted above). That really hit home. Thanks!

---


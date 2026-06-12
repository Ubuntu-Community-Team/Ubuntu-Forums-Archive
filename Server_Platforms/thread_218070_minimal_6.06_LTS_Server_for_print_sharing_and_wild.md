---
title: "minimal 6.06 LTS Server for print sharing and wildfire"
date: 2006-07-18
forum: Server Platforms
---

### Post by warren.stanley on 2006-07-18
Hi all

I have a HP eVectra PC, currently running win2K for sharing a printer to a domain. it's also running Wildfire (Jive Software) IM server(small amount of users, internal network). With only 128MB of Ram (minus the i810e stealing memory) it's chugging. I can possibly source a 256MB chip to upgrade (only one slot) but am wondering how much better it could be done with *nix.

My questions:
- How/what to do for 6.06 LTS Server install with minimal needed for sharing Samsung ML1710 usb printer and Wildfire(assuming 6.06 LTS Server needs java, can't find dependency list)?

- Install the absolute minimum for a local X display?

Worth it....I'd like to hope it is, but i'm open for realism ;)  .

Cheers

---

### Post by Soleil-Raid on 2006-07-18
Looking at similar apps: Cups uses about 4-10 MB depending on printer. Wildfire (3.0.0 beta) uses about 20-40 MB, and gdm can use... lots (at least 15, maybe up to 60).

gdm might be the killer. If you only need X use occasionally, look at turning off gdm, and use startx from the console (.xinitrc will help you there) to start a X server when you need it. Also, be aware that you can access remote X applications over SSH without the use of gdm.

Hope this helps.

---

### Post by warren.stanley on 2006-07-18
Cool....thanks for advice, figured GDM would be a hog on this tiny pc.

OK

Anyone have pointers for how to do this in a minimal way - excluding the Wilfire component - this I can research after. just essential packages (startx to get a basic gui would be nice)? There seems to be lots of guides to building "everything in one" servers, nothing that starts basic for basic tasks.

Step 1 - instal 6.06 LTS Server (not lamp)
Step 2 - Apt update and upgrading

---

### Post by warren.stanley on 2006-07-18
Step 3 - enable a root account
step 4 - What next?? X, config X, cups, config and testing cups - This is where i need the help.

Cheers

---

### Post by doogy2004 on 2006-09-14
I was in the same boat as you are, I have a 330 mhz p3 with, 512mb ram (used to be 92mb).  I have it running WINS, Azureus server, DNS server, Jabber server, Samba server and much more.  I also have detailed documentation on all of this.

note - my server serves Windows, Linux, and Mac

What all do you want to do with this computer?

---

### Post by crouton on 2006-09-16
Do you really need a X server?  You should be able to install and run all of the daemons (cups, wildfire, etc) from the CLI.

---

### Post by houstonbofh on 2006-09-16
> **warren.stanley said:**
> Cool....thanks for advice, figured GDM would be a hog on this tiny pc.

OK

Anyone have pointers for how to do this in a minimal way - excluding the Wilfire component - this I can research after. just essential packages (startx to get a basic gui would be nice)? There seems to be lots of guides to building "everything in one" servers, nothing that starts basic for basic tasks.

Step 1 - instal 6.06 LTS Server (not lamp)
Step 2 - Apt update and upgrading
Since you want X and need lite, I would install xubuntu-desktop, or actually start with the xubuntu cd.  Much lighter than Gnome, and still functional.  Then configure your aps, and kill the GDM.

---

### Post by warren.stanley on 2006-10-16
Doogey 2004....

It's just going to do Wildfire IM and Printer Sharing of a samsung ml-1710 USB laser printer. Not actually do the domain auth, just a member.

Tips anyone ?

---

### Post by doogy2004 on 2006-10-17
crouton is right all of those things you can do using the command line.  I'm like you, I'm a windows users most of the time, i used to work as a windows workstation tech/admin.  So i like to use the gui to help me learn linux.  over time i'm becomming more and more inclined to simply run my server straight from command line, since everything that i am doing with my server can be done using command line as a service(daemon) except azureus.  also, i'm not using WINS(samba) for domain authorization, WINS(samba) is simply being used to resolve netBios names and workgroup membership for the network.

Ok other than wildfire and printer sharing, are there any other things that you would like to do with this server, such as static ip, which you are probably going to need.  going along with that you are going to have to set the static DNS as well.  this type of stuff will need to be known before diving into a command line only server, because doing these things can take a little bit of research as far as how to accomplish the task, rather that using the gui which is easier to and faster to figure out for new users.

as far as what particular gui you use is up to you.  Yes, your computer should run just fine with the standard Ubuntu(Gnome gui).  Or you could opt for Xubuntu(XFCE gui) which has a different set of packages that come preinstalled.  If you are just starting out using linux in general, start buy installing Ubuntu 6.06, and setting up your server from there.  When I started i was running all kinds of services on 330mhz PIII and 92mb of ram, it was kept up with things preaty well, and was responsive without azureus running.  But once azureus was started it was able to keep up with everything except it was slow when i tried to do any thing else with it, e.g.  update, browse the web, etc.  So my solution was to stop azureus before starting those tasks.

RECAP
- New to linux - use a gui, try each one out and see how you like it
- Comfortable with linux - use a command line server

---

### Post by airtonix on 2007-02-11
i have this setup and running minus the ldap or pam authentication....

from my dapper workstation(10.1.1.11), i do this to run firestarter on the server(10.1.1.1) ....from term :

1- airtonix@10.1.1.11:$ ssh airtonix@10.1.1.1 -X
2- [then type your ssh password on the remote machine]
3- airtonix@10.1.1.1:$ sudo firestarter
4- [then type the sudo password of your account on remote machine]
result - firestarter will then open on my screen at 10.1.1.1

just about any program can be run this way.....i can even run nautilus or thunar.

---


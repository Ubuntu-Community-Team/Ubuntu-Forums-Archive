---
title: "new user setting up home file server"
date: 2009-08-13
forum: Server Platforms
---

### Post by Ak_IT_Guy on 2009-08-13
Hi Guys
    I know this has been asked before and I am sorry if this is just a dupe of what has been asked in past threads. I am a IT student and new to the Forums and Linux platform. what I am needing is a basic home file server for the 4 systems in my home network to share data files and digg image files.
    I am thinking of using UBUNTU 8.04.3 server on my retired desktop system  a old home built AMD dual core 3800, 4 gig ddr2 800, 2 hhd ( 75 gb WD Raptor for OS and 1.5Tb Barracuda) for Files, What other things or software will I have to do in order to make this work. what I am net working is 3 laptops 2 with win xp pro and 1 with Vista home prem and a Desk top running win XP pro. other equip is linksys 54g wireless router, linksys print server with a Brother B/W laser printer, Lexmark all in one photo quality inkjet.

What I am trying to make happen is once the server is setup  it will be a low maintance an space saving set so that I can get rid of the keyboard, mouse and LCD screen. and if I need to change or work on I can use a remote desk top set up with my laptop

Thanks Guys
any tips, comments or Ideas are always welcome an taken in to consideration.

---

### Post by alexlafreniere on 2009-08-13
Are you comfortable with the command line? If so, go ahead and install the latest and greatest Ubuntu Server Edition on your machine. If not, do a desktop installation and install a VNC server so that it could be a headless server as you describe. To share files on your local network, all you need to do is set up a folder you want to share (note: shouldn't be /). There are tons of guides out there for sharing files on a home network, here ([http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)) is a good one.

---

### Post by ugm6hr on 2009-08-13
I would strongly recommend FreeNAS for this instead of Ubuntu.

It is dead easy to install, can be booted from a USB flash drive, is managed from an easy web interface (i.e. no need for typing lots of commands etc), and is upgraded from the same interface.

It will share your files with SMB (Windows share) with a few clicks.

I cannot see any reason why you wouldn't choose it!

See the FreeNAS link below for details.

---

### Post by HermanAB on 2009-08-13
As usual, there is more than one way to do it.  You need both a print server and a file server.  The print server is CUPS and the wizard is called system-config-printer.  The File server can be either Samba or NFS.  

The most difficult way to do it, is with Samba.  Go to the Samba web site and read the Official Howto.  They also have an Ubuntu specific howto.  Configuring Samba requires hundreds of lines of crap in /etc/samba/smb.conf.

The easiest way to do it is with NFS.  Go to the Microsoft web site and download and install Services For UNIX and install it on each Windows machine.  Then install the NFS server on the Linux machine.  Configuring NFS requires only one line in /etc/fstab.  A little Googling will get you going, or you can see this: [http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

---

### Post by ugm6hr on 2009-08-13
> **HermanAB said:**
> You need both a print server and a file server.  

S/he has a linksys print server, so a file server will probably suffice.

---

### Post by Ak_IT_Guy on 2009-08-13
> **alexlafreniere said:**
> Are you comfortable with the command line? If so, go ahead and install the latest and greatest Ubuntu Server Edition on your machine. If not, do a desktop installation and install a VNC server so that it could be a headless server as you describe. To share files on your local network, all you need to do is set up a folder you want to share (note: shouldn't be /). There are tons of guides out there for sharing files on a home network, here ([http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)) is a good one.
Thank you for the reply
as for the command line, I have very little if any experance with it at all, how ever I am willing to learn and try new things.
At this time I am using my desktop for file and print sharing and finding out that it is more of a pain than any thing. 7 out of 10 times windows has a hard time finding the share even when my other systems are mapped to the folders or drive. so my thinking was setting up my old system as file server only with a static Ip address would make it more stable and less time trying to find stuff..lol
thanks for the info and I will look into if more.

Thanks
Johnny

---

### Post by HermanAB on 2009-08-13
Uhmm, a server MUST have a static IP address (unless you are a masochist!).

Also, don't use VNC if you can help it.  Install SSH Server, it is secure and can do everything VNC does and much more.

---

### Post by Ak_IT_Guy on 2009-08-13
> **HermanAB said:**
> Uhmm, a server MUST have a static IP address (unless you are a masochist!).

Also, don't use VNC if you can help it.  Install SSH Server, it is secure and can do everything VNC does and much more.
Thank you ..lol I know that a sever has a static Ip and I have not got to the point of (masochist) yet and the key word is YET.. how ever if my wife and kids keep screwing up my system that could very well change.

I was not implying or trying to make my self sound stupid what I was trying to say was that I have been using my main desk top for file and print sharing at this time and that it has been to much trouble to keep up on. I was just thinking it would prob work better for me if I used a file server with a perm IP address rather using my main desk top to share files on because of all the problems that go along with that. because I use  cpl diff Os some times windows will not see the shares or other systems on the network. at least a file server with a perm address I would not have that problem.  thats all I was trying to say. sorry if It I did not make any sense, will do better next time around.....

thank you 
johnny

---

### Post by HermanAB on 2009-08-13
You should also look into a DHCP server.  If you run one on your server (instead of using your little Linksys/Netgear/Whatever firewall DHCP) then you have more control and can provide the PCs with more information so that they know where to find all network services including the server, printer, gateway and the like.  That will make the usual network blues go away.

---

### Post by Ak_IT_Guy on 2009-08-14
> **HermanAB said:**
> You should also look into a DHCP server.  If you run one on your server (instead of using your little Linksys/Netgear/Whatever firewall DHCP) then you have more control and can provide the PCs with more information so that they know where to find all network services including the server, printer, gateway and the like.  That will make the usual network blues go away.
Thanks for the info.
I will look into it, I have been looking into lots of diff setups trying to find one that will fit my needs.

thank you
Johnny

---

### Post by ultimatebuster on 2009-08-14
I actually made a similar tutorial just now. :)

[http://thekks.net/456](http://thekks.net/456)

---

### Post by garfonzo on 2009-08-15
For what it's worth...

I had the same situation (multiple PCs, one printer, all needing access to files). For a bit I had made my desktop the 'server' and shared files/printer from it. It became a bother and so I began the hunt for a better way. 

I got my hands on a second hand PC and first tried FreeNAS. I *was* working really well until one day it crapped out on me. I never figured out why. Generally, it is a great, simple, reliable OS. I just ran into troubles I couldn't figure out and jumped to Ubuntu (I have some experience with Linux and the UNIX base of FreeNAS was different enough to be frustrating for me).

I now have Ubuntu Server 9.04 running on a dedicated tower (similar specs to what you have). It runs on a shelf in my garage with 6 hard drives installed, no keyboard, no mouse, and no monitor. When I need to access it (which is rare - it takes care of itself) I use Putty on any windows box to log into it via command line. All PCs in my house (all Windows) have mapped network drives to the server - accomplished by setting up Samba on the server (very easy). 

It will soon be setup to also record TV, but for now it just shares files and does backups weekly. 

I know that this doesn't really 'help' you based on your original post. I just thought I'd throw out there that it is doable.

---


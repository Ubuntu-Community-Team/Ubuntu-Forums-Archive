---
title: "Help Setting Up Ultimate Home Server"
date: 2011-01-10
forum: Server Platforms
---

### Post by Rastlosen on 2011-01-10
I am trying to set up the ultimate Linux server (with a GUI interface.) I would like to be able to run this linux server with Multiple running servers imbedded over top of it running constantly. I need to have a permanent webserver up at all times. I will need a seperate dedicated file server for backup of all other machines on the network (one mac, three win 7 machines, and one win 95 box.) I would like to have IP Masqurade builtin infront of the webserver. We need one media server built in that can be pulled to anywhere in the two story building. I also need to be able to remote into the machine from outside the network and within the network. I would also like to have a copy of windows on the machine that I can access from remote. If possible I would like to run a domino server aswell to be able to configure email and sametime between machines. 

I guess the hardest part for me is figuring out how to a) get the base setup, b) how to make all of these run simultaniously on the same piece of hardware with no conflicts, c)how to get an almost vmware style of view to the setup.

The system that this would be going on is a 6tb (sata) quadcore (2 x 2.3 duals) setup with dual video (1 gb ea) and 6 gb ram and two nic cards. 

Does anyone know how to set this up? I have had about a year of working with 10.4 desktop edt, but honestly this project is so big that I have no Idea where to begin... Any help in the even the process that I should follow to get this setup going is much appreciated.

---

### Post by schwascore on 2011-01-10
Virtualization is relatively easy using vmware or virtualbox.

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

[http://www.virtualbox.org/](http://www.virtualbox.org/)

You'll need to think out your network setup prior to configuring the VMs, but what you are asking about really isn't that difficult. You can even create a virtual router/switch/firewall for your IPmasq requirements. Behind this, your web server, file server, media server and windows.

Your hardware specs may need to be beefier, but it all depends on your usage.

---

### Post by mclimber43 on 2011-01-11
I don't know if this is much help, but on my network I run a Samba server, ftp server, apache.  I have webmin as a GUI interface.  I also run VMware server with a Windows XP guest OS.  The virtualization solved a number of problems for me.  One thing you could do is run the server(s) off one or more virtual machines, so you could log in via VNC or something remotely and have a graphical interface.

---

### Post by mclimber43 on 2011-01-11
By the way, the information at [http://woodel.com](http://woodel.com) helped me a lot.  If you haven't set up a server before, I recommend running through this "tutorial" once.

---

### Post by West201 on 2011-01-11
Let me know which OS works best. :)

I'm setting up Home Server my self, but don't know weather to use Win Server 2008 or which linux distro to use.

I use Ubuntu on my notebook, and i'm loving it !

[http://ubuntuforums.org/showthread.php?t=1664601]("http://ubuntuforums.org/showthread.php?t=1664601")

---

### Post by ajcis55 on 2011-01-11
VMWare ESXi is definitely the way to go. It is a little picky on hardware, but does support quite an array. Note that you'll want to have a proper hardware array for this to be of any use, unless you plan to only use one harddrive (which I don't recommend for any server).

---

### Post by Rastlosen on 2011-01-12
Thank you all for the feedback. I have looked into vmware esxi and it seems that they have a very expensive version and a free version. Will the free version work for this useage? I have used Sun's vbox in the past for emulation, but never thought of it for this, as it always seemed a bit unstable when multiple os's were running at the same time with it; but I will definately look into it for this application now that its been a few versions past. The woodel.com link has been very helpful as well and I have been reading through it. 

Once again Thank you all for your help. It is very, very much appreciated. 

-Rastlosen

---


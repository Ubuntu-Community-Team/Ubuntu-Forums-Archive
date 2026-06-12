---
title: "Ubuntu Server 14 - GUI and Remote Access"
date: 2015-10-17
forum: Server Platforms
---

### Post by Billy_Martinez on 2015-10-17
Hello everyone,

I'm a network admin for company. I revived an old dell server that I had lying around and installed Ubuntu Server 14 on it. While I was installing the server I got a screen where it asked about the features that I wanted to add to my installation. I checked "Basic Server" and "Open SSH Server," and went on with the installation. When the installer finished the installation and restarted I was surprised to be greeted by a command prompt. I thought that Ubuntu Server was going to come with its own lightweight GUI and have Vino installed. I'm no Linux guru, but I'm somewhat familiar with Ubuntu Desktop. I've used Vino to remotely access my Ubuntu Desktop in the past and it worked great. I have two questions. 

1. What GUI do you guys recommend that I use as a light weight GUI for my server?

2. What would be the best way for me to access that GUI remotely?

I tried this site and it didn't work.
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04)

I was surprised to see at the end of the guide that I had to open up a tunnel using ssh in order for me to remotely log into my VNC server. I don't want to have to open up a tunnel. I just want to be able to open up VNC Viewer and type the server name and port number like this "servername:5901." I'm not asking for anyone to hold my hand, I'm just asking to be guided to the right place that will help me figure out how to set it up. Google is not helping me right now. 

Please Help

---

### Post by deadflowr on 2015-10-17
Moved to Server Platforms

---

### Post by darkod on 2015-10-17
You might not like this reply, but ubuntu server comes like that because most administration is supposed to be done over ssh session. That allows the OS to use less resources and to have less possibilities to be hacked.

If the machine is only on a local network, you could say that the danger from hacking is somewhat low. I hope your employees would not try hacking into the server. :)

The common suggestion is to try learning administering linux servers over ssh, the way it's supposed to be. You will find it valuable experience for the future too.

On the other hand, the machine is yours to do what you want and if you really insist on a GUI among the popular ones seems to be XFCE and LXDE. Those are lightweight so not to take too much resources from the server. Look at their main websites to compare and to be sure it fits your needs. I don't use any GUI so can't recommend any first hand.

For installation you should do it with apt-get over ssh session (don't try compiling from source code). You can use ssh on any linux, or using putty in windows.

---

### Post by TheFu on 2015-10-17
+1 to administration over ssh only. Running a server doesn't really have any GUI config tools for the server processes. The services work the same basic way:
* edit 1 or more config files
* start or restart the service to re-read the config files. Some services have a "reload" command
* setup the firewall settings to restrict access to the service as desired.

Be happy.  Learn the shell. Know the shell. Love the shell.

I hven't used VNC in over a decade. If you need a remote desktop, there are more efficient, and much more secure options. I stopped using the big heavy DEs about 2 yrs ago on my netbook/desktops. Openbox, but if you are new to Unix, that won't help too much. 

I hear people like LXDE and XFCE for remote desktops. Heard that VNC has a security option to prevent access from remote systems - thus forcing an ssh tunnel to be used. I find it is just much easier to use x2go which already uses ssh and has more efficient compression/xfer of the pixels.

More about x2go: [http://wiki.x2go.org/doku.php/doc:newtox2go](http://wiki.x2go.org/doku.php/doc:newtox2go)  they have a PPA and installation instructions.

---

### Post by Billy_Martinez on 2015-10-17
> **TheFu said:**
> +1 to administration over ssh only. Running a server doesn't really have any GUI config tools for the server processes. The services work the same basic way:
* edit 1 or more config files
* start or restart the service to re-read the config files. Some services have a "reload" command
* setup the firewall settings to restrict access to the service as desired.

Be happy.  Learn the shell. Know the shell. Love the shell.

I hven't used VNC in over a decade. If you need a remote desktop, there are more efficient, and much more secure options. I stopped using the big heavy DEs about 2 yrs ago on my netbook/desktops. Openbox, but if you are new to Unix, that won't help too much. 

I hear people like LXDE and XFCE for remote desktops. Heard that VNC has a security option to prevent access from remote systems - thus forcing an ssh tunnel to be used. I find it is just much easier to use x2go which already uses ssh and has more efficient compression/xfer of the pixels.

More about x2go: [http://wiki.x2go.org/doku.php/doc:newtox2go](http://wiki.x2go.org/doku.php/doc:newtox2go)  they have a PPA and installation instructions.

I'm going to check out X2GO thanks.

---

### Post by Billy_Martinez on 2015-10-17
> **TheFu said:**
> 
Be happy.  Learn the shell. Know the shell. Love the shell.


I do want to learn the shell, but everything can't be done through it. What if I want to install Virtual Box and run a virtual machine on my server? That program has a GUI.

---

### Post by deadflowr on 2015-10-17
> **Billy_Martinez said:**
> I do want to learn the shell, but everything can't be done through it. What if I want to install Virtual Box and run a virtual machine on my server? That program has a GUI.
Virtualbox can be run completely from the command line
[https://www.virtualbox.org/manual/ch08.html#idp45859066137568](https://www.virtualbox.org/manual/ch08.html#idp45859066137568)

---

### Post by TheFu on 2015-10-17
> **Billy_Martinez said:**
> I do want to learn the shell, but everything can't be done through it. What if I want to install Virtual Box and run a virtual machine on my server? That program has a GUI.

Don't use virtualbox. Use KVM. Then you can run VMs like the big-boys do. Openstack - is based on KVM.  Use virsh for simple stuff and from any workstation, you can connect with a "GUI" tool called virt-manager to create, start, run, access, KVM VMs.  

For desktop-on-desktop virtualization, virtualbox is probably the best free answer. If you have $100 to blow, VMware Workstation is slightly nicer, I hear.  Around 2010, I started switching our servers from a few different virtualization tools into KVM. Don't regret it at all.  We were running ESXi, Xen, VirtualBox at the time. Now we use KVM only ... and are looking at LXC/Docker for internal (non-secure) use only.

FYI - my normal desktop ... the one I'm using RIGHT NOW .... is a KVM VM running inside a private cloud, being accessed from a Win7 laptop, through x2go, over ssh.  There are many reasons I elect to do this.
1) Hardware agnostic!
2) Backups are trivial.
3) Moving to a faster system is really bonehead easy.
4) Performance --- from **anywhere** in the world.  I travel with a $200 chromebook that has an x2go client. From 5 different continents, my "desktop" is available, secure, and performs based on the remote CPU, not the cheap chromebook.
5) No important data on the portable devices.  If the chromebook gets stolen, I haven't lost anything but $200 in hardware.  A smartphone loss is MUCH worse.
6) Secure access to other systems that do not provide secure access ... like RDP on Windows. I can RDP from my "desktop VM" into a Windows desktop when access to Visio or 100% MSFT Office is required. That happens about once a year.  Most of the time, it is used to schedule a TV recording in media center, not much else.

[http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) explains more.  Basically, I read a blog post about a guy who was using an iPad as his desktop. That got me thinking. I've been using virtualization since the 1990s for many of those reasons listed above, but my internet connection is **extremely** solid - perhaps 3 hrs/yr of downtime - usually less.  I've been running programs on different systems since the early 1990s - it is built-into X/Windows and has worked well for long before I used Unix.  Why have my desktop only on a laptop?  Why not have it available to any client-machine I'm at?  Plus that laptop was heavy, big, power-hungry, and had 2 hrs of battery.  The chromebook has 7+ hrs of batter and is under 2lbs. It feels more like a tablet - which I've tried to use too. Tablets aren't quite enough OS for my needs.

If you want to learn, love, know, the CLI:  [http://blog.jdpfu.com/search/?q=learning+linux](http://blog.jdpfu.com/search/?q=learning+linux) has my best suggestions for that.

Anyway - lots of opinions above. Hope it is helpful.

---

### Post by Billy_Martinez on 2015-10-18
Thank you all for answering my questions. I had no idea that you could so much from the command line, and that I had so many options when it came to remote access and virtualization.

---


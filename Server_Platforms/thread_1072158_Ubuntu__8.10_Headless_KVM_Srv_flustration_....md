---
title: "Ubuntu  8.10 Headless KVM Srv flustration ..."
date: 2009-02-17
forum: Server Platforms
---

### Post by lewtwo on 2009-02-17
This is a meaningless thread. I am just venting after having spent several days beating my head against the aforementioned "wall" because if I do not get it off my chest the trash folks are going find a small pile of electronics on the street tomorow morning.:(

Lest anyone ask ... yes I come from a Windows world and have been managing MS networks for more years than I will admit (before that it was Novel and arcnet).

The idea:
Build a small headless server as a virtual machine host to house a windows domain for testing various software packages, concepts etc. After all who wants waste real hardware for Windows 7 Beta (or for that matter Vista). I also want to do a head to head comparison of Windows 2008 Server/HyperV to Ubuntu Server/KVM.

I have a nice little box by lenevo with an intel quad cpu, 4 GB ram and a 750 GByte hard drive. It also has an extra nic (intel) and external esata card (for backups). I already have the Windows 2008 installed on an indentical box.

OK download the Ubuntu Server DVD and burn it. Do the install. 
Select OpenSSH and Virtual Machine Server for packages. 
Things I did not find: 
   FTPserver ... 
   ...    why or why did they leave that out. 
   Statis IP address  ... 
   ...    do people really run servers from DHCP ?

Credit where credit is due: The installation went very fast and the system came up quickly. 

Now for the work to begin. What is the IP address ?? Well after digging around a bit I found the comand ifconfig (I had actually tried ipconfig). So I load PUTTY.EXE and connect. Now I can stop swapping the keyboard and monitor around finally.

H'mmmmm I should mention that I am a bit set in my ways. Two things that I absolutely refuse to use unless desperate beyond all reason are: VNC and VI (or VIM). I see to remember a command somewhere that will allow me to change the default editor from VI to Nano but I can find it now. 

First off install WebAdmin. No problem. It works well. 
It also gets around the problem of VI as long as I do not try to "man" anything. 

Next I need to fix the static IP address .... not supposed to be too difficult. 
I cruise down to file manager in webadmin and pull up /etc/network/interfaces in the editor. Make the apropriate changes and save it. 

Then I switch to the real keyboard again (drat) to restart the network. 
That broke everything. IFCONFIG shows all is well. However the machine will no longer communicate with anything. Drat .... Nano the config file and try again. No Joy.

OK ... install it all again (good thing the install goes so fast). 
Go into web admin and use its Network control panel to try the same thing ... 
well at least the results are consistent! I am back to ding a fresh install again.

I have been through this a few times. 
Is there something I am missing ??

-----------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

iface eth1 inet static
        address 192.168.1.111
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

# we will be back here for bridging later.
------------------
# sudo /etc/init.d/networking restart

While I am asking stupid questions:
  1) Where do I put in the DNS server address ?

  2) Is there anyway to remove the virtual switch for KVM
     My DSL router gets very upset when sees another 
     router behind it. It turns that router's address space 
     into a DMZ and sends all Internet trafic to it.
     (another device that is WAY TOO "user friendly").

  3) Has anyone built a Ubuntu package of Redhat's 
     virtual Machine Manager (release 0.6.1) ?

  4) The ubuntu server install has a text mode partition 
     program with an excelent user interface. I am guessing
     (hoping) that I can install and use this program from
      a SSH termial. Anyone want to tell me what ti is ???

OK ... time for bed and a fresh start tomorow night.


cheers,

lewis

---

### Post by windependence on 2009-02-17
You are still in "Windoze Mode".

You will do a  lot of Googling but it will be well worth it in the end. Hang in there. I applaud you for trying to use the server edition to cut you teeth on, but be careful you don't bite off too much.

First off, to install nano:

```
apt-get install nano
```

then just type 

```
sudo nano /path/to/filename
```

to edit your file.

You don't ever need ftp on a Unix box, use scp or wget. There are others as well.

Your interface setup looks fine. BTW, reinstalling a hundred times is so.....Windoze. You could have easily fixed your setup with a bit of googling. You probably didn't restart the network. Even taking the interfaces down and back up probably would have fixed it.  Rebooting or re-installing is rarely necessary in Linux. Trash your router BTW. They are cheap, and if you can't turn off "features" you don't want, why have it? 

DNS is set in your /etc/resolv.conf file. Note there is no 'e' in resolv. So,

sudo nano /etc/resolv.conf

Make your changes and then do <ctl> <o> and hit return to save the changes. You can only have three DNS servers in the file. Well, you can have more but they won't be used. 

As far as the VM is concerned, I don't use KVM so maybe someone can help you. You don't want to remove the bridging for KVM or that will really screw things up. I use VMware either the free server version or preferably ESXi (also free). the tools to manage it are free so no need to build your own. KVM has no admin tool? I gotta look that up now, I'm curious.

As far as partitioning, gee, I dunno, I always do that before my install but there are tons of cli tools out there. fdisk is one of them as well as parted.

Let us know how you make out.......and next time, just ask here first and we can tell you how to do it the Linux way. :)

-Tim

---

### Post by lewtwo on 2009-02-18
Thanks for the reply .. Actually I also run a HPUX box but there is very little resemblance between HPUX and Linux ... except for vi and I do not use it there.

Nano comes installed on the srv version by the way.

I do not want to trash the network because I want a flat network. There is absolutely no reason to have multiple IP range with less than a dozen devices (both real and virtual) on the LAN. Nating in this case just adds an unecesarry layer of complication.

The reason to do a reinstall is its takes less time to get back to known state. The install takes less than 10 minutes.

There is a trick to setting up a static IP on the server install.
Leave the network cable unplugged. It will then offer to allow you to configure the IP manually.

---


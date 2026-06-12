---
title: "access to headless virtualbox guest via rdp"
date: 2012-04-23
forum: Virtualisation
---

### Post by sean abbott on 2012-04-23
Hello,

I'm trying to set up an environment where I can have  headless guests running to host selenium tests, but that I can reach  into with a remote desktop/rdp.  The guests must be able to talk to each  other for selenium grid, they must be able to talk to the host (where  I'll launch the selenium tests from), and they must be able to see  outside the virtual network (because the website they're testing against  is hosted elsewhere).

My current setup:

Two ubuntu 12.04 Server guests.

Host:   ubuntu 10.04, corporate lockdowns (firewall), domain user (having  trouble adding my ldap use to the local vboxusers group) running  virtualbox 4.1.12 (not ose)

Guest 1 (Hub):  
  Network Adaptor 1:  Host-only, vboxnet0.  
  Network Adaptor 2:  NAT
  Had to put the first network adaptor as the internal network in order to get selenium to bind to it properly.
Guest 2 (htmlunit node):  
  network adaptor 1:  NAT
  network adaptor 2:  Host only, vboxnet0

These  work. I'm able to start my services via SSH, launch and run selenium.   Now, i'm trying to add a full ubuntu desktop guest (and, if ever  successful, add a windows guest as well).
Guest 3 (ubuntu gui browser node):
  nic 1:  host only, vboxnet0
  nic 2: NAT
Installed fine, guest additions installed fine.  HOWEVER.

1)   I can't figure out how to connect to the Remote Desktop of the guest.   Display shows Remote Desktop start, port 3389.  However, I can't  connect with  ubuntu's Terminal Server Client or with ubuntu Remote  Desktop Viewer.  I've tried all the options.  So.  
2)  Inside the  guest, I started remote desktop sharing.  After doing this, I was able  to connect using remote desktop viewer using VNC.  However, when I  restarted the guest using vboxheadless, this no longer works.   Obviously, as I'm using vboxheadless, the initial user isn't logged  in...do I have to configure auto-login?  (I'd rather not)

What's  the best way to move forward?  How I can I (usually) leave this guest  running the background, but be able to connect to a remote desktop for  it so I can see my selenium tests run sometimes?

Thanks!

---

### Post by cmont899 on 2012-04-23
Try using the hosts's VNC server instead of running VNC from the guest, try starting the VM with the following command:

VBoxHeadless --vnc --vncport <port> --vncpass <pw> --startvm <name|uuid>

then you can connect with the following command:

vncviewer localhost:<port>

When testing locally I was able to reboot with:

VBoxManage controlvm centos reset

Afterwards I was still able to connect via VNC viewer.

---

### Post by sean abbott on 2012-04-23
My version of vboxheadless doesn't include those options.  (4.1.12):

Oracle VM VirtualBox Headless Interface 4.1.12
(C) 2008-2012 Oracle Corporation
All rights reserved.

Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   -v, -vrde, --vrde on|off|config       Enable (default) or disable the VRDE
                                         server or don't change the setting
   -e, -vrdeproperty, --vrdeproperty <name=[value]> Set a VRDE property:
                                         "TCP/Ports" - comma-separated list of ports
                                         the VRDE server can bind to. Use a dash between
                                         two port numbers to specify a range
                                         "TCP/Address" - interface IP the VRDE server
                                         will bind to
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension

I tried (vbh is an alias for VBoxHeadless): 
vbh --vnc --vncport 5901 --vncpass ubuntu --startvm ubuntu_1204_selnode_base

just in case it was undocumented and
vbh -vdre on --vrdeproperty TCP/Ports=5900 --vrdeproperty TCP/Address=192.168.56.104 --startvm ubuntu_1204_selnode_base,

that starts the machine.  However....
vncviewer localhost::5900
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

same for vncviewer localhost:5900

netstat -an does not show the host listening on 5900.  

However...I'm not a member of the vboxusers group, because my user is an ldapuser and I haven't figure out how to add an ldap user to a local group...  would that prevent this from getting set up correctly?

---

### Post by sean abbott on 2012-04-24
Ok, so the issue was you need Oracle's proprietary extensions installed (or someone else's extension installed) to make this work.  

Also, don't have screwed with your vrde TCP/Address setting, or even after installing the extension, you'll be unable to start the vrde server.

Seems like someone ought to write an open source extension to get this done.  

Also, I couldn't get the 10.04 included RDP viewer to connect to a different port than 3390, so I had t install remmina, which works great.

---


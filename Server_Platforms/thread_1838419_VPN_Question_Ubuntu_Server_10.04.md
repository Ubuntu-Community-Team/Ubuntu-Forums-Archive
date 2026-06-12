---
title: "VPN Question: Ubuntu Server 10.04"
date: 2011-09-03
forum: Server Platforms
---

### Post by frotzed on 2011-09-03
I've been running my own home server for several months now.  It's using Ubuntu Server 10.04 and I'm using Webmin for some of the more mundane tasks.

I'm fully educated on _what_ a VPN is.  And I'm fully able to _connect_ to a remote server via VPN.  My company runs a MS Exchange server and I can connect to it via VPN easily enough.   I've done many many Google searches, but there's a hole in my knowledge, and I'm hoping for a shove in the right direction.

What is the process to VPN into my home server?  I have a static IP with DynDns, so do I just create a user account on the Server and VPN into it via the Public IP and put in the user name and password?  Is it that simple?

Or, is there something I have to set up on the Server to allow VPN connections?

---

### Post by papibe on 2011-09-03
As far as I know, there are two options: pptpd or OpenVPN. There are plenty of help docs on the last one: [Overview]("https://help.ubuntu.com/community/OpenVPN"), [VPNServer]("https://help.ubuntu.com/community/VPNServer/"), [VPNClient]("https://help.ubuntu.com/community/VPNClient"), and [Installation]("https://help.ubuntu.com/10.04/serverguide/C/openvpn.html"). This is what I found for pptpd: [Gaming_VPN_Using_PPTPD]("https://help.ubuntu.com/community/Gaming_VPN_Using_PPTPD"), and [Setup a ubuntu vpn server]("http://ariejan.net/2010/10/11/setup-a-ubuntu-vpn-server/").

Hope that helps.

As a personal note, I don't use VPN to connect to my home network. OpenSSH provides all that I need. To connect to the server I use the ssh client. To access my files I use sftp (command line and Nautilus from Ubuntu, and WinSCP from Windows).

When I really need to do some work "as if I were connected to my network", I use ssh tunneling. It works great for applications that can handle socks proxies, like Firefox, Thunderbird, and JDownloader.

Just some thoughts,
Regards.

---

### Post by frotzed on 2011-09-03
That was definitely the shove in the right direction I needed and I appreciate it.  I've been SSH-ing into my server remotely just fine with terminal or Putty (depending on the OS being used at the time).  I'm just trying to get my head around as many aspects of running a Linux server as I possibly can.

---

### Post by SeijiSensei on 2011-09-03
SSH tunnelling is one approach; specifically [tunnelling X]("http://answers.oreilly.com/topic/269-how-to-tunnel-x-over-ssh/") is another.  If you connect with "ssh -X user@host", you can run applications on the remote machine but have them display on your local machine.  If you run "firefox &" from the command prompt after logging in with "ssh -X", you'll see Firefox pop up on your screen.  The application runs remotely; only the display window and keyboard and mouse actions are sent over the ssh connection.  Type "man ssh" at a command prompt to see more documentation.

---

### Post by kgatan on 2011-09-03
Note that there are two diffrent versions of Open VPN. One which is totally free and open and one that only allows 2 concurent connections free. 

The last onr has more features by default and is easier to setup.

---


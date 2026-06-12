---
title: "VNC Server service which will auto-start on boot"
date: 2015-05-22
forum: Server Platforms
---

### Post by gobstopper on 2015-05-22
I would class myself as a "familiar dabbler" having run a host of Debian/Ubuntu-based distributions over the years, but am happy to admit that I only know enough to get by.

My current requirement is to set up a machine running Plex and as the machine in question will be headless would like to be able to remotely access it using SSH and also VNC. As I would like the machine to be running a relatively lightweight distro I have previously looked at Mint-based distros (such as Peppermint) but have been restricted by the fact that they don't support in-line updates.

So I have decided to give Lubuntu 15.04 a try, knowing that it will provide me with the means of easily keeping it up to date. However, I have established that 15.04 has introduced a new method of running services and it would seem that all searches to find out a method of installing and running VNC server as a service that auto-starts at boot appear to pre-date this new mechanism.

Is anyone able to provide a walk through which will allow me to achieve this. I know there are a number of VNC server implementations available (x11VNC, tightvnc, etc...) and I'm not particularly worried about which implementation to use. All I would like to ensure is that the it can be run as a service on the machine without needing to physically log into it and manually start the service before I am able to access it remotely. 

Many thanks in advance.

---

### Post by bashiergui on 2015-05-24
I would recommend against VNC if you're accessing it over the internet. VNC is not encrypted so it can be intercepted by anyone sniffing traffic. VNC can be forced over ssh. But there's no reason to install a GUI on your remote server which would make ssh access sufficient.

There are stickies in the security forum that cover important points to consider before using VNC.

---

### Post by Elfy on 2015-05-24
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2015-05-24
If you do feel compelled to use VNC, then use OpenVPN or SSH to create an encrypted tunnel and route the VNC traffic through that.  I find [static-key OpenVPN tunnels]("http://openvpn.net/static.html") the easiest solution in most cases.  They are especially helpful if the target machine is behind a firewall.  You can set up OpenVPN as a client on that machine, and it will make the connection through the firewall when the machine boots up.

---

### Post by gobstopper on 2015-05-25
> **bashiergui said:**
> I would recommend against VNC if you're accessing it over the internet. VNC is not encrypted so it can be intercepted by anyone sniffing traffic. VNC can be forced over ssh. But there's no reason to install a GUI on your remote server which would make ssh access sufficient.

There are stickies in the security forum that cover important points to consider before using VNC.

Thanks for the reply, you make some valid points.

In this instance all access to the machine in question would be 99% within my own network. I have SSL-VPN remote access to my should I wish to access the machine from the outside world and certainly wouldn't consider using native VNC over the internet.

My decision to not use a server-derived version can be attributed to my "familar dabbler" description. I do have some experience with CLI-based environments (my general exposure to IT *long* pre-dates GUI-based operating systems), but I've found it a little easier to address Linux issues when I've had a GUI to call upon. I can probably count on the fingers of one hand the number of times I have needed to access the Plex server which I am planning to re-build, but being able to do so using VNC has made the process a little more comfortable. When I find I am able to access the Plex GUI on the local host it normally confirms that any problem I am experiencing with it can be attributed to fat-finger syndrome when trying to access the same on any other machine.

Of course, if there are any other reliable mechanisms which I could use and which can be configured to run at boot time I'd be more than happy to learn of them.

---


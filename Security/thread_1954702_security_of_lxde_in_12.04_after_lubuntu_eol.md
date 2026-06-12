---
title: "security of lxde in 12.04 after lubuntu eol"
date: 2012-04-08
forum: Security
---

### Post by sudodus on 2012-04-08
What exactly does it mean, that Lubuntu does not have LTS status? What is the difference in support for the following cases for version 12.04, Precise Pangolin?
 
 1. install from Lubuntu iso file 
 2a. install from Xubuntu iso file and into that installing lubuntu-desktop
 2b. install from Ubuntu iso file and into that installing lubuntu-desktop
 3a. install from Xubuntu iso file and into that installing LXDE
 3b. install from Ubuntu iso file and into that installing LXDE

In other words: It would be possible to get 'near-lubuntu functionality' for three or five years. But what about the security? The LXDE packages are part of the Ubuntu repository system, but will the support stop at the end of life of Lubuntu? And how dangerous would it be?

This issue is particularly important for some old CPUs without pae (for example in IBM Thinkpad T41) because 12.04 will be the last Ubuntu version with non-pae kernel.

---

### Post by jerrylamos on 2012-04-08
Just for jollies I took a lubuntu 3.2.0-22 and did apt-get install ubuntu-desktop on Thinkpad T40 which has no pae flag.

After a while and over a GB it worked.  Lubuntu install was 2 GB it's now 3.3 GB.  I can log on and get lubuntu, lubuntu-desktop, ubuntu (no -3D), ubuntu-2D, openbox, GNOME/openbox as I remember.

Kernel started out as generic and stayed that way, no -pae in sight.

On that pc, my preference is lubuntu.  I'm on a 3.3 GHz Celeron which will run -3D but I run it as -2D since with fuzzy foggy borders and images and vaguely see through windows I think I've lost my reading glasses and get eye strain.

Jerry

---

### Post by WasMeHere on 2012-04-09
> **sudodus said:**
> 
 3b. install from Ubuntu iso file and into that installing LXDE

Hi everybody interested in security for servers!

What implications are there for someone who is not primarily interested in Lubuntu, but has an ubuntu-server and runs LXDE for convenience (instead of the CLI)? Will LXDE get security updates all five years of LTS? I think it should, because it is available from the repos without any reference to Lubuntu.

Having fun finding out :-)
Olle

---

### Post by 2F4U on 2012-04-09
Well, a lot of things are available from the repositories, but not everything is supported for the extended period of 5 years. Just because you can install it on a server doesn't mean it gets support over the whole time. It seems to be a bit difficult to determine what is a server package and what is not, but at least the packages available on the server install cd are server packages.

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

---

### Post by sudodus on 2012-04-09
> **2F4U said:**
> Well, a lot of things are available from the repositories, but not everything is supported for the extended period of 5 years. Just because you can install it on a server doesn't mean it gets support over the whole time. It seems to be a bit difficult to determine what is a server package and what is not, but at least the packages available on the server install cd are server packages.

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)
Thanks 2F4U :KS

From the ServerFaq:
> Can I add a "graphical user interface" (GUI) to a server?

Whilst we don't recommend running a GUI on a server for security and performance reasons, yes you can. Depending on what window manager you wish to use you can install the X Server and the window manager via apt-get. For details see the ServerGUI page.

> What packages and repositories are maintained (supported)?

Not all packages in the main repository are maintained (supported) equally in an LTS release: Server packages are maintained for 5 years, and all packages that are part of the the seeds "server-ship" or "supported-common" are supported for five years.
 
For regular releases, all the packages in main are maintained for 18 months. 

Packages in all other repositories (universe, multiverse, etc) are not officially maintained but may be getting some support from the community or an ISV. Be aware that apt does not check if a package is maintained (supported) or not, you have to do that on your own. 

For more info: 
To check out the seed, see germinate's output at: [http://people.ubuntu.com/~ubuntu-archive/germinate-output/](http://people.ubuntu.com/~ubuntu-archive/germinate-output/) 
The ubuntu-maintenance-check script allows to check the maintenance cycle of each package installed on a server. 
More details on how seeds are managed in Ubuntu is available at [https://wiki.ubuntu.com/SeedManagement](https://wiki.ubuntu.com/SeedManagement) 

What happens if I install packages that are not supported? Are there security patches for five years for those packages also?

If you install packages that are not supported, you are on your own. No security update is guaranteed to be provided for unsupported packages or bug fixes.

---

### Post by WasMeHere on 2012-04-09
> **2F4U said:**
> Well, a lot of things are available from the repositories, but not everything is supported for the extended period of 5 years. Just because you can install it on a server doesn't mean it gets support over the whole time. It seems to be a bit difficult to determine what is a server package and what is not, but at least the packages available on the server install cd are server packages.

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)
Conclusion:

The LXDE package gets security updates for 18 months. After that it should not be used, particularly not in a server.

---

### Post by bodhi.zazen on 2012-04-09
> **Olle Wiklund said:**
> Conclusion:

The LXDE package gets security updates for 18 months. After that it should not be used, particularly not in a server.

I personally would not use X at all on a server, it is completely unnecessary.

This thread was posted in the security section, so as such I am going to tell you to learn to manage your server properly.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

The guide for 12.04 will be out soon enough.

---

### Post by WasMeHere on 2012-04-09
> **bodhi.zazen said:**
> I personally would not use X at all on a server, it is completely unnecessary.

This thread was posted in the security section, so as such I am going to tell you to learn to manage your server properly.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

The guide for 12.04 will be out soon enough.
Thank you for the clear directive about server management :KS

What about the desktop at home, that is also an ssh- and samba-server in the LAN? If there is no [authorized] access from outside the router firewall, what is your opinion about that? Would you strongly recommend a dedicated server (for example an old computer)? I ask because many people, including me, use the 'main desktop' as a LAN server for files and sometimes for printers and scanners too ;-)

---

### Post by bodhi.zazen on 2012-04-09
> **Olle Wiklund said:**
> Thank you for the clear directive about server management :KS

What about the desktop at home, that is also an ssh- and samba-server in the LAN? If there is no [authorized] access from outside the router firewall, what is your opinion about that? Would you strongly recommend a dedicated server (for example an old computer)? I ask because many people, including me, use the 'main desktop' as a LAN server for files and sometimes for printers and scanners too ;-)

SSH - You need to secure ssh , personally I advise you use keys and disable password authentication.

File servers / samba - depends on your paranoia. If you are behind a firewall (router) you are probably fine.

For any servers I want to keep on my LAN only, I configure the sever to listen only on a private IP (Listen 192.168.0.100:80) , use iptables (sudo iptables -A INPUT -p tcp --dport 80 -s 192.168.0.0/16 -j ACCEPT )

Personally , I use old boxes as dedicated servers , and I do not use X on servers. 

If I do not have the hardware, I isolate them from the desktop with virtualization (KVM , openvz, and LXC).

---

### Post by WasMeHere on 2012-04-09
Thanks again bodhi.zazen,
Having fun finding out :-)
Olle

---

### Post by sudodus on 2012-04-09
> **Olle Wiklund said:**
> Thanks again bodhi.zazen,
Having fun finding out :-)
Olle
+1
I'm reading and learning :-)

---

### Post by bodhi.zazen on 2012-04-09
> **Olle Wiklund said:**
> Thanks again bodhi.zazen,
Having fun finding out :-)
Olle

No problem , good luck.

For what it is worth, most people use the term "servers" for computers, physical or virtual, that are dedicated to performing services (htp, ssh, nfs, etc).

Desktops are for desktop activity (graphical interface, email, web browsing, etc).

When you install a server package on a Desktop , it is generally still called a desktop as long as you are using it for graphical tasks (email, web browsing, games).

The servers are also called "services"

---


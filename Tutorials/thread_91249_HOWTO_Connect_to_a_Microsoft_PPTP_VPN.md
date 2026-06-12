---
title: "HOWTO: Connect to a Microsoft PPTP VPN"
date: 2005-11-16
forum: Tutorials
---

### Post by endersshadow on 2005-11-16
This process has been made MUCH easier in Edgy and Feisty.  I just never updated this...and I'm sorry.  In order for legacy support, I'm leaving up Dapper/Breezy/Hoary instructions.

**Feisty/Edgy x86**

You will need NetworkManager installed:
```
sudo apt-get install network-manager-gnome network-manager-pptp
```

Then, a network icon will appear in your notification area.  Select it, and then select VPN Connections > Configure VPN.  Add your VPN to the list, and then in the terminal do the following:

```
sudo NetworkManager restart
```

Click the icon again, and go to VPN Connections and then select your VPN.  Voila. You're connected!

**Feisty/Edgy AMD64** (thanks go to nyvalbant)
Grab the AMD64 Packages from [this page](http://sourceforge.net/project/showfiles.php?group_id=33063&package_id=121786).

Convert and install them using this command:
```
sudo alien filename.rpm
sudo dpkg -i filename.deb
```

Next, install pptpconfig:
```
sudo apt-get install pptpconfig
```

You may not be able to connect using pptpconfig directly, but you can create your profile in it and connect using:
```
pon <profile name>
```
(give that a minute or so to connect; check ifconfig periodically for a ppp0 entry)

Finally, after you have a ppp0 network, you may need to fix your routing table using something like:
```
sudo route add -net 11.22.0.0 netmask 255.255.0.0 dev ppp0
```
(substitute 11.22.0.0 for your network)

**Dapper/Breezy/Hoary**
After much searching for how to connect to a plain old PPTP VPN, I finally figured out how to do it, and since there's no guide on here that doesn't relate to the Cisco client, I figured I'd post one.  The source of this information is at the bottom of the post.  Here goes:

1. First, you need to install the pptp-client for Linux.  Open up the terminal and type in:

```
sudo apt-get install pptp-linux
```

2. Next, you will need to add a source to your sources.list file.  Here's how.  
Run this command.

```
sudo gedit /etc/apt/sources.list
```

When the window pops up (gedit), append the following lines to the end of the file:

```
# James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./
```

Save it and close gedit.

3. Run these commands in the terminal:

```
sudo apt-get update
sudo apt-get install pptpconfig
```

4. To run pptpconfig, simply use this command in the terminal:

```
sudo pptpconfig
```

**NOTE: You *must* run pptpconfig as root, otherwise, it will not work.

5. Enter in the info for your VPN to the GUI, click "Add," select the server you just added by clicking on it, and then hit "Start."  Make sure that your options are set, as well.  If you are unsure of what options your VPN needs, contact your system administrator.

For a more complete guide, check out this site:
[http://pptpclient.sourceforge.net/howto-debian.phtml#install](http://pptpclient.sourceforge.net/howto-debian.phtml#install)

---

### Post by WetWilly on 2005-11-19
[http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp](http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp)

---

### Post by arnieboy on 2005-11-19
[QUOTE=WetWilly][http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp](http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp)[/QUOTE]
yes but thats for hoary.. and its a good thing that this has been ported to the breezy forums (even though the instructions are identical). good job.

---

### Post by WetWilly on 2005-11-20
[QUOTE=arnieboy]yes but thats for hoary.. and its a good thing that this has been ported to the breezy forums (even though the instructions are identical). good job.[/QUOTE]


I wrote is cuz there is more info in that post e.g. How to start it without using terminal and make a shortcut using gksudo.

---

### Post by jmooney on 2005-11-27
OK, installed ptppconfig and it's telling me that I have successfully connected to my VPN network at work.

Now what?   How do I browse this network?  I've tried entering various addresses into Nautilus and Firefox but it isn't working.  Assuming I have all the address and network names right, can't I just mount this as a network location?  Say by selecting "Places/Connect to Server..."?

My VPN is running, how do I browse the remote network?

Thanks,

Joe

---

### Post by WetWilly on 2005-11-27
Joe, under the routing tab I suggest that you use the "Client to LAN" Routing Style so only the necessary traffic go via the VPN.

Then there is the "Routes To Be Added Via Tunnel".

So click on "Edit Network Routes.." and add the network that u want to connect to using the tunnel.

For example if its a standard 192.168.1. net then u write

Network: 192.168.1.0/24
Name: Whatever

Then u press update and u are good to go.

---

### Post by jmooney on 2005-11-27
[QUOTE=WetWilly]Joe, under the routing tab I suggest that you use the "Client to LAN" Routing Style so only the necessary traffic go via the VPN.

Then there is the "Routes To Be Added Via Tunnel".

So click on "Edit Network Routes.." and add the network that u want to connect to using the tunnel.

For example if its a standard 192.168.1. net then u write

Network: 192.168.1.0/24
Name: Whatever

Then u press update and u are good to go.[/QUOTE]


OK, I've done that, I still have no idea how to browse files on that network.

I've got in working in windowsXP.  For that OS, under START-RUN... I type in a network location {timcont09.timco.aero}, once I do that, it asks for a username and password, then Windows explorer appears with all the files and folders I was looking for.

What is the equivalent for Ubuntu?  How do I do that using Nautilus, or Firefox, of gftp, or whatever?


Thanks,

Joe

---

### Post by endersshadow on 2005-11-28
You're connected.  Have you tried just opening up Firefox?  PPTP has a username and password field in it where you specify the server.

---

### Post by jmooney on 2005-11-28
[QUOTE=endersshadow]You're connected.  Have you tried just opening up Firefox?  PPTP has a username and password field in it where you specify the server.[/QUOTE]

Yes, I tried entering the vpn address {vpn2.timco.aero}, the DNS numbers I got from the Debug window of PPTPConfig, the actual server address {timcont09.timco.aero},  I've also tried {vpn2.timco.aero/timcont09.timco.aero} The closest I get to a hit is something like a "Firewall - Forbidden" message when I enter one of the DNS numbers.

Has anybody here successfully set up a VPN tunnel to thier office and actually viewed files on their work network?  Could one of you explain how you did it?

If it helps, I also have the Firestarter firewall program installed.  It originally blocked the connection until I allowed traffic from the "GNS" address that the work network was trying to use.

I can't believe there is not documentation on this.  Why provide directions on how to set up a VPN tunnel and not provide directions on how to browse the network on the other side?:???:

---

### Post by reuben on 2005-11-28
If anybody has problems connecting, and are running Firestarter, try running GuardDog instead. Open PPTP and VPN in the internet zone.

---

### Post by chiefofthejojos on 2005-11-29
I am VERY pleased with this program!  It's so nice to finally have my home desktop connecting to the VPN!  One question:
I set it up so that it starts tunneling as soon as pptpconfig is opened.  Can anyone think of a good way to start tunneling on startup of the computer?
That would be the icing on the cake.

---

### Post by chiefofthejojos on 2005-11-30
There's a very nice tutorial at [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml) that helped me get set up to automatically start tunneling and add routes when my machine starts up.  The howto is geard toward debian, but it seems to directly translate to ubuntu.  Since I already created a tunnel using the gui it was mostly done for me.  In order to connect to the vpn at startup all I had to do was add the following to the /etc/network/interfaces file:
auto ppp0
iface ppp0 inet ppp
        provider myprovider
Where ppp0 is the name of the network interface (like eth0) and myprovider is the name created using pptpconfig to represent this connection.

However, adding routes to enable me to see all the computers in the remote network proved more difficult.  I tried adding "route add" statements to the /etc/ppp/ip-up.d/myprovider file, but that wasn't working.  "run-parts /etc/ppp/ip-up.d" returned:
run-parts: failed to exec /etc/ppp/ip-up.d/myprovider: Exec format error
run-parts: /etc/ppp/ip-up.d/myprovider exited with return code 1
So, I put the "route add" statements directly into the /etc/ppp/ip-up file for now, and it works great.  If anyone has any ideas what might be causing this problem, please suggest them.  Oh, the contents of my myprovider file:
#!/bin/sh
route add ...
route add ...
Thanks!

---

### Post by ubuntunooob on 2005-12-26
This is awesome.  Major barrier to me converting my home PC.  Only other problem for me - how to specify an IP address for the connection?  Under Windows, I would specify an IP address under the tcp/ip setttings.  I don't see that option here.  Basically, VPN server assigns IP addy via DHCP.  When I'm in the office, trying to connect back home, I want to be able to know what my VPN ip address is, so I can always map to it or tsc (vnc) in back home.  Any ideas?

---

### Post by Balachmar on 2006-01-03
I have tried connecting with vpnc, but that doesn't seem to work. Now I'm trying this, and it does seem to connect, but it creates a network loop or something. And it is sending bytes like crazy, and my processor is loaded heavily. This is the route table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.155.14.99   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

And it breaks after a minute or so.
What do I do wrong?

---

### Post by chiefofthejojos on 2006-01-03
I'm not sure, but that first line looks kind of funky, panticularly the part where the genmask is 255.255.255.255.  I think it should be 255.255.255.0.  Is that a manually added route or did the gui add that?[U]
[/U]

---

### Post by chiefofthejojos on 2006-01-03
[quote=jmooney]
Has anybody here successfully set up a VPN tunnel to thier office and actually viewed files on their work network? Could one of you explain how you did it?
[/quote]

Yes, I have.  Simply open nautilus and hit ctrl+L.  Type in smb:// followed by the **full domain name** or ip address of any machine on the vpn and press enter.  A little dialog should pop up asking for your username/domain name and password.  Fill these in correctly and your golden!

---

### Post by Balachmar on 2006-01-03
[QUOTE=chiefofthejojos]I'm not sure, but that first line looks kind of funky, panticularly the part where the genmask is 255.255.255.255.  I think it should be 255.255.255.0.  Is that a manually added route or did the gui add that?[U]
[/U][/QUOTE]
I guess it is something the GUI added, since I didn't do anything with the route.
Also when I quit the gui it looks like this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by Balachmar on 2006-01-07
Anyone?

---

### Post by chiefofthejojos on 2006-01-07
I'm sorry, I really don't know why it would do that, but maybe it would help if I offered my routes for comparison.  When the tunneling has started, my routing table has three new routes.  I added a route for 10.0.0.0/8 using the gui.  You may want to do the same.
<private>   192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
10.1.0.115      *               255.255.255.255 UH    0      0        0 ppp0
10.0.0.0         *               255.0.0.0            U     0      0        0 ppp0

this isn't my whole routing table, just the routes created by pptp.
I see a lot of differences in the top line there, unfortunately I have no idea why it is different.  I think the second and third lines are a result of the route I added (10.0.0.0/8).  This route gives me the ability to reference all of the computers on the vpn by their local ip because they are all on the same 10.0.0.0 subnet.
Good luck.

---

### Post by Bone Down on 2006-01-08
First off thanks for this post, I have utilized twice now on two different installs.
My situation is this, I am able to connect (at least it says I am connected), but I am unable to hit my works secure intranet site.
I am unable to check my emails.
I am unable to surf the inet period.

Following is a log from pptpconfig:
pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.2 2004/06/19 08:57:15
# pppd --version
pppd version 2.4.3
# uname -a
Linux DC-Comics 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686 GNU/Linux
# grep mppe /proc/modules
# modinfo ppp_mppe
Array
(
    [name] => kwevpn
    [server] => xxx.xxx.xxx.xxx
    [domain] => 
    [username] => login
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1
pptpconfig: debug information dump ends, 
Cannot determine ethernet address for proxy ARP
local  IP address xxx.xxx.xxx.xxx
remote IP address xxx.xxx.xxx.xxx
primary   DNS address xxx.xxx.xxx.xxx
secondary DNS address xxx.xxx.xxx.xxx
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1
pptpconfig: pppd process exit status 0 (started)
ip route add xxx.xxx.xxx.xxx via 192.168.99.99 dev eth1  src 192.168.99.105
RTNETLINK answers: File exists

pptpconfig: command failed, exit code 2
pptpconfig: routes added to remote networks
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.99.0    0.0.0.0         255.255.255.128 U     0      0        0 eth1
0.0.0.0         192.168.99.99   0.0.0.0         UG    0      0        0 eth1

Please point me into the correct direction so that I can at least get my work email to function.

Thanks in advance for your guidence and support.

BD

---

### Post by Bone Down on 2006-01-08
I have tried the many different configurations within pptpconfig and the only one that appears to connect is the one listed above.
I can't figure out how to stop this thing once it is started, without rebooting, in order to do more research on the subject.

I work for a large global company, and the network admins do not have time to assist with this as they are swamped with other issues and have basically told me that it is not support software and they reccomend that I stay with the windows setup.

Dual boot is a hassle, if I can not get this pptp to work then I fear I will have to bag ubuntu (linux) for a while.

I have spent on this stupid pptp problem now a total of 63 hours (21 hours alone out of the last 28 hours)(19 straight yesterday).

Here is the kick in the pants, this is the only thing keeping me from dropping windows, it is like the switch to cut power to windows is just one foot out of reach and no matter what angle I try I can not reach it.

---

### Post by chiefofthejojos on 2006-01-08
I really wish I could help more, but we have already passed the extent of my knowledge on the subject.  Maybe someone who knows more could jump in and help?

---

### Post by TheOrangeRider on 2006-01-10
Sorry, I lack the knowledge to help out Bone Down, but I was hoping that someone out there could help me with my own connection problem. I try to connect to company's VPN, but it fails and gives me this information in pptpconfig: 

```

rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
Disabling 40-bit MPPE; MS-CHAP LM not supported
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M -S +L -D -C>]
MPPE required but peer negotiation failed
sent [LCP TermReq id=0x3 "MPPE required but peer negotiation failed"]
```

To me it looks like my company's VPN only supports 40-bit MPPE encryption, and my Ubuntu box only supports 128-bit? And if that's the case, can anyone tell me how I can get 40-bit MPPE support?

Thanks!

---

### Post by Buenaventura Durruti on 2006-01-12
I couldn't pass installation :-(

$ sudo apt-get install pptpconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-pcntl (>= 4.3.7) but it is not installable
              Depends: php-gtk-pcntl (>= 1.0.0) but it is not installable
E: Broken packages
$

---

### Post by dholwerda on 2006-01-19
head over to the following address and download manually those files (php-pcntl php-gtk-pcntl), use sudo dpkg -i <files> to install 

[http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig)

---

### Post by TheOrangeRider on 2006-02-15
[QUOTE=Bone Down]First off thanks for this post, I have utilized twice now on two different installs.
My situation is this, I am able to connect (at least it says I am connected), but I am unable to hit my works secure intranet site.
I am unable to check my emails.
I am unable to surf the inet period.[/QUOTE]

Hi Bone,

I think I'm at about the same place that you were at this time. It looks like my DNS resolve file gets overwritten to refer to a server on my remote LAN, but I can't seem to reach any computers on that network. And I'm unable to surf the inet unless I change my /etc/resolv.conf file to what it was before I initiated the vpn. Did you ever figure out what was wrong with your setup?

Thanks,
Orange

---

### Post by amagee on 2006-04-18
[QUOTE=Buenaventura Durruti]I couldn't pass installation :-(

$ sudo apt-get install pptpconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-pcntl (>= 4.3.7) but it is not installable
              Depends: php-gtk-pcntl (>= 1.0.0) but it is not installable
E: Broken packages
$[/QUOTE]

I had this same problem when I was using the x86_64 version of ubuntu, it seems for that these packages are not available for x86_64.  I actually formatted and installed the i386 version of the operating system for that reason (and a few others, eg. wmv playing).  You could do the same, or maybe try to build those packages from source yourself.  It seems in general that x86_64 linux is more trouble than it's worth, though.

---

### Post by linuxwalleye on 2006-04-19
Thanks Endersshadow! I now have PPTP to my Watchguard firebox working. I have tried this on many distributions and have not been able to get it to work on any of them. (Xandros works but you have to pay $$) BTW-I am running Ubuntu Dapper Drake Flight 6. Way to GO!!

---

### Post by linuxwalleye on 2006-04-19
Thanks Endersshadow! I now have PPTP to my Watchguard firebox working. I have tried this on many distributions and have not been able to get it to work on any of them. (Xandros works but you have to pay $$) BTW-I am running Ubuntu Dapper Drake Flight 6. Way to GO!!

---

### Post by bensode on 2006-05-13
Best post ever 8) 

I had been searching for months back in December to get my vpn working and had given up under SuSE.  Little did I know that it was PPTP and I found this little gem recently after giving Ubuntu dist. a whirl.  Many thanks!

---

### Post by badmacktuck on 2006-05-20
hi all.

for me, being able to connect to my work vpn and use a vnc/remote desktop client is a make or break situation for my switch to ubuntu.

i followed the directions to install pptp-linux, but i get the following error every time i try and run pptpconfig:

modinfo: could not find module ppp_mppe

I turned on debug output, but i think the errors im seeing are related to the fact that it can't find that module... but i thought that was part of the kernel.

any suggestions would be much appreciated. thanks in advance for helping out an noob.

---

### Post by caravela on 2006-05-25
i Instaled a Base Server, installed all stuff needed to manual configure the tunnel.
The tunnel works and it creates a ppp0 interface but iam unable to route all traffic through the tunnel, i followed the instrucions on the site to do so, but they didn't seem to work. 
The Tunnel is used to acess the internet so all traffic must go to the ppp0 interface i think.  does anyone knows how to do it ?

---

### Post by RaZoR1394 on 2006-08-03
Is there really no solution for 64bit users?

---

### Post by Geoff2077 on 2006-08-03
Joe,
Did you ever get to bottom of how to view files - I have same problem as you - connected but cannot find out how to view files.

Geoff


> **jmooney said:**
> OK, I've done that, I still have no idea how to browse files on that network.

I've got in working in windowsXP.  For that OS, under START-RUN... I type in a network location {timcont09.timco.aero}, once I do that, it asks for a username and password, then Windows explorer appears with all the files and folders I was looking for.

What is the equivalent for Ubuntu?  How do I do that using Nautilus, or Firefox, of gftp, or whatever?


Thanks,

Joe

---

### Post by dbw on 2006-08-08
So, I got pptp-linux and pptpconfig installed.  When I tried to connect using
```
pon tunnel_name
```
I could not access the secure network.  I had to follow that command with:

```
sudo ip route replace 192.220.206.39 via 192.168.2.1 dev eth0
sudo ip route replace default dev ppp0 
```

Where 192.220.206.39 is the initial connection address.  I guess what I am saying is that I had to add routing information, and I don't think anyone has mentioned that thus far on this post.

---

### Post by MisterD on 2006-08-26
Nice tutorial, I've already made the full 100% switch at home to Ubuntu, but still want/need to get into work via PPTP+VNC, so this seemed like the way to go. I got everything installed, and created a tunnel, however, when I try to start it, I get the following error...

```

Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
Unknown MS-CHAP authentication failure: E=691 R=1 C=2E2285276B7AB3FC1FA5B802367A3732 V=3
CHAP authentication failed
Connection terminated.
pptpconfig: pppd process terminated by signal 19 (failed)
pptpconfig: SIGSTOP

```

Any ideas? TIA

Mr D

---

### Post by Geoff2077 on 2006-08-26
Joe,
Did you ever get to the bottom of how to view the folders on your server.
Cheers
Geoff

---

### Post by LCCano on 2006-09-19
> **Geoff2077 said:**
> Joe,
Did you ever get to the bottom of how to view the folders on your server.
Cheers
Geoff

Joe/Geoff

If you've got a successful pptp connection, to go Places/Connect to Server. In the dialog box set service type to Windows Share, fill in server name or IP if no DNS is in place, enter share name if you have it, username and domain.  When you click connect the dialog box goes away.  Then go to Places and you should see your network servers listed.  Or at this point you can click Places/Network Servers and open the browse window.

In pptpconfig you can specify additional dns servers, including the internal dns for your remote lan.  Just remember to include your local dns so you can resolve any local hosts and also make sure you add the remote LAN on the routing tab of the config utility.  This will allow you to use fully qualified names for the lan servers, else you must have ip addresses.  I'm stil working on figuring out how to use short names without having to edit my own hosts file.

good luck

LCCano

---

### Post by antoxa on 2006-10-03
how i connect to vpn in edgy?

---

### Post by tombott on 2006-10-18
many thanks for this info.
Got this installed and connected without any problems on Dapper.
Once I had added a few routes in for my work network i was able to VNC / RDP and connect to shares without any problems!

---

### Post by prodonjs on 2007-01-14
Well here is my issue. I'm using Kubuntu Dapper and I have everything working with PPTP config. I can connect to my VPN fine but what I want to do is use the Client to LAN setting so that I only use my VPN for connecting to the three shared network drives that I need to use.

So far I cannot figure out how to get this to work. Two of the network drives are just folders on the same IP whereas the third one resides on another machine but both IPs for the shared drives I need to map are distinct from the IP I use to VPN. I'm doing all of this to access shared stuff on my college's network from my machine here at home.

I can do this in Windows but there, I cannot figure out how to avoid sending all my traffic through the VPN tunnel rather than just the parts that I need. I can use Samba inside of Konqueror to map to any of these drives if I have the settings in PPTPConfig set to All to Tunnel, but otherwise I cannot. I am still very new to all of this Linux stuff but I am a CS undergraduate student and am really anxious to learn.

I basically just want to be able to set up mount points for these 3 network drives, map them whenever I want to connect to the VPN, synchronize data with my local data and then disconnect my VPN. Can anyone help me out?

---

### Post by TheOrangeRider on 2007-01-14
> **prodonjs said:**
> I can do this in Windows but there, I cannot figure out how to avoid sending all my traffic through the VPN tunnel rather than just the parts that I need.

For a Windows vpn, you should make sure that you have the option "Use default gateway on remote network" unchecked. I think the setting is under Properties->Networking->TCP/IP->Properties->Advanced. I believe that should make it so only traffic destined for your VPN will be routed through the tunnel.

---

### Post by prodonjs on 2007-01-14
Ok well I'll try that the next time I boot back into Windows.

Now applying that logic, how can I do the same in Kubuntu. I want to be able to use the Client to LAN setting in PPTPConfig and still access those folders?

---

### Post by TheOrangeRider on 2007-01-14
I haven't done this so if someone else is more of an expert feel free to jump in.

Have you tried the following?

> **WetWilly said:**
> Joe, under the routing tab I suggest that you use the "Client to LAN" Routing Style so only the necessary traffic go via the VPN.

Then there is the "Routes To Be Added Via Tunnel".

So click on "Edit Network Routes.." and add the network that u want to connect to using the tunnel.

For example if its a standard 192.168.1. net then u write

Network: 192.168.1.0/24
Name: Whatever

Then u press update and u are good to go.

Basically you're setting up explicit routes for prefixes so that your computer will know where to divert traffic based on the destination IP address. I've previously had problems with pptp configuring routing tables so you may have to figure out how to set them manually if WetWilly's suggestion doesn't work.

---

### Post by prodonjs on 2007-01-14
Well see here is my problem and maybe this is due to my lack of in depth networking knowledge.

One of the IPs is only a small difference from the IP I use for connecting to the VPN. Only the the last number is different. But the other two IPs are completely distinct from the VPN address. I'm not sure what that /24 refers to but I remember seeing that it meant 255.255.255.0 or xFF FF FF 00. How exactly do I take a server IP and a folder location and translate it into Route to be Added Via Tunnel.

---

### Post by TheOrangeRider on 2007-01-14
The /24 refers to a subnet mask. The 24 means that the first 24 bits of the IP address denote the subnet. So if you enter a route for 192.168.1.0/24, you're telling your computer to route any traffic that begins with "192.168.1." to be tunneled to your VPN. If you are interested in only accessing only one or two computers on your remote network you can specify them as /32 addresses. As an example, an entry with 192.168.1.130/32 will only route traffic destined to that exact destination IP address through your tunnel. So you could just make ip_address/32 entries into your routing table for the exact machines you want to reach and it should work fine.

---

### Post by vyvar on 2007-01-20
> **chiefofthejojos said:**
> 
However, adding routes to enable me to see all the computers in the remote network proved more difficult.  I tried adding "route add" statements to the /etc/ppp/ip-up.d/myprovider file, but that wasn't working.  "run-parts /etc/ppp/ip-up.d" returned:
run-parts: failed to exec /etc/ppp/ip-up.d/myprovider: Exec format error
run-parts: /etc/ppp/ip-up.d/myprovider exited with return code 1
So, I put the "route add" statements directly into the /etc/ppp/ip-up file for now, and it works great.  If anyone has any ideas what might be causing this problem, please suggest them.  Oh, the contents of my myprovider file:
#!/bin/sh
route add ...
route add ...
Thanks!

This helped me:

 # chmod +x /etc/ppp/ip-up.d/tunnel

...replace tunnel with appropriate name.

its from 
[http://pptpclient.sourceforge.net/routing.phtml](http://pptpclient.sourceforge.net/routing.phtml)

):P

---

### Post by NoJock on 2007-01-31
Badmactuck: hope you have resolved and can lead me in the right direction! I mave been trying to get this to work with to no avail and dont know much at all abought networing. This is my out put from pptp debug it would be nice if some one could direct me in the right direction??

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option: 
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>	Pass <number> to remote host as phone number
  --nolaunchpppd	Do not launch pppd, for use as a pppd pty
  --quirks <quirk>	Work around a buggy PPTP implementation
			Currently recognised values are BEZEQ_ISRAEL only
  --debug		Run in foreground (for debugging with gdb)
  --sync		Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>	Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer		Disable packet buffering and reordering completely
  --idle-wait		Time to wait before sending echo request
  --max-echo-wait		Time to wait before giving up on lack of reply
  --logstring <name>	Use <name> instead of 'anon' in syslog messages
  --localbind <addr>	Bind to specified IP address instead of wildcard
  --loglevel <level>	Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux lee-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
Array
(
    [name] => usm
    [server] => vpn.name.com
    [domain] => (hidden by pptpconfig)
    [username] => Me
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 1
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/usm)
updetach		# (from command line)
logfd 1		# (from command line)
linkname usmo		# (from /etc/ppp/peers/usm)
dump		# (from /etc/ppp/peers/usm)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name us\\me		# (from /etc/ppp/peers/usm)
remotename usm		# (from /etc/ppp/peers/usm)
		# (from /etc/ppp/options.pptp)
pty pptp vpn.name.com --nolaunchpppd 		# (from /etc/ppp/peers/usm)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam usm		# (from /etc/ppp/peers/usm)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/usm)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
		# (from /etc/ppp/peers/usm)
		# (from /etc/ppp/peers/usm)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 16
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xaca60dd0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x4a <mru 1500> <asyncmap 0xa0000> <auth chap MS> <magic 0x6a378b5e> <pcomp> <accomp>]
sent [LCP ConfNak id=0x4a <auth chap MS-v2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xaca60dd0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x4b <mru 1500> <asyncmap 0xa0000> <auth pap> <magic 0x6a378b5e> <pcomp> <accomp>]
sent [LCP ConfAck id=0x4b <mru 1500> <asyncmap 0xa0000> <auth pap> <magic 0x6a378b5e> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xaca60dd0]
sent [PAP AuthReq id=0x1 user="**\\ME" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x6a378b5e 00 00]
rcvd [PAP AuthAck id=0x1 "Login ok"]
Remote message: Login ok
PAP authentication succeeded
MPPE required, but MS-CHAP[v2] auth not performed.
sent [LCP TermReq id=0x2 "MPPE required but not available"]
rcvd [IPCP ConfReq id=0xcc <addr 10.50.11.4> <compress VJ 07 00>]
Discarded non-LCP packet when LCP not open
rcvd [LCP TermAck id=0x2]
Connection terminated.
Waiting for 1 child processes...
  script pptp vpn.name.com --nolaunchpppd , pid 10125
Script pptp vpn.name.com --nolaunchpppd  finished (pid 10125), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 10 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
 have been reading referances of tunneling but now idea if that is the probem it look slike the mppe is failing and im using ubuntu dapper drake is it in the kernel??

Thanks.

---

### Post by speedothebrief on 2007-02-13
I have two things:

first:

AMD 64 USERS!!!!
YES YOU CAN SET UP PPTP CONFIGURATIONS ON YOUR MACHINE!!!
no... it isn't nearly as easy!
I'm using AMD64 and I'm very close to having a working vpn connection.

Here is what I did so far:

download the pptp-linux stuff just forget the pptpconfig utility ever existed and use the "[HTML]<a href=http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand">configuring pptp by hand</a>[/HTML]" instructions to set up the pptp config files (it really isn't that hard, trust me).

Next, I had to change my tunnel's subnet mask from 255.255.255.255 to 255.255.255.0. I did this programatically by editing the ip-up config file ( /etc/ppp/ip-up)
I added this:
```
#set the remote server IP mask
/sbin/ifconfig ppp0 netmask 255.255.255.0
```

Then I added some stuff to resolv.conf.tail (which is appended to resolv.conf) since dhclient overwrites any user settings in resolv.conf.
/etc/resolv.conf.tail
```
search name.address.of.nameserver.com
nameserver $IP_ADDRESS_OF_NAMESERVER
```
You'll need to know the nameserver's IP address and name (i.e. 192.168.0.1 and vpn.myserver.com)

now I connect to the vpn successfully, authenticate successfully and can ping my vpn server at 192.168.0.10 successfully

I can even use smb://(ipaddress) to browse machines on the network.

Now onto my second thing:
I can't seem to get any mail. And I can't access things on the samba network by their name (only IP address). If I use mutt to get mail on the IMAP server, I can see that it get stuck trying to fetch message headers. It just shows:
```
fetching message headers... (1/41)
```
and never makes any progress.

Any Ideas? Thanks for all of the help!

---

### Post by monkeyking on 2007-03-21
I get this broken dep on feisty fawn
```

sudo apt-get install pptpconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-pcntl (>= 4.3.7) but it is not installable
              Depends: php-gtk-pcntl (>= 1.0.0) but it is not installable
E: Broken packages


```

---

### Post by shoogax12 on 2007-04-16
Thanks for the tutorial! It's simple and easy to understand. But I'm having a small problem. When I attempt to install pptconfig, it says it cannot find the package. I have followed all the instructions up to this point. I can apt-cache search this package. 

I'm running Ubuntu 6.10 with KDE. Any suggestions would be greatly appreciated. Thanks!

Here's what happens in the console:

root@laptopper:~# apt-get install pptconfig
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pptconfig

---

### Post by endersshadow on 2007-04-20
shoogax12: Sorry for the late reply.  Edgy and Feisty have a new built in way to deal with VPNs.  Try this:

```
sudo apt-get install network-manager-gnome network-manager-pptp
```

You will see a network icon pop up in your notification area.  If you click it, select VPN Connections > Configure VPN.  Add your VPN info that way, then do this in the terminal:

```
sudo killall NetworkManager
sudo NetworkManager &
```

The icon will disappear and then come back.  Click it again, select VPN Connections, and then select your VPN, and it will connect.

---

### Post by mgmiller on 2007-04-20
I am running Feisty and have followed these instructions.  They are not hard.  However, my network manager icon does not give me any VPN choices.  The only choice I get is manual configuration and there are no VPN entries in there either.  The old pptp config used to work well for me in Dapper, but I have not had VPN since I upgraded to Edgy and now Feisty.

---

### Post by endersshadow on 2007-04-21
mgmiller:

Try:

```
sudo killall NetworkManager
sudo NetworkManager &
```

Instead of restart.

---

### Post by mgmiller on 2007-04-21
Thank you for the suggestion.  Unfortunately, it does not work.  The network manager icon disappears and then comes back, but there is no change in what it displays.  There is still no VPN choice.

---

### Post by glo on 2007-04-21
I experience the same problem that mgmiller described.
After entering the command "sudo apt-get install network-manager-gnome network-manager-pptp" into the terminal, it will complain network-manager-pptp cannot be found, and once the manager is restarted no VPN option will be shown.

---

### Post by endersshadow on 2007-04-21
Oh, okay, what's your /etc/apt/sources.list look like?

---

### Post by glo on 2007-04-21
I've just burnt Feisty Fawn Live CD iso, so it should be default.

---

### Post by endersshadow on 2007-04-22
Oh, I don't believe that universe is enabled by default.  See [How to Add Extra Repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories) and make sure you enable universe and multiverse.

---

### Post by mgmiller on 2007-04-22
> I experience the same problem that mgmiller described.
After entering the command "sudo apt-get install network-manager-gnome network-manager-pptp" into the terminal, it will complain network-manager-pptp cannot be found, and once the manager is restarted no VPN option will be shown.

This really is not the same as my problem.  I do have the Universe repos enabled and network-manager-pptp did install.  It just has no effect on my network manager applet.

---

### Post by colonelk on 2007-04-23
Hi

I can install the VPN components (on vanilla Feisty) but not establish a VPN connection because our work VPN uses RSA SecurID authentication.

Any ideas on how to get a SecurID client on Feisty?

---

### Post by HunterK on 2007-04-23
I am having the same problem as these folks.  Weird!!

---

### Post by kalahari875 on 2007-04-23
I have read several other posts about the NetworkManager applet and getting the routes added. I can successfully connect to the PPTP VPN, but it does not of course add routes by default. I added the executable script below, /etc/ppp/ip-up.d/addroutes (from [http://pptpclient.sourceforge.net/routing.phtml)](http://pptpclient.sourceforge.net/routing.phtml)), but it never adds any routes. 

Has anyone gotten a PPTP connection managed via NetworkManager to add routes upon connection? If so, could you supply a complete example? The problem may be that I have no idea what the name of the tunnel is that gets passed as $PPP_IPPARAM or how to debug this. No messages get logged to /var/log/messages. :confused:   Thanks!


[INDENT]#!/bin/sh
#echo ${PPP_IPPARAM}
#if [ "${PPP_IPPARAM}" = "vpn" ]; then
   route add -net 192.168.157.0/8 dev ${IFNAME}

iptables --insert OUTPUT 1 \
   --source 0.0.0.0/0.0.0.0 \
   --destination 192.168.157.0/8 \
   --jump ACCEPT --out-interface ${IFNAME}

iptables --insert INPUT 1 \
   --source 192.168.157.0/8 \
   --destination 0.0.0.0/0.0.0.0 \
   --jump ACCEPT --in-interface ${IFNAME}

iptables --insert FORWARD 1 \
   --source 0.0.0.0/0.0.0.0 \
   --destination 192.168.157.0/8 \
   --jump ACCEPT --out-interface ${IFNAME}

iptables --insert FORWARD 1 \
   --source 192.168.157.0/8 \
   --destination 0.0.0.0/0.0.0.0 --jump ACCEPT

iptables --table nat --append POSTROUTING \
   --out-interface ${IFNAME} --jump MASQUERADE

iptables --append FORWARD --protocol tcp --tcp-flags SYN,RST SYN \
   --jump TCPMSS --clamp-mss-to-pmtu
#fi[/INDENT]

---

### Post by stavrica on 2007-04-23
> **mgmiller said:**
> Thank you for the suggestion.  Unfortunately, it does not work.  The network manager icon disappears and then comes back, but there is no change in what it displays.  There is still no VPN choice.

In layman terms, it seems that if you configure a static IP address for your workstation in Feisty, the network manager no longer offers the VPN menu within the Network Manager applet.

If you remove your interface listing from the manual configuration file, the Network Manager will again see your local NIC and also offer you the VPN options (presumably, associated with that NIC).  From what I can tell, the downside is that you'll need to get your IP address assigned to you by a DHCP server on your local network.

Here's what worked for me:
(make sure you have a DHCP service running on your local network first)

From the shell prompt,

Edit /etc/network/interfaces ( sudo vi /etc/network/interfaces )

Delete everything EXCEPT for the following two lines:

[INDENT]
auto lo
iface lo inet loopback
[/INDENT]

Save the file and reboot your machine.

Network Manager should now see your local NIC.  It will attempt to configure it using DHCP.  Once you get your address, you'll find the menus you're looking for on the Network Manager applet.  Note, however, that if you click on the "Manual configuration" option and configure your static IP address again, your VPN option will again disappear.  (which you can fix again by editing your interfaces file)

I'd call this a bug, as users shouldn't have to choose between having a static IP or using their VPN client connections.

---

### Post by Ferri on 2007-04-24
Same problem here. VPN doesn't show, apparently because I have a "Manual network configuration", i.e. a static IP.
Any workarounds? I don't really feel like reconfiguring my whole network...

---

### Post by Ferri on 2007-04-24
I'll answer myself ;) 
I've tried the most obvious workaround, the "old way" from the first post, and it works. I've just changed the source to this new one:```
deb http://quozl.linux.org.au/pptp/pptpconfig ./
```

---

### Post by getaceres on 2007-04-24
I have a strage problem. I installed and configured the network manager pptp. I have two entries in the network-manager vpn menu:

Configure VPN
Disconnect VPN (disabled)

I have configured a connection named 'VPN connection' but I don't know how to connect. In the menu there are only those two entries.

---

### Post by endersshadow on 2007-04-24
getacres: Either reboot or in the terminal run:

```
sudo NetworkManager restart
```

If your configured VPN doesn't show up, try this:

```
sudo killall NetworkManager
sudo NetworkManager &
```

---

### Post by Azalin on 2007-04-29
> **kalahari875 said:**
> I have read several other posts about the NetworkManager applet and getting the routes added. I can successfully connect to the PPTP VPN, but it does not of course add routes by default. I added the executable script below, /etc/ppp/ip-up.d/addroutes (from [http://pptpclient.sourceforge.net/routing.phtml)](http://pptpclient.sourceforge.net/routing.phtml)), but it never adds any routes. 

Has anyone gotten a PPTP connection managed via NetworkManager to add routes upon connection? If so, could you supply a complete example? The problem may be that I have no idea what the name of the tunnel is that gets passed as $PPP_IPPARAM or how to debug this. No messages get logged to /var/log/messages. :confused:   Thanks!



Would this "not adding of routes" be the cause of my problems with this network-manager-pptp plugin? I can connect to the vpn but can not ping the vpn nor can I connect to it with my terminal server client.

It would be great if I could fix this problem...

---

### Post by mwob on 2007-04-30
Hi.

I have a stupid (I hope) question about getting this working. I followeed the guide for fesity, and now that I have finished, I can see the VPN connection I created, but I can't connect. When I go to "VPN Connections", the VPN connection is there but its greyed out - I can't choose it :-(

Any ideas? I restarted my PC, still the same. I'm using an ADSL modem, but that shouldn't affect anything....

---

### Post by ksudbury on 2007-05-01
Nice work, works great! Needed a reboot after adding first VPN account tho for it to appear in the list correctly! 

FYI I am connecting to a Draytek pptp server incase anyone else is trying to find a way of doing this  :D 

Regards

---

### Post by rickr765 on 2007-05-08
Still trying to get the installation steps to work in 6.10 (Edgy). As installed "out of the box", there is no "Notification Area".  I figured out how to add one, but it's empty.

Eventually got the icon to appear using the 'killall' approach, however, the error I get is 'can't connect due to a connection error' - a message that sounds truly Microsoft-inspired.

(edit) Saw this other thread "Problems with vpn, MS-CHAP[v2] auth not performed", but it doesn't appear to be helpful. Also, the icon tends to disappear from the notification area; I don't see any other way to get to the Configure VPN dialog. The 'System - Administration - Network' dialog doesn't include any VPN information. (Why not?)

It appears this is another area of Linux which users will have to wait another couple of releases to get working properly...

---

### Post by Firex726 on 2007-05-09
Hello,

I am really new at this but I am trying to setup a VPN to my station at work.

At the terminal I ran the command:

```
 sudo apt-get install network-manager-gnome network-manager-pptp 
```

Which seemed to execute just fine, but no new network icons appeared in my notification area. 

I then checked under:

Applications -> Internet -> VPN Connection Manager (PPP Generic)

But for some reason it never executes by using the GUI, so I went to the terminal again, and did:

```
 sudo /home/isaac/Desktop/nm-ppp.desktop 
```

But get the error:

```
 sudo: ./nm-ppp.desktop: command not found 
```

Any advice on how to setup a VPN to my Windows computer at work would be very much appreciated.

################

EDIT: I am using :

Ubuntu Feisty 7.04
Gnome 2.18.1

---

### Post by mgmiller on 2007-05-10
I hadn't noticed that there was an entry in applications>internet>VPN connection manager.  When I looked at the command it is using it  is:
```
nm-vpn-properties --import-service org.freedesktop.NetworkManager.ppp_starter --import-file %f
```

It will not run from the menu, but will run in a terminal.  It allows me to set up the VPN tunnel, but not start it.  Also, if I exit it and go back, the tunnel I defined is not there.

It also produces the following error messages in the terminal:
```
** (nm-vpn-properties:21454): WARNING **: Widget show event

(nm-vpn-properties:21454): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

```

If I run it with sudo before the command, the defined tunnel is retained after restarting the GUI, but the error message changes slightly from properties:21454 to properties:22247.  
If run with gksudo the error number changes to 22411.  

There is still no way I can find to actually open the tunnel that I have defined, but at least I'm a bit closer.

---

### Post by crb on 2007-05-14
You shouldn't need to use the icon in the menu.  The next version removes it.  You should have an option on your network-manager in your notification area.

If you don't have an icon there, install nm-applet.

If you can't figure out how to work it, left click, not right click.

If you're game, try this new package: [http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/](http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/)

---

### Post by jbrice on 2007-05-16
I have followed the excellent instructions in this thread several times for getting Feisty to connect to a VPN, but without success.  VPN connections didn't connect, and although appearing in the Network Manager applet they were not shown in the list in the "Configure VPN"  dialogue box so that I could delete them

After wasting lots of time, I have discovered by trial and error what all you Linux experts probably think is blindingly obvious, that **CONNECTION NAMES MUST NOT INCLUDE SPACES** (although the Connection Manager is happy to accept them with spaces).

Would some kind person save me yet more time and tell me where I can find the config file for PPTP connections, so that I can hand delete the unwanted connections with spaces in their names.

TIA

---

### Post by crb on 2007-05-17
> **jbrice said:**
> After wasting lots of time, I have discovered by trial and error what all you Linux experts probably think is blindingly obvious, that **CONNECTION NAMES MUST NOT INCLUDE SPACES** (although the Connection Manager is happy to accept them with spaces).

Would some kind person save me yet more time and tell me where I can find the config file for PPTP connections, so that I can hand delete the unwanted connections with spaces in their names.


Erm, that's either odd, or totally wrong.  The keys are stored in gconf, and I've used (and continue to use) keys with spaces in their names.

They're stored in /system/networking/vpn_connections/.  Let me know if changing them works.

Craig (packager, but not maintainer)

---

### Post by maximk on 2007-05-17
What should I do if vpn option is absent in nm-applet menu? Left click opens one item "Manual configuration..." and the right one - only three: "Enable networking", "Connection information" (grayed) and "About"

I tried to reinstall package (gnome-network-manager) but no effect.

Please, help.

---

### Post by maximk on 2007-05-17
The issue with VPN and dhcp is described and logged here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/107070](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/107070)

---

### Post by mgmiller on 2007-05-17
I also have an entry that I can't remove that causes the whole applet to crash if I select it.  I would like to find the config file so I can edit it.  However, as you state:

> Erm, that's either odd, or totally wrong. The keys are stored in gconf, and I've used (and continue to use) keys with spaces in their names.

They're stored in /system/networking/vpn_connections/.

The path you give does not exist.  Searching for gconf found a folder in /etc, but none of the rest of your path is there.  Where is the config file?

---

### Post by crb on 2007-05-17
> **mgmiller said:**
> The path you give does not exist.  Searching for gconf found a folder in /etc, but none of the rest of your path is there.  Where is the config file?

Run gconf2-editor.

---

### Post by mgmiller on 2007-05-17
```
Run gconf2-editor
```

I tried every combination of this I could think of,  with and without sudo and they all returned the same "command not found".  What am I doing wrong?
](*,)

---

### Post by mgmiller on 2007-05-17
I finally found the path, it is:
~/.gconf/system/networking/vpn_connections

It's a hidden directory in my home directory.  There are a few files named %gconf.xml that are just empty files with nothing in them.  Are they safe to delete?  The %gconf.xml in the one correct VPN folder entry has lots of data in it, all the rest are blank.

---

### Post by crb on 2007-05-18
> **mgmiller said:**
> ```
Run gconf2-editor
```

I tried every combination of this I could think of,  with and without sudo and they all returned the same "command not found".  What am I doing wrong?
](*,)

Sorry, just gconf-editor.

Craig

---

### Post by mgmiller on 2007-05-19
ok, I can use gconf-editor.  Where are the keys for vpn?  There is no entry under system for networking.  Thank you for sticking with me through this.

---

### Post by Drachen on 2007-05-19
> **stavrica said:**
> In layman terms, it seems that if you configure a static IP address for your workstation in Feisty, the network manager no longer offers the VPN menu within the Network Manager applet.

If you remove your interface listing from the manual configuration file, the Network Manager will again see your local NIC and also offer you the VPN options (presumably, associated with that NIC).  From what I can tell, the downside is that you'll need to get your IP address assigned to you by a DHCP server on your local network.

Here's what worked for me:
(make sure you have a DHCP service running on your local network first)

From the shell prompt,

Edit /etc/network/interfaces ( sudo vi /etc/network/interfaces )

Delete everything EXCEPT for the following two lines:

[INDENT]
auto lo
iface lo inet loopback
[/INDENT]

Save the file and reboot your machine.

Network Manager should now see your local NIC.  It will attempt to configure it using DHCP.  Once you get your address, you'll find the menus you're looking for on the Network Manager applet.  Note, however, that if you click on the "Manual configuration" option and configure your static IP address again, your VPN option will again disappear.  (which you can fix again by editing your interfaces file)

I'd call this a bug, as users shouldn't have to choose between having a static IP or using their VPN client connections.


Thank you, thank you!! :)

Finally, thanks to your comment I was able to put my VPN connection to my Uni working. The problem was that in the network manager I had an static IP, so no VPN menu was showing. I deleted the static IP and puff...the VPN connection appear :guitar:

---

### Post by Raa on 2007-05-22
> **Balachmar said:**
> I have tried connecting with vpnc, but that doesn't seem to work. Now I'm trying this, and it does seem to connect, but it creates a network loop or something. And it is sending bytes like crazy, and my processor is loaded heavily. This is the route table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.155.14.99   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

And it breaks after a minute or so.
What do I do wrong?

I had the same problem too. I was reading all the posts (thanks for great ideas!) and playing with my config on Ubuntu Feisty, and produced next recomendations:

**1.** If you have dynamic IP address (DHCP, not static), and of you do not need to have the VPN tunnel started on boot, then you can play with PPTP plugin for Gnome Network Manager (see [here]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml"), follow the first chapter for Ubuntu Feisty only).
Otherwice try pptp-linux, but do not install/use pptpconfig configuration tool.

[http://pptpclient.sourceforge.net/howto-debian.phtml#install]("http://pptpclient.sourceforge.net/howto-debian.phtml#install")

If you already installed all those tools then just ignore this step.

**2.** Configure the pptp client by own hands using these simple steps, but do not start for a while.

[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand]("http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand")

**3.** Check the /etc/ppp/ip-up.d directory. If there are some files then backup and remove them. They are probably produced by another programs you tried before and make things bad.

**4.** Try the ip command in your terminal. If it does not exists then install it.

Create file /etc/ppp/ip-up.d/routing and make it executable:

```

$sudo chmod 700 /etc/ppp/ip-up.d/routing

```

Starting the pptp client may produce strange affect with bad routings, so this file should contain fixes. Write to file:

```

ip route del x.x.x.x dev ppp0
ip route replace x.x.x.x via y.y.y.y dev eth0

```

Replace x.x.x.x with a pptp server IP address you are trying t connect to, and y.y.y.y with the IP address of your default getway. If you do not have a getway then omit "via y.y.y.y". This rules will allow your pptp client to send correct packets to eth0, not to ppp0 through tunnel. And be sure your network device is really eth0, or replace it with eth1 or whatever you have. You can determine you network devices. Type ifconfig command in terminal.

**5.** Your pptp client should connect successfully now, but the VPN will not be reachable unless you setup correct routing rules for that. You can define them in your routing file or using your firewall. That's for you decision. For example, you can add the following rule to routing file to have all packets directed to the VPN:

```

ip route replace default dev ppp0

```

**6.** Try to connect you pptp client with debug output and see whether it works or not. I hope it will work :)

---

### Post by crb on 2007-05-22
> **mgmiller said:**
> ok, I can use gconf-editor.  Where are the keys for vpn?  There is no entry under system for networking.  Thank you for sticking with me through this.

There should be unless you just deleted all the files off the disk :-)

Create one if it's not there.

---

### Post by mgmiller on 2007-05-22
> 
Originally Posted by mgmiller View Post
ok, I can use gconf-editor. Where are the keys for vpn? There is no entry under system for networking. Thank you for sticking with me through this.

crb said:
There should be unless you just deleted all the files off the disk
Create one if it's not there.


These forums are amazingly useful.  This is the first time in over a year that i felt I was close to getting this working again. :p

I have not deleted anything.

Please tell me, once I run gconf, exactly where the new keys should be and what they should be.  ](*,)

Thanks again for your help.

---

### Post by ShiftyPowers on 2007-05-23
> **stavrica said:**
> In layman terms, it seems that if you configure a static IP address for your workstation in Feisty, the network manager no longer offers the VPN menu within the Network Manager applet.

If you remove your interface listing from the manual configuration file, the Network Manager will again see your local NIC and also offer you the VPN options (presumably, associated with that NIC).  From what I can tell, the downside is that you'll need to get your IP address assigned to you by a DHCP server on your local network.

Here's what worked for me:
(make sure you have a DHCP service running on your local network first)

From the shell prompt,

Edit /etc/network/interfaces ( sudo vi /etc/network/interfaces )

Delete everything EXCEPT for the following two lines:

[INDENT]
auto lo
iface lo inet loopback
[/INDENT]

Save the file and reboot your machine.

Network Manager should now see your local NIC.  It will attempt to configure it using DHCP.  Once you get your address, you'll find the menus you're looking for on the Network Manager applet.  Note, however, that if you click on the "Manual configuration" option and configure your static IP address again, your VPN option will again disappear.  (which you can fix again by editing your interfaces file)

I'd call this a bug, as users shouldn't have to choose between having a static IP or using their VPN client connections.

This is still a very annoying BUG!

---

### Post by jbrice on 2007-05-26
> **jbrice said:**
> I have followed the excellent instructions in this thread several times for getting Feisty to connect to a VPN, but without success.  VPN connections didn't connect, and although appearing in the Network Manager applet they were not shown in the list in the "Configure VPN"  dialogue box so that I could delete them

After wasting lots of time, I have discovered by trial and error what all you Linux experts probably think is  blindingly obvious, that **CONNECTION NAMES MUST NOT INCLUDE SPACES** (although the Connection Manager is happy to accept them with spaces).

Would some kind person save me yet more time and tell me where I can find the config file for PPTP connections, so that I can hand delete the unwanted connections with spaces in their names.

TIA

Following up on this, and on comments that others have successfully added VPN connection names with spaces without problem:

 - on further, testing connection names with one space show up OK in the "Configure VPN" dialogue box but those with two (or more?) spaces DO NOT - and are therefore not deletable via the conventional interface. Looks like a bug here, guys.

 -  the VPN connection config information is held in a hidden folder at /home/USER_ID/.gconf/system/networking/vpn_connections in the form of a folder for each connection currently set up. Deleting these folders seems to remove the connections (after a restart) without any negative side effects  (use at your own risk, bearing in mind I'm a Linux newbie).

---

### Post by kikkoman55 on 2007-05-26
> **stavrica said:**
> In layman terms, it seems that if you configure a static IP address for your workstation in Feisty, the network manager no longer offers the VPN menu within the Network Manager applet.

If you remove your interface listing from the manual configuration file, the Network Manager will again see your local NIC and also offer you the VPN options (presumably, associated with that NIC).  From what I can tell, the downside is that you'll need to get your IP address assigned to you by a DHCP server on your local network.

....

I'd call this a bug, as users shouldn't have to choose between having a static IP or using their VPN client connections.

This is still a bug, verified on my 7.04 install.

---

### Post by crb on 2007-05-26
Yes, and here is it's reference on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364)

Until it is fixed (probably with the upstream release of NetworkManager 0.70) there is nothing that can be done.

---

### Post by mawdryn on 2007-05-27
I think I've missed something fundamental. I'm running Feisty and followed the instructions, but it when I go to connect to the vpn by clicking on the network manager, my vpn is not listed anywhere except under 'Configure VPN'. It's created the approprate %gconf.xml file, but no files have been created in /etc/ppp/peers. 
Any help appreciated

*** Fixed *** - I had to restart the computer. Seems that restarting networking and gnome wasn't enough.

---

### Post by pedrohp on 2007-05-28
Hi there,

I'm using the gnome-network-pptp mode and i would like to know if there is a method to define DNS Servers manually... My tunnels are for LAN only (no internet routing over the tunnel).

---

### Post by crb on 2007-05-28
> **mawdryn said:**
> I think I've missed something fundamental. I'm running Feisty and followed the instructions, but it when I go to connect to the vpn by clicking on the network manager, my vpn is not listed anywhere except under 'Configure VPN'. It's created the approprate %gconf.xml file, but no files have been created in /etc/ppp/peers. 
Any help appreciated

Correct.  NM uses a plugin to pppd, and passes all the options to the service (including username and password).  It's all stored in gconf, but not in a peers file.

---

### Post by Robbyx on 2007-06-02
I have pptpconfig connecting to the vpn server. I use firefox and although pptpconfig is running it is not being used by Firefox. 

Does anyone know how to set up firefox so that it routes traffic over the vpn tunnel?

---

### Post by Crick on 2007-06-06
I had a devil of a time getting this to work. It literally took the better part of 20-30 hours of hair pulling, an ubuntu feisty reinstall, trying random things, and googling. I was almost crying with frustration because (at least) the last 10 hours consisted of me being able to get a connection up to the VPN but not being able to receive a ping from any of the servers on the remote subnet.

This may have been helpful:
[http://ubuntuforums.org/showpost.php?p=2152009&postcount=49](http://ubuntuforums.org/showpost.php?p=2152009&postcount=49)

I have the exact same problem as:
[http://ubuntuforums.org/showpost.php?p=2520201&postcount=63](http://ubuntuforums.org/showpost.php?p=2520201&postcount=63)
(looks like a bug)

This may have been helpful:
[http://ubuntuforums.org/showpost.php?p=2701421&postcount=87](http://ubuntuforums.org/showpost.php?p=2701421&postcount=87)

These pages were helpful:
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)
[http://pptpclient.sourceforge.net/routing.phtml#automatic-setup](http://pptpclient.sourceforge.net/routing.phtml#automatic-setup)
[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)
My setup involved a computer with a network card, connected by ethernet to an ADSL modem/router, connected to the internet, and at the other end a VPN server and another server inside the company network.

e.g. Here are some made up IPs to get the idea across:
My machine 10.1.1.2
ADSL modem router 10.1.1.1
Corporate VPN 200.9.36.127
Corporate remote network 192.168.20.*
Corporate Remote Desktop Server 192.168.20.5

I'm not sure whether this had anything to do with my problems or not.

I tried both the network-manager route and the pptpconfig route. Many times, many different options, reinstall twice. Neither worked as it should have done, although at least pptpconfig supplied me with a useful starting point for the scripts, since it could connect, just not do the routing properly. And for some reason the ppp0 connection would vanish a couple minutes into the piece even though it said it was still connected (and could still ping and everything).

And the 
> sudo pon tunel_name
just sat there and did nothing. For some reason I had to use various combinations of
> sudo pon tunnel_name debug dump logfd 2 nodetach
to even get it to work properly.

And I had to create the script /etc/ppp/ip-up.d/tunnel_name by hand too, as listed here:
/etc/ppp/ip-up.d/

I also put the first two route commands from here:
[http://ubuntuforums.org/showthread.php?t=91249&highlight=microsoft+pptp+vpn&page=9](http://ubuntuforums.org/showthread.php?t=91249&highlight=microsoft+pptp+vpn&page=9)
> ip route del x.x.x.x dev ppp0
ip route replace x.x.x.x via y.y.y.y dev eth0
But do not do the "route replace default" one later unless you want to kill access to your internet locally (at least I think that's what did it).

So to get the thing running, first I had to do the sudo pon tunnel debug etc thing, and then type

> sudo pon tunnel_name debug dump logfd 2 nodetach
(wait until it had finished doing its stuff)
sudo /etc/ppp/ip-up.d/tunnel_name
ping 192.168.30.5 (to see if it worked)

And for some reason, it gets a bunch of "unknown protocol" from memory, the first time it tries this, and then after you turn it off (with sudo poff tunnel) and do the process again, it works.

Overall, an extremely frustrating, agonizing process. Not unlike the way Ubuntu barfs on trying to mount my PCLinuxOS partition, and forced me to Control D to get in (and modify my fstab), but that was another story.

From memory, I also modified a few other files such as /etc/ppp/options and /etc/ppp/options.pptp (from memory, names may not be correct, I'm back in Windows now).

When I get the time I will return to it, do a reinstall on another drive and figure out exactly what it is I need to do to get it to work (and nothing more), and also to work practically (so that I can turn it on and shut it off when I want to, how to get rdesktop to look decent), etc etc.

If I had to advise anyone doing this for the first time, try both pptpconfig and network-manager, give them maybe 2 hours tops to prove themselves, but don't rely on them. It may end up being quicker and easier just doing it by hand. I swear, I think I'd rather have a good command line howto than a GUI (or choice of GUIs) that don't work, or work partially!

I certainly hope that this can be gotten to work brainlessly soon with gui means, because I'm sure there are loads of people in my situation who are required to use M$ products for work but have access to them 24/7 through the work VPN. Getting access to the VPN is the dealbreaker when it comes to adopting linux.

Pretty much everything else I do (and probably most people) can be done in linux - ripping, burning, basic office stuff, mail, irc, music and video. Even games, if you are willing to find out what the best linux games are and addict yourself to them instead of needing to play the latest and greatest. For example, Wesnoth - it's as quality and endlessly addictive as any $ game I've played.

It's just that the dual boot XP/linux for a lot of people is like a recovering alcoholic keeping alcohol in the house. First you only go into XP to do work with the best of intentions to leave and go back to Linux for everything else. Then you stay in XP longer and longer. And then you change grub to default to your Windows install, and then you may as well not have bothered with installing linux in the first place.

If you can gain windows work functionality with a VPN/rdesktop linux single boot solution, you are 9/10 of the way there.

Anyway, I hope this helps someone. I may end up posting a better howto once I can actually replicate what I did with a separate ubuntu reinstall.

---

### Post by crb on 2007-06-06
Whew!  Wouldn't you just have rather used NetworkManager?

---

### Post by Crick on 2007-06-06
> **crb said:**
> Whew!  Wouldn't you just have rather used NetworkManager?

!!!!!!!!@*(*(@ Maybe if I could get the buggy thing to work, I would have?!

> **I tried both the network-manager** route and the pptpconfig route.

If it had worked properly, it would have been GREAT. But even though I could get the network connection "configured", and able to at least get it to look like it was doing something, it would not work, no matter how many options I tried, which post I listened to, and how much I looked through syslog etc.

All I got was the extremely helpful "Connection Failure" message to come up. This is ignoring the other errors that had to be hard-erased such as the two configurations that appeared but could not be edited or deleted through the GUI. NetworkManager is anything but a panacea as some posters make out on this thread, making out as if all you have to do is pass the hurdles of getting it to appear at the top right of your desktop, and getting it to display the name of your VPN so that you can connect to it.

And this was through hours of playing around with it, and a full format of ubuntu and reinstall.

---

### Post by Raa on 2007-06-07
> **Crick said:**
> 
But do not do the "route replace default" one later unless you want to kill access to your internet locally (at least I think that's what did it).


Sure you did not have to add "route replace default". That was just an example. I was too tired to explain how to route, and just added a small example.

> **Crick said:**
> 
So to get the thing running, first I had to do the sudo pon tunnel debug etc thing, and then type

> sudo pon tunnel_name debug dump logfd 2 nodetach
(wait until it had finished doing its stuff)
sudo /etc/ppp/ip-up.d/tunnel_name
ping 192.168.30.5 (to see if it worked)


Actually the files in ip-up.d folder should not be named exactly as the tunnel name. And they shuld not be runned manually. When pptp tunel starts, it should be runned automatically. Just ensure it is executable and have correct permissions.

---

### Post by ronnieredd on 2007-06-07
Mine works!
I installed all of the network manager plug-ins and all of the knetwork-manager packages. I use the standard Ubuntu (Gnome) window manager. I use some of the kde stuff in other places so you may need all of the regular kde dependencies. I'm connected to our watchguard firewall right now. Some of the things I have installed that may help (or not):
[LIST]
[*]dhcdbd
[*]dhcp3-client
[*]ifplugd
[*]ifupdown
[*]iproute
[*]kde
[*]kdenetwork
[*]kdnssd
[*]knetworkconf
[*]knetworkmanager
[*]kppp
[*]laptop-net
[*]netbase
[*]netgo
[*]net-tools
[*]network-manager
[*]network-manager-gnome
[*]network-manager-openvpn
[*]network-manager-pptp
[*]network-manager-vpnc
[*]networkstatus
[*]wireshark (will help capture data for diagnosis)
[*]wlassistant
[*]wpasupplicant (just for your wireless)
[*]Plus any smb (Samba) packages you may need
[/LIST]
I'm sure there's more than you need listed, however, these are the things I installed along the way to get it to work. The last couple of things I installed, that worked for my setup, was the plugins for network manager and KNetworkManager. I ran KNetworkManager and everything came together.
I also tried Kvpnc and it would connect, but I couldn't talk to anything on the other network. It may work better once the above mentioned plugins are installed.
When/If I get some time, I'll uninstall some things to narrow it down to what's really needed.

---

### Post by crb on 2007-06-07
> **Crick said:**
> !!!!!!!!@*(*(@ Maybe if I could get the buggy thing to work, I would have?!

If it had worked properly, it would have been GREAT. But even though I could get the network connection "configured", and able to at least get it to look like it was doing something, it would not work, no matter how many options I tried, which post I listened to, and how much I looked through syslog etc.

Sorry, didn't mean to come across as nasty. 

It's less than "friendly" at the moment, and I'm doing my best to improve it in Ubuntu while the upstream author is missing, and development upstream is slow (or effort being spent in other directions, e.g. OLPC/wireless).

Connections that appear and can't be deleted can be removed from gconf.  Ultimately I'm trying to get new packages into a state where you can't add bad connections, and this is a bug I don't see myself so its hard to diagnose.

At the end of it, all NM-PPTP does is call the command line PPTP client with options on the command line, instead of from a peers file.  If you can get the options that work for you in the peers file, you can probably get it to go from NM.

In the event of failure, lots of useful information goes to syslog, and more goes there if you enable debug in the properties dialog.  Not obvious to new users, of course, but it exists.

I've got lots of people raising a bug on the package saying "error 15, can't connect".  It's the standard PPTP error.  I am hoping one of the people with the error will actually give me a debug log so I can try and find out if there is a common problem!

Where were you looking for help with this?  Is there somewhere I can document all this where you would likely have found it?

---

### Post by shelzmike on 2007-06-11
Okay, quick intro - I am a complete noob to Ubuntu (and Linux for that matter) but am already an adoring fan. 

I was able to get the VPN configured through the network manager; however, everytime I try to connect, I get an error message that says "Could Not Start CONNECTION NAME DUE TO CONNECTION ERROR VPN Connection Failed" (More or Less). I have no idea what is wrong, except for maybe a router issue? Is that possible? I can connect to the same VPN from other M$ machines at my home with no problems. 

I have attached the syslog file. 


I appreciate the help here. Being able to do this is vital for me as this is a work VPN and I am a telecommuter  for the most part. Thanks in advance.

---

### Post by crb on 2007-06-11
> **shelzmike said:**
>  ppp-debug / no 

Please set 'Debug mode' to ticked in the properties dialog and post the syslog again.

Craig

---

### Post by Hortinstein on 2007-06-13
yeah i did this and am still having problems its connected, but i dont think the DNS is updating right or something (trying to connect to WSU campus)

---

### Post by shelzmike on 2007-06-13
> **crb said:**
> Please set 'Debug mode' to ticked in the properties dialog and post the syslog again.

Craig

I realized  that  I had not since I have posted. I appreciate the response. I will do this, but it may take a day or two. Thanks in advance for your help!

---

### Post by shelzmike on 2007-06-15
> **crb said:**
> Please set 'Debug mode' to ticked in the properties dialog and post the syslog again.

Craig

Okay, I have had a time the past couple of days. My MB crashed and I needed to get a new one. I now have an AMD 64 bit. (many be important to what I am about to say).

So, I installed ubuntu AMD 64 (Feisty)  (again) and installed the Network Manager and configured the VPN through that. Everything Seemed to be straight forward, but when I went to connect, it was not. 

Per your last post I did enable debugging on the connection (and this is the noob in me, I am not sure how to access that log, unless it is just under the syslog file)

Either way, I think I am now getting less accomplished with the connection now than I did from the last post. 

Now the only thing that I get back is the following:
```

Jun 15 15:35:27 mike-ubuntu kernel: [11499.721013] nm-ppp-auth-dia[6635]: segfault at 0000000000000088 rip 00002b9d2e7d721b rsp 00007fff81e66770 error 4
```

I think I got further last time because I was using pptconfig. However, I cannot install pptpconfig due to dependencies that are needed. Unfortuntately, I cannot install those dependencies because i get an error stating unsupported 'i386' error, which I am taking to mean that because I have AMD64, I cannot install pptpconfig.

Yesterday, I tried setting up the vpn manually, which I probably do not have to tell you did not work to well. However, I have since had to reinstall Ubuntu, so there is no strange code laying around.

So, there you have it, any possible help here? I am willing to do whatever it takes as I have to be able to connect to my office VPN and would hate to have to go back to M$. Thanks in advance for any help!

---

### Post by mgmiller on 2007-06-16
I don't know if it will help, but if you were closer using 32 bit Feisty, there is no reason why you can't install that instead of 64 bit.  The 32 bit  version runs great on a 64 bit AMD CPU.

---

### Post by shelzmike on 2007-06-17
> **mgmiller said:**
> I don't know if it will help, but if you were closer using 32 bit Feisty, there is no reason why you can't install that instead of 64 bit.  The 32 bit  version runs great on a 64 bit AMD CPU.

Ever the hard-head, (I still have this on my table  of options); however, I want to see if I can get this to work. It is not a main machine, so I have time to kill. Thanks  for the  reply!

---

### Post by Garf on 2007-06-18
Sorry if I have missed a whole lot of posts, but I installed both of those packages, and nothing happens...

I didn't get anything in the notification area, and when I went to run the program from the Applications Menu, nothing happened..

I also went into the terminal and tried to run NetworkManager from there... as normal user and root... nothing..

Whats going on??

This happened on two ubuntu machines today, the first of which I put down to being a virtual machine, but my standalong machine at home is doing the same thing..

Any help apreciated.

---

### Post by vishalwarke on 2007-06-18
I am having trouble connecting to my schools VPN. I installed PPTP, rebooted my computer and configured the connection. But when I try to connect to it I get following error msg: "Could not start the VPN connection UA VPN due to a connection error. VPN connection failed"

Someone pl help. Thanks,

---

### Post by shelzmike on 2007-06-18
To start with, I do not have the answer to this, as you can see am having problems of my own. However, what I did want to let you know is that you are going to want to run a syslog in debug mode so that the people in the forums can troubleshoot the exact step that does not go through. Also, in case you have not, there are other posts in this thread dealing with the same issue, and if you have not done so yet, you may want  to view all  the posts in this thread to see if anything in there can help. Good Luck!

---

### Post by Djeneral on 2007-06-20
I have problem connecting to VPN wireless !
I'm new to linux and using Ubuntu 7.04.I'v get access to network (dc++ is running in local hub) but VPN is not responding also the pptpconfig.Please help!

---

### Post by KevinBuntu on 2007-06-21
If you are having problem connecting to a Windows 2003 server's VPN server, try this:

In VPN Configuration panel:

in "Authentication" tab, check "refuse EAP"

in "Compression and Encryption" tab, check both "Require MPPE encryption" and "Require 128 bit MPPE encryption".


That did the trick for me! :D

---

### Post by patsimon12 on 2007-06-25
I am having similar issues using KVpn to connect to my works PPTP network. I know I can access this from behind my home router as my windows laptop connects without issue.

The log from KVpn is  (removing log in details)

info: Global configuration loaded.
debug: Profile found: EMU
debug: Wallet enabled and available, reading passwords from wallet.
debug: Folder for kvpnc has been set.
debug: read of user password was successful.
debug: read of preshared key was successful.
debug: read of preshared key password was successful.
debug: Last used profile found: EMU
debug: New type: pptp.
info: The required daemons (pppd and pptp) are available, connect will be enabled.
debug: Preserving network environment
info: Connect try requested
debug: pppd: /usr/sbin/pppd
debug: /usr/sbin/pppd has MPPE support and uses new style.
debug: Test support of replacedefaultroute pppd: failed
debug: Some passwords which are need got from password enter dialog.
debug: No default interface given, tried default interface, got success, using "eth0".
info: "PppdUpScript" started.
info: "PppdUpScript" finished.
debug: pppd peer script: /etc/ppp/peers/kvpnc.EMU 
debug: pppd chat script: /etc/ppp/chap-secrets 
debug: Username: AD\patrick
debug: chmod of /etc/ppp/chap-secrets (go-rwx) started.
debug: pppd: /usr/sbin/pppd 
debug: Trying to connect to server "blah.blha.blah.blah" with user "AD\patrick"... 
info: "pppd" started.
info: "pppdDelDefaultRouteProcess" started.
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/5
debug: [pppd] LCP: timeout sending Config-Requests
info: Connection has been terminated.
debug: [pppd] Connection terminated.
info: Connection has been terminated.
info: Disconnect requested
info: Not connected.


Can anyone shed any light on this?

---

### Post by weedenbc on 2007-07-11
When I run
```
sudo apt-get install network-manager-pptp
```

I get an error that it couldn't find the package.  Did the package get renamed or maybe my repositories are screwed up somehow?

Using a new install of Fiesty.

---

### Post by tienhn on 2007-07-19
Hi All,
I am new to Ubuntu but ok with computer/linux. I followed your post to install the network-manager-pptp and here is the message I got:
==========

tienhn@ubuntu:~$ sudo apt-get install network-manager-gnome network-manager-pptp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-manager-pptp

==========

What did I do wrong?

TIA.

---

### Post by mgmiller on 2007-07-19
network-manager-pptp is in the universe repository.  Make sure it is checked as enabled in synaptic package manager in the Settings > Repositories area.

---

### Post by Crick on 2007-08-01
Well, I figured out how to do it quickly, easily and painlessly. I'm going to outline how in what I hope is a fairly braindead fashion.

The first thing to recognize is that IF YOU HAVE AN ADSL ROUTER and you are connecting via VPN to a machine that IS IN THE NETWORK OF THE VPN then you have a LAN TO LAN connection, not a CLIENT TO LAN connection.

So here is a howto for Ubuntu Feisty, if you have this setup. (Should also work if for some reason the machine you are VPNing to is the machine you want to, say, rdesktop to).

1. Go here: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

2. Start at "Installing the Configuration Program"

3. Go until number 10 of "Configuration". My clarifications below:

4. Now, for my settings. I am going to be referring to the diagram here:
[http://pptpclient.sourceforge.net/routing.phtml#lan-to-lan](http://pptpclient.sourceforge.net/routing.phtml#lan-to-lan)

[IMG]http://i11.tinypic.com/682q2hl[/IMG]

10.20.0.36 -> Your ADSL Router's address (you might know this because you can access it via a browser directly)

22.0.0.22 -> The VPN that you connect to. You will know this if you use the windows VPN client - it's in properties -> General -> (Host name or IP Address of destination (such as microsoft.com or 157.54.0.1)

192.168.0.0 netmask 255.255.255.0 -> The subnet you wish to connect to. I'm not sure what to do if your local and remote subnets are the same down to the first 3 bytes, ask someone else, I don't know. Maybe configure your ADSL router so that your subnet is different to the remote one?

Also, note that the login name and password is with the "user name: password" in the windows connect dialog for the sake of this example is "dave" and "my_secret_password".

Ok, now we plug in values. In the pptpconfig "Server" tab, we put in the following
name: foo (name doesn't matter)
Server: 22.0.0.22
Domain: 
Username: dave
Password: my_secret_password

I don't think the routing tab does anything, but you can click LAN to LAN, that probably doesn't hurt.

Encryption tab, check Require MPPE, Refuse Stateless Encryption, Refuse to Authenticate with EAP. Maybe yours is different, start with these options.

And misc, we may as well check the first two options, start tunnel when this program starts, and reconnect if disconnected.

Once we are done there, click "Add" to add all this info, which will create a new configuration labelled "foo". This is an important step.

Start this connection.

It should say something like:
> Using interfacte ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <---> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP.

That last thing about the proxy ARP thing is not a bad sign, don't worry about it.

if we do an ifconfig, we should see an entry for ppp0, and if we do a route -n, we should see something like the following:
> 
202.4.29.106    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
203.0.0.55     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.20.0.36        0.0.0.0         UG    0      0        0 eth0


But that's not enough. We need to add a couple entries to the routing table.

Open up an xterm,
> route add -host 22.0.0.22 gw 10.20.0.36
route add -net 192.168.0.0 netmask 255.255.255.0 dev ppp0

Both of those are necessary to get it to work.

Your routing table should look like the following with route -n:
> 202.4.29.106    10.20.0.36         255.255.255.255 UGH    0      0        0 ppp0
202.4.29.106    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.30.0    0.0.0.0         255.255.255.0    U   0     0      0     ppp0
203.0.0.55     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.20.0.36        0.0.0.0         UG    0      0        0 eth0


Now, try and ping the mail server, it should work. e.g.
> ping 192.168.0.7
rdesktop should work too, you might try that as well.
Now that we have proven it to work, we will want to automate it.

Put the two routing commands in /etc/ppp/ip-up.d/routing and chmod it so that it is executable. Make sure that there is a line in /etc/ppp/ip-up to execute the script. Put it at the end, e.g.
> /etc/ppp/ip-up.d/routing

If you keep getting an annoying error saying that it is "Unable to remove undo file /var/run/pptpconfig.foo.undo", you can counter that by putting in the following into your "routing" script:
> touch /var/run/pptpconfig.foo.undo

Lastly, you want to make sure that when you close the connection, you correct the routing table. Add the following lines to a script here: /etc/ppp/ip-down.d/routing, and chmod +x so that it can execute.
> route del -net 192.168.0.0 netmask 255.255.255.0 dev ppp0
route del -host 22.0.0.22 gw 10.20.0.36


And again, make sure that script executes by referencing it as in the above by puting a line in /etc/ppp/ip-down          .
> /etc/ppp/ip-down.d/routing

I'm not sure that's the best way, but it works for me. Please let me know if what I am doing is somehow insecure or wrong. If others like it, feel free to include it in the documentation somewhere. I'm sure search engines will find it soon enough anyway.

Edit: Thank heavens that there is now an easy way to connect to the corporate VPN. For many power users, this will enable them to break free from the clutches of MS because they can now do complicated office stuff without paying the MS tax. This was the deal breaking feature for my new non-MS OS, and unfortunately it was just a bit too hard in PCLinuxOS (rdesktop would freeze a connection I could ping fine to), other than that, it's a great distro. Maybe in PCLinuxOS2008...

I'd also add that the resulting connection is MUCH more stable than using putty.exe with windows. My old ssh sessions would always time out within several hours (but sometimes in as little as half an hour) if I hadn't typed anything. It also appears less laggy.

---

### Post by HautingLu on 2007-08-04
> **KevinBuntu said:**
> If you are having problem connecting to a Windows 2003 server's VPN server, try this:

In VPN Configuration panel:

in "Authentication" tab, check "refuse EAP"

in "Compression and Encryption" tab, check both "Require MPPE encryption" and "Require 128 bit MPPE encryption".


That did the trick for me! :D

Thank You!!!! :mrgreen::mrgreen::mrgreen:

Now if I can only get Terminal Server Client to work.

---

### Post by msprygada on 2007-08-07
OK, I can create a VPN connection. I then left click on the Network Manager in the notifications area. I select VPN Connections and the VPN connection I created. It opens the "Authenticate Connection" dialog box. I enter my login (domain\userid) and password. I click "Remember Password for this Session" and click "OK". The "Authenticate Connection" dialog box disappears and nothing seems to happen. Should I get a connection window or notification as it is attempting to connect like it does in Windows? If I go back into the Network Manager, I do not have Disconnect VPN as an option in the VPN connection menu so I am assuming that I am not connected plus I cannot get anywhere on my companies network.

I did the terminal commands of installing and killing the network manager and all this worked as expected.

Any help would really be appreciated.

Matt

---

### Post by jim.guenzel on 2007-08-29
This worked for me after giving up on pptp config
pptp config worked in 6.06 but not in 6.1 or 7.04.

This worked for me in 7.04. I used net work manger

From the root terminal

sudo apt-get install network-manager-gnome

then

sudo apt-get install network-manager-ppt

then

reboot

the network app ought to show up in the upper right work bar

if not then
/usr/sbin/NetworkManager

I also ran network manager as sudo once before rebooting
sudo nm-applet


Then click on the applet in the upper right work bar it to connect and to configure / add the vpn 

Thanks
Jim

---

### Post by schierly on 2007-09-07
I have the following VPN connection on my Win XP working, but I dont get it to work in Ubuntu Feisty AMD64. 

I tried the pptp network manager plugin, which lets me create and select the VPN Network. Nevertheless it seems that I can't connect to the internet. The network card is working fine, I receive the DNS Server and an IP Address, but to be able to use the Internet, I need to connect to 172.16.0.1. In Windows all encryptions are dissabled.

Can anyone help me.

```
Windows-IP-Konfiguration

        Host Name. . . . . . . . . . . . . : axel
        Primary DNS-Suffix . . . . . . . : 
        Node Typ . . . . . . . . . . . . : Hybrid
        IP-Routing enabled. . . . . . . : No
        WINS-Proxy enabled. . . . . . . : No
        DNS-Suffix Search List . . . . . . . : xxx.bbb.tld # 

Ethernetadapter LAN-Verbindung:

       Connection specific DNS Suffix: xxx.bbb.tld
        Description. . . . . . . . . . . : Fast Ethernet Card
        Physical Address . . . . . . : xx-E0-xx-92-00-00
        DHCP enabled. . . . . . . . . . : yes
        Autoconfiguration enabled . . . : yes
        IP-Address. . . . . . . . . . . . : 172.16.1.77
        Subnet Mask. . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 172.16.0.1
        DHCP-Server . . . . . . . . . . . : 193.170.62.162
        DNS-Servers. . . . . . . . . . . . : 172.16.0.1
        Primärer WINS-Server. . . . . . . : 172.16.0.1

PPP-Adapter INTERNET:

        Connection specific DNS Suffix 
        Description. . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Addresse . . . . . . : 00-53-45-00-00-00
        DHCP enabled. . . . . . . . . . : Nein
        IP-Address. . . . . . . . . . . . : 192.168.10.4
        Subnet Mask. . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 192.168.10.4
        DNS-Server. . . . . . . . . . . . : 172.16.0.1
                                            172.16.0.1

```

/var/log/messages
```

Sep  6 22:49:26 xxx-desktop kernel: [ 2049.368231] nm-ppp-auth-dia[8301]: segfault at 00000000
00000088 rip 00002ae13c02821b rsp 00007fff74612f30 error 4
```

I maybe have to add a route or so, but which one? Can anybody help?

EDIT [SOLVED]

Never believe Windows when it's saying that's a VPN Connection. The connection typ was a point to point connection.
I did the setup through the config files of linux-pptp , and it's working now.

---

### Post by OskarB on 2007-09-08
Hi,

I tried to follow the howto in the first post... but I'm not sure if I got it right... is it any way to see if the VPN works?

When I write in the servername ([http://www.sobernet.nu](http://www.sobernet.nu)) in Evolution I get no Error-prompt.. but I dont get any answere mails from the server either...

Anyone know how I can see if the vpn-connection is OK?

Thanks! 

//Oskar

---

### Post by Snipershot on 2007-09-09
I'm silly, ignore this message for now.

---

### Post by sarasotab on 2007-09-10
I followed the instructions, but pptpconfig would not install.  The following error ensued:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages
root@ubuntu-laptop:~#

Is there something I am missing?  I am running Dapper 6.06 Lts

Bob

---

### Post by coloured on 2007-09-10
Here is the fix for this problem below - [http://ubuntuforums.org/showthread.php?t=547991](http://ubuntuforums.org/showthread.php?t=547991)

> **msprygada said:**
> OK, I can create a VPN connection. I then left click on the Network Manager in the notifications area. I select VPN Connections and the VPN connection I created. It opens the "Authenticate Connection" dialog box. I enter my login (domain\userid) and password. I click "Remember Password for this Session" and click "OK". The "Authenticate Connection" dialog box disappears and nothing seems to happen. Should I get a connection window or notification as it is attempting to connect like it does in Windows? If I go back into the Network Manager, I do not have Disconnect VPN as an option in the VPN connection menu so I am assuming that I am not connected plus I cannot get anywhere on my companies network.

I did the terminal commands of installing and killing the network manager and all this worked as expected.

Any help would really be appreciated.

Matt

---

### Post by Snipershot on 2007-09-10
```
Sep 11 03:11:10 sharine pppd[27199]: using channel 17
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xb1e2038d> <pcomp> <accomp>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xac <accomp> <pcomp> <magic 0xd8be53a6> <auth pap> <mrru 1600> <ssnhf> <endpoint [MAC:00:15:c5:f7:da:e9]>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfRej id=0xac <mrru 1600> <ssnhf>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfAck id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xb1e2038d> <pcomp> <accomp>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xad <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfNak id=0xad <auth chap MS-v2>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xae <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfNak id=0xae <auth chap MS-v2>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xaf <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfNak id=0xaf <auth chap MS-v2>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb0 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfNak id=0xb0 <auth chap MS-v2>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb1 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfNak id=0xb1 <auth chap MS-v2>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb2 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfRej id=0xb2 <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb3 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfRej id=0xb3 <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb4 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfRej id=0xb4 <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: rcvd [LCP ConfReq id=0xb5 <accomp> <pcomp> <magic 0xd8be53a6> <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: sent [LCP ConfRej id=0xb5 <auth pap>]
Sep 11 03:11:11 sharine pppd[27199]: Script /usr/sbin/pptp 10.0.0.1 --nolaunchpppd finished (pid 27200), status = 0x0
```
Ive fiddled around and i feel I'm now ready to ask for some help. What does this log tell you that I'm doing wrong? If anything.

---

### Post by tphillippe on 2007-09-15
KevinBuntu's advice (post #116) worked great for me.

---

### Post by jpastore on 2007-09-16
I find myself going mad trying to get this pptp connection to work. I've tried a few howto's and I'm hoping that I didn't botch something in the process.

I'm trying to get nm-pptp to connect to my pffoce pptp server.

I'm trying to connect from my wireless card. I'm using the network-manager to create the vpn connection

Under the authentication tab I have only "Refuse EAP" checked

under the compression adn encryption tab I have checked: "Require MPPE Enc...", "Require 128bit MPPE Enc", "Enable statefule MPPE"

under ppp options only "Exclusive device access UUCP style lock" is checked. default settings for input boxes

under routing I checked only use VPN connection for these address and put in the CIDR notation for my internal network at the office.

I'm running:
Linux [hostname] 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux


Please help.

---

### Post by jpastore on 2007-09-16
I tried deleting the connection and re adding it after trying many things.

I'm getting this in the /var/log/syslog

Sep 16 18:23:24 [HOSTNAME] NetworkManager: <information>^IWill activate VPN connection 'EMD', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jpastore', vpn_data 'ppp-connection-type / pptp / pptp-remote / 69.65.65.40 / usepeerdns / no / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Sep 16 18:23:24 jpastore-laptop NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.

---

### Post by bsn on 2007-09-17
> **jpastore said:**
> I tried deleting the connection and re adding it after trying many things.

I'm getting this in the /var/log/syslog

Sep 16 18:23:24 [HOSTNAME] NetworkManager: <information>^IWill activate VPN connection 'EMD', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jpastore', vpn_data 'ppp-connection-type / pptp / pptp-remote / 69.65.65.40 / usepeerdns / no / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Sep 16 18:23:24 jpastore-laptop NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.


I've got the same thing :((((((( What am i doing wrong?

Sep 17 10:47:11 bsn-laptop NetworkManager: <information>^IWill activate VPN connection 'DDC', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'bsn', vpn_data 'ppp-connection-type / pptp / pptp-remote / 82.148.208.111 / usepeerdns / no / encrypt-mppe / yes / encrypt-mppe-128 / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Sep 17 10:47:11 bsn-laptop NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN.

---

### Post by jpastore on 2007-09-17
well I have it working from a wired connection but it won't work over my wireless which is weird. I'm about to see if I can ifdown my eth0 and see if that will force it to work over the wireless (eth1)

here's how I set mine up (assuming you have all the right packages installed and you're going through network-manager)

Connection tab (this should be self explanatory but I'll run it down anyway) 
Name: MY OFFICE
type: Windows VPN (PPTP)
gateway: my office ip (xxx.xxx.xxx.xxx)

Authentication tab
checked - Authenticate Peer and Refuse EAP
unchecked - refuse chap and refuse ms chap

compression and encryption tab
basically unchecked all under compression and everything under encryption is checked

ppp options tab
custom ppp options is blank
checked - use peer dns, exclusive device access
unchecked debug output
packet params I left along which is set to 1416
timeouts and delay left alone defaults to: 0, 10, 10

routing tab
checked peer dns through tunnel
checked only use vpn for these networks and specified the internal work at my office so I would use my internet connection for everything else


I did notice some DNS issues...it didn't automatically add my internal dns server to the /etc/resolv.conf

so I added the ip of the name server to the name server list through network-manager...to be honest I haven't tried it yet....I was able to ssh to an internal ip which was I needed


now if I can just figure out how to make it work over the wifi instead of only the wired....

---

### Post by jpastore on 2007-09-17
also connecting to the vpn seems to blow out the contents of the /etc/resolv.conf I'm wondering if the use peer option is responsible for that... there needs to be more documentation on this....

---

### Post by dlogic on 2007-09-18
Hello everyone, my first post :)
I'm new to Ubunutu, but that's beside the inquiry.  I'm in the process of setting up VPN to access my corporate network.  I don't see an option for it, but, my company uses hardware token rings to generate  a random number for a Challen Response, that along with a PIN.  Is this something I can do with Network Manager?  DO I gotta just gotta stick with WinXP?

---

### Post by jpastore on 2007-09-18
It sounds like you're using secure id, I would talk to your IT deparment and see if they you can get the company name of who makes the particulr security system you are using and see if they have a linux client. Idon't think network manager is going to help you.  That doesn't mean you have to go back to windows yet either.

I just installed Innotek's Virtual box and just setup 2 xp virutal machine's for testing web apps with IE 7 and IE 6. Maybe you could use a virtual machine for connecting to the office if there's no linux client for you, but if it's the company I think it is I'm pretty sure they have linux client

---

### Post by thale on 2007-09-18
Hey, so, I am able to connect to the VPN via PPTP successfully. I used the ubuntuguide.org method for feisty. However, when I try to access web based content via a web browser it says it's connected, but never actually displays anything. I'll then try to hit a known site, like google or yahoo, and I get the same result. There doesn't appear to be a lot of setting so I don't know what I am missing. I was able to do this just about out of the box with the previous version of ubuntu.

---

### Post by jpastore on 2007-09-18
There is a problem when you make a successful connection that network manager blows out the contents of your resolv.conf when you disconnect it puts it back the way it's supposed to be...

it's a known bug that hasn't been assigned to be resolved yet and I wish someone would take the time to look at it...

in the mean time I made a copy of the resolv.conf and I just run a quick shell script to copy it over when I connect to deal with it...

---

### Post by dlogic on 2007-09-18
jpastore:  I use a program made by Nortel Networks called VPN Contivity, for Windows XP.  I think they are the same company that provides the hardware token ring as well.

---

### Post by jpastore on 2007-09-18
I didn't Nortel had that. that must have come from that purchase of ascend like 10 years ago. 

I would contact them and see if they have a linux client to connect into the office.

---

### Post by dlogic on 2007-09-18
I did some snooping around on the net, specifically Nortel's website.  They do have a linux client, however, a license is required for it; otherwise, they have a 30-day trial.  I may need to end up calling my company's tech support and inquiry whether our company has the Linux client available.  I was hoping I wouldn't have to go that route, but it seems there's no other way.  Since my company relies heavily on the Windows environment, it may be safe to assume they will not have the linux client - I may be SOL at that point.

---

### Post by jpastore on 2007-09-18
or talk to someone about expensing it or seeing if you can trade up your license....

---

### Post by turbohor on 2007-10-01
This works for me:lolflag:

> **KevinBuntu said:**
> If you are having problem connecting to a Windows 2003 server's VPN server, try this:

In VPN Configuration panel:

in "Authentication" tab, check "refuse EAP"

in "Compression and Encryption" tab, check both "Require MPPE encryption" and "Require 128 bit MPPE encryption".


That did the trick for me! :D

---

### Post by jpastore on 2007-10-01
I resolved to reloading feisty. Evidently doing a distribution upgrade was the problem, but out of the box pptp was fine using the recommend settings described in this forum.

---

### Post by mb01915 on 2007-10-03
> **jpastore said:**
> There is a problem when you make a successful connection that network manager blows out the contents of your resolv.conf when you disconnect it puts it back the way it's supposed to be...

it's a known bug that hasn't been assigned to be resolved yet and I wish someone would take the time to look at it...

in the mean time I made a copy of the resolv.conf and I just run a quick shell script to copy it over when I connect to deal with it...

jpastore - I understand the concept of what you are doing but I do not have a clue what to do or how to do it.  Would you mind providing more detail and help the clueless?

---

### Post by jpastore on 2007-10-03
Well open your favorite editor, I prefer vim but if you are a beginner I would use gedit.

contents of the file would look like this:

```

#!/bin/bash

cp /etc/resolv.conf.pptp_backup /etc/resolv.conf


```

save this shell script to /usr/bin called fix_pptp_dns.sh

then open up a terminal (like gnome-terminal) and do the following:

1. create the resolv.conf.pptp_backup be surfe you are not connected to the vpn or it will defeat the purpose of this exercise.
```

sudo cp /etc/resolv.conf /etc/resolv.conf.pptp_backup

```

2. allow the shell script we create to execute
```

sudo chmod 700 /usr/bin/fix_pptp_dns.sh

```
for more information on what chmod does and what the numbers mean I would read this:
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
I don't want to get off topic but if you are a beginner you should take the time to understand each aspect of what you are doing. God forbid you run across a how-to with misinformation and trash stuff on your system...

then create a shortcut on your desktop to run this shell script
```

1. right click on your desktop
2. select create launcher
3. file in form: Name = "Fix PPTP DNS", command = "gksudo /usr/bin/fix_pptp_dns.sh", comment="Jon showed me how to fix DNS because someone on the network-manager project has been slacking", feel free to choose an icon.

```

now after you connect you can just run this icon on your desktop and it should work.

if you need to use internal DNS for your company for some reason I would edit the /etc/resolv.conf.pptp_backup file while you are disconnected, or you will have to disconnect and reconnect to test.

```

sudo gedit /etc/resolv.conf.pptp_backup

```

you should see 1 or 2 line that look like:
```

nameserver some.ipAddress.for.DNS
nameserver some.ipAddress.for.secondaryDNS

```

change those lines to your internal nameserver(s) and save.

then reconnect and test.

hope this helps...

now if only I could figure out why it's giving me a segmentation fault all of a sudden I would be happy...this was working and now it's not...maybe I need to roll back an update?

---

### Post by jpastore on 2007-10-03
Also would like to point out that I think I found the culprit as to why DNS is shot post vpn connections...

while trying to troubleshoot my segmentation fault I came across:
[http://sujitpal.blogspot.com/2007/05/installing-ubuntu-on-fujitsu-lifebook.html](http://sujitpal.blogspot.com/2007/05/installing-ubuntu-on-fujitsu-lifebook.html)

which mentioned files in: /etc/ppp/ip-up.d

there's 2 files in here that rework the resolv.conf:
0000usepeerdns
0dns-up

I'm not a bash scripting expert, (I only automate basic stuff using bash scripting)  but from what I can tell this what's broken.  When I figure it out I'll post another reply with how I fixed it to avoid the above instructions...but before I can fix it I need to figure out this seg fault... =(

---

### Post by rikalaj on 2007-10-03
Is the bug fixed or when it's going to be fixed?

I've been thinking, reading forums and trying different ways to make vpn work with static ip until I found out that it's a bug. :(

---

### Post by jpastore on 2007-10-03
This is a bug that has not been resolved yet. I'll look for a link to the network-manager bug so we can track it from here as well. I don't have it readily available since reloading feisty seemed to fix the problem...doing a dist-upgrade was not clean and the source of my initial problems

---

### Post by mb01915 on 2007-10-06
> **jpastore said:**
> This is a bug that has not been resolved yet. I'll look for a link to the network-manager bug so we can track it from here as well. I don't have it readily available since reloading feisty seemed to fix the problem...doing a dist-upgrade was not clean and the source of my initial problems

Thanks for all your help.  Interesting that the problem went away with a fresh install.  I did the upgrage to 7.10 beta.  Maybe I will do a fresh install after the 18th on a different old eMachine box and see what happens.

---

### Post by hollymcr on 2007-10-18
In case anyone is interested:

I just followed the Feisty 32-bit instructions at the top of this thread on Gutsy (7.10) AMD64 and they worked flawlessly; I was connected to my office VPN in a few clicks.

Thanks!

---

### Post by psiklotron on 2007-10-24
I had a lot of trouble trying to figure it out on Gutsy Gibbon but it's working now. yay! In the end what worked for me is the following:

**Before connecting**
configuring the network-manager -> vpn connections-> configure vpn ->(select connection) -> edit

Authentication Tab: 'Refuse EAP' checked. Everything else unchecked.
Compression & Encryption Tab: 'Require MPPE encryption' and 'Require 128 bit MPPE encryption' checked. Everything else unchecked.
PPP Options Tab: 'Use Peer DNS' and 'Exclusive device access (UUCP-style lock)' checked. Everything else unchecked.
Routing: Peer DNS through tunnel checked. Everything else blank.


**After connecting to VPN:**
Adding the line
"nameserver 192.168.1.4"
to my resolv.conf file AFTER successfully connecting to VPN. 192.168.1.4 is the IP of my VPN server.

Hope this helps someone. Or possibly me, in the future. :)

---

### Post by codedmin on 2007-10-26
I install and reinstall network-manager-pptp and still don't have vpn connection in nm-applet...


How can i have this please...

Thanks

---

### Post by arrrghhh on 2007-11-03
ok everyone needs to read thru entire threads before asking questions - codedmin, that question has been answered.

now to address the static issue - someone suggested wiping out everything except the loopback interface from the /etc/interfaces file - this works... however, there's a much easier way.

i found that the ethernet card has to be set to 'roaming mode' to get the vpn options to appear when you click on the network manager icon.  switching to anything but 'roaming mode' on eth0 seems to break it, and re-enable roaming mode and vpn settings are back.

so onto why i'm posting...

i have tried to configure a PPTP VPN so many different ways i can't even remember where this all started.  but i am definitely closer than i have ever been before - the vpn connects and ppp0 has an ip address.  now my issue is, routing!  it seems the default routes that the vpn sets up are not good - i have no internet whatsoever when the vpn is connected - i can't access local intranet pages or anything on the internet.  i can, however, ping the ip address for the ppp and eth connection.  i'm pretty sure i need to configure routing, but configuring it manually via CLI every time i connect?  that is ridiculous.  i would think that the vpn would set all the appropriate routing for me, but it doesn't.  is there an easy way to configure routing?  all my attempts have failed miserably.  thanks!

---

### Post by cmnorton on 2007-11-04
What I have found is seems to be related to WEB encrypted networks. First, given these "roaming mode" settings, you have to be able to have a regular, non-VPN, connection. With manual connections and no Network-Manager installed I was able to connect on 6.06.

Under 7.04 NetworkManager auto configuration, I cannot connect on my WEP encrypted network. I can connect if I go with manual configuration.

Second, under 7.04 there are many reports that pptpconfig will not work. It also has been deprecated in favor of NetworkManager. If you are using NetworkManager for VPN, you first have to be able to have a non-VPN connection work. 

So far, I cannot have a non-VPN NetworkManager connection on my wep-encrypted network. I still have to go with manual configuartion. And, no NetworkManager means no NetworkManager VPN, at least in my case.

---

### Post by Scotty562 on 2007-11-05
Worked great on my 7.10 install. Although I did have a small brain fart when configuring it.  I coudlnt figure for the life of me what "gateway" was talking about.. I was thinking.. default gateway??? that doesn't make any sense at all. Then the brain fart subdued and all was good in the world :).

It would be nice if this was included by default though.

---

### Post by jen3 on 2007-11-08
I finally got this to work on a LiveCD of Gutsy Gibbon (Xubuntu 7.10) and it's really not that bad even if 
[LIST]
[*]you have a DSL router on the client side
[*]your subnet is the same as the one behind the VPN
[/LIST]

As long as on the client side your machine has its IP address assigned by DHCP, you can do this all using Gnome Network Manager and its plugin for PPTP VPN as described in previous posts.

Here's what worked for me.

The setup:
[LIST]
[*]Xubuntu 7.10 (LiveCD)
[*]client has ethernet and wireless, ethernet works out of the box
[*]client behind DSL router which assigns IP address via DHCP in the 192.168.1.0 subnet -- 192.168.1.97 in this example
[*]gateway for VPN at work 200.100.20.10 (let's pretend)
[*]PPTP VPN assigns addresses via DHCP in the 192.168.1.0 subnet
[/LIST] 

What I did:

To keep things simple, I wanted to make sure the wireless was happily disabled so it couldn't complicate things.  (You can probably make it work with just wireless, or with them both enabled.)  So I used the Restricted drivers manager to get the driver for my wireless card, and then I used Gnome Network Manager to disable wireless.

Next I installed the PPTP plugin for Gnome Network Manager.  (E.g. System -> Add/Remove, search for 'vpn', select "VPN Connection Manager (PPP generic)".)

In theory now Network Manager should have an entry for VPN Connections.  If not try restarting network manager.

Now you can create a new VPN connection.  Go to Network Manager and choose VPN Connections -> Configure VPN ...

In the VPN Connections window that opens, choose Add. Click Forward, choose "PPTP tunnel" and click Forward. 

Now you're at the Connection tab. Give the connection a name. The Type should be Windows VPN (PPTP) and the Gateway 200.100.20.10 (in this example).

On the Authentication tab, make sure "Refuse EAP" is checked. 

On the Compression & Encryption tab, verify that "Require 128 bit MPPE encryption" and "Enable stateful MPPE" are checked. 

On the PPP Options tab, in addition to the other IP options already checked (Use Peer DNS and Exclusive device access), check the Debug Output box so you'll have debug info if there's a problem. I also changed the Packet parameters settings for MTU and MRU to 1500, but I don't know if that's essential. 

Finally on the Routing tab, "Peer DNS through tunnel" should be checked. Also check the "Only use VPN connection for these addresses" box and then type "192.168.1.0/24". This means that anytime you want to access an address that starts with 192.168.1 it will use the VPN, and otherwise it won't. That way when you're trying to browse the internet it doesn't use the VPN connection. Alternatively you could figure out exactly which addresses on the 192.168.1 network you need, and only list those. This could be advantageous if your home network, like mine, uses the same subnet as work (192.168.1). However listing the whole subnet does even work if you're in that situation - the only thing you can't do while the VPN is connected is access a home machine that has the same address as a machine at work. 

Click Apply. 

At this point you should bring up a Terminal and type 
```
sudo tail -f /var/log/syslog
```
in order to see debug messages.

In theory if you go back to the Gnome Network Manager VPN Connections it should show the connection you just made.  But it probably won't.  So as mentioned in earlier posts you want to go to another terminal and type
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```
Now watch the first terminal that is tailing the log and wait until messages in the terminal window completely stop.  Once they're finished, in the other terminal you just typed in you can now type
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart 
```

Now you can use Network Manager to try out the connection you've just created. It should work. 

In order to access both the internet and the intranet at the same time, you need to edit your routing table. Execute the following command in another Terminal window: 
```
route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
``` 

Each time you connect to the VPN you need to update the routing table, so you may want to put it in a script to execute.

After connecting to the VPN but before adding the route, in my case if you do
```
ip route show
```
in a terminal looks like:

    200.100.20.10 via 192.168.1.1 dev eth0
    192.168.1.0/24 dev eth0  proto kernel  scope link   src 192.168.1.97
    default via 192.168.1.1 dev eth0

Then once you add your route it adds

   192.168.1.0/24 dev ppp0  scope link

after the first entry.

---

### Post by AlexEagar on 2007-11-13
It would be very useful if someone could explain which connection settings in Windows map to which connection settings in the Linux VPN Network Manager. I have a working Windows configuration, but I don't know replicate those settings in Linux.

Here is my working configuration in Windows:
[LIST=1]
[*]Go to 'Start > Control Panel > Network Connections > Virtual Private Network'
[*]The connection icon displays the connection name, the connection status, the text 'WAN Miniport (PPTP)'
[*]Right click on the connection icon and select Properties
[*]General > Host name:  192.168.201.1
[*]General > Dial another connection first: Not Checked
[*]General > Show icon in notofiction area: Checked
[*]Options > Display progress while connecting: Checked
[*]Options > Prompt for name and password, certificate, etc.: Checked
[*]Options > Include Windows logon domain: Not Checked
[*]Options > Redial attempts: 3
[*]Options > Time between redial attempts: 1 minute
[*]Options > Idle time before hanging up: Never
[*]Options > Redial if the line is dropped: Not checked
[*]Security > Security options: Typical
[*]Security > Validate my identity as follows: Require secured password
[*]Security > Automatically use my Windows user name and password (and domain if any): Not Checked
[*]Security > Require data encryption (disconnect if none): Not Checked
[*]Networking > Type of VPN: Automatic
[*]Networking > Type of VPN > Settings > Enable LCP extentions: Not Checked
[*]Networking > Type of VPN > Settings > Enable software compression: Checked
[*]Networking > Type of VPN > Settings > Negotiate multi-link for single link connections: Not Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP): Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Obtain an IP Address Automatically: Selected
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Obtain DNS Server Address Automatically: Selected
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > General > Use default gateway on remote network: Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > DNS > DNS Server Addresses: Empty
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > DNS > Append primary and connection specific DNS Suffixes: Selected
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > DNS > Register this connection's addresses in DNS: Not Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > DNS > Append parent suffixes of the primary DNS suffix: Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > WINS > WINS addresses: Empty
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > WINS > Enable LMHOSTS lookup: Checked
[*]Networking > This connection uses the following settings > Internet Protocol (TCP/IP) > Properties > General > Advanced > WINS > Enable NetBIOS over TCP/IP: Selected
[*]Networking > This connection uses the following settings > QoS Packet Scheduler: Checked
[*]Networking > This connection uses the following settings > File and Printer Sharing for Microsoft Networks: Checked
[*]Networking > This connection uses the following settings > Client for Microsoft Networks: Checked
[*]Networking > This connection uses the following settings > Client for Microsoft Networks > Properties > RPC Service > Name service provider: Windows Locator
[*]Advanced > Windows Firewall > Settings > Let me know if you need to know these settings
[*]Advanced > Allow other network users to connect through this computer's Internet connection: Not Checked
[/LIST]

Now here are my VPN Connection settings in Ununtu 7.10:
[LIST=1]
[*]Connection > Name: DefaultSettingsWithDebugOutput
[*]Connection > Type: Windows VPN (PPTP)
[*]Connection > Gateway: 192.168.201.1
[*]Authentication > Athenticate Peer: Not Checked
[*]Authentication > Refuse EAP: Checked
[*]Authentication > Refuse CHAP: Not Checked
[*]Authentication > Refuse MS CHAP: Not Checked
[*]Compression & Encryption > Require MPPC Compression: Not Checked
[*]Compression & Encryption > Allow Deflate compression: Not Checked
[*]Compression & Encryption > Allow BSD Compression: Not Checked
[*]Compression & Encryption > Require MPPE encryption: Not Checked
[*]Compression & Encryption > Require 128 bit MPPE encryption: Checked
[*]Compression & Encryption > Enable stateful MPPE: Checked
[*]PPP Options > Custom PPP Options: Blank
[*]PPP Options > Use Peer DNS: Checked
[*]PPP Options > Require Explicit IP Addr: Disabled
[*]PPP Options > Exclusive divice access (UUCP-style lock): Checked
[*]PPP Options > Debug Output: Checked
[*]PPP Options > MTU: 1416
[*]PPP Options > MRU: 1416
[*]PPP Options > connect-delay: Disabled
[*]PPP Options > lcp-echo-failure: 10
[*]PPP Options > lcp-echo-interval: 10
[*]Routing > Peer DNS through tunnel: Checked
[*]Routing > Only use VPN connection for these addresses: Not Checked
[/LIST]

I just noticed some other settings on the Windows box which may be relavent:
[LIST=1]
[*]Go to 'Start > Control Panel > Network Connections > LAN or High Speed Internet > Local Area Connection > Right Click > Properties > Internet Protocol (TCP/IP) > Properties > Alternate Configuration'
[*]User Configured: Selected
[*]IP address: 192.168.202.187
[*]Subnet mask: 255.255.248.0
[*]Default gateway: 192.168.201.1
[*]Preferred DNS server: 192.168.201.1
[*]Alternate DNS server: 192.168.201.1
[*]Preferred WINS server: 192.168.201.1
[*]Alternate WINS server: 192.168.201.1
[/LIST]

I discovered these settings when I realized that I was not able to ping 192.168.201.1 from my Ubuntu machine. I then manually set my IP settings in Ubuntu to what they are in Windows and I could then ping 192.168.201.1 however, I think that having a manual IP address makes it so that Ubuntu no longer even tries to connect over VPN because I'm no longer getting messages logged to /var/log/ppp-connect-errors and the network icon no longer shows the conncting animation when I try to connect to the VPN. I don't have the Windows machine and the Ubuntu machine plugged in to the network at the same time. I imagine I'll probably need to have a different manual IP address to have them both on the network at the same time, but I'll worry about that after I can get my connection working.

So what settings should I change to get my VPN working?

---

### Post by cmnorton on 2007-11-19
>>I finally got this to work on a LiveCD of Gutsy Gibbon (Xubuntu 7.10) and it's really not that bad even if 
>>you have a DSL router on the client side
>>your subnet is the same as the one behind the VPN

Are you saying that if the subnet behind my employer's firewall is 10.100.0, my client side subnet also has to be 10.100.0, and not, say, 192.168.1?

---

### Post by cmnorton on 2007-11-19
> **cmnorton said:**
> What I have found is seems to be related to WEB encrypted networks. First, given these "roaming mode" settings, you have to be able to have a regular, non-VPN, connection. With manual connections and no Network-Manager installed I was able to connect on 6.06.

Under 7.04 NetworkManager auto configuration, I cannot connect on my WEP encrypted network. I can connect if I go with manual configuration.

Second, under 7.04 there are many reports that pptpconfig will not work. It also has been deprecated in favor of NetworkManager. If you are using NetworkManager for VPN, you first have to be able to have a non-VPN connection work. 

So far, I cannot have a non-VPN NetworkManager connection on my wep-encrypted network. I still have to go with manual configuartion. And, no NetworkManager means no NetworkManager VPN, at least in my case.

Wrinkle 1 is solved. I cleaned up the interfaces file, tried connecting at home. First I connected by wired network. Then, I searched for my wireless network, and connected to it. I had misinterpreted the login screen for my wep-encrypted network. I was supplying a 128-bit hex key, but not selecting the type as a 64/128 hex pass phrase.

Now, on to Wrinkle 2, using some of the excellent posts I've found today.

---

### Post by quick_dudley on 2007-11-20
> **jmooney said:**
> OK, installed ptppconfig and it's telling me that I have successfully connected to my VPN network at work.

Now what?   How do I browse this network?  I've tried entering various addresses into Nautilus and Firefox but it isn't working.  Assuming I have all the address and network names right, can't I just mount this as a network location?  Say by selecting "Places/Connect to Server..."?

My VPN is running, how do I browse the remote network?

Thanks,

Joe

You need to install samba and smbfs to actually mount windows shares.
In nautilus: in the address field type smb:/// to browse the windows "network places"

---

### Post by cmnorton on 2007-12-01
After doing a lot of testing, including speaking with eSoft support about how their firewall works, my adding a Cardbus Linksys wireless card was the final cure to connecting VPN. 

The advice in this and other notes regarding tweaking your settings was very important. My laptop is an older Acer Travelmate 630. I don't know what kind of wireless card is in it, but it's not as good as the Linksys.

---

### Post by jpastore on 2007-12-01
not sure if that is the best cure for the problem as my vpn connection did work. an update caused it to stop working. 

I'm anxiously awaiting the 0.7.0 gnome network manager release which claims to fix just about everything and cure cancer =)

---

### Post by pocomaxa on 2007-12-10
> **endersshadow said:**
> 

Then, a network icon will appear in your notification area.  Select it, and then select VPN Connections > Configure VPN.  Add your VPN to the list, and then in the terminal do the following:



I'm sorry but I have failed at the very 1st step, e.g. the VPN icon doesn't appear over the Network Manager icon. I've tried exactly what's been written here. Could you advise please what am I doing wrong? :confused:

thank you in advance!

poco

ps. I have Ubuntu 7.10, Gutsy Gibbon
pps. ok, on page 16th I see the question "has been answered". Have to re-read, sorry :( It would help editing the very 1st post.

---

### Post by jen3 on 2007-12-20
> **cmnorton said:**
> >>I finally got this to work on a LiveCD of Gutsy Gibbon (Xubuntu 7.10) and it's really not that bad even if 
>>you have a DSL router on the client side
>>your subnet is the same as the one behind the VPN

Are you saying that if the subnet behind my employer's firewall is 10.100.0, my client side subnet also has to be 10.100.0, and not, say, 192.168.1?

No, sorry for the confusion.  A (much earlier) post by someone had mentioned not knowing how to handle the situation when both subnets have the same address.  So I wanted to show that it could be done, and how.  I'd say it's actually preferable and simpler if your client side subnet is different than your employer's.  

To clarify, when you are setting up the VPN connection, on the Routing tab when you add a subnet address (in my example 192.168.1.0/24), it should be the subnet at work.  Similarly, at the very end when you add a route, that is also the work subnet.

---

### Post by Orfintain on 2008-01-05
Do I need IPV6 for this to work ?

---

### Post by musicinmybrain on 2008-01-08
Works flawlessly on Gutsy. Thanks!

---

### Post by thommo on 2008-01-14
realise this might not be the appropriate thread, but anyhoo.
has anyone had any success using a linux machine with a microsoft l2tp vpn that requires certificates?

---

### Post by legolas_w on 2008-01-19
Hi
I perform the installation steps according to first post of the thread.
but no new icon appeared in notification area?
there were two icons there, on is to monitor "network connection:eth0" and the other one an icon which when I click on it it shows a pop-up menue with one option: "Manually configuration..." is there something else that I should do?

Thanks

---

### Post by musicinmybrain on 2008-01-19
> **legolas_w said:**
> Hi
I perform the installation steps according to first post of the thread.
but no new icon appeared in notification area?
there were two icons there, on is to monitor "network connection:eth0" and the other one an icon which when I click on it it shows a pop-up menue with one option: "Manually configuration..." is there something else that I should do?

Thanks

Try doing ```
sudo NetworkManager restart
```. Maybe the VPN menu just hasn't showed up yet.

---

### Post by double07 on 2008-01-22
I'm trying get this setup at the moment (pretty much just used the defaults). I can connect the vpn ok, however when I'm connected I lose all Internet traffic and I can't seem to ping any hosts as I would normally be able to in windows. I can ping the IP of the server but normally I can ping a hostname. Once the vpn is connected, I'd like to be able to use the terminal server which is usually referred to by a hostname.

Any ideas?

---

### Post by kultex on 2008-02-01
same thing with me - I can connect to the VPN ok, but all traffic goes through the tunnel - as soon as I choose under Routing "Only use VPN connection for theses addresses" and add just one number - the apply butten is not any more available.
What can I do?

---

### Post by corwinckler on 2008-02-06
When I click on Network Manager in the 'tray' I only get one option coming up:
MANUAL CONFIGURATION

I cant find any place to configure a VPN.

The MANUAL CONFIGURATION brings up the extisting list of configured interfaces, with no menu items to add anything...

Any Ideas?

--Cor

UPDATE:
I searched for the problem under another thread. Found a solution that sounds terribly feeble, but worked for me. I went into manual configuration and enabled ROAMING MODE in the wireless (in spite of the fact that I was not even using wireless) and suddenly the menu came back when clicking network manager.....)

---

### Post by tango_ninja on 2008-02-19
same as **double07**....

when connected to VPN anything on the host network is fine, but I lose all internet access (i.e. i had to disconnect VPN to get here to ubuntuforums.org)

any reason why this is ??

---

### Post by 1jackjack on 2008-03-25
i dunno if this will help, but i was having that problem in windows; once connected to vpn, seems to try and use vpn's internet connection, so suddenly you internet is very slow/dies.

solution was:
network>ipv4>properties>advanced>ip settings: UNCHECK use default gate

maybe there is an equivalent in ubuntu?

---

### Post by RotarySMP on 2008-04-05
I am also a newbie. I am trying to connect to my ADSL ISP which uses a VPN through an old Alcatel speed touch home Ethernet ADSL modem, with a fix IP address.

Tried the Network manager route on: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

I am running Unbutu 7.10 (gutsy). It was interesting that the recommendation to install network-manager-pptp doesn't help as this package is not on the disk. (maybe it is in the Universe repository, but I didn't know such a thing existed when I tried tutorial two last week). Back to the WINXP boot (like now) and I found a .deb package of the network-manager-pptp and installed it.

I also installed pptp-linux, because it was in the repository and some of the how to's refer to it. Not sure if that was a good idea or not.

Using the Network manager I can install a VPN, but only with a roaming IP, which doesn't work.

I have done a bunch more research in the internet, and I seemd that this is a know BUG/Feature of teh network manager that it doesn't support Fix IP's and VPN's at the same time. Sounds like the 0.7 release of NM may or may not solve this. Therefore it would seem that Cricks manual config method in #121 may be the solution.

Following his manual config instructions, where you start with steps 1 thru 10 of James Camerons How to, I first used SUDO GEDIT and 

1/ add the following lines to the sources list file, /etc/apt/sources.list :

# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

---> This worked. on to step two.
2/  update the list of packages:

apt-get update
I don't think this worked. I Sudo'd it for good luck, but still just get....

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mark@mark-desktop:~$ sudo apt-get update
Err [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release.gpg
  Could not resolve 'quozl.netrek.org'
Err [http://quozl.netrek.org](http://quozl.netrek.org) ./ Translation-en_US
  Could not resolve 'quozl.netrek.org'
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Packages
Err [http://quozl.netrek.org](http://quozl.netrek.org) ./ Packages
  Could not resolve 'quozl.netrek.org'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://quozl.netrek.org/pptp/pptpconfig/./Release.gpg](http://quozl.netrek.org/pptp/pptpconfig/./Release.gpg)
  Could not resolve 'quozl.netrek.org'
Failed to fetch [http://quozl.netrek.org/pptp/pptpconfig/./en_US.bz2](http://quozl.netrek.org/pptp/pptpconfig/./en_US.bz2)
  Could not resolve 'quozl.netrek.org'
Failed to fetch [http://quozl.netrek.org/pptp/pptpconfig/./Packages.gz](http://quozl.netrek.org/pptp/pptpconfig/./Packages.gz)
  Could not resolve 'quozl.netrek.org'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

--->Since I wasn't sure if that represented a pass or a fail, I tried step three...

3/ install the PPTP Client GUI:

apt-get install pptpconfig
This didn't work, I got...

mark@mark-desktop:~$ sudo apt-get install pptpconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pptpconfig

---> I really appreciate Crick, and James Cameron for providing these two rescources, but I guess I need a further dumbed down version. I tried without success searching for a .deb version of the pptpconfig package on the web, as I haven't worked out how the TAR.GZ system works yet (and it is a real PITA having to reboot into WINXP every time I need to search for info in the internet).

---

### Post by street spirit on 2008-04-08
Thanks for the tutorial.

I kept running into errors with kvpnc on Kubuntu Dapper, and using the pptpconfig package fixed my problems.
For the archives, the message in the kvpnc debug output was "unrecognized option mppe" - apparently related to [this bug]("http://lists.alioth.debian.org/pipermail/pkg-kde-extras/2006-March/000565.html").

---

### Post by lucaspr on 2008-04-15
I'm trying to get VPN working here... In a Windows XP machine it works, but not in Ubuntu 7.10...

```

Apr 15 14:05:18 notebook1 NetworkManager: <info>  Will activate VPN connection 'mee*****', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'eigenaar', vpn_data 'ppp-connection-type / pptp / pptp-remote / 217.166.***.*** / usepeerdns / no / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / no / mtu / 1492 / mru / 1492 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / no / routes /  / use-routes / no', route ''. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 1 of 4 (Connection Prepare) scheduled... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6938) 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 1 of 4 (Connection Prepare) complete. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 2 of 4 (Connection Prepare Wait) complete. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 3 of 4 (Connect) scheduled... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 3 of 4 (Connect) sending connect request. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 3 of 4 (Connect) reply received. 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Apr 15 14:05:18 notebook1 NetworkManager: <info>  VPN Activation (mee*****) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Apr 15 14:05:18 notebook1 pppd[6939]: Plugin nm-pppd-plugin.so loaded.
Apr 15 14:05:18 notebook1 pppd[6939]: nm-pppd-plugin: plugin initialized.
Apr 15 14:05:18 notebook1 pppd[6941]: pppd 2.4.4 started by root, uid 0
Apr 15 14:05:18 notebook1 pppd[6941]: using channel 11
Apr 15 14:05:18 notebook1 pppd[6941]: Using interface ppp0
Apr 15 14:05:18 notebook1 pppd[6941]: Connect: ppp0 <--> /dev/pts/1
Apr 15 14:05:18 notebook1 pptp[6943]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Apr 15 14:05:18 notebook1 pptp[6946]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Apr 15 14:05:18 notebook1 pptp[6946]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Apr 15 14:05:18 notebook1 pptp[6946]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Apr 15 14:05:19 notebook1 pppd[6941]: nm-pppd-plugin: CHAP check hook.
Apr 15 14:05:19 notebook1 pppd[6941]: sent [LCP ConfReq id=0x1 <mru 1492> <asyncmap 0x0> <magic 0x49b36ac7> <pcomp> <accomp>]
Apr 15 14:05:19 notebook1 pptp[6946]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Apr 15 14:05:19 notebook1 pptp[6946]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Apr 15 14:05:19 notebook1 pptp[6946]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 60665). 
Apr 15 14:05:22 notebook1 pppd[6941]: sent [LCP ConfReq id=0x1 <mru 1492> <asyncmap 0x0> <magic 0x49b36ac7> <pcomp> <accomp>]
Apr 15 14:05:28 notebook1 last message repeated 2 times
Apr 15 14:05:29 notebook1 pppd[6941]: Terminating on signal 15
Apr 15 14:05:29 notebook1 pppd[6941]: sent [LCP TermReq id=0x2 "User request"]
Apr 15 14:05:29 notebook1 NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Apr 15 14:05:29 notebook1 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Apr 15 14:05:29 notebook1 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Apr 15 14:05:29 notebook1 NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'meewisse' because service was 6. 
Apr 15 14:05:29 notebook1 pptp[6946]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Apr 15 14:05:29 notebook1 pptp[6946]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Apr 15 14:05:29 notebook1 pptp[6946]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Apr 15 14:05:29 notebook1 pppd[6941]: Modem hangup
Apr 15 14:05:29 notebook1 pppd[6941]: Connection terminated.
Apr 15 14:05:29 notebook1 pppd[6941]: Child process /usr/sbin/pptp 217.166.**.*** --nolaunchpppd (pid 6942) terminated with signal 15
Apr 15 14:05:29 notebook1 pppd[6941]: Exit.

```

I've got a Microsoft VPN server here too, to which I can connect perfectly.. Works like a charm, but then I change the IP-address to the remote host (which we use in Windows and does work) then I get the above error. 

**EDIT:**

And the output of PPTPCONFIG (with debug ON)
```

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option: 
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>	Pass <number> to remote host as phone number
  --nolaunchpppd	Do not launch pppd, for use as a pppd pty
  --quirks <quirk>	Work around a buggy PPTP implementation
			Currently recognised values are BEZEQ_ISRAEL only
  --debug		Run in foreground (for debugging with gdb)
  --sync		Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>	Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer		Disable packet buffering and reordering completely
  --idle-wait		Time to wait before sending echo request
  --max-echo-wait		Time to wait before giving up on lack of reply
  --logstring <name>	Use <name> instead of 'anon' in syslog messages
  --localbind <addr>	Bind to specified IP address instead of wildcard
  --loglevel <level>	Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4
# uname -a
Linux notebook1 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/net/ppp_mppe.ko
version:        1.0.2
alias:          ppp-compress-18
license:        Dual BSD/GPL
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
author:         Frank Cusack <fcusack@fcusack.com>
srcversion:     39166EF06A40CF00F255FC5
depends:        ppp_generic
vermagic:       2.6.22-14-generic SMP mod_unload 586 
# grep mppe /proc/modules
Array
(
    [name] => mee******
    [server] => 217.166.***.**
    [domain] => 
    [username] => (Hidden by me...... :))
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 
    [require-mppe] => 1
    [nomppe-40] => 1
    [nomppe-128] => 
    [refuse-eap] => 1
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/mee******)
updetach		# (from command line)
logfd 1		# (from command line)
linkname mee******		# (from /etc/ppp/peers/mee******)
dump		# (from /etc/ppp/peers/mee******)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name vpngebruiker		# (from /etc/ppp/peers/mee******)
remotename mee******		# (from /etc/ppp/peers/mee******)
		# (from /etc/ppp/options.pptp)
pty pptp 217.166.***.*** --nolaunchpppd 		# (from /etc/ppp/peers/mee******)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam mee******		# (from /etc/ppp/peers/mee******)
proxyarp		# (from /etc/ppp/options)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
		# (from /etc/ppp/peers/mee******)
		# (from /etc/ppp/peers/mee******)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 14
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe65e1bd> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp 217.166.***.*** --nolaunchpppd , pid 7024
Script pptp 217.166.***.*** --nolaunchpppd  finished (pid 7024), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

Can somebody help me out here? Thanx in advance!

---

### Post by slolerner on 2008-04-15
i installed the network-manager-pptp in gutsy gibbon 7.10 without issue. i got to the vpn logon prompt where i was asked for my id and password. can the vpn connection be configured to require a pin+token code?

i've tried my domain user name and domain pw.. tried domain name\user name and domain password.. tried user name and pin+token code.. no joy.

i feel like i'm close, and likely missing something simple. any help would be greatly appreciated. thanks in advance.

---

### Post by legolas_w on 2008-04-15
hi
Thank you for reading my post
Does anyone knows whether in 8.04 we can have static IP address and VPN connection together or it is still a problem (In 7.10 we can not have VPN over a static IP address connection)

Thanks

---

### Post by nekur0 on 2008-04-27
> **legolas_w said:**
> hi
Thank you for reading my post
Does anyone knows whether in 8.04 we can have static IP address and VPN connection together or it is still a problem (In 7.10 we can not have VPN over a static IP address connection)

Thanks

Sadly, roaming still has to be enabled (no static IP)

---

### Post by legolas_w on 2008-04-28
Thank you for reply.
I will install Hardy next day and here is how my internet connection will work from next week.

- I have a ethernet ADSL modem and it is configured to connect to internet.
- My network connection uses DHCP to connect to my ethernet modem.

with this conditions, should I follow the instruction given in the first post to activate VPN?



thanks.

---

### Post by trspencer on 2008-05-31
I've been through a couple dozen posts, tried everything under the sun, but this combination of settings did the trick. Thanks very much.

---

### Post by OTll on 2008-06-01
Hey all,

Still having problems to connect to vpn at my work. Well, a bit the usual story as I've seen in other posts: it works like charm in Windows, but I can't get it to work in Ubuntu so far. 
I have a wireless usb-adapter, and I'm quite sure that it has something to do with it: I configured it like described in [http://dreamlinuxforums.org/index.php?topic=334.msg1933](http://dreamlinuxforums.org/index.php?topic=334.msg1933)
This means: manual configuration, 'manual' meaning 'from the console' in this context. Whenever I look at my 'network configuration' in Ubuntu, it doesn't show any of the connections running, although my network is working fine - well, probably due to the manual configuration of the wireless network. Seems logic so far, at least to me.

Now the VPN... I can configure a VPN network, and I can select it without any problems, so it asks my username and password, which I fill out of course, but it doesn't connect.
When I run sudo tail -f /var/log/syslog, I get the message I do not have an active network device (although I have one, but it is configured manually, since configuring with the gui doesn't work), so it's not connecting:
```

Jun  1 17:03:09 kurtpjoeter NetworkManager: <info>  Will activate VPN connection 'Colsen VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'kurt', vpn_data 'ppp-connection-type / pptp / pptp-remote / 84.53.116.189 / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Jun  1 17:03:09 kurtpjoeter NetworkManager: <WARN>  nm_vpn_manager_activate_vpn_connection(): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN. 

```

How can I make Ubuntu know that I have an active network device, or how can I activate the VPN connection another way?


Thanks a lot!
Kurt

---

### Post by OTll on 2008-06-02
Some additional information:
* I'm using Ubuntu Hardy Heron (8.04).
* My /etc/network/interfaces -file
```
auto lo
iface lo inet loopback

# WPA DHCP DHCP
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid pjoeternetwerkje
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=10
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=*<<my password>>*
pre-up iwpriv wlan0 set TxRate=0
mtu 1500

```
* I set my router so I always recieve the same ip-address for this computer (192.168.19.15):
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:4f:f1:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36298 (35.4 KB)  TX bytes:36298 (35.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:f3:19:e9  
          inet addr:192.168.19.15  Bcast:192.168.19.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12180 errors:0 dropped:20 overruns:20 frame:20
          TX packets:2720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2871520 (2.7 MB)  TX bytes:560390 (547.2 KB)

```

Any help, please?

Thanks,
Kurt



> **OTll said:**
> Hey all,

Still having problems to connect to vpn at my work. Well, a bit the usual story as I've seen in other posts: it works like charm in Windows, but I can't get it to work in Ubuntu so far. 
I have a wireless usb-adapter, and I'm quite sure that it has something to do with it: I configured it like described in [http://dreamlinuxforums.org/index.php?topic=334.msg1933](http://dreamlinuxforums.org/index.php?topic=334.msg1933)
This means: manual configuration, 'manual' meaning 'from the console' in this context. Whenever I look at my 'network configuration' in Ubuntu, it doesn't show any of the connections running, although my network is working fine - well, probably due to the manual configuration of the wireless network. Seems logic so far, at least to me.

Now the VPN... I can configure a VPN network, and I can select it without any problems, so it asks my username and password, which I fill out of course, but it doesn't connect.
When I run sudo tail -f /var/log/syslog, I get the message I do not have an active network device (although I have one, but it is configured manually, since configuring with the gui/NetworkManager doesn't work), so it's not connecting:
```

Jun  1 17:03:09 kurtpjoeter NetworkManager: <info>  Will activate VPN connection 'Colsen VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'kurt', vpn_data 'ppp-connection-type / pptp / pptp-remote / 84.53.116.189 / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Jun  1 17:03:09 kurtpjoeter NetworkManager: <WARN>  nm_vpn_manager_activate_vpn_connection(): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN. 

```

How can I make Ubuntu know that I have an active network device, or how can I activate the VPN connection another way?


Thanks a lot!
Kurt

---

### Post by Vel0x on 2008-06-12
deleted - being an idiot

---

### Post by BU_ on 2008-10-08
Hi, is it possible to connect to Microsoft PPTP VPN using an Ubuntu/Kubuntu LiveDVD (without having system installed)? Thanks.

---

### Post by StrangeWill on 2008-10-11
I got an interesting issue, I add my VPN to the list, I click on it, put in my login information, hit enter.... and the window goes away and I get nothing, no error message, no network connection, nothing.

This kind of sucks, works fine on windows.

---

### Post by Mikorist on 2008-11-27
> **StrangeWill said:**
> I got an interesting issue, I add my VPN to the list, I click on it, put in my login information, hit enter.... and the window goes away and I get nothing, no error message, no network connection, nothing.

This kind of sucks, works fine on windows.


[http://ubuntuforums.org/showthread.php?t=994185](http://ubuntuforums.org/showthread.php?t=994185)

it will work on any distribution... :guitar:

---

### Post by Hypocritus on 2008-12-04
> **StrangeWill said:**
> I got an interesting issue, I add my VPN to the list, I click on it, put in my login information, hit enter.... and the window goes away and I get nothing, no error message, no network connection, nothing.

This kind of sucks, works fine on windows.

Hey, when you put in your creds and hit enter, you should see some activity on your network manager tray icon, where your nm-applet shows your network status. If you do not get any popups telling you that the connection failed, then it should have succeeded and you should be connected, and you should have a lock on your network manager tray icon (in x/ubuntu).

---

### Post by High Camp on 2009-02-23
Hi All

The new company I work for insists on using a VPN but I insist on using my personal laptop and having the ability to connect from home. I've been messing around with this for a few days now. On Friday I was able to connect and use the VPN but today I was not. I was thinking I had changed nothing between but then I realized I changed how I connect to the internet, I bought a wireless router. I connected my laptop via the CAT5 cable and all of a sudden the VPN worked again. I have tried the following in my "messing around":
1. While connected via wireless to the VPN, connecting to the internet - doesn't work.
2. While connected via CAT5 to the VPN, connecting to the internet - Works and is fast enough for me to believe its not going through the VPN.
3. While connected via wireless to the VPN, connecting to the shares on the remote network - Doesn't work.
4. While connected via CAT% to the VPN, connecting to the share on the remote network - Works
5. While connected via wireless, creating a new VPN connection - All the same problems persist (I set up the connection originally while on CAT5 so figured it could some how have an impact).

Since I can't connect to the internet while connected to the VPN I don't think it's a router issue, but I could be wrong. Either way, for those having problems it gives you something to think about and some tests to do to figure out exactly where the problem lies. For me, it would be ideal to connect via wireless but I can live without.

Hope that helps,

Update: I can connect my work laptop running windows to the VPN on wireless but cannot connect my personal laptop running Ubuntu on wirless, but I can on the wired connection. This seems very odd to me, I don't know why the network connection would play a role in this.

---

### Post by digao45 on 2009-04-15
[COLOR="Blue"][QUOTE][QUOTE=Buenaventura Durruti;651230]I couldn't pass installation :-(

$ sudo apt-get install pptpconfig
Reading package lists... Done[/COLOR]

**********************************

the pptpconfig seems to be old in ubuntu:

*"On distributions that support NetworkManager, pptpconfig is deprecated in favour of the PPTP Plugin for Network Manager. On Ubuntu and derivatives the package name is **network-manager**-pptp."*

[http://quozl.netrek.org/pptp/pptpconfig/pptpconfig.phtml]("http://quozl.netrek.org/pptp/pptpconfig/pptpconfig.phtml")

---

### Post by mgmiller on 2009-04-17
> It will connect with windows VPN?Yes it will.  Here is how to install and configure it:

You need to install 2 packages:
network-manager-pptp
pptp-linux
If you do the first, it will install the second as a dependency. 

Open Network Configuration (System, Preferences, Network Configuration).
Highlight your VPN connection, hit Edit.

At IPv4 Settings Tab: choose method Automatic (VPN).

At VPN Tab:
1 - input the IP address of the target computer.
2 - input your user name. Leave all else blank, unless you are tunneling to a domain, then enter the domain name where indicated.
3 - hit Advanced button.

At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2.

At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.

At Echo: check Allow PPP echo packets.
Leave all else blank. Hit OK, OK to save and get out.

Note: Your password is requested on VPN startup. I did not try to add it to the keyring.

Once the vpn is open, you can remote desktop over it by entering the nat address of the machine on the other side.
To browse, now the browse network gui may work, you may need to manually enter the (for example) 10.0.0.5 (or whatever the natted addresses look like) in the top and click reload a few times.
or if you saved it as a bookmark, select it and then click reload a few times.

You may need to enter gvfs-mount smb://url  example: gvfs-mount smb://10.0.0.5, although, I found clicking reload a few times above
seems to work well.

---

### Post by trspencer on 2009-04-18
I've tried a number of suggestions listed here, the only way I've been able to successfully connect to a Microsoft VPN (in 8.10) is via kvpnc. 

That's not entirely true...I can connect without it, but I have the same routing issues listed above (can't disable using the default gateway on remote network). 

The kvpnc interface gives you the option to keep your existing route and send all traffic within a user-defined IP range through ppp0, while all other traffic traverses your local connection.

---

### Post by pinakas on 2009-04-21
Hello.............

I have switch from xp to ubuntu.

As vpn account  I use the hotspotvpn.com

I have download the pptp manager and i have add the following settings:

Gataway: es.hotspotvpn.com
Authentication: MSCHAP2
Use point to pointe encryption : 128 bit
Stratefull connection: yes
all the other options unchecked. SOmetimes i check send ppp echo packets.

I get always a timed out error. See what the log says: what does it mean?
I have the 9.04 with all updates installed,
I tried various combinations with no use,

pr 21 22:08:18 eleftherios-laptop pppd[4880]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 21 22:08:18 eleftherios-laptop pppd[4880]: pppd 2.4.5 started by root, uid 0
Apr 21 22:08:18 eleftherios-laptop pppd[4880]: Using interface ppp7
Apr 21 22:08:18 eleftherios-laptop pppd[4880]: Connect: ppp7 <--> /dev/pts/8
Apr 21 22:08:26 eleftherios-laptop pppd[4880]: CHAP authentication succeeded

---

### Post by ultratux on 2009-06-21
I got this same timeout problem. Occurs every 2min approximately. Seems to be a bug:
[http://ubuntuforums.org/showthread.php?p=6133370](http://ubuntuforums.org/showthread.php?p=6133370)

Ubuntu 9.04, 64-bit

---

### Post by michwill on 2009-07-15
How do you perform all steps from the command line?  I ask because I am currently out of the office and won't be back for another week or so.  I do, however, have SSH access to the Linux machine which I use to VPN to another campus.  I've tried X forwarding to use the GUI, but it fails.

---

### Post by arnoldjames on 2009-07-17
Sorry for being slow to get this, this thread does not appear to tell me how-to yet.  using HH 8.04.  I connect to a VPN with no trouble, such that even VirtualBox winxp can browse to the IP address of the server 192.168.1.2.  The VPN routing config won't light up the "apply" button in network manager unless there is a slash and number: /24 or something.  I have no idea what number might be appropriate.  Next is how do you browse the files on the server?  I expected to enter 192.168.2.1 in nautilus and see the server files.  But nope, it says it can't handle this.  In windows it is proceeded by 2 slashes \\, but // doesn't work either.  

At the moment I will continue to use VirtualBox and Windows XP reluctantly to do this file access.

---

### Post by michwill on 2009-10-04
> **trspencer said:**
> The kvpnc interface gives you the option to keep your existing route and send all traffic within a user-defined IP range through ppp0, while all other traffic traverses your local connection.

Has anyone made any progress on this issue under Gnome?  I need to keep my local IP and local access for everything else.  Are there any managers that allow this?  It would appear that "Network Manager" has an option, but it doesn't seem to work -- all traffic is still sent through the connection.

---

### Post by mstjohn1974 on 2009-10-27
Try this one, that's what I do and it works

[http://mstjohn1974.blogspot.com/2009/10/vpn-into-microsoft-pptp-server-with.html](http://mstjohn1974.blogspot.com/2009/10/vpn-into-microsoft-pptp-server-with.html)

---

### Post by aaronLund on 2009-10-31
Doesn't seem to work in 8.10.

What a discouraging issue.............

---

### Post by mgmiller on 2009-10-31
> Doesn't seem to work in 8.10.

What a discouraging issue.............

True,  I couldn't get it to work in 8.10 either.  It does work well in 9.04 and 9.10.  I use it every day.

---

### Post by elperrillo on 2009-11-29
Best article I have found on the subject, Works from 8.04 to 9.10 (Karmic Koala)

[http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/](http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/)

---

### Post by TidyBhoy on 2010-01-18
Does any1 find there vpn connection Randomly disconnects? sometimes after a few minutes, other times after a few hours?

---

### Post by eklem on 2010-01-19
Yes, the few times I get it to connect, it disconnects after a while.

---

### Post by mgmiller on 2010-01-19
I have not noticed any random disconnects.  I use my vpn almost every day and it hooks right up every time (The only time it's failed to connect, was a router problem on the office side that needed to be rebooted.).  I'm usually not connected for longer than a half hour at a time though, so I can't comment on it's long term stability.

---

### Post by TidyBhoy on 2010-01-19
just out of interest whats your advanced settings look like Network Manager? I found it incredibly irritating... a fix would be a god send.

---

### Post by mgmiller on 2010-01-19
My advanced settings are as follows:

Authentication:
I unchecked PAP and EAP, all the others are checked.

Security & Compression:
Allow Stateful Encryption is checked, all others unchecked.

Echo:
Send PPP echo packets is checked.

That's it.

---

### Post by TidyBhoy on 2010-01-19
thanks for that my man! i've the same.. such a wierd random problem :(

---

### Post by mgmiller on 2010-01-21
The only other thing I can think of is that I do not use DHCP on either end.  Both my office server and my home machine are on static IP addresses and I am forwarding port 1723 on the server side.

---

### Post by ruuebs on 2010-05-16
Has anyone successfully managed to get this working in lucid? I have tried many of the suggestions on this page, with so far no luck.

It's frustrating that it works perfectly on Win-XP (running on vmware), using the default settings with almost no configuration. I wonder if it is possible to find out the default settings that Windows uses, then replicating them exactly on Ubuntu...

---

### Post by mgmiller on 2010-05-16
> Has anyone successfully managed to get this working in lucid?Yes, it continues to work perfectly after my upgrade from Karmic to Lucid.

In case you don't want to try to find the info posted earlier in this thread, here is how I did it starting with a clean install of Karmic.  After I got it working in karmic, I did the Lucid upgrade and no further action was required.  It just continued to work.

Before trying this, be sure your router allows PPTP service.

You need to install 2 packages:
network-manager-pptp
pptp-linux
If you do the first, it will install the second as a dependency. 

Reboot the computer.  (This is important, don't skip this step)

Open Network Configuration (System, Preferences, Network Configuration).
Highlight your VPN connection, hit Edit.

At IPv4 Settings Tab: choose method Automatic (VPN).

At VPN Tab:
1 - input the IP address of the target computer in the gateway field.
2 - input your user name. Leave all else blank, unless you are tunneling to a domain, then enter the domain name where indicated.
3 - hit Advanced button.

At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2. Uncheck all others.

At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.

At Echo: check Allow PPP echo packets.
Leave all else blank. Hit OK, OK to save and get out.

Log off  (also important, don't skip this step)
Log on

Note: Your password is requested on VPN startup. You can add it to the default keyring if you want, or leave it out for a little more security.

Once the vpn is open, you can remote desktop over it by entering the nat address of the machine on the other side.
To browse, now the browse network gui may work, you may need to manually enter the IP of the remote machine (eg. 10.0.0.5) in the top.  You may need to click reload a few times.
Or if you saved it as a bookmark, select it and you may again have to click reload a few times.

You may need to enter gvfs-mount smb://url  example: gvfs-mount smb://10.0.0.5, although, I found clicking reload a few times above seems to work well.

In fact, since 9.04, clicking reload was not needed at all.  The clicking reload bit was needed in Intrepid (8.04), which is what these instructions were originally written for.

---

### Post by atyankov on 2010-06-30
Despite the thorough explanation above I still seem to have problems connecting to a Microsoft VPN.
I installed 10.04 today => I have the pptp-packages, I configured my VPN connection (un)chiecking the necessary boxes (trying other combinations as well) and I'm quite sure my router allows PPTP since this connection was running on Win-XP without difficulties.

The error message I get is "VPN Connection Failed" without further information... :S

Where could another problem hide?

---

### Post by mgmiller on 2010-06-30
The only other things I can think of are that I am running static IP addresses on both my windows XP server and on my Ubuntu machine.  Also, don't assume anything about your routers.  Make sure you have pptp pass through enabled and if needed, forward port 1723 to the appropriate machines.

If you followed my how to above, you should have rebooted at one point and then logged off and back on at another.  These are very important steps, if you did not do both where indicated, it will not work.

---

### Post by atyankov on 2010-07-01
I followed your how-to step-by-step at least 5 or 6 times. I even uninstalled both packages to have a clean start. All IP's are static here, the server assigns me per DHCP always the same address which is fixed with the dial-in rules for my user.
Is it wrong to assume that I have access through pptp since it worked flawlessly on windows?

And is there a possible way to find out where exactly the connecting process goes wrong? Is it with the connection itself or with the authentication.....?

And another thing: since settings tend to be so delicate, do I have to check during the configuration for example "Connect automatically" or "Available to all users" ? :))

---

### Post by mgmiller on 2010-07-01
> All IP's are static here, the server assigns me per DHCP always the same  address which is fixed with the dial-in rules for my user.This statement confuses me.  Either you have static IP or you have DHCP, it can't be both.  I am using static IP at both ends, both my server and home machine.  

I also have routers at both ends and both of them had to be configured correctly.

> Is it wrong to assume that I have access through pptp since it worked  flawlessly on windows?Since it's not working for you, I would not assume anything.

> do I have to check during the configuration for example "Connect  automatically" or "Available to all users" ?
Yes, on the Ubuntu side, when you set up the static IP in network connections, both of those items should be checked.

What I suggest is to check both routers configurations to make sure that PPTP pass through is enabled.  Since every brand of router is different in how you do this, you may need to Google for information for your specific routers.  Then, temporarily place both machines into the DMZ on their respective routers and try again.  This way, you are taking port forwarding and other filtering out of the equation.

---

### Post by atyankov on 2010-07-01
I succeeded today connecting as i brought my notebook to another place (away from home), which means the problem is as you say somewhere in the outgoing router (with the server is everything fine).... the other problem is that I have to contact my system administrator tomorrow and ask him to open the corresponding port for me  :D
I hope it is always trying to go through port 1723 no matter if linux or windows?
Anyway, sorry I wasted your time a little and thanks for your help :)

And yes, I use DHCP as a "VPN User/Client" but the assigned IP is always the same because I've set it so on the server machine. So it is not 'static' as in what you meant about your case.

---

### Post by josepcoves on 2010-08-24
Hi mgmiller,

Thanks a lot for your post!! I finally managed to connect to the VPN, the proof is ping responds to an internal address!

Now I have the following problem: I have an apache application on port 8080, at the machine which is responding to the ping, but I cannot access through the browser. Do I have to change any other configuration to forward ports? I also tested to connect this VPN at the same router with a Windows machine and it works, so it should be a linux configuration problem... any ideas?

---

### Post by mgmiller on 2010-08-25
Your problem is a little beyond my experience level.  That being said, you could look in the following area.....
Left click the network icon in your top panel and select VPN Connections > Configure VPN.

Select the connection you want to modify and click "Edit"

Go to the IPv4 settings tab and click the "Routes" button at the bottom.

Click the Add button and fill in the info you need.

Put a check mark in the "Use This Connection only for resources on its network" check box.

Click OK and then click apply.

Close out of the configure VPN options.

Open the VPN and see what happens.

I suspect some variation of the above instructions should get you going.  If you are successful, please post back here with your solution as an aid to others viewing this thread.

---

### Post by zzarko on 2010-08-29
I had a problem connecting to my faculty's VPN, but I solved it like this:
1. I created VPN connection with PAP and EAP unchecked, I enabled point-to-point encryption, selected 128-bit security and checked stateful encryption (as adviced on this thread)
2. Because I use Firestarter, I added rules for Microsoft VPN (as stated in [http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php)) to /etc/firestarter/user-pre:
```
 # Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```If you use another firewall frontend, find where to put these lines (I'm not familiar with iptables, but I guess this is it's notation). Or, If you don't need it, disable the firewall, it should work straight away.
3. In Firestarter, I added my VPN server in "Policy/Allow connections from host" and added rule for same host to "Policy/Allowed service" for port 1723
4. Restart firewal - and it works (at least, in my case... :P )

---

### Post by zaigham_tt on 2010-09-24
Dear all fellows,

i have installed Linux i.e ubuntu 10.04 on my PC in which i have installed pptp client and able to connect it successfully but problem is that it unable to browse internet. in windows it works fine.
Kindly help me out.
Regard,
Syed Zaigham Ali.

---

### Post by kartal on 2010-10-18
> **endersshadow said:**
> This process has been made MUCH 
```
sudo route add -net 11.22.0.0 netmask 255.255.0.0 dev ppp0
```
(substitute 11.22.0.0 for your network)

For a more complete guide, check out this site:
[http://pptpclient.sourceforge.net/howto-debian.phtml#install](http://pptpclient.sourceforge.net/howto-debian.phtml#install)

Holly CRAPPP, that is what I needed exactly. Thank you

I was searching for a solution to my VPN disconnect for hours.

Btw I have 2 questions, I hope that someone could help me out

-How can I automatically start this connection during startup?

-I just want certain connections to go through the Vpn, not all my internet traffic. How do I do that with the manual setup. I always had issues with the gui VPN so I need to stick to manual configs.


thanks again

---

### Post by f0rcegr0wn on 2010-11-26
Any news on the 10.x connection side? Being trying it for a while with no success (based on settings suggested here).

---

### Post by soltaran on 2011-03-22
I've a working, DNSing Maverick VPN connection - it will connect successfully to a WinXP Pro VPN server.
Be aware; make sure that the network at the client end of the VPN doesn't have the same subnet as that of the VPN server end
or the system can get confused with who's talking to what.

Pulling up the VPN connections settings, I have the usual General/Optional entries (IP/gateway name, username/password).

Under ADVANCED:  Use MPPE (automatically selects legal authentication protocols), and all tickboxes under Security & Compression, and 'send echo'.

IPv4 Settings.

Method: Addresses only!
DNS servers: IP of the DNS server at the far end of the VPN
Search domain: Name of the domain at the far end (allows ping by machine name only or by FQDN)

Routes: (example)
If VPN server IP is 192.168.2.60, then ...
Address: 192.168.2.0
Netmask: 255.255.0.0
Gateway: 192.168.2.60 (the VPN server)
Metric:  1

untick 'ignore ... routes'
tick 'use ... resources on its network'

This allows me to use 'Connect to server' using the machine name to see the shares available for connection.

---

### Post by newbiefly on 2011-07-22
thank you so much mgmiller i am now vpning!

> You need to install 2 packages:
network-manager-pptp
pptp-linux
If you do the first, it will install the second as a dependency. 

Reboot the computer. (This is important, don't skip this step)

Open Network Configuration (System, Preferences, Network Configuration).
Highlight your VPN connection, hit Edit.

At IPv4 Settings Tab: choose method Automatic (VPN).

At VPN Tab:
1 - input the IP address of the target computer in the gateway field.
2 - input your user name. Leave all else blank, unless you are tunneling to a domain, then enter the domain name where indicated.
3 - hit Advanced button.

At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2. Uncheck all others.

At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.

At Echo: check Allow PPP echo packets.
Leave all else blank. Hit OK, OK to save and get out.

Log off (also important, don't skip this step)
Log on

Note: Your password is requested on VPN startup. You can add it to the default keyring if you want, or leave it out for a little more security.

Once the vpn is open, you can remote desktop over it by entering the nat address of the machine on the other side.
To browse, now the browse network gui may work, you may need to manually enter the IP of the remote machine (eg. 10.0.0.5) in the top. You may need to click reload a few times.
Or if you saved it as a bookmark, select it and you may again have to click reload a few times.

You may need to enter gvfs-mount smb://url example: gvfs-mount smb://10.0.0.5, although, I found clicking reload a few times above seems to work well.

In fact, since 9.04, clicking reload was not needed at all. The clicking reload bit was needed in Intrepid (8.04), which is what these instructions were originally written for.

---

### Post by saeed144 on 2011-08-02
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

### Post by giuseph90 on 2011-11-08
I gave Guarddog a try but it didn't really have that much difference with Firestarter regarding the methods on how to do it. Anyway, if any of you guys want some VPN protection for your ipad, better check out this great [VPN for ipad]( http://www.vpnchoice.com/blog/ipad-vpn/) I myself am using. Trust me it works.

---


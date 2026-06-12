---
title: "HOWTO: Create Wired/Wireless Router with dnsmasq"
date: 2008-03-05
forum: Tutorials
---

### Post by hedgefighter on 2008-03-05
I made my own custom wireless and wired router and I had to search around a lot to figure out how to do it. So, I decided to post what I did here to help others. I don't have much time to field a lot of questions or suggestions so I hope others can answer any questions.

Alright! Let's get started.

[SIZE="4"]Tutorial Instructions[/SIZE]
[INDENT]This tutorial will show you how to create a wireless **and/or** wired router. Instructions in **[COLOR="Green"]green[/COLOR]** are only necessary for the wired router. Things in **[COLOR="DarkOrchid"]purple[/COLOR]** are for wireless only. So, if you only want a wired router, ignore the **[COLOR="DarkOrchid"]purple[/COLOR]** stuff. If you only want a wireless router ignore the **[COLOR="Green"]green[/COLOR]** stuff. If you want both, then follow all instructions. If you want neither, then why are you reading this? For input in files **bold** things are lines you need to add, and things in [COLOR="Red"]red[/COLOR] must be changed. Things _underlined_ are optional.[/INDENT]

[SIZE="4"]What you need[/SIZE]
[INDENT]A computer w/ a wired network card
Monitor and Keyboard (only necessary for installation)
An ubuntu server CD ([[COLOR="Blue"]Get it here[/COLOR]]("http://www.ubuntu.com/getubuntu/download-server"))
[COLOR="DarkOrchid"]A wireless network card[/COLOR]
[COLOR="Green"]A second wired network card[/COLOR]
[COLOR="Green"]A switch[/COLOR] ([[COLOR="Blue"]One of these is fine[/COLOR]]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Description=Switch&x=0&y=0")) [COLOR="Green"]or a crossover cable if you only want one computer on your LAN[/COLOR][/INDENT]

[SIZE="4"][COLOR="DarkOrchid"]Choosing a wireless card[/COLOR][/SIZE]
[INDENT]You need to make sure that the wireless card you choose not only works in Linux but can be put into Master Mode. Unfortunately, I couldn't find any good resources on that. I'm using a [[COLOR="Blue"]D-Link DWL-G550[/COLOR]]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1271195&CatId=2691") because it has an external antenna and it works in Linux in Master Mode.[/INDENT]

[SIZE="4"]Install Ubuntu[/SIZE]
[INDENT]Install according to your wishes. If you need help there, a good tutorial is [[COLOR="Blue"]here[/COLOR]]("http://howtoforge.com/perfect_server_ubuntu7.10"). [B]
You only need to follow the first 2 pages of that tutorial![/B]

[COLOR="Green"]You will be prompted to select which interface you want to be configured with DHCP. Just choose the first one unless you have some reason to do otherwise.[/COLOR]
[/INDENT]

[SIZE="4"]Get started[/SIZE]
[INDENT]Instead of sudoing a lot, we'll just become root:
```
sudo -s
```[/INDENT]

[SIZE="4"][COLOR="DarkOrchid"]Get your wireless working[/COLOR][/SIZE]
[INDENT]Install the drivers for your wireless card. If you're not using an Atheros chipset you'll have to find instructions elsewhere to get it going then move on the the next part. If you do have an Atheros then read on.

Check if you have an Atheros card:
```
lspci | grep Atheros
```

If that shows your card you're good to install the driver. You can check for compatibility [COLOR="Blue"][here[/COLOR]]("http://madwifi.org/").

The newer Atheros drivers don't support Master mode. We need to install the older madwifi driver. We'll get the latest stable madwifi driver with subversion.
```
sudo aptitude install linux-headers-`uname -r` subversion build-essential
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi
```

This will take a little bit. Then we'll install the driver:
```
cd madwifi
sudo make
sudo make install
```

And we need to blacklist the other Atheros drivers.
```
nano /etc/modprobe.d/blacklist.conf
```
and add these lines:
```
[B]blacklist ath9k
blacklist ath5k
[/B]
```
Save and exit (Ctrl+X)

Now you'll need to put it in Master Mode. Edit this file
```
nano /etc/modprobe.d/madwifi.conf
```
and type this:
```
**options ath_pci autocreate=ap**
```
Save and exit (Ctrl+X)[/INDENT]

[SIZE="4"]Configure your network interfaces[/SIZE]
[INDENT]Check to make sure your internet is plugged in and working. [COLOR="Green"]If you have more than one wired card you may need to try both cards to find the one setup with DHCP.[/COLOR] Test with:
```
ping google.com
```
If you get a response then you're good to go. [COLOR="Green"]If you don't get a response, try the other card.[/COLOR]

Assuming that's working, take a look at your interfaces:
```
ifconfig -a
```

You should see all your interfaces. [COLOR="DarkOrchid"]If your wireless (probably ath0) isn't showing up, then something went wrong installing the drivers.[/COLOR] eth0 should be your WAN and should have an "inet addr" assigned. [COLOR="Green"]eth1 would be your LAN interface. If eth1 has an inet addr assigned then your eth0 and eth1 are switched. That means that from now on you need to swap these in the rest of the tutorial instructions.[/COLOR]

Now, we need to setup your ip addresses. If you have both wired and wireless interfaces there are two options. The first option serves different ip addresses to either the wired and wireless networks. It doesn't affect whether the computers in the LAN can see each other, it just gives them different ip addresses. The second option bridges the interfaces together into one so that ip addresses are served from a common pool. If you just have wired or just wireless, follow the first option instructions.

[SIZE="3"]**Option 1 (Keep them separated)**[/SIZE]
[INDENT]Since most commercial routers use 192.168.0.xxx, [COLOR="Green"]I chose 192.168.1.xxx for the LAN,[/COLOR] [COLOR="DarkOrchid"]and 192.168.2.xxx for the WLAN[/COLOR]. You're free to choose whatever you want, but be careful to propagate those changes to the rest of the instructions. Let's set them up:
```
nano /etc/network/interfaces
```
You file should look like this after you add the lines in bold:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B][COLOR="Green"]auto eth1
iface eth1 inet static
	address 192.168.1.1
	network 192.168.1.0
	netmask 255.255.255.0
	broadcast 192.168.1.255[/COLOR]

[COLOR="DarkOrchid"]auto ath0
iface ath0 inet static
	wireless-mode master
	wireless-essid [COLOR="Red"]myessid[/COLOR]
	_wireless-key s:[COLOR="Red"]mykey[/COLOR]_
        _wireless-channel [COLOR="Red"]1[/COLOR]_
	address 192.168.2.1
	network 192.168.2.0
	netmask 255.255.255.0
	broadcast 192.168.2.255[/COLOR][/B]
```
[COLOR="DarkOrchid"]_The first underlined line is for wireless encryption. It is not necessary, but recommended._ Change **[COLOR="Red"]myessid[/COLOR]** to whatever you want your wireless network to be called. _And change **[COLOR="Red"]mykey[/COLOR]** to whatever ASCII password you want to use. The second line lets you change the channel in case a particular channel is heavily used.[/COLOR]_

Save and exit (Ctrl+X).
[/INDENT]

[SIZE="3"]**Option 2 (Bridge them)**[/SIZE]
[INDENT]First we need to install the necessary packages to bridge the interfaces:
```
apt-get install bridge-utils
```

Since most commercial routers use 192.168.0.xxx, I chose 192.168.1.xxx for the LAN/WLAN. You're free to choose whatever you want, but be careful to propagate those changes to the rest of the instructions. Let's set them up:
```
nano /etc/network/interfaces
```
You file should look like this after you add the lines in bold:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B]#Internal(LAN) interface eth1 is brought up when br0 is

auto ath0
iface ath0 inet manual
	wireless-mode master
	wireless-essid [COLOR="Red"]myessid[/COLOR]
	_wireless-key s:[COLOR="Red"]mykey[/COLOR]_
        _wireless-channel [COLOR="Red"]1[/COLOR]_

#Network bridge
auto br0
iface br0 inet static
       address 192.168.1.1
       network 192.168.1.0
       netmask 255.255.255.0
       broadcast 192.168.1.255
       bridge-ports eth1 ath0[/B]
```

_The first underlined line is for wireless encryption. It is not necessary, but recommended._ Change **[COLOR="Red"]myessid[/COLOR]** to whatever you want your wireless network to be called. _And change **[COLOR="Red"]mykey[/COLOR]** to whatever ASCII password you want to use. The second line lets you change the channel in case a particular channel is heavily used._

**Note: Instructions with the bridged interface will be a little different later on so pay attention.**

Save and exit (Ctrl+X).
[/INDENT]


Reboot and verify that the interfaces have the ip addresses you just chose for them:
```
reboot
ifconfig
```[/INDENT]

[SIZE="4"]Serve up some ip addresses[/SIZE]
[INDENT]Now it's time to setup dnsmasq to give ip addresses and DNS services to your LAN/WLAN.

Install it:
```
sudo -s
apt-get install dnsmasq
```

Now let's set it up:
```
nano /etc/dnsmasq.conf
```

For non-bridged interfaces, go to the end of the file and add the following lines:
```
[B][COLOR="Green"]interface=eth1
dhcp-range=192.168.1.100,192.168.1.250,72h[/COLOR]

[COLOR="DarkOrchid"]interface=ath0
dhcp-range=192.168.2.100,192.168.2.250,72h[/COLOR][/B]
```

And if your interfaces are bridged, go to the end of the file and add the following lines instead:
```
[B]interface=br0
dhcp-range=192.168.1.100,192.168.1.250,72h[/B]
```
Save and exit (Ctrl+X).

Restart dnsmasq:
```
/etc/init.d/dnsmasq restart
```[/INDENT]

[SIZE="4"]Test dnsmasq[/SIZE]
[INDENT][COLOR="Green"]Hook up your switch from your 2nd wired card and hook another computer into the switch. Your other computer should be able to connect and receive an ip address.[/COLOR]

[COLOR="DarkOrchid"] You should see your wireless network on another wireless computer. Go ahead and connect _with your key_. You should be able to connect and receive an ipaddress.[/COLOR]

Check your ip address on your other computer(s):
```
ifconfig
```
The ip should match the ip addresses that dnsmasq is supposed to serve.

**Note: Although your LAN/WLAN computers are connected, there's no internet yet. So don't panic!**[/INDENT]

[SIZE="4"]Share the love[/SIZE]
[INDENT]Now it's time to bring the internet to the masses.

First we flush and current traffic rules we may have:
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -t raw -F
iptables -t raw -X
```

Now for non-bridged interfaces, these commands should turn on packet forwarding:
```
[COLOR="Green"]iptables -A FORWARD -i eth1 -s 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.1.0/255.255.255.0 -j ACCEPT[/COLOR]
[COLOR="DarkOrchid"]iptables -A FORWARD -i ath0 -s 192.168.2.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.2.0/255.255.255.0 -j ACCEPT[/COLOR]
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
For bridged interfaces, use these instead:
```
iptables -A FORWARD -i br0 -s 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.1.0/255.255.255.0 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
And we need to turn ip forwarding on in the kernel:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Now give it a whirl. Try connecting to a website from a computer on your LAN/WLAN. If it works, congrats! But keep reading - you're not done yet![/INDENT]

_[SIZE="4"]Optional: SSH Server[/SIZE]_
[INDENT]Install it and punch a hole in the firewall so you can access it from the WAN.
```
apt-get install openssh-server
```[/INDENT]

_[SIZE="4"]Optional: A little security[/SIZE]_
[INDENT]We'll setup some iptables rules to increase the security a bit. It's not strictly required, but it's a good idea.

We'll setup default policies to handle unmatched traffic. We'll drop all incoming traffic and all forwarded (traffic destined for our LAN/WLAN) but we'll allow all traffic originating from our router.
```
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
```

We'll allow all traffic coming to our router from itself:
```
iptables -I INPUT 1 -i lo -j ACCEPT
```

And we'll allow all traffic heading to the router that is coming from the LAN/WLAN. This makes all of the services from the router (ftp, samba, etc) accessible from our internal network but it remains closed to the public.

For non-bridged interfaces:
```
[COLOR="Green"]iptables -I INPUT 1 -i eth1 -j ACCEPT[/COLOR]
[COLOR="DarkOrchid"]iptables -I INPUT 1 -i ath0 -j ACCEPT[/COLOR]
```

For bridged interfaces, use:
```
iptables -I INPUT 1 -i br0 -j ACCEPT
```

We want to allow all requests initiated from our router to continue:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

The earlier iptables rules should still handle forwarding traffic. So we're done. Now, if we have any services like ftp or ssh on our router that we'd like to open to the public we need to poke holes in our firewall. For each service we need to run this command:
```
iptables -A INPUT -p [COLOR=Red]**type**[/COLOR] --dport [COLOR=Red]**port**[/COLOR] -i eth0 -j ACCEPT
```
Change [COLOR=Red]**type**[/COLOR] to the packet type: tcp or udp. Change [COLOR=Red]**port**[/COLOR] to the port number. For example, a SSH server runs with tcp on port 22.
[/INDENT]

_[SIZE="4"]Optional: Port Forwarding[/SIZE]_
[INDENT]If you have services running on a computer in your internal network that you want to be public you'll need to forward the ports on the router to it. You can even change the port number in the process. For example, if you run a SSH server on your internal computer on the standard port 22, you can have the port 1022 on your router forward to port 22 on your internal computer. This lets you still have a SSH server running on your router with port 22 without conflicting.
```
iptables -t nat -A PREROUTING -p [COLOR=Red]**type**[/COLOR] --dport [COLOR=Red]**in-port**[/COLOR] -j DNAT --to [COLOR=Red]**ip**[/COLOR]_:[COLOR=Red]**out-port**[/COLOR]_
```
[COLOR=Red]**type**[/COLOR] is tcp or udp. [COLOR=Red]**in-port**[/COLOR] is the port incoming to your router (1022 in the above example). [COLOR=Red]**ip**[/COLOR] is the ip address of the internal computer to forward to. _[COLOR=Red]**out-port**[/COLOR] is the port that the packets will have when they reach the internal computer. Omit the colon and the out-port to keep the port number unchanged._
[/INDENT]

_[SIZE="4"]Optional: DHCP Hosts[/SIZE]_
[INDENT]Dnsmasq will tend to give the same ip address to a computer time after time, but it's unpredictable. If you want to force a specific computer to have a certain ip address then edit your dnsmasq.conf file again. (This is helpful for the port forwarding rules above.)
```
nano /etc/dnsmasq.conf
```

For each computer you want to have a permanent ip address enter this at the end of the file:
```
**dhcp-host=[Color=Red]Name[/COLOR],192.168.1.[COLOR=Red]2[/COLOR]**
```
Where [Color=Red]Name[/COLOR] is the name of the computer. Change the red number to whatever you want in range (2-255).

Save and exit (Ctrl+X).

Restart dnsmasq:
```
/etc/init.d/dnsmasq restart
```

Alternatively, you can give ip addresses using the computer's MAC address (get with ifconfig - HWaddr) using:
```
**dhcp-host=id:[Color=Red]MAC Address[/COLOR],192.168.1.[COLOR=Red]2[/COLOR]**
```
[/INDENT]

[SIZE="4"]Make it stick[/SIZE]
[INDENT]Now we need to make all this stuff permanent. First, the kernel setting:
```
nano /etc/sysctl.conf
```

Change this line:
```
#net.ipv4.conf.default.forwarding=1

```
to this:
```
net.ipv4.ip_forward=1
```

Now for the iptables:
```
iptables-save > /etc/iptables.conf
nano /etc/rc.local
```

Add this line **before** "exit 0":
```
**iptables-restore < /etc/iptables.conf**
```[/INDENT]

_[SIZE="4"]Optional: Dynamic DNS[/SIZE]_
[INDENT]If you want to be able to access your router from your WAN you'll need to know its ip address. This can become a chore though, because most ISPs give you a dynamic ip address (i.e. one that changes). So you can either jot it down each time you leave the house or you can setup DNS. There are lots of places that provide free dynamic DNS services. I use [[COLOR="Blue"]DynDNS[/COLOR]]("http://dyndns.org/"). After you have your account setup you need to tell their servers what your ip address is on a regular basis. You can do this with a dynamic DNS client call inadyn. Install it and try it out:
```
apt-get install inadyn
inadyn -u [COLOR="Red"]username[/COLOR] -p [COLOR="Red"]password[/COLOR] --update_period_sec 600 --alias [COLOR="Red"]url[/COLOR] --background
```
Make sure to put in your username, password, and url!

You can test it by pinging your url:
```
ping [COLOR="Red"]url[/COLOR]
```

Make this permanent:
```
nano /etc/rc.local
```

Add this line **before** "exit 0":
```
**inadyn -u [COLOR="Red"]username[/COLOR] -p [COLOR="Red"]password[/COLOR] --update_period_sec 600 --alias [COLOR="Red"]url[/COLOR] --background**
```[/INDENT]

_[SIZE="4"]Optional: Router, Know Thy Name![/SIZE]_
[INDENT]You may have noticed that computers on the LAN/WLAN can reach each other by the name of the computer thanks to Dnsmasq. Unfortunately, the router won't respond by its name by default. You have to use it's ip address (e.g. 192.168.1.1). But if you edit the hosts file on the router you can change that.
```
nano /etc/hosts
```

Find the line that looks like:
```
127.0.1.1          [COLOR=Red]Name[/COLOR]
```

And change it to:
```
192.168.1.1        [COLOR=Red]Name[/COLOR]
```
Save and exit (Ctrl+X).

Restart dnsmasq:
```
/etc/init.d/dnsmasq restart
```
[/INDENT]

_[SIZE="4"]Printer/Scanner Server[/SIZE]_
[INDENT]You can share a printer on your LAN by installing a CUPS server on your router.

Install the server and edit the config file:
```
sudo apt-get install cupsys
sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf.original
sudo nano /etc/cups/cupsd.conf
```

Find the line that says "Listen localhost:631" and change it to "Port 631".

Find "Browsing Off" and change it to "Browsing On"

Find the sections "<Location />", "<Location /admin>", "<Location /admin/conf>" and add "Allow all" on a line before the closing "</Location>".

Close the file (Ctrl+X).

Npw, add yourself to the 'lpadmin' group so that you can use the cups admin tools.
```
sudo adduser lpadmin [COLOR=Red]username[/COLOR]
```

Restart the CUPS server and you should be up and running.
```
sudo /etc/init.d/cups restart
```

Before you can use it, you must add your printer to CUPS. On a computer within your WLAN/LAN navigate your browser to [http://192.168.1.1:631/](http://192.168.1.1:631/) (your router's internal ip address on port 631). From here you can perform all CUPS admin stuff. The first thing you should do is add your printer from Administration->Add Printer. Enter the admin username and password on the router when prompted. Once added, the printer should be available via ipp(Internet Printing Protocol) on port 631.

If you have a scanner (or if your printer has a scanner attached) you can share that with SANE. You will connect using XSANE (Seems to be Linux only) from your LAN computers. Install this:
```
sudo apt-get install libsane-extras
```

Now we need to tell the SANE daemon to run:
```
sudo nano /etc/default/saned
```
Change "RUN=no" to "RUN=yes" and save and exit.

Now edit this file:
```
sudo nano /etc/sane.d/saned.conf
```
After the line "#scan-client.somedomain.firm"
Add a line that says:
```
192.168.1.0/24
```
(Note: Tailor this to the right subnet for the correct subnet address.)

Reboot the router and it should be good to go. You can test with:
```
scanimage -T
```

**[COLOR=Red]On Karmic there is a permissions bug that may only allow you to access the scanner as root. Click [here]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/121082") to see this bug. The fix is comment 24.[/COLOR]**

On your LAN computers, you'll need to edit this file:
```
sudo nano /etc/sane.d/net.conf
```
At the very end of the file add the ip address of your router on a line by itself.

Now run XSANE and if should find the remote scanner. Happy scanning!
[/INDENT]

[SIZE="4"]Final Words[/SIZE]
[INDENT]There you go. Hopefully it should all be working. If not, check out these references to see if your question is answered there. Good luck!

**References**
[INDENT][http://ubuntuforums.org/showthread.php?t=376283]("http://ubuntuforums.org/showthread.php?t=376283")
[http://www.gentoo.org/doc/en/home-router-howto.xml]("http://www.gentoo.org/doc/en/home-router-howto.xml")[/INDENT][/INDENT]

---

### Post by wieman01 on 2008-03-05
Would you also consider explaining how to configure WPA/WPA2? WEP isn't the latest security standard and is highly flawed & insecure. Nice guide apart from this.

---

### Post by hedgefighter on 2008-03-06
Thanks a lot. As I said I don't have too much time to maintain this. I just spent a lot of time gathering the information and thought I'd share it. WEP is good enough for my needs. I really just have it to keep my neighbors from hopping on my wireless. I'm more than happy to get WPA setup, but it would take me a while to do it with my schedule. If you have any specific instructions I'd be happy to add them. I notice that you seem to be an expert in that area.

---

### Post by wieman01 on 2008-03-06
Not quite an expert, really, but perhaps it is not even necesarry looking at it again. People can easily combine information found here with staff from other threads. So I guess it'll be OK. Again, thanks for your thread, it looks really neat. Hope you find time to support users. :-)

TURTLE POWER!

---

### Post by hedgefighter on 2008-03-06
Yeah, that's a good point. There's so many things you could do with it from this point like ftp and http servers. Hopefully the basic setup will be sufficient. Thanks again.

---

### Post by ante.wessels on 2008-03-22
Thanks! I got my pc working as a router with this howto. I do have a question. Before turning the pc into a router I had the Guarddog firewall running, according to [www.grc.com](www.grc.com) it was stealth. Now the first 1023 ports are stealth, the others are closed. 

The last two lines of your firewall rules are:
iptables -A INPUT -p TCP -i eth0 -d 0/0 --dport 0:1023 -j DROP
iptables -A INPUT -p UDP -i eth0 -d 0/0 --dport 0:1023 -j DROP

It would seem to me that by changing them a bit I could make the machine stealth again?

---

### Post by jumanji3031 on 2012-02-12
Hi all..

I'm a Linux noob that wanted to use UFW instead of iptables to setup the firewall-part of this guide. I'm not sure if i have done this right so feel free to comment...

This is what i did..

In /etc/default/ufw change  DEFAULT_FORWARD_POLICY to ACCEPT

In /etc/ufw/sysctl.conf uncomment net/ipv4/ip_forward=1

In /etc/ufw/before.rules add, from the top, after the comments...

[PHP]# nat Table Rules
*nat
:POSTROUTING ACCEPT - [0:0]

# Forward traffic...
-A POSTROUTING -s 192.168.1.0/255.255.255.0 -o eth0 -j MASQUERADE

COMMIT

# allow all on loopback
-A ufw-before-input -i eth1 -j ACCEPT #added this here[/PHP]

Shields up on [www.grc.com](www.grc.com) shows that the firewall is ok.

---


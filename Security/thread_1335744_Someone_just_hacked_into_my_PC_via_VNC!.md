---
title: "Someone just hacked into my PC via VNC!"
date: 2009-11-23
forum: Security
---

### Post by Amorphous_Snake on 2009-11-23
I don't know how this happened but here is the story.

I connect to the internet through a router with a firewall that is set on medium.

I have an old PC with Ubuntu on it that I mainly use to download torrents and is kept running all the time. I control it via VNC and through its own keyboard, mouse and monitor. I use uTorrent via Wine and I have manually opened a port in the router. This PC doesn't have Windows at all or even a FAT/NTFS partition.

It happened that I have been using it at the moment and then I noticed that the Vino server notification come and goes and I managed to just see an IP ending with .hu or .hr I think that's Hungary, right? The address was written like the IP addresses in uTorrent which was running. I mean with the ISP name and so, but it was so fast I couldn't catch it. I immediately disabled Vino, then went into the router gui and made the firewall on high then manually unplugged the power to the router and then connected it again.

I think it's my fault to allow this to happen as I didn't specify which IPs can connect to Vino, but I have been doing this for years. Can I guess that this attack happened before? And how could this guy get past my firewall? The problem with the high level of the firewall router is that sometimes it blocks browsing and I find in the log something about TCP flood or UDP but I guess this is because of bittorrent.

I want to know what is currently wrong and how to prevent it from happening again. Sorry for the long post!

---

### Post by jrusso2 on 2009-11-23
VNC should never be exposed to the Internet it should be used locally only.

Since you say you have a router you must have the ports forwarded to allow someone in.

---

### Post by Amorphous_Snake on 2009-11-23
The PC is connected to a switch then to the router along with all my other PCs. I have UPnP enabled at the router but only one port is opened manually to allow uTorrent to connect, because somehow it never manages to use UPnP.

---

### Post by Amorphous_Snake on 2009-11-23
Also, shouldn't Ubuntu have some kind of firewall? I know that it has no GUI but it could have done something.

Thank God that I never enable Remote Desktop under Windows. If this happened to me under Linux I wonder what would have happened if I have been running Windows. All my other PCs run Windows, by the way, which is why I am very worried.

---

### Post by rogman on 2009-11-23
Something weird happened to me this evening as well. 

I was literally posting on Facebook to a friend about getting Ubuntu and its lack of security concerns and virus, and then later i'm surfing but then kind of see a new page of google with exe being typed in the search. then the mouse moving down to find (bottom left of firefox) and type something in it. I disconnected my machine from the net, but later realised the remote desktop symbol.

i looked and it was connected to: dsl-189-242-189-59-dyn-prod-infinitum.com.mx. i tried searching but nothing in google. i then tried getting to a website but nothing except: [http://www.prod-infinitum.com/](http://www.prod-infinitum.com/) would work and its one of those probably fake search engines.

firstly how did i become comprimised and what could they have done, just browse files etc?? or more sinister?, anyway to find out?. i was running firefox and also lottanzb which is an nzb binary downloader from newsgroups. 

it might be worth noting i loaded the remote desktop for the first time last week and tried it out within my machine as i was looking to remote my desktop from work.

Secondly, what can i do to protect myself. I have a modem which is connected by LAN, and to Shaw in Canada. I don't run any firewall software, antivirus. Am i missing something, or should i be configuring a firewall and if so where should i start on Ubuntu?

Thanks
Rogman

---

### Post by rookcifer on 2009-11-24
> **Amorphous_Snake said:**
> Also, shouldn't Ubuntu have some kind of firewall? I know that it has no GUI but it could have done something.

Thank God that I never enable Remote Desktop under Windows. If this happened to me under Linux I wonder what would have happened if I have been running Windows. All my other PCs run Windows, by the way, which is why I am very worried.

You left VNC open to the Internet and someone doing a port scan found you and got in.  It's your fault.  What do you want the OS to do?

---

### Post by cariboo on 2009-11-24
The first thing to do is turn off any services you have running, vnc is one of the most common ways new users get cracked. Go to System-->Preferences-->Startup Applications and turn off remote desktop.

If you have a router, turn off any port forwarding. Then read the security [stickie]("http://ubuntuforums.org/showthread.php?t=510812")  at the top of the page.

---

### Post by lisati on 2009-11-24
> **rogman said:**
> 

i looked and it was connected to: dsl-189-242-189-59-dyn-prod-infinitum.com.mx. i tried searching but nothing in google. i then tried getting to a website but nothing except: [http://www.prod-infinitum.com/](http://www.prod-infinitum.com/) would work and its one of those probably fake search engines.



[WhatIsMyIpAddress]("http://whatismyipaddress.com") gives the following results:
> Hostname:	dsl-189-242-189-59-dyn.prod-infinitum.com.mx
ISP:	Uninet S.A. de C.V.
Organization:	Uninet S.A. de C.V.
Proxy:	None detected
Type:	Cable/DSL

> 
Country:	Mexico
State/Region:	15
City:	Nezahualcóyotl
Latitude:	19.4136
Longitude:	-99.0331
Area Code:	


---

### Post by Amorphous_Snake on 2009-11-24
> **rookcifer said:**
> You left VNC open to the Internet and someone doing a port scan found you and got in.  It's your fault.  What do you want the OS to do?

You misunderstood me. I am not blaming Ubuntu. I want to know why this happened. I do a firewall test every now and then and the results reveal that I am invisible, and that while using the medium level of the router firewall.

---

### Post by Amorphous_Snake on 2009-11-24
> **cariboo907 said:**
> The first thing to do is turn off any services you have running, vnc is one of the most common ways new users get cracked. Go to System-->Preferences-->Startup Applications and turn off remote desktop.

If you have a router, turn off any port forwarding. Then read the security [stickie]("http://ubuntuforums.org/showthread.php?t=510812")  at the top of the page.

That was the first thing that I did: disable Vino.

And thanks for the link. It's full of great info.

---

### Post by QLee on 2009-11-24
[QUOTE=Amorphous_Snake] I want to know why this happened. I do a firewall test every now and then and the results reveal that I am invisible, and that while using the medium level of the router firewall.[/QUOTE]

Since I don't have the same router/firewall as you, I don't have any idea of what the terms "medium level" or 'high level" refer to, however, that "invisible" you mention probably means that you have tested at some site like GRC and your ports are "stealth". That only means they aren't showing as open or listening, as soon as you use your browser to surf the net, the "bad guys" know that there is a computer at your IP address and the probes and attacks begin if they weren't already doing a sweep of IPs.

Edit: an addition, I suggest you don't enable  UPnP in the router unless you know you need it for something.

---

### Post by Amorphous_Snake on 2009-11-24
My router is a 3Com OfficeConnect ADSL2+ Wireless Router.

Thanks for the info.

I enable UPnP because it handles port forwarding on bittorrent clients automatically on Winodws and I think it also open ports when I am playing online on Steam. Am I wrong?

---

### Post by QLee on 2009-11-24
[QUOTE=Amorphous_Snake]My router is a 3Com OfficeConnect ADSL2+ Wireless Router.[/QUOTE]

Okay, I believe you, I still don't have the documentation for that router which would likely explain the terms medium and high.


[QUOTE=Amorphous_Snake]I enable UPnP because it handles port forwarding on bittorrent clients automatically on Winodws and I think it also open ports when I am playing online on Steam. Am I wrong?[/QUOTE]

I don't know, I don't use it, let's just assume you are correct. If UPnP does the port forwarding you need then you should probably be setting your firewall to "high", whatever that means.

Someone will probably be along here who does have have that gateway/router and can confirm or deny.

---

### Post by Amorphous_Snake on 2009-11-24
Here are some information from the help tap in my router's gui.

> Firewall
Your Router is equipped with a firewall that will protect your network from a wide array of common hacker attacks including Ping of Death (PoD) and Denial of Service (DoS) attacks. You can turn the firewall function off if needed. Turning off the firewall protection will not leave your network completely vulnerable to hacker attacks, but it is recommended that you turn the firewall on whenever possible.

There is the detailed information about the three firewall levels below.

    * Low Level: IP spoofing check only.
    * Medium Level: Adding DoS pattern match, RIP defect (for P2P application).
    * High Level: Adding SPI feature.

Special Applications
Some applications such as games, video conferencing, remote access applications and others require that specific ports in the Router's firewall be opened for access by the applications. You can configure the port settings from this screen. Note: Opening ports in your firewall can pose a security risk. You can enable and disable settings very quickly. It is recommended that you disable the settings when you are not using a specific application.

Special Applications let you specify ports to be open for specific applications to work properly with the Network Address Translation (NAT) feature of the Router. A list of popular applications has been included to choose from. Select your application from the drop-down list from the top of the screen. Select the row that you want to copy the settings to from the drop-down list, and then click "Copy To". The settings will be transferred to the row you specified. Click "Apply" to save the setting for that application. If your application is not here, you will need to check with the application vendor to determine which ports need to be configured. You can manually input this port information into the Router. Multiple ports can be entered by separating the port numbers by commas (E.g. 10,20,30) or ranges of ports can be specified by using dashes (E.g. 20-30).

Virtual Servers
This function will allow you to route external (Internet) calls for services such as a web server (port 80), FTP server (Port 21), or other applications through your Router to your internal network. Since your internal computers are protected by a firewall, machines from the Internet cannot get to them because they cannot be 'seen'. If you need to configure the Virtual Server function for a specific application, you will need to contact the application vendor to find out which port settings you need. To manually enter settings, enter the IP address in the space provided for the internal machine, the port type (TCP or UDP) and the LAN & Public port(s) required to pass, select Enable and click "Set". You can only pass one port per internal IP address. Opening ports in your firewall can pose a security risk. It is recommended that you disable the settings when you are not using a specific application.
The ports for well known services are listed below:

      AUTH port 	113
      FTP port 	21
      ISAKMP port 	500
      Email (POP3) port 	110
      Email (SMTP) port 	25
      Email (IMAP4) port  	143
      PPTP port 	1723
      Telnet port 	23
      Web (http) port 	80
      Web (https) port 	443
      NetMeeting port 	1720


Client IP Filters
The Router can be configured to restrict access to the Internet, e-mail or other network services at specific days and times. Restriction can be set for a single computer, a range of computers, or multiple computers.

Access Control
An IP address or a range of IP addresses can be configured to be restricted of access to the Internet, e-mail or other network services. Furthermore, scheduled access control can be defined at specific times of the day and days of the week.

To use the URL filter function, the "URL Filter" rules must be first defined under the "URL Filter page".

To use the scheduling function, a schedule rule must be first defined under the "Schedule Rule" page.

URL Filter
The URL Filter feature permits/blocks defined websites based on the URL address and/or keywords. For each site rule, enter the URL address or a keyword then choose whether to permit or block it. To complete this configuration, be sure to select the option for "Enable URL Filter" in the Client PC Service table under the Access Control Section by creating or modifying an access rule. Note: The URL Filter rules overwrites the Content Filter rules.

Content Filter
To configure the Content Filter feature, specify the Content Filtering Server Name or IP address. You should also specify the access right(Allow/Deny) for each content category. Click "Apply" to activate the change. To complete this configuration, be sure to select the option for "Enable Content Filter" in the Client PC Service table under the Access Control Section by creating or modifying an access rule. Note: The URL Filter rules overwrites the Content Filter rules. How it works? Please refer to the picture as below.

Schedule Rule
The Schedule Rule allows for the scheduling of Access Control rules and LAN Server rules. Each Access Control rule or LAN Server rule can be selectively activated at the predefined scheduled time. The user must first define a schedule rule under the "Schedule Rule" page, then associate the schedule rule with an access control rule in the "Access Control" page. A maximum of 10 schedule rules may be defined.

DMZ
If you have a client PC that cannot run an Internet application properly from behind the firewall, you can open the client up to unrestricted two-way Internet access. This may be necessary if the NAT feature is causing problems with an application such as a game or video conferencing application. Putting a client PC in DMZ will allow all ports of this PC can be accessed by any Internet hosts without any restriction. Use this feature on a temporary basis. The computer in the DMZ is not protected from hacker attacks. To put a computer in the DMZ, enter the last digits of its LAN IP address in the Static IP field and click "Apply" for the change to take effect. If there are more than one Internet addresses, you can assign each Internet address a DMZ host.

Server Control
The Router can be configured to restrict access to the public hosts in LAN from Internet, e-mail or other network services at specific days and times. Restriction can be set for a single computer, a range of computers, or multiple computers.

Qos
The bandwidth gap between LAN and WAN may significantly degrade performance of critical network applications, such as VoIP, gaming, and VPN. This QoS function allows users to classify traffic of applications and provides them with differentiated services (Diffserv).

    * Diffserv Forwarding Groups: Below shows the Diffserv forwarding behaviors this router supports. User can further configure the bandwidth allocation of each forwarding behavior.
    * Edit Traffic Class: This page is for user to specify a classify rule. First, define the class by the traffic type and the local and remote addresses. Then set the Diffserv forwarding group this class is mapped to. Finally, select the outgoing VC that traffic of this class would be routed to.

Traffic Mapping
Up to 16 rules can be defined to classify traffic into Diffserv forwarding groups and outgoing VCs.

Traffic Statistics
This page shows the WAN outbound traffic statistics of all the Diffserv forwarding groups in the last 12 hours (automatically update every 5 mins).

NAT Enabling
Before you enable this function, MAKE SURE YOU HAVE SET THE ADMINISTRATOR PASSWORD.Network Address Translation(NAT) is a commonly used IP translation and mapping technology. It is a technology that allows your network to share internet access. Using a device or piece of software that implements NAT allows an entire home network to share a single internet connection over a single IP address. A single cable mode, DSL modem, or even 56k modem could connect all the computers in your home to the internet simultaneously. Additionally, NAT keeps your network fairly secure from hackers.NAT acts as an interpreter between two networks. In the case of a network, it sits between the internet and your network. The internet is considered the public side and your network is considered the private side. When a computer in the private side request data from the public side (the internet), the NAT device will open a little conduit between your computer and the destination computer. When the public computer returns results from the request, it is passed back through the NAT device to the requesting computer. Turning off NAT will not affect your firewall functions.

IPSEC NAT-T Pass-through
NAT Traversal(NAT-T) is an Internet Draft proposed to IETF in order to help the problems associated with passing IPSec traffic through NAT routers. For NAT-T to work both ends of the connection need to support this function. Please only turn NAT-T on if needed as it will reduce LAN-WAN throughput. This router supports NAT-T draft 2 implementation.

Universal Plug and Play
Universal Plug & Play is a technology that offers seamless operation of voice messaging, video messaging, games, and other applications that are Universal Plug & Play compliant. Some applications require the Router's firewall to be configured in a specific way to operate properly. This usually requires opening TCP and UDP ports and in some instances setting trigger ports. An application that is Universal Plug & Play compliant has the ability to communicate with the Router, basically "telling" the Router which way it needs the firewall configured. The Router ships with the Universal Plug & Play feature disabled. If you are using any applications that are Universal Plug & Play compliant, and wish to take advantage of the Universal Plug & Play features, you can enable the Universal Plug & Play feature. Simply select "Enable Universal Plug & Play" in the "Universal Plug and Play" section of the Advanced page. Click "Apply" to save the change. But for security concern, we recommend you to keep this feature "disabled".

WAN Ping Blocking
Computer hackers use what is known as "Pinging" to find potential victims on the Internet. By pinging a specific IP address and receiving a response from the IP address, a hacker can determine that something of interest might be there. The Router can be set up so it will not respond to an ICMP Ping from the outside. This heightens the level of security of your Router. To turn off the ping response, select "Block ICMP Ping" and click "Apply". The router will not respond to an ICMP ping.

MSS Clamping
A technique, which works with TCP under specific scenarios only, is so-called "MSS clamping". With that technique or rather a "hack", the TCP packets' Maximum Segment Size (MSS) is reduced by tunnel endpoints so that the TCP connection automatically restricts itself to the maximum available packet size. Obviously, this does not work for UDP or other protocols that have no MSS. This approach is most applicable and used with PPPoE, but could be applied otherwise as well; the approach also assumes that all the traffic goes through tunnel endpoints that do MSS clamping -- this is trivial for the single-homed access links, but could be a challenge otherwise.

Remote Administration
Before you enable this function, MAKE SURE YOU HAVE SET THE ADMINISTRATOR PASSWORD. Remote administration allows you to make changes to your Router's settings from anywhere on the Internet.
Remote management allows you to manage the Router from anywhere on the internet. Before you enable remote management, 3Com advise you to change the Administrator password. To remotely manage the Router, the remote user should type into their browser. http://<Router WAN IP address>:8000

SNMP
SNMP (Simple Network Management Protocol) allows remote management of the router by a computer that has an SNMP management agent installed on it. To configure SNMP, the following options need to be set:

    * Community: This is the name of the SNMP communication channel. The management agent needs to be configured with this name to communicate with the router.
    * Read/Write: Selecting 'Read' allows the management agent to collect data such as bandwidth usage from the router. Selecting 'Write' allows the management agent to change the operation of the router.
    * Valid: Ticking this option enables this particular communication channel.

The router can also be configured to send status messages to the SNMP management agent if a problem occurs on the network. This is done by using the 'Trap' option on the left hand side menu. To configure this, the following options need to be set:

    * IP Address: This is the IP address of the computer that the status messages are to be sent to.
    * Community: This is the name of the SNMP communication channel that the status messages are to be sent to.
    * Version: The router supports both V1 and V2c trap messaging. This should be set to match the version of trap messaging that your SNMP management agent supports.


---

### Post by Amorphous_Snake on 2009-11-24
I have disabled UPnP to be safe.

---

### Post by OpSecShellshock on 2009-11-24
If you haven't already, you'll want to disable the remote desktop function. It's never a good idea, it's just that sometimes it's necessary. However, it may violate the security policy of your workplace, and it leaves your home computer open to remote sessions. This goes for the firewall's administration page as well.

If you have to set special rules for certain applications, make sure that rather than leaving ports open in general, your hardware firewall is set up to only open the ports when an outbound request is sent from a computer inside your home network. If the connection is initiated from inside, then the response should automatically be accepted. I believe this is the default configuration for most home routers. For most people's needs, there should never be any reason to specifically open an inbound port.

---

### Post by Amorphous_Snake on 2009-11-24
I have disabled VNC as I have already said. And I will keep it disabled until I have the time to learn to use SSH.

OpSecShellshock, I think you mean port triggering instead of port forwarding. Port triggering doesn't work well with bittorrent because there are no definite outgoing ports to trigger the incoming port opening, leading to loss of speed as the incoming port will close as the outgoing port will change. You can read more [here]("http://forum.utorrent.com/viewtopic.php?pid=16740#p16740").

So, what I have done so far was to disable UPnP and Vino, increase the level of the router firewall. I have no option but to keep a port manually open for uTorrent (on Wine), unless anyone can tell me of a better way. I will try to change the port every few days, and it's only open for that PC's internal IP.

---

### Post by rogman on 2009-11-24
[lisati]("http://ubuntuforums.org/member.php?u=327635") thanks.

is this a plausible reason. i remembered i was using virtualbox to download some stuff through Usenext (this version works with NZB whereas Ubuntu versions doesn't), is it possible that when i was connected to the net through windows that i got hooked on to? i had just loaded it on to the machine a day or so ago and had yet to sort out anti-virus etc.. windows firewall was on though. by logging out of virtualbox wouldn't disconnect the person would it, so they could then have control of my machine..

i'm a total beginner so sorry if i don't make so much sense. just interested in how this occurred to me.

---

### Post by bodhi.zazen on 2009-11-24
IMO, VNC is the most commonly cracked server on these forums. This is due to two reasons :

1. VNC is commonly used by new users.

2. Protection is fairly minimal, you have only a password to protect you.

My advice is :

1. Use strong passwords.

[Password Strength Checker]("http://www.passwordmeter.com/") 

2. If you use VNC, firewall it. The easiest way is to limit port 5900 (the default port)

```
sudo ufw limit 5900:5910/tcp
```Or if you use Gufw, Add a new rule, preconfigured ...

In the first box Limit 
In the second box Service
In the third box VNC

For further firewall advice, I just posted a few blog :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by XCan on 2009-11-25
To add to bodhi's tips:

3. If you use VNC, change its default port! (This may also be a good idea for other services, such as SSH)

---

### Post by HermanAB on 2009-11-25
Hmm, VNC is pretty much the **only** way in which Ubuntu machines gets hacked.  VNC is mainly a Windows thing.  On Linux, you should use SSH instead, since SSH can do everything VNC does and much more and it is secure.

---

### Post by XCan on 2009-11-25
Except painless remote desktop (not remote session). Although setting up VNC through SSH is quite painless as well.

---

### Post by Amorphous_Snake on 2009-11-25
All right guys, thanks for all the info. Is there a quick guide to setup VNC through SSH? Thanks.

And as for Vino and VNC, if it's so easily a way into your system being hacked, why is it included in Gnome by default?

---

### Post by HermanAB on 2009-11-25
Install OpenSSH on your server, then from the client computer do:
$ ssh -C -c blowfish -X user@server gnome-panel

That works from Windows clients with XminGW and PuTTY as well.

VNC is good for co-session training on a LAN.  Over the internet, you should use SSH and once you have SSH, VNC is redundant.

---

### Post by bodhi.zazen on 2009-11-25
> **Amorphous_Snake said:**
> All right guys, thanks for all the info. Is there a quick guide to setup VNC through SSH? Thanks.

There are many many

[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

You may also consider only ssh, all you need is putty and an X server on windows, Xming

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

Both putty and Xming run as portable applications from a flash drive.

[/quote]And as for Vino and VNC, if it's so easily a way into your system being hacked, why is it included in Gnome by default?[/quote]

Well, it is disabled by default and with all servers you need to stop for a minute and think about what you are doing. I assume you chose a weak password, this is by far the #1 reason people are cracked.

Second you enabled the VNC server.

Third you forwarded port 5900 from your router.

None of these steps are really the default configuration ;)

Other then that, IMO I would end to agree and would not mind if vino were removed.

---

### Post by Amorphous_Snake on 2009-11-25
Well, I have a confession to make! I wasn't using any kind of password for VNC! I never thought that it would be accessible from the internet and I never forwarded its port on my router and I didn't think that it may use UPnP.

It's my fault, but you learn something new everyday, that's why I love Linux.

I will experiment with SSH and update you with the results.

In fact, if SSH works and I no longer need Vino and VNC, I might even go the extra mile and use a lighter distro on this old PC or keep Ubuntu and install something light like LXDE or XFCE because the main reason I was using Gnome was that VNC was configured easily and it wasn't on the "menu" in other DE (except KDE which I am not a big fan of).

Thanks for all the help.

---

### Post by jrusso2 on 2009-11-25
SSH gets hacked probably the second most after VNC.  I would suggest using an encrypted key and not using a plain password which is how they are usually hacked.

Also don't run it on port 22 which is default.

---

### Post by HeadHunter00 on 2009-11-25
@Amorphous_Snake: I'm happy for your positive attitude. Stay that way, brother (or sister)

---

### Post by bodhi.zazen on 2009-11-25
> **Amorphous_Snake said:**
> Well, I have a confession to make! I wasn't using any kind of password for VNC! I never thought that it would be accessible from the internet and I never forwarded its port on my router and I didn't think that it may use UPnP.

I am glad you are learning, but I would advise you look at your router. Your VNC port should NOT be accessible from the internet so perhaps your router is misconfigured (is your computer in a "DMZ" with no firewall ? ) or worse, perhaps you were cracked from within your LAN or WAP.

For ssh, keys are sufficient if you then disable password logins.

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

Also use a service such as denyhosts or fail2ban.

Also check the strength of your passwords.

[Password Strength Checker]("http://www.passwordmeter.com/") 

If you do all those things, you really do not nee dto change the default port and it is much easier when connecting to go with the default (for the lazy typer that is).

---

### Post by Amorphous_Snake on 2009-11-25
> **HeadHunter00 said:**
> @Amorphous_Snake: I'm happy for your positive attitude. Stay that way, brother (or sister)

Thanks! It's a brother.

Due to lack of time, I tend to find something that works and stick with it till I have the time to try something better. But I think I stayed too long with VNC! 3 years to be exact.

---

### Post by CharlesA on 2009-11-25
> **bodhi.zazen said:**
> There are many many

[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

You may also consider only ssh, all you need is putty and an X server on windows, Xming

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

Both putty and Xming run as portable applications from a flash drive.

Thanks for the link. I wonder how that would work. I guess it's forwarding X11 over the SSH tunnel.

@OP: Most newer routers use SPI (stateful packet inspection), so it might be advantageous to set yours to "high" and see if you have any problems with torrents and whatnot.

---

### Post by Amorphous_Snake on 2009-11-25
> **bodhi.zazen said:**
> I am glad you are learning, but I would advise you look at your router. Your VNC port should NOT be accessible from the internet so perhaps your router is misconfigured (is your computer in a "DMZ" with no firewall ? ) or worse, perhaps you were cracked from within your LAN or WAP.

For ssh, keys are sufficient if you then disable password logins.

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

Also use a service such as denyhosts or fail2ban.

Also check the strength of your passwords.

[Password Strength Checker]("http://www.passwordmeter.com/") 

If you do all those things, you really do not nee dto change the default port and it is much easier when connecting to go with the default (for the lazy typer that is).

Thanks. You was really a great help.

I still didn't try SSH, and I will tell you when I do.

My LAN is only inside my flat with no wires outside and I have a strong WPA1/WPA2 mode passphrase and MAC address filtering enabled. I also don't broadcast my SSID to add an extra layer of protection. Besides, none of the neighbours are tech savvy!

I still haven't forwarded a port for VNC. The only ports that I opened were for bittorrent and their values are totally different from 5900.

I don't think that I will know exactly what happened. But it doesn't matter any more.

---

### Post by Amorphous_Snake on 2009-11-25
@CharlesA: I don't think I have this feature. The newest firmware for my router was in 2007. Anyway, if you look into the thread, you can see a copy/paste of the help file of my router regarding security. Tell me if you find it by a different name.

---

### Post by CharlesA on 2009-11-25
> **Amorphous_Snake said:**
> @CharlesA: I don't think I have this feature. The newest firmware for my router was in 2007. Anyway, if you look into the thread, you can see a copy/paste of the help file of my router regarding security. Tell me if you find it by a different name.

> Firewall
Your Router is equipped with a firewall that will protect your network from a wide array of common hacker attacks including Ping of Death (PoD) and Denial of Service (DoS) attacks. You can turn the firewall function off if needed. Turning off the firewall protection will not leave your network completely vulnerable to hacker attacks, but it is recommended that you turn the firewall on whenever possible.

There is the detailed information about the three firewall levels below.

* Low Level: IP spoofing check only.
* Medium Level: Adding DoS pattern match, RIP defect (for P2P application).
*** High Level: Adding SPI feature.**

Bolded it. You said that it was set to Medium. Try setting it to High and see if the torrents work.

---

### Post by bodhi.zazen on 2009-11-25
> **CharlesA said:**
> Bolded it. You said that it was set to Medium. Try setting it to High and see if the torrents work.

Great post, thank you for spotting that.

:popcorn:

---

### Post by Amorphous_Snake on 2009-11-25
I think I should have my eyes checked!

I tried to run uTorrent through Wine without opening any ports and with the firewall on high. It worked, but the problem was that the speed would drop and the NAT status in uTorrent says that the port is open, then moments later, it says that it is closed.

Deluge and Transmission report that the port that they chose (random) were closed. But with these 2 programs, this happen almost all the time regardless of the firewall level and regardless if UPnP was on or off.

Big thanks for spotting it.

---

### Post by BkkBonanza on 2009-11-25
I use Deluge a lot. What I've found is that running with ports closed the speed is initially slower but over a while it tends to get up to similar levels to when the port is open. I think this is because having ports closed doesn't really slow down anything except peer discovery. Peers can't contact you and you depend on contacting them instead (which happens even with ports closed). I believe you discover other peers via DHT so if ports are closed I think you should have DHt enabled otherwise maybe it's harder to connect to peers. Once connected to enough peers your speed should be just as good. Well, in my experience anyway. I don't have access to my building's router so I can't open the needed port anyway. 

I do sometimes use ssh as a secure proxy to run torrents through a tunnel to my server. That actually works really well. Better than local actually because my building has rather limited routers and too many connections tends to bog things down. With ssh only one connection is open no matter how many peer connections are active.

---

### Post by Amorphous_Snake on 2009-11-26
Something strange happened today. I was logged out of the system to the log in screen. I didn't do anything, I was just using Firefox.

This is getting scary! I did everything I can from the router and I have no extra services installed on Ubuntu except SMART Notify and Samba.

I stopped using uTorrent and I think I will switch to something native to Linux. But the thing is, they need to have their own ports open in the router or UPnP enabled. Which is the lesser evil?

---

### Post by memilanuk on 2009-11-26
Given that you don't *know* what all the intruders got their hooks into... I would strongly suggest re-installing, from scratch.  First thing, before you even do 'sudo apt-get update && apt-get upgrade' is bring up the firewall via ufw.  If you need more info on that, head over to the excellent tutorials located [here]("http://blog.bodhizazen.net/2009/11/") now, before you begin your reinstall.  Worry about your frivolous stuff like bit torrent, etc. *after* you have a stable system, at least nominally locked down and secured behind a firewall.  

You will never really know if you have successfully punted the intruder(s) otherwise.

---

### Post by Amorphous_Snake on 2009-11-26
Actually, I am highly considering this now. And it will be a good chance to install 9.10.

---

### Post by Amorphous_Snake on 2009-11-26
WOW! You do learn something new everyday!

UFW is disabled by default?!!! Why?! I have ALWAYS thought that it was enabled by default but it lacks a GUI.

This wasn't really a good choice from Ubuntu! Mandriva and openSUSE both have firewalls enabled by default. Windows has a firewall enabled by default!!!

---

### Post by bodhi.zazen on 2009-11-26
> **Amorphous_Snake said:**
> WOW! You do learn something new everyday!

UFW is disabled by default?!!! Why?! I have ALWAYS thought that it was enabled by default but it lacks a GUI.

This wasn't really a good choice from Ubuntu! Mandriva and openSUSE both have firewalls enabled by default. Windows has a firewall enabled by default!!!

Yes, but unlike windows, by default, on Ubuntu, there are no significant servers (services) listening for connections.

---

### Post by memilanuk on 2009-11-26
what can I say?  Maybe they should - but with the larger number of 'new' users that Ubuntu gets, they'd probably be just as swamped by people pitching a fit about why they can't do this, that or something else because the firewall is blocking them.

---

### Post by Amorphous_Snake on 2009-11-26
Mmm... Strange. I enabled ufw via the command line then went and installed gufw and also enabled it at startup with the default is to deny everything. But Firefox and KTorrent connected and worked without any problems whatsoever, and without appearing in the log. Have I missed someting here? Or these programs have enabled themselves in the firewall by default, because I remember seeing when a program installs that it triggers post-installation ufw. Right?

---

### Post by XCan on 2009-11-26
UFW and GUFW aren't made to block outgoing connections. Once you enter some addy in FF, it is FF that initializes the connection, thus traffic is allowed to flow back.

---

### Post by Maheriano on 2009-11-26
> **rogman said:**
> Something weird happened to me this evening as well. 

I was literally posting on Facebook to a friend about getting Ubuntu and its lack of security concerns and virus, and then later i'm surfing but then kind of see a new page of google with exe being typed in the search. then the mouse moving down to find (bottom left of firefox) and type something in it.

Did it look like this?

[http://lmgtfy.com/?q=random+things](http://lmgtfy.com/?q=random+things)

---

### Post by bodhi.zazen on 2009-11-26
> **XCan said:**
> UFW and GUFW aren't made to block outgoing connections. Once you enter some addy in FF, it is FF that initializes the connection, thus traffic is allowed to flow back.

ufw will manage outgoing connections.

See :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

There is an entire section on outgoing connections.

See also man ufw

GUFW will not manage outbound traffic.

---

### Post by memilanuk on 2009-11-26
> **Amorphous_Snake said:**
> Mmm... Strange. I enabled ufw via the command line then went and installed gufw and also enabled it at startup with the default is to deny everything. But Firefox and KTorrent connected and worked without any problems whatsoever, and without appearing in the log.

This is what is referred to as 'stateful packet inspection' or 'SPI'.  Basically the firewall inspects outgoing packets, and then when it gets corresponding inbound packets, it knows that those are legit - i.e. when Firefox sends off a http request to Google and then Google sends back the requested information, its all good.  But when someone else attempts to *initiate* a connection with your machine, the firewall blocks it unless otherwise instructed.  I don't run any torrent software on my Linux boxes (yet) so I can't say for sure how that interacts with the firewall for sure when for instance, someone else attempts to connect to you as a peer.

---

### Post by XCan on 2009-11-26
> **bodhi.zazen said:**
> ufw will manage outgoing connections.

See :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

There is an entire section on outgoing connections.

See also man ufw

GUFW will not manage outbound traffic.

Ah, interesting indeed, didn't know that about ufw.

---

### Post by HermanAB on 2009-11-27
On a Linux system, a simple 'ps -e' will show you what is running.  Therefore, it is very easy to find and turn off services that you don't want to run.  Consequently the use of an outgoing firewall filter is not particularly useful and is usually not used on Linux systems.

---

### Post by Amorphous_Snake on 2009-11-27
Thanks for all the input.

I am still learning my way into ufw.

Before reading bodhi.zazen's guide, I used [this guide]("http://www.funnestra.org/ubuntu/jaunty/#samba") to open ufw for Samba. Is this any good?

> sudo ufw allow from 192.168.0.0/16 to any app Samba


I am sure than no one can enter my home network (i.e. not through wireless or LAN), so is it safe to open the port or open for IPs?

---

### Post by bodhi.zazen on 2009-11-27
So long as you deny other traffic and trust your LAN.

Best learn to use a port scanner and test your firewall ;)

If your router is properly configured you should not need a firewall on your server. So do not open ports in your router without considering the consequences. Do not un a server without considering the security implications.

---

### Post by Amorphous_Snake on 2009-11-27
The above rule was the only one I added.

I don't think I can trust port scanners anymore. I had one test a couple of weeks before the first hack attempt and it told me that I was in the clean! A user has posted in this thread that while the ports may be stealthed, when someone finds my IP and probes it, he can find the open ports.

I don't have any ports on the router opened anymore.

---

### Post by bodhi.zazen on 2009-11-27
depends on the port scanner. Learn to use nmap ;)

Also learn about forewalls and the "proper" terminology. "Stealth" is a term used by "ShiledsUp" and is a term unique to that site.

So while it sounds "cool" to be "stealth" I suggest you learn how firewalls work.

The first few sections on this page should help :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Edit: You can not "trust" a toll you do not understand. You need to understand what a port scanner is telling you and how to secure your servers, especially VNC.

Learn to use more secure connections such as ssh. You can mount a remote file system with sshfs rather then samba.

Samba is fine on your LAN, but when installing a server, the security section is, IMO, mandatory reading.

---


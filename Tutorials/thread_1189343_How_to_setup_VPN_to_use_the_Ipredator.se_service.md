---
title: "How to setup VPN to use the Ipredator.se service"
date: 2009-06-16
forum: Tutorials
---

### Post by Luke1972 on 2009-06-16
As I was lucky enough to get a beta invite to sign up for the new Ipredator VPN service I jumped at the chance but was slightly nervous when there were no instruction on how to set up with Linux, just Windows and MacOS ones.  I'm not particularly good with Ubuntu but a little while reading these forums gave enough knowledge to get it working.

You'll need to install PPTP-Linux and also the PPTP plug in for Network Manager then configure the VPN.  Once configured Network Manager needs to be restarted and the connection can be made. 


First off open a terminal and type

```
sudo apt-get update
```

then
```

sudo apt-get install network-manager-pptp

```
This should also install the pptplinux dependency too.

Once installed click on the network-manager in the system tray, choose VPN Connections; Configure VPN, click Add.

[img]http://bayimg.com/image/kabcmaacc.jpg[/img]

When at VPN tab of NetworkManager click ADD

[img]http://bayimg.com/image/labceaacc.jpg[/img]

On connection type make sure protocol is PPTP

[img]http://bayimg.com/image/labcmaacc.jpg[/img]

At **VPN** tab:

Connect automatically if you want (I did)
Gateway field enter: vpn.ipredator.se
Username and Password are per your Ipredator acount.

[img]http://bayimg.com/image/mabcaaacc.jpg[/img]

Click **Advanced**

At Security and Compression:

Check Use Point-to-point encryption (MPPE)
Select 128-bit (most secure)
I turned off EAP as one guide I read on VPN setup said to do so but I'm not sure it is necessary.

[img]http://bayimg.com/image/mabcbaacc.jpg[/img]

Then NetworkManager needs to be restarted.  I simply rebooted my laptop though I know that it can be done at the command line but the commands I tried didn't work so didn't want to spend time fiddling around.

Once NetworkManager was restarted my normal wifi connection was made then the VPN was made and I had a Swedish IP address geo-located to Lund in Sweden. 


This is also [posted on my blog here]("http://rot13.baywords.com/2009/06/16/setting-up-ipredator-vpn-on-ubuntu/")

---

### Post by fleton on 2009-06-21
Very nice guide, thank you :D

---

### Post by Sillywombat on 2009-07-03
Thanks! Got my beta confirmation in the mail a couple of days ago.
Article was nice and easy to understand, going to give it a try at home tonight.

Have have you found the speeds while using your new VPN? has it slowed down a bit? greatly? or nothing worth noting?

---

### Post by Luke1972 on 2009-07-04
Speed wise it seems fine and the only thing I've noticed is that DNS lookups take a little longer than if I wasn't on the VPN.  But I mean maybe it takes a second longer and it isn't anything unreasonable.

---

### Post by fleton on 2009-07-07
What is the speed cap on ipredator?

---

### Post by Luke1972 on 2009-07-09
> **fleton said:**
> What is the speed cap on ipredator?

Not noticed any at all and seem to browse/download at my usual speed for my ISP.

---

### Post by 1/0 on 2009-07-31
I just reinstalled Ubuntu and can't get it to work again. I followed all the steps like last time and I can connect to Ipredator but as soon as I am connected, it's impossible to go to a new homepage or to ping...

Any ideas?

---

### Post by KhaaL on 2009-08-08
hey guys

Since I was a bit unhappy with how network manager handles vpns (once disconnected, it dosent autoconnect) and considering I'm slowly going back to kde, I gave KVpnc a shot and managed to get ipredator to work there. Here's the steps to do it:

[LIST=1]
[*]install and Start KVpnc - you can download debs from here: [http://home.gna.org/kvpnc/en/download.html]("http://home.gna.org/kvpnc/en/download.html")
[*]start the wizard and press next on the welcome screen
[*]on the select VPN type, choose Microsoft PPTP
[*]on the PPTP specific settings, make sure the following are checked: Refuse 40 bit encryption, require MPEE. Have chap as a authorization method
[*]In the next screen (User settings), enter your login name and password
[*]Network settings can be left as it is.
[*]I have virtual IP adresses unchecked
[*]On the connection status check, enable reconnect after connection lost.
[*]In the final settings page (i skipped the page with "connect after creating new profile)  general settings, Give it a name and at VPN gateway type in **vpn.ipredator.se**
[*]click finished, connect and enjoy!
[/LIST]

Unfortunatly there is no kde4 version of kvpnc for ubuntu yet. If someone makes an unofficial deb for KDE4, that'd be great and appriciated by me at least :-)

---

### Post by 1/0 on 2009-08-08
> **1/0 said:**
> I just reinstalled Ubuntu and can't get it to work again. I followed all the steps like last time and I can connect to Ipredator but as soon as I am connected, it's impossible to go to a new homepage or to ping...

Any ideas?

After I updated Network manager the problem disappeared. I guess it was a bug in Karmic.

---

### Post by Sheep78 on 2009-08-10
anyone else has problems with connection drops in ipredator?
especially with a lot of connections or high bandwith usage.
it seems that the LCP packets time out or something.q

---

### Post by 1/0 on 2009-08-11
> **Sheep78 said:**
> anyone else has problems with connection drops in ipredator?
especially with a lot of connections or high bandwith usage.
it seems that the LCP packets time out or something.q

Only twice in two weeks for me.

---

### Post by lambdacore on 2009-08-11
great, thanks a lot!
i just registered and was messing around with the VPN configuration.
it worked when i did the 3 steps you said in Advanced configuration.

also about Kvpnc, we used to have a vpn at school and i had to use kvpnc to make it work. so if you have problems, try this.

---

### Post by dpet on 2009-08-13
> **Sheep78 said:**
> anyone else has problems with connection drops in ipredator?
especially with a lot of connections or high bandwith usage.
it seems that the LCP packets time out or something.q

Yes, I have the same problem. As you say, it only happens when i have lots of (torrent)connections.

---

### Post by Blobba on 2009-08-15
I have the same problem! and its when you are having lots of torrenttraffic you really need the vpn-tunnel, although i prefer to always have connected. 

Maybe a noob question (most likely :) ) i have Gnome can i use this KDE package that automaticly reconnects? 

Maybe there is a way to script this with gnome?

/Blobba

---

### Post by Bad_Byte on 2009-08-17
Any **K**ubuntu 8.04 users managed to use ipredator or a PPTP VPN service?

Knetworkmanager doesn't work (high on my wishlist: have some one put a voodoo curse on its maker), bugtracker sent me to 'kvpnc' which connects but creates a conflicting net route which has the same effect as taking out the ethernet cable and wait for connections to timeout.

---

### Post by Noggenfogger on 2009-08-23
Is there anyone that know's how to do this when running server (i have no kde/gnome desktop environment)?

---

### Post by DPic on 2009-08-25
Has anyone gotten this working in Karmic?

---

### Post by natacho on 2009-09-01
> **Sheep78 said:**
> anyone else has problems with connection drops in ipredator?
especially with a lot of connections or high bandwith usage.
it seems that the LCP packets time out or something.q

I have that problem, anyway to solve it?

---

### Post by KhaaL on 2009-09-05
a small headsup, you cannot run this in karmic due to "pppd" and "pptpd" daemons missing. pptpd package exists, but pppd does not. will look into this further and update my post...

---

### Post by DPic on 2009-09-05
...but i have since gotten it working in karmic!

---

### Post by KhaaL on 2009-09-05
oh? share your magic then :P

---

### Post by DPic on 2009-09-05
i don't think i did anything special-- just some update fixed the problem. now the only problem is it doesn't automatically (re)connect at startup or after getting disconnected.

---

### Post by KhaaL on 2009-09-06
well, i just forgot to install pptp-linux... 

[SIZE="7"]Do'h![/SIZE] #-o

---

### Post by mikaellarson on 2009-09-15
I run Ubuntu netbook remix 9.04. Before my recent reinstall vpn.ipredator.se worked just fine. After the necessary reinstall of UNR I did exactly as described but I get the error message popped up saying "the vpn client service fail to start" when I select the correctly configured vpn connection. Any thoughts?

---

### Post by Bakoo on 2009-09-16
I've lost my connection several times now.  I contacted support and was told to lower my connections, which did nothing, still lost the vpn.  I have it now set at (Wine, uTorrent) at upload 45 kB/s, down 55kB/s, Global max 75, max peers per torrent 25, upload slot 4 (more if up speed less than 90%), and net max halfopen 20.

Its worked for the past day, but that doesn't really mean anything as it worked for the first 4 days or so OK.

Is there anyway to keep the connection being reset to the non-vpn once the connection drops?  That is what really bugs me.  No security there.

---

### Post by Bakoo on 2009-09-20
Ipredator support said about 40 connections max is what is stable.  I changed my global max & max peers connected to 35.  Now the connection seems OK.  I probably will also set the firewall to prevent a non-VPN connection from being inadvertently established.

---

### Post by Bakoo on 2009-09-23
Lost Ipredator connection again.  According to SwissVPN, a router firewall is what should be used to prevent a re-establishing of a non-VPN connection after the VPN connection fails.  I got a DL-604 router that is now configured to prevent an outgoing connection except to link to the router and to the VPN tunnel.

Interesting commentary on IPREDator:  [http://www.p2pnet.net/story/24418](http://www.p2pnet.net/story/24418)

SwissVPN is cheaper and has OpenVPN.  Got a response from SwissVPN on their speed:

We're offering OpenVPN as
it is much more reliable in networks where providers try to block services.

We provide 5'000/2'000 Kbit/s at our ports -  please take into account
that all traffic is being routed through Switzerland.
Depending on application additional latency may reduce performance.

---

### Post by bigboy7foru on 2009-09-25
How can i try the Ipredator.se service??

---

### Post by KhaaL on 2009-09-26
After using ipredator for 3 months, i'm giving up on it and have gone over to swissvpn and their openvpn service. They're cheaper and offer openvpn, if they're better or worse remains to tell however!

---

### Post by aphelionos on 2009-11-12
I am trying hard to make PPTP work though network manager on Karmic, but with no luck. I have installed Network-manager-pptp pptp-linux and more... but still it says that VP fails to start. Here is my output from tail -f /var/log/syslog while I try to connect to VPN twice:

---
Nov 12 11:22:33 Cyrano NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov 12 11:22:33 Cyrano NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2325
Nov 12 11:22:33 Cyrano NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Nov 12 11:22:33 Cyrano NetworkManager: <info>  VPN plugin state changed: 1
Nov 12 11:22:33 Cyrano NetworkManager: <info>  VPN plugin state changed: 3
Nov 12 11:22:33 Cyrano NetworkManager: <info>  VPN connection 'Ipredator' (Connect) reply received.
Nov 12 11:22:33 Cyrano NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'Ipredator' failed to connect: 'No VPN secrets!'.
Nov 12 11:22:33 Cyrano NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov 12 11:22:33 Cyrano NetworkManager: <info>  Policy set 'Auto SU' (ra0) as default for routing and DNS.
Nov 12 11:22:46 Cyrano NetworkManager: <debug> [1258021366.001256] ensure_killed(): waiting for vpn service pid 2325 to exit
Nov 12 11:22:46 Cyrano NetworkManager: <debug> [1258021366.001514] ensure_killed(): vpn service pid 2325 cleaned up
Nov 12 11:22:55 Cyrano wpa_supplicant[972]: CTRL-EVENT-SCAN-RESULTS 
Nov 12 11:22:55 Cyrano kernel: [  199.656068] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1066
Nov 12 11:23:25 Cyrano NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov 12 11:23:25 Cyrano NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2575
Nov 12 11:23:25 Cyrano NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Nov 12 11:23:25 Cyrano NetworkManager: <info>  VPN plugin state changed: 3
Nov 12 11:23:25 Cyrano NetworkManager: <info>  VPN connection 'Ipredator' (Connect) reply received.
Nov 12 11:23:25 Cyrano NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'Ipredator' failed to connect: 'No VPN secrets!'.
Nov 12 11:23:25 Cyrano NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov 12 11:23:25 Cyrano NetworkManager: <info>  Policy set 'Auto SU' (ra0) as default for routing and DNS.
Nov 12 11:23:38 Cyrano NetworkManager: <debug> [1258021418.004184] ensure_killed(): waiting for vpn service pid 2575 to exit
Nov 12 11:23:38 Cyrano NetworkManager: <debug> [1258021418.004466] ensure_killed(): vpn service pid 2575 cleaned up


Please help me make this work, I've tried googling everywhere without any success. This is a critical feature we need in Ubuntu!

---

### Post by aphelionos on 2009-11-12
Ok, now I got pptp to work partly in Karmic.

The main bug seems to lie in communication between the pptp app and the keyring. At least: By leaving password open, and not saving any passwords to tthe keyring it works just fine.

---

### Post by Eldis on 2010-01-29
> **aphelionos said:**
> Ok, now I got pptp to work partly in Karmic.

The main bug seems to lie in communication between the pptp app and the keyring. At least: By leaving password open, and not saving any passwords to tthe keyring it works just fine.

Yeah I couldn't get it to work either when I checked connection available for all users.

1) don't save the password to the keyring permanently (for this session seems to work)

2) Don't check connection available for all users.

Then it seems to work. I haven't had any connection drops that people have been reporting. I have also been getting very close to my max speeds. Granted I have had moments when I very slow connections but the majority of the day seems to work fine. I haven't been able to get it to automatically connect at boot but I'm fine with that I boot very rarely.

---

### Post by ugm6hr on 2010-02-06
Given how common VPN's must be, I'm somewhat surprised that the wiki doesn't have any recent detail on NM 0.7's VPN capability and how to set things up.

This was brilliant.  Thanks.

For people struggling, the restart of the laptop seemed to be thing I was missing!

---

### Post by outlaw45k on 2010-05-02
also if you try to connect but nothing happen you need to reboot

also to get this working on linux dont use on your password characters like **ñ ç &#537; &#539; &#259; î â** this only work on windows

---

### Post by Doki on 2010-05-12
Hi all :)

So I finally decided to subscribe Ipredator VPN... But I had lot of troubles to make it work on Ubuntu 10.04 64 ^^
I had first to not store the password in the keyring (seems to be a common problem here) before it actually tries to connect...
Then I had a connection timed out message...
I finally get rid of this last one by putting the IP address 93.182.181.2 instead of vpn.ipredator.se ...
It's doesn't seems to be a problem from the DNS I'm using (ping vpn.ipredator.se or telnet are working fine on it... ) so it may be a problem with the network manager or just with the pptp layer...

I hope it will help somebody else to connect :)

---

### Post by Acoustyk on 2010-05-20
> **Doki said:**
> Hi all :)

So I finally decided to subscribe Ipredator VPN... But I had lot of troubles to make it work on Ubuntu 10.04 64 ^^
I had first to not store the password in the keyring (seems to be a common problem here) before it actually tries to connect...
Then I had a connection timed out message...
I finally get rid of this last one by putting the IP address 93.182.181.2 instead of vpn.ipredator.se ...
It's doesn't seems to be a problem from the DNS I'm using (ping vpn.ipredator.se or telnet are working fine on it... ) so it may be a problem with the network manager or just with the pptp layer...

I hope it will help somebody else to connect :)

Wow I think that I'm in the same boat as you.  Did you ever connect?  I'm pinging vpn.ipredator.se but I'm not getting a connection with the VPN.  Did you end up finding a solution?  Please post if so...  Mine stopped working today and I can't figure out the issue.  It seems like there might be a keyring issue because sometimes the password isn't listed when I check the settings.

Thanks!

---

### Post by Acoustyk on 2010-05-21
> **Acoustyk said:**
> Wow I think that I'm in the same boat as you.  Did you ever connect?  I'm pinging vpn.ipredator.se but I'm not getting a connection with the VPN.  Did you end up finding a solution?  Please post if so...  Mine stopped working today and I can't figure out the issue.  It seems like there might be a keyring issue because sometimes the password isn't listed when I check the settings.

Thanks!

I've since got it working on my netbook via wifi but not on my main computer via ethernet.  Still don't know what is wrong...

---

### Post by Acoustyk on 2010-05-24
Bump

---

### Post by wertmnbv on 2010-05-27
hi guys,
in 9.10 i got ipredator working but since the update to 10.04 it doesn't work anymore. i tried to put the ip-address in as mentioned above and i got the same 'failed' message as before ... is here anybody who got it working?
cheers jo

---

### Post by Acoustyk on 2010-05-31
Bump.  10.04 NBE isn't giving me problems but lucid is... Any ideas?

---

### Post by p3nix on 2010-06-26
I'm having problems connecting using 10.04 Netbook Remix on my Lenovo IdeaPad S10. My Win 7 desktop has no problems, just the netbook. I've tried wifi and ethernet connections with no success. 

I've tried all kinds of options in the GUI config, and done every suggestion I could find on Google. I started messing with the command line version but it doesn't seem much different.

```
root@netbook:/var/log#pon ipredator nodetach debug
using channel 18
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
send [LCP ConfReq id-0x1 <asyncmap 0x0> <magic 0xfb20b5c8> <pcomp> <accomp>]
--- above line prints 10 times ---
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
```

```
Contents of /etc/ppp/peers/ipredator:
pty "pptp vpn.ipredator.se --nolaunchpppd"
lock
noauth
nobsdcomp
nodeflate
name myusername
remotename ipredator
ipparam ipredator
require-mppe-128

```

Update June 27, 2010:
I tried installing Ubuntu desktop instead of netbook edition. No difference. Next I bypassed the router and connected the computer directly to the DSL modem... and it worked. The thing is my Windows 7 computers CAN connect without a problem through the router. I know some other people have had problems with certain routers as well. If Windows can do it and Ubuntu can't, I suspect that there is some problem or limitation with Ubuntu preventing this from working.

---

### Post by regomodo on 2010-08-15
Ipredator on Ubuntu has been really flakey for me. Generally, it won't connect.

So far the following appears to have worked:

```
me@my-desktop:~$ nslookup vpn.ipredator.se
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	vpn.ipredator.se
Address: 93.182.149.2
Name:	vpn.ipredator.se
Address: 93.182.150.2
Name:	vpn.ipredator.se
Address: 93.182.151.2
Name:	vpn.ipredator.se
Address: 93.182.152.2
Name:	vpn.ipredator.se
Address: 93.182.153.2
Name:	vpn.ipredator.se
Address: 93.182.164.2
Name:	vpn.ipredator.se
Address: 93.182.179.2
Name:	vpn.ipredator.se
Address: 93.182.180.2
Name:	vpn.ipredator.se
Address: 93.182.181.2
Name:	vpn.ipredator.se
Address: 93.182.185.2
Name:	vpn.ipredator.se
Address: 93.182.186.2
Name:	vpn.ipredator.se
Address: 93.182.187.2
Name:	vpn.ipredator.se
Address: 93.182.188.2
Name:	vpn.ipredator.se
Address: 93.182.189.2
Name:	vpn.ipredator.se
Address: 93.182.190.2
Name:	vpn.ipredator.se
Address: 93.182.130.2
Name:	vpn.ipredator.se
Address: 93.182.133.2
Name:	vpn.ipredator.se
Address: 93.182.146.2
Name:	vpn.ipredator.se
Address: 93.182.147.2
Name:	vpn.ipredator.se
Address: 93.182.148.2

```

I picked the 1st address and used that as the Gateway instead of "vpn.ipredator.se"

---

### Post by isecore on 2010-08-27
I've got it setup and it connects without a problem. When doing ifconfig in a shell it shows there's two connections - my regular eth0 and a ppp0 with an additional IP-adress.

However, when I surf It doesn't use the VPN-tunnel and instead goes through my regular connection, which is the opposite of what I want.

Why is that?

**Update: never mind, I was an idiot and didn't triplecheck stuff before running off to wail on the forums. Sorry!**

---

### Post by vectorm12 on 2010-09-14
Would you mind giving me your exact setup? I'm running a fully updated 10.4 Ubuntu Desktop but I despite not saving the password and using the IP instead of DNS name I still get the "VPN connection failed" message.

> **isecore said:**
> I've got it setup and it connects without a problem. When doing ifconfig in a shell it shows there's two connections - my regular eth0 and a ppp0 with an additional IP-adress.

However, when I surf It doesn't use the VPN-tunnel and instead goes through my regular connection, which is the opposite of what I want.

Why is that?

**Update: never mind, I was an idiot and didn't triplecheck stuff before running off to wail on the forums. Sorry!**

---

### Post by isecore on 2010-09-14
I login to name, not IP. Username, password hidden and remembered.

Under the Advanced settings I have "Use Point-to-Point encryption" enabled. This was not enabled by default, but the post here: [http://christianengstrom.wordpress.com/2010/03/07/installing-ipredator-under-ubuntu-linux-9-10/](http://christianengstrom.wordpress.com/2010/03/07/installing-ipredator-under-ubuntu-linux-9-10/) said that it should be enabled. Other than that no real changes. I basically followed the guide on that page, with some modifications since the software center has changed since 9.10, I simply used aptitude to install packages instead.

Hope this helps!

> **vectorm12 said:**
> Would you mind giving me your exact setup? I'm running a fully updated 10.4 Ubuntu Desktop but I despite not saving the password and using the IP instead of DNS name I still get the "VPN connection failed" message.

---

### Post by peternz on 2010-10-28
> **outlaw45k said:**
> also if you try to connect but nothing happen you need to reboot

also to get this working on linux dont use on your password characters like **ñ ç &#537; &#539; &#259; î â** this only work on windows

Thank you! Spent an age on this with no luck. But when I removed ALL special characters (including punctuation) from my password, it works just fine.

Thus far.

---

### Post by Kaheil on 2010-10-30
I followed the tutorial and it worked like a charm on my main pc. However it does not work on my two other computers (another desktop and a netbook). 
I've done the exact same procedure on all computers.

(all running 10.10)

---

### Post by mpbb77 on 2012-09-24
Has anyone already tried IPredator through openvpn ? I have just signed and followed their instructions to import the config file to the network-manager-openvpn plugin. It actually worked without a glitch and so far I'm very satisfied.

The issue is I tried to do the same through command line and  it didn't work. They don't have instructions for Ubuntu CLI but they do for Debian, Freebsd and Openbsd. The connection with this config actually is successful but the routing in this case is different from the NM setup. 

The culprit seems to be the push commands from the server, there is a route command and a redirect-gateway one which apparently issues a duplicated route command just after. The system complains that the "file exists" and apparently does not finish the push job since I get slight different tables (gateway is still local) and eventually no vpn connection.

I'm surprised that NM works with the same commands and CLI don't , I would think that generally is the other way around.
Does anyone have a clue, I can post the route messages and tables if needed.

---


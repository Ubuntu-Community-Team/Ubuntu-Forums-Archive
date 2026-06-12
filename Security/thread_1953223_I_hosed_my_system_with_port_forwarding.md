---
title: "I hosed my system with port forwarding"
date: 2012-04-05
forum: Security
---

### Post by Ms. Daisy on 2012-04-05
oops...

I've been trying to use my new ssh session to browse the internet.  The option I tried first was from this document:

[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

Specifically, I followed the Dynamic Port Forwarding section.
 
And now my server & the laptop won't connect to the internet.  I'm not sure how to undo what I did, but I think it centers around this command that I tried:

```
ssh -D 9999 -C me@ipaddress.com
```

Help! How do I fix this?
[EMAIL="me@ipaddress.com"][/EMAIL]

---

### Post by kevdog on 2012-04-05
No panic -- which computer doesn't work, the server or the client?  I don't think anything you did is unreversible.  If both don't connect, I'd say its either a router issue or network issue.

---

### Post by Ms. Daisy on 2012-04-06
It's both.  

I assigned both computers static internal IPs which are part of the network (I accidentally put them on a separate subnet at first LOL, but now they're definitely all on 192.168.1.x with 255.255.255.0) 

The only thing I changed in my router was to port forward ssh to my server on the obscure port.  That worked fine yesterday.

What shall I investigate on my network?

---

### Post by QIII on 2012-04-06
Oh Noooooo!  Ms. Daisy!  My hero!  Say this isn't so!  ;)

Don't have anything by way of help to offer.  But I'm going to watch the thread.  Something interesting for me to learn here.

(Remember what I said about thoughtful questions?  Congrats on the membership by the way!)

---

### Post by redmk2 on 2012-04-06
> **Ms. Daisy said:**
> It's both.  

I assigned both computers static internal IPs which are part of the network (I accidentally put them on a separate subnet at first LOL, but now they're definitely all on 192.168.1.x with 255.255.255.0) 

The only thing I changed in my router was to port forward ssh to my server on the obscure port.  That worked fine yesterday.

What shall I investigate on my network?

Is the router LAN interface in the same 192.168.1.0 /24 subnet?  Are the gateway IP addresses on your 2 hosts defined as the LAN interface of the router?

---

### Post by mr-woof on 2012-04-06
As mentioned is the router on 192.168.1.x? Take off the static's, you might of put the wrong subnet mask/gateway in there, put them back on dhcp and give them a reboot.

In your browser, for the ssh forwarding to work, have you changed any of the network settings?

Do they work now?

---

### Post by darkod on 2012-04-06
And what actually are you trying to achieve with the Dynamic Port Forwarding? I sounds very confusing to me.

Also, did you notice the part where it says if you configure a proxy in Firerox to use the Dynamic PF after you finish with the connection you need to disable the proxy or firefox won't work.

If you explain what you need, you might be able to receive better advice. If you have only a single server, and how Dynamic PF is explained in the link you provided, I really can't see any benefit from it. Just problems. :)

Also, if you tried to use a port different than 22 on the server, you are aware you need to change it in /etc/ssh/sshd_config right?

---

### Post by SeijiSensei on 2012-04-06
In your earlier posting about port forwarding you wrote:

> 2. Whenever I turn my computer off, it gets reassigned a new local IP (192.168.0.x) - do I need to set permanent internal IP addresses for this to work? 

If you assigned the machines addresses in 192.168.1.0/24, that's the problem.  They need addresses in the 192.168.0.0/24 subnet.

---

### Post by Ms. Daisy on 2012-04-06
> **mr-woof said:**
> As mentioned is the router on 192.168.1.x? > Is the router LAN interface in the same 192.168.1.0 /24 subnet?  Are the  gateway IP addresses on your 2 hosts defined as the LAN interface of  the router? 	
Yes. Router is 192.168.1.1. The client is still dynamic, I never set a static IP.  The sshd machine (host) was statically set to 192.168.1.100

> **mr-woof said:**
> Take off the static's, you might of put the wrong subnet mask/gateway in there, put them back on dhcp and give them a reboot. 
I'm not certain what the default is supposed to look like.  Right now on both machines my /etc/network files say
```
auto lo
iface lo inet loopback
```
I added dhcp in there, but then bash complained that it couldn't read the file. Anyone know what the default should look like?

> In your browser, for the ssh forwarding to work, have you changed any of the network settings? > Also, did you notice the part where it says if you configure a proxy in  Firerox to use the Dynamic PF after you finish with the connection you  need to disable the proxy or firefox won't work. Yes but those were easy to undo and they're now back to default.

> And what actually are you trying to achieve with the Dynamic Port Forwarding? I sounds very confusing to me. Also, if you tried to use a port different than 22 on the server, you  are aware you need to change it in /etc/ssh/sshd_config right? 	 LOL- obviously it's confusing to me too.  I had to port forward so that I can ssh from an external IP into my home sshd machine.  It worked perfectly until I started screwing around with tunneling firefox. Maybe I misnamed my thread. I don't think port forwarding hosed it, but trying to tunnel firefox through ssh did.

> Oh Noooooo!  Ms. Daisy!  My hero!  Say this isn't so!LOL hero?? That's a lot to live up to!

---

### Post by Ms. Daisy on 2012-04-06
> **SeijiSensei said:**
> In your earlier posting about port forwarding you wrote:

If you assigned the machines addresses in 192.168.1.0/24, that's the problem.  They need addresses in the 192.168.0.0/24 subnet.
Yes- I was actually wrong in that post, and that led me to put them on the wrong subnet at first.  The actual address of my router is 192.168.1.1

---

### Post by darkod on 2012-04-06
The lo is the loopback interface. What you should have in /etc/network/interfaces below the lo entry, is something like:
```
auto eth0
iface eth0 inet dhcp
```

or
```
auto eth0
iface eth0 inet static
   address 192.168.1.x
   netmask 255.255.255.0
   gateway 192.168.1.1

```

Usually what you would need to do to access your server from outside is:
1. Configure the server to has static private IP. It seems yours is already configured with 192.168.1.100.
2. Enter the router config page and configure port forwarding of port 22 (if you haven't changed the default SSH port on the server) to 192.168.1.100.

That's it. Using your router public IP you should be able to enter your server with SSH. Note that you will probably receive many attacks especially if you leave the port at 22, so think about security too.
If your router doesn't have fixed public IP you will need to know it if it changes in order to access from outside.

---

### Post by Doug S on 2012-04-06
> I'm not certain what the default is supposed to look like. Right now on both machines my /etc/network files say
 
Code:
auto loiface lo inet loopback
I added dhcp in there, but then bash complained that it couldn't read the file. Anyone know what the default should look like?
Do you mean /etc/network/interfaces?
Anyway, I think we now know why it doesn't work... I think it should look like
```
# The loopback network interface
auto lo
iface lo inet loopback
# The primary interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by Ms. Daisy on 2012-04-06
That seemed to work on the desktop machine. Thank you!

For the laptop, I'm assuming I need the wlan0 interface as well so the /etc/network/interfaces file now looks like this:
```
# The loopback network interface 
auto lo 
iface lo inet loopback 

# The primary interface 
auto eth0 
iface eth0 inet dhcp

# wireless interface
auto wlan0
iface wlan0 inet dhcp
```I restarted networking at this point using sudo /etc/init.d/networking restart
And bash HATED that. It said```
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
Failed to bring up eth0. 
Ignoring unknown interface wlan0=wlan0
```Right. So I tried ```
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
sudo ifconfig eth0 down && sudo ifconfig eth0 up
```bash didn't complain, but I still can't get firefox to connect to the internet.

when I look at ifconfig on the laptop I see eth0, lo, and wlan0 all as they always have appeared. (I'd copy and paste the output here but... oh wait... I can't connect to firefox :/)

---

### Post by Ms. Daisy on 2012-04-06
And BTW, I checked firefox's settings on the laptop. I have "configure Proxies to Access the Internet" set to "no proxy."

in about:config, I have network.proxy.socks_remote_dns set to false.

So I think firefox is configured properly.  Anything else I should check?

---

### Post by darkod on 2012-04-06
It seems the problem is the interfaces not coming up. Right now it looks it's not related to firefox settings.

But I can't figure out what is wrong myself. Anything else you touched in the laptop config? Messing around with the interfaces?

Note: The wireless interface might not be wlan0 sometimes. It depends. Have you seen it as wlan0 earlier?

---

### Post by Doug S on 2012-04-06
I don't use wireless (at least in this way), but I think you might need something similar to:```
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid mynetworkname
    wpa-psk mysecretpassphrase
```
No sure. Once you get it all going again, be sure to save "master" copies of configuration files before experimenting (I so learned that the hard way).

---

### Post by Ms. Daisy on 2012-04-06
Yes, as far as I can remember ifconfig has always showed the wireless connection to be wlan0.  
#note to self: make detailed notes of what I do when experimenting from now on!!!

Does the contents of /etc/network/interfaces file that I posted above look right?
Is there another configuration file I need to check?

---

### Post by Ms. Daisy on 2012-04-06
> **Doug S said:**
> I don't use wireless (at least in this way), but I think you might need something similar to:```
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid mynetworkname
    wpa-psk mysecretpassphrase
```No sure. Once you get it all going again, be sure to save "master" copies of configuration files before experimenting (I so learned that the hard way).
Yes, I believe there are a few hard lessons in this thread for me as well.

That makes sense. However, I am actually connected to my wireless router right now.   The network manager applet shows that I'm connected. I can ping the router.  I can ping 8.8.8.8.  But Firefox won't connect to the internet. I get the "server not found" error message when it tries to connect to [www.google.com](www.google.com)

How do you use wireless if not in this way?  I need to set it back to default but I don't know what that is.

---

### Post by redmk2 on 2012-04-06
> **Ms. Daisy said:**
> Yes, as far as I can remember ifconfig has always showed the wireless connection to be wlan0.  
#note to self: make detailed notes of what I do when experimenting from now on!!!

Does the contents of /etc/network/interfaces file that I posted above look right?
Is there another configuration file I need to check?

If this laptop is using wireless then you are most likely using Network-Manager or WICD to manage the interfaces.  Neither use /etc/network/interfaces to configure the interfaces.  I don't run any wireless hosts so I can't give you the definitive answer, but Google should provide the answers to wireless config.

Maybe something like [**_[COLOR="Blue"]this[/COLOR]_**.]("http://ubuntuforums.org/showthread.php?t=1480826")

---

### Post by cryptotheslow on 2012-04-06
On a laptop here (12.04 Desktop) with ethernet and wireless, on which the wireless is active and working (otherwise I wouldn't be posting this :D ) and this is my complete /etc/network/interfaces:

```

crypto@ubulaptop1204:/etc$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```No mention of either eth0 or wlan0 there at all.

Digging a bit further it looks like Network Manager keeps it's configurations in /etc/NetworkManager

The 2 WLANs I have connected to from this laptop appear as files in /etc/NetworkManager/system-connections

It is those files that contain the wireless details like ssid, wpa key, IPv4 and IPv6 for each connection.

Sorry if I missed it, but are you on a standard desktop install or a server?

If desktop, try editing your /etc/network/interfaces file back to just the loopback entries, reboot then reconfigure your wlan and ethernet connections using Network Manager. I'd think having both Network Manager trying to manage them and manually putting entries in /etc/network/interfaces  is going to cause a conflict somewhere.

As for Firefox, make sure you haven't accidentally left a proxy configuration in there. Edit > Preferences > Advanced > Network Tab > Settings button  => check it is set to No Proxy

---

### Post by darkod on 2012-04-06
If you can ping 8.8.8.8 but not [www.google.com](www.google.com), then you have lost your DNS servers.

Look in /etc/resolv.conf and there should be like:
nameservers x.x.x.x
nameservers x.x.x.x

You can have one or more. Not sure right now if the word was 'nameservers' or 'nameserver'. You can try using your router as nameserver, usually works. Or just put googles dns, 8.8.8.8. Once you get connected you can google for your ISP nameservers which sometimes are faster choice (but not always).

---

### Post by Doug S on 2012-04-06
I only use Ubuntu server version, so sorry if I misguided because network manager does other things, and thanks to the others that jumped in.
 
for this:> How do you use wireless if not in this way?I use a linksys router set up as a switch to handle all the wireless clients. My Ubuntu server is still the network router, but I don't have to think about the wireless at all.

---

### Post by redmk2 on 2012-04-06
> **Doug S said:**
> ...for this:I use a linksys router set up as a switch to handle all the wireless clients. My Ubuntu server is still the network router, but I don't have to think about the wireless at all.

Also know as an access point (AP).  I do the very same thing on my network.  The network router just sees the traffic and the AP does the wireless setup for my 2 laptops and iPhone.

---

### Post by Ms. Daisy on 2012-04-06
> **darkod said:**
> If you can ping 8.8.8.8 but not [www.google.com]("http://www.google.com"), then you have lost your DNS servers.

Look in /etc/resolv.conf and there should be like:
nameservers x.x.x.x
nameservers x.x.x.x

You can have one or more. Not sure right now if the word was 'nameservers' or 'nameserver'. You can try using your router as nameserver, usually works. Or just put googles dns, 8.8.8.8. Once you get connected you can google for your ISP nameservers which sometimes are faster choice (but not always).
That was it!!! I had no DNS at all.  

Lessons for Ms. Daisy: 
1. When you play with config files, SAVE THE ORIGINALS
2. Write down what you do when experimenting. Makes undoing much easier!
3. This forum rocks.

Thanks to all for helping!

---

### Post by Ms. Daisy on 2012-04-06
However...

if you edit /etc/resolv.conf manually, it will be overwritten at system restart (or maybe even every 900 seconds according to one old blog I found).

I only found a way to make the DNS change permanent through the GUI. You have to open network --> wireless --> configure
In the new window, go to IPv4 tab, add the address to the DNS servers box.  (I used my router address)
I restarted the computer and the DNS remained.

---

### Post by darkod on 2012-04-07
> **Ms. Daisy said:**
> However...

if you edit /etc/resolv.conf manually, it will be overwritten at system restart (or maybe even every 900 seconds according to one old blog I found).

I only found a way to make the DNS change permanent through the GUI. You have to open network --> wireless --> configure
In the new window, go to IPv4 tab, add the address to the DNS servers box.  (I used my router address)
I restarted the computer and the DNS remained.


Hmm, the dns shouldn't change unless you are using DHCP to assign IP to your computer/laptop. But in that case it should have worked earlier too since DHCP assign dns servers too.
Otherwise, the dns should remain the same if you have static setup.

Anyway, if it works now it's solved. Maybe the dns assigned by DHCP doesn't work properly.

---

### Post by kevdog on 2012-04-07
Ms Daisy

I'm really confused about what you've done here.  I've used ssh dynamic port forwarding like one hundred times and have never had to edit the /etc/resolv.conf file.  In can only see the resolv.conf coming into play if you are using static IP's or something is wrong with your router.

---

### Post by Ms. Daisy on 2012-04-07
> **kevdog said:**
> Ms Daisy

I'm really confused about what you've done here.  I've used ssh dynamic port forwarding like one hundred times and have never had to edit the /etc/resolv.conf file.  In can only see the resolv.conf coming into play if you are using static IP's or something is wrong with your router.
I was trying various things to tunnel firefox through ssh. It included setting static IPs on both computers.  I'm fairly certain now that I hosed dns when I was setting up proxy in firefox, or when I was configuring static IPs, or when I tried to route dns through the tunnel.

---

### Post by kevdog on 2012-04-07
I'd bet it was when you tried to use static IPs.  If you are running a small network at home based on dhcp, even if you are running systems with dynamic addresses, the IP address assigned to the machine is usually unlikely to change unless you turn off and reboot the router. 

Even when setting static IPs you don't usually remember having to set static DNS servers (although I do on windows).

/etc/resolv.conf if a dynamic file -- its not persistent after reboot.

On older versions of ubuntu, persistent name declarations used to be kept at /etc/dhcp3/dhclient.conf.  I'm wondering if this was the file that was actually edited through your gui modification.

---

### Post by SeijiSensei on 2012-04-07
> **kevdog said:**
> /etc/resolv.conf if a dynamic file -- its not persistent after reboot.

Yes, and managing resolv.conf has become a [really annoying problem]("http://ubuntuforums.org/showthread.php?t=1914807") in 12.04.

---

### Post by Ms. Daisy on 2012-04-07
> **SeijiSensei said:**
> Yes, and managing resolv.conf has become a [really annoying problem]("http://ubuntuforums.org/showthread.php?t=1914807") in 12.04.
I found [this]("http://lenss.nl/2008/11/making-permanent-changes-to-resolvconf-under-ubuntu/"), don't know if it would help you.  As far as I can tell, this has been a problem since 10.04.  But I've only got experience with 11.10 and I can confirm that it gets overwritten in that version.
> On older versions of ubuntu, persistent name declarations used to be  kept at /etc/dhcp3/dhclient.conf.  I'm wondering if this was the file  that was actually edited through your gui modification. The link above also mentions that file, perhaps that's the way to make permanent changes rather than /etc/resolv.conf

---

### Post by kevdog on 2012-04-07
Ms. Daisy, can you post your /etc/dhcp3/dhclient.conf file?  Altering this file really isn't a new thing.

---

### Post by redmk2 on 2012-04-07
> **Ms. Daisy said:**
> I found [this]("http://lenss.nl/2008/11/making-permanent-changes-to-resolvconf-under-ubuntu/"), don't know if it would help you.  As far as I can tell, this has been a problem since 10.04.  But I've only got experience with 11.10 and I can confirm that it gets overwritten in that version.
 The link above also mentions that file, perhaps that's the way to make permanent changes rather than /etc/resolv.conf

You are aware that /etc/resolv.conf and resolvconf are two different things.

The conf file /etc/resolv.conf is where DNS name servers are defined.  If you do this manually then you need to insure that it is not overwritten.  

You can do this in a number of ways.  Removing the resolvconf package is one way.  This is an optional package.  I don't have it on any of my workstations (10.04 and 11.04).  Editing the dhclient.conf file is another.  Defining the DNS name servers is an option in the dhclient.conf file, not a mandatory setting.  I have no options identifying name servers in that file.  Of course the DHCP client isn't running anyway.  :-)

---

### Post by Ms. Daisy on 2012-04-08
> **kevdog said:**
> Ms. Daisy, can you post your /etc/dhcp3/dhclient.conf file?  Altering this file really isn't a new thing.
It's empty.

---


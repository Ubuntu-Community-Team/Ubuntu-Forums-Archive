---
title: "Ubuntu as an access point"
date: 2005-11-24
forum: Server Platforms
---

### Post by Daveo on 2005-11-24
Hi all, 

I want to build an access point with ubuntu. I have got this far...

```

iwconfig ath0 essid daveo mode master
iwpriv ath0 mode 3

```

Now I can connect to the access point, but I need to know where to go from here. Sorry for being so vague. 

- Dave

---

### Post by odin on 2005-11-24
I have done it and what I would do now is to set the dhcp server.You have just to install it with

sudo apt-get install dhcp3-server

then edit /etc/dhcp3/dhcpd.conf to configure all the options.

That was my second step but it depends on how far you wanna go.What driver do you use,madwifi,hostap?

Dont know what you wanna do.you can set a wep-key for example.

---

### Post by Daveo on 2005-11-24
Currently I have a DHCP server on the network that can assign IPs for me, but here's my wish list..

Ubuntu access point with madwifi (Atheros chipset)

- DHCP server (is this essential?)
- WPA
- Mac address filtering
- Maybe authing via radius (only if this is easier)

Right now, I just want to use my apache server as a WPA access point and am looking for the easiest and quickest way for that to happen. I can then play with Radius later. Is this doable?

Also does ubuntu automatically work out the routing or do I have to manually fudge iptables or something to make the box actually route wireless traffic to the internet?

---

### Post by odin on 2005-11-25
What I have done was with hostap but I guess the configuration thing must be the same once is installed and running.

The thing about dhcp is not essential you can set the ip of every machine connected to the acces point static.Guess the dhcp server you have is for your wired network.

dont now about wpa but I'm interested if you can get it working ;) 

The mac filtering can be done via the dhcp server (touching a bit dhcpd.conf) or with the commands iwpriv  "device" maccmd( here there are different options,1 for allowing macs you'll add with the next command,2 for denying macs you'll add with the next command,and 4 is to kick all the connections out) and then iwpriv "device" addmac "mac address"(this to add a mac address following the rule you create with the previous command)

For the forwarding thing to get acces to the internet is as simple as this:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o "inet_device" -j MASQUERADE

where inet_device is the device with acces to the internet.

What I suggest you is to make a script with all these things so you dont have to type all this everytime.

hope this is comething you can use

---

### Post by Daveo on 2005-11-25
[QUOTE=odin]For the forwarding thing to get acces to the internet is as simple as this:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o "inet_device" -j MASQUERADE

where inet_device is the device with acces to the internet.[/QUOTE]

Yeah.. That didnt seem to work for me. My wireless interface is ath0 and my ethernet (internet) interface is eth0. I replaced inet_device with eth0 and I had no joy. :( 

A couple of things;

- I havent assigned an IP to the wireless interface, do I need to do that?
- Do both ath0 and eth0 need to be the same or different subnets?
- What is my default gateway set to?
- should I be doing anything with the route command to get this working?
- How can I test what's going wrong?
- Do you have the steps from start to finish on how to make this happen?

---

### Post by odin on 2005-11-26
[QUOTE=Daveo]Yeah.. That didnt seem to work for me. My wireless interface is ath0 and my ethernet (internet) interface is eth0. I replaced inet_device with eth0 and I had no joy. :( 

A couple of things;

- I havent assigned an IP to the wireless interface, do I need to do that?
- Do both ath0 and eth0 need to be the same or different subnets?
- What is my default gateway set to?
- should I be doing anything with the route command to get this working?
- How can I test what's going wrong?
- Do you have the steps from start to finish on how to make this happen?[/QUOTE]

Ok I'll try to make a mini-howto for this but I can tell you a couple of things that may help you to start.

yes,you have to assign an ip address to the wireless interface.I do that setting in /etc/network/interfaces.

The interfaces dont have to be in the same subnet.

Now I need to get some sleep but I think that if you have the wireless in master mode assign the ip and do the two lines I told you in the other post it should work.there is a log file that tells you what's going on in your system but I cant tell you right now cause I dont have my linux box here.try this and soon I'll try to give you more information.A simple ocnfiguration of all this it's not very difficult so dont worry,we'll get working.

---

### Post by Daveo on 2005-11-27
Awesome, I'll give that a go and let u know. :)

---

### Post by snakeman on 2005-11-29
odin:


Sorry for Hijacking the thread a little. I need some help with this also.  I am trying to create a AP with Breezy also. I need a few more step explained to me.
I have the interface up and running I need more help with Bridging and Lan setup . Did you ever finish the mini-howto?




snakeman

---

### Post by odin on 2005-11-29
[QUOTE=snakeman]odin:


Sorry for Hijacking the thread a little. I need some help with this also.  I am trying to create a AP with Breezy also. I need a few more step explained to me.
I have the interface up and running I need more help with Bridging and Lan setup . Did you ever finish the mini-howto?




snakeman[/QUOTE]

Sorry I'm really busy at work but I'm still working on it.I cant promise anything but I hope I have a bit of time this week so I can do it.It would be of help If you tell me how far you wanna get and if you need a bit of help with the config of the interface which has internet access so I can write exactly what you need.But I can tell some things that may help to start:

I guess you alredy installed the driver you need to set your wireless card in master mode.If the driver is installed it should automaticly set your interface in master mode.After this the first thing you need to do is give an IP and the rest of the parameters(as many as you want)to the interface.

Let's say teh interfaceis wlan0(if you are using madwifi it could be ath0).
A basic configuration would be something like this:

**ifconfig wlan0 your_ip netmask  your_netmask**
**iwconfig wlan0 essid essid_you_want **(the essid is just the network name)

this 3 parameters are the essentials but you can also set the wep_key ,channel, rate...

Now in order to forward your the connections from your AP to the internet you need this:

[B]echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o "inet_device" -j MASQUERADE[/B]

instead of inet_device you have to type the interface with internet access(in my system eth0)

To try if everything si ok try to conect another computer to your AP.I guess you now how but just in case:
[B]
iwlist interface scan[/B] (by interface I mean the interface you wanna conect to the AP which of course should be up).Now you'll see a list of AP in the range of your interface.Look for the one with the name you set before and type:

**iwconfig interface essid APessid** (again by interface I mean the interface you wanna conect to the AP).Type **iwconfig interface** to see in you are associated to the AP.

Now is time to set an IP:
**ifconfig interface your_IP netmask your_netmask** (I dont think I have to say again what I mean by interface :) )It's important that you remember to set the ip in the range of the AP and also the netmask.

Now time to try!!!

Well I'm reading it now and can see it might be a bit confusing aso dont hesitate to ask whatever you didnt understand and I'll answer as soon as possible.I promise I'll give the final document soon.Next step for me would be to set a dhcp server so you dont have to do all this every time.I can tell that you can install it with sudo apt-get install dhcp3-server and configure it in the /etc/dhcp3/dhcpd.conf file.It's very easy to do and I can help.

hope this helped you to get started.

---

### Post by snakeman on 2005-11-29
Thanks for the reply, I was a little slow on reading this one, but I can show you how far I am now. 

ath0      Link encap:Ethernet  HWaddr 00:0D:88:C7:46:D7
          inet6 addr: fe80::20d:88ff:fec7:46d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:16132 (15.7 KiB)
          Interrupt:18 Memory:e0dc0000-e0dd0000

br0       Link encap:Ethernet  HWaddr 00:0D:88:C7:46:D7
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fec7:46d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:15754 (15.3 KiB)

br0:0     Link encap:Ethernet  HWaddr 00:0D:88:C7:46:D7
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:00:6C:15:2E:1A
          inet addr:192.168.10.120  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe15:2e1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17633 (17.2 KiB)  TX bytes:30387 (29.6 KiB)
          Interrupt:22 Base address:0x2000

eth0:0    Link encap:Ethernet  HWaddr 00:00:6C:15:2E:1A
          inet addr:192.168.10.121  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:2B:29:D8
          inet6 addr: fe80::20e:a6ff:fe2b:29d8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I finally have all that working with DHCP, now to work on Named.  But I intend on loging in to the internet via ADSL and PPPOE  but I am struggling a little with this one.  It doesn't have Adsl-start and Stop.  Like the slackware days.  Anyway soon eth0 will basically be ppp0 and the other two interfaces will be bridged like above.  Are you using Hostapd with your AP configuration?  Working on PPPoE now and named (caching named server)


Thanks for the help, I dont have my Radius Server up and running yet but working on that tonite and maybe a web interface (just kidding)


snakeman

---

### Post by snakeman on 2005-11-30
Are you back yet?



snakeman

---

### Post by odin on 2005-11-30
[QUOTE=snakeman]Are you back yet?



snakeman[/QUOTE]

I'm sorry but I have more work than I thought.I'm using hostap and reading a bit I found out (I understood it well) that the hostapd(hostap daemon) may help a lot for configuring the interface used as AP even for wpa with and without Radius server.You can find in the same place as the driver.Have a look there,I'm really trying to find time for this but I'm getting a week of holydays very soon and I have to do my "duties" at work before I leave...at least that's what my boss says..

---

### Post by odin on 2005-11-30
Here is a good howto to start with hostap.i couldnt write my own yet but this may help you.

[http://trekweb.com/~jasonb/articles/hostap_20030727.shtml](http://trekweb.com/~jasonb/articles/hostap_20030727.shtml)

---

### Post by snakeman on 2005-11-30
Thanks, I will have a look.




snakeman

---

### Post by snakeman on 2005-12-01
SO far so good not really happy with my current setup, but I have Dhcp/DDNS working great on the LAN :)


snakeman

---

### Post by Daveo on 2005-12-04
Ok, 

**  So here is the quick and dirty version. (No DHCP server on box) **

This assumes that eth0 is on a 192.168.0.x/24 network, and that your wireless card is called ath0.

```


echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADE
ifconfig ath0 192.168.1.1 netmask 255.255.255.0
iwconfig ath0 essid my_wap mode master
iwpriv ath0 mode 3
ifconfig ath0 up


```

- Now set the IP on your laptop between 192.168.1.2 - 254 
- netmask to 255.255.255.0
- gateway to 192.168.1.1
- you will need to set your own name servers as well.

You should now be on the net.  :cool: 

Now to get WPA supplicant configured...

---

### Post by Daveo on 2005-12-05
ok, this has officially stumped me. I can find lots of info on how to get ubuntu to connect to a WPA access point but no info on how to "MAKE" ubuntu "BE" a WPA access point. 

Now I assume that I need to do something with /etc/wpasupplicant.conf and then need to run the line..

```


wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi


```

Can anyone help please? :confused:

---

### Post by odin on 2005-12-05
[QUOTE=Daveo]ok, this has officially stumped me. I can find lots of info on how to get ubuntu to connect to a WPA access point but no info on how to "MAKE" ubuntu "BE" a WPA access point. 

Now I assume that I need to do something with /etc/wpasupplicant.conf and then need to run the line..

```


wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi


```

Can anyone help please? :confused:[/QUOTE]

I'm still working on it si I can't tell you exactly how but as far as I know wpa_supplicant is only for the client side.The only way I found to make ubuntu be a wpa access point is using hostapd.It doesnt matter if you are using madwifi driver,it also works.Guess you know but you can get it in [http://hostap.epitest.fi/hostapd](http://hostap.epitest.fi/hostapd) .Then you need to change the parameters you need  in hostap.conf and in your case something in madwifi.conf.I'm really sorry I could not help more in all my posts...

---

### Post by Daveo on 2005-12-14
Yeah I gave hostapd a go but I couldn't get it working. 

I look forward to your document on it. :D 

Are you far off making it?

---

### Post by anthro398 on 2005-12-20
Could you please describe your hardware.  I'm interested in this, but don't have a wireless card for my server and am wondering if it's worth it to do this on the server or buy an off-the-shelf access point/router/firewall solution.  They're pretty cheap these days and much easier to configure and, most likely, maintain.  Are you using a third-party antenna?  What kind of range to you get?  

Taking this a step further, I was thinking of using iptables to redirect outbound network traffic to squid on the server.   I've also considered using nocat to authenticate users and then using iptables to redirect traffic to squid over ssl.    Haven't decided if that's possible yet, though.  Anyway, spending $30 on an access point would be much, much easier.  Any thoughts?

---

### Post by Daveo on 2005-12-28
Well, you can always go out and buy an access point and have it work out of the box. Having said that though, there is unlimited possibilities doing it with a server instead. So I guess it depends what you're after. 

Having said that I'm trying to build an all in one mini-itx server and so far its going pretty well. The range I get on the wireless card is quite good, but of course you could always just boost it with an external aerial. 

The only thing stopping me is getting this wireless secured. No one seems to be able to help me with hostap or whatever I need to get this thing secured. 

:mad:

---

### Post by Jengu on 2005-12-29
Isn't network-manager supposed to be able to do this for you?

---

### Post by Daveo on 2006-01-02
Personally I've never tried it, but from what I can see it requires X running. The server I'm trying to build is not running X. it's all terminal.

Uses less resources that way.

---

### Post by Daveo on 2006-01-02
Odin,

Can you post us your hostap.conf or something? I'd love to get this thing secured as I cant use it until then. 

:mad:

---

### Post by odin on 2006-01-04
yep I'll post it when I get home this eve.I dont have it here

---

### Post by Daveo on 2006-01-08
[QUOTE=odin]yep I'll post it when I get home this eve.I dont have it here[/QUOTE]

Awesome. I look forward to it. :p

---

### Post by Daveo on 2006-01-08
[QUOTE=odin]yep I'll post it when I get home this eve.I dont have it here[/QUOTE]

Hey odin, how is that hostapd.conf coming?

---

### Post by Daveo on 2006-01-09
btw: Here's how to get a WEP enabled AP up and working. 

```
iwconfig ath0 key s:password
``` is the wep password line. 
so replace password with a real password.

```


echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADE
ifconfig ath0 192.168.1.1 netmask 255.255.255.0
iwconfig ath0 essid my_wap mode master
iwpriv ath0 mode 3
iwconfig ath0 key s:password
ifconfig ath0 up


```

This will keep me going until I hear back from Odin on the WPA setup.

---

### Post by odin on 2006-01-09
sorry but I couldnt post it.I'm at work now but I promise I'll do it today.This time I'll give you my kidney If I dont...

BTW you should know that your network interface must have a a quite new firmware so WPA works.Now I dont remember how to find that out but If you think is in the the documentation you have in the hostapd package.

promise the latest tonight.

---

### Post by odin on 2006-01-09
[QUOTE=Daveo]Odin,

Can you post us your hostap.conf or something? I'd love to get this thing secured as I cant use it until then. 

:mad:[/QUOTE]
 
well here it is what works for me:

interface=wlan0
auth_algs=1
wpa=1
wpa_passphrase= WireLess 
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP

but again check the version of your firmware, that could be the reason why it doesnt work.BTW this works with hostap,if you are using madwifi then I dont know yet I wanna finish the AP with hostap and then I'll try with madwifi,well when I get a pci card for my desktop...

---

### Post by Daveo on 2006-01-10
[QUOTE=odin]well here it is what works for me:

interface=wlan0
auth_algs=1
wpa=1
wpa_passphrase= WireLess 
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP

but again check the version of your firmware, that could be the reason why it doesnt work.BTW this works with hostap,if you are using madwifi then I dont know yet I wanna finish the AP with hostap and then I'll try with madwifi,well when I get a pci card for my desktop...[/QUOTE]

Yep, that's it. :razz: 

the only difference I have is driver=madwifi.

So this is, in full, what I did to get mine working.

*NOTE* I am not using DHCP to assign anything. I have that all statically assigned on my laptop. If you need this example with DHCP let me know and I'll write it again. 

Equipment used;
- Dlink DWL-G520 PCI wifi card
- Breezy 5.10
- 2.4Gghz celeron el cheapo PC. 

Ubuntu already detects my D-Link (atheros) card and has madwifi installed, so I just did this. 

```
apt-get install hostapd
```

Edit /etc/hostapd/hostapd.conf, delete everything and put this
```

interface=ath0
driver=madwifi
auth_algs=1
wpa=1
wpa_passphrase=put_a_password_here
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP

```

then you need to make the wireless access point
```

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADE
ifconfig ath0 192.168.1.1 netmask 255.255.255.0
iwconfig ath0 essid my_wap mode master
iwpriv ath0 mode 3
ifconfig ath0 down

``` 

then bring up all services.
```

ifconfig ath0 up
/etc/init.d/hostapd restart

```

you should now be able to connect to your access point, if not try;
```

ifconfig ath0 up

```

That's it. If you have your ip's assigned correctly on the client machine you should be fine. 

Thanks Odin for the hostapd stuff. :D

---

### Post by odin on 2006-01-10
Glad to finally help with this.

And thank you very much for the information, I can see it's very similar to hostap so with what you posted should be enough when the time comes.

I dont know if you are interested but I found a way so you can hide the essid so anyone who wants to connect to your AP must know the real essid.

**iwpriv ath0 enh_sec 0** (so you show your essid)
**iwpriv ath0 enh_sec 1** (so you hide it)
**iwpriv ath0 enh_sec 2** (so when someone tries the option "any" for the essid             connection is rejected)
**iwpriv ath0 enh_sec 3 **(this applies  1 and 2 at the same time,I think is more secure)

---

### Post by Daveo on 2006-01-10
That's awesome! That was my next question, thanks alot!

---

### Post by Paris Heng on 2007-08-15
Hi Odin,


Might to ask u, where the How-To u promised to post?

Regards

---

### Post by alcohol99a on 2008-03-17
Hi..new to Linux..& im so interest with linux :) and want to build wirelss AP..
i followed ur intructions, i have some issue on that.im so sorry im linux newbie..

i have done....

ifconfig wlan0 your_ip netmask your_netmask  10.0.0.1 netmask 255.255.255.0 up
iwconfig wlan0 essid essid_you_want  (MY-WIFI)

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o **eth0** -j MASQUERADE {eth0 is my ADSL connection 192.168.1.1

after that i have try my nokia 9500 to scan my wireless .

do i need to reboot after all this?..once i reboot ..i lost all the things i have done
and is tht any permenant way to saveall the settings...is that by VI editor?

Thanks
[email]alcohol99a@yahoo.com[/email]

---


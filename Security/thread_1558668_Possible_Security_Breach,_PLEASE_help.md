---
title: "Possible Security Breach, PLEASE help"
date: 2010-08-22
forum: Security
---

### Post by actsofaith on 2010-08-22
Hi, 
For th past couple of days my cpu has been acting weird, it started with my mouse which at times would start moving on its own. sometimes all over the place. Since that happened i have installed firestarter, that recently started to close on its own , jus like my browsers. I am confused as to what is happening?it seems like i have no control over my comp, even when i am not connected to the net. I suspect it could be a hacker? any suggestion. 
thanks in advance,

---

### Post by cj.surrusco on 2010-08-22
The best way to test if somebody is actually in your system is to disconnect it from the internet, restart, and see if the problem persists.

---

### Post by uRock on 2010-08-22
Sounds like someone could be connecting and using the Remote Desktop. If you have previously enabled remote desktop, then you should disable it.

---

### Post by actsofaith on 2010-08-22
> **uRock said:**
> Sounds like someone could be connecting and using the Remote Desktop. If you have previously enabled remote desktop, then you should disable it.
 i havent enabled anything , im not sure what the remote desktop is  on ubuntu, kinda of a noob. how should i go about disabling it?

---

### Post by uRock on 2010-08-22
> **actsofaith said:**
> i havent enabled anything , im not sure what the remote desktop is  on ubuntu, kinda of a noob. how should i go about disabling it?
Go in your menus to System> Preferences> Remote Desktop. If it is enabled, then it will be obvious. If it is not enabled, then it should look like the screenshot.

Also, enabling UFW(firewall) will prevent anyone from connecting to your machine. In a terminal, enter this command; ```
sudo ufw enable
```

---

### Post by actsofaith on 2010-08-22
Also, enabling UFW(firewall) will prevent anyone from connecting to your machine. In a terminal, enter this command; ```
sudo ufw enable
```[/QUOTE]
Did that . and its says Firewall is active and enabled on system startup, but i knew that already. Could i do anything with firestarter to better block out unwanted connections?

---

### Post by uRock on 2010-08-22
> **actsofaith said:**
> Did that . and its says Firewall is active and enabled on system startup, but i knew that already. Could i do anything with firestarter to better block out unwanted connections?
By default, when the firewall is enabled all ports are blocked unless opened from your side, like when you open a browser and create a connection with the outside. All incoming connections are blocked unless you open them via command line or GUFW/Firestarter.

Firestarter has not been updated since 2005.

---

### Post by actsofaith on 2010-08-22
[QUOTE=uRock;9752388]By default, when the firewall is enabled all ports are blocked unless opened from your side, like when you open a browser and create a connection with the outside All incoming connections are blocked unless you open them via command line or GUFW/Firestarter.

Firestarter has not been updated since 2005.[/Q
 
i dont know if its that simple,how would u explain my mouse moving on its own,even when i lock the net? im jus asking because it seems like theres something else goin on? id really appreciate any feedback

---

### Post by uRock on 2010-08-22
> **actsofaith said:**
> 
i dont know if its that simple,how would u explain my mouse moving on its own,even when i lock the net? im jus asking because it seems like theres something else goin on? id really appreciate any feedback
If it is not coming from outside the LAN, then maybe it is a bad mouse?

I have run port scans against a ubuntu machine that had ufw enabled with the default settings and it could not detect the system was even there.

---

### Post by actsofaith on 2010-08-22
> **uRock said:**
> If it is not coming from outside the LAN, then maybe it is a bad mouse?

I have run port scans against a ubuntu machine that had ufw enabled with the default settings and it could not detect the system was even there.

its not a bad mouse i made sure of it. anyway thanks

---

### Post by actsofaith on 2010-08-22
**Any input from passerbys?????** ):P
thankss

---

### Post by uRock on 2010-08-22
Have you run nmap against your system to see if all ports are in fact closed? ```
nmap 192.168.1.0/24 
```Obviously you would need to change the address if you are not using the typical.

Here is the results of nmap against my own network. You will see that nmap sees my Wii, but can't find any ports and it doesn't even see the UFW enabled Netbook's 192.168.156.103 address that I pinged afterwards.
```
rabbit@rabbit-desktop:~$ nmap 192.168.156.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-22 14:35 PDT
Interesting ports on 192.168.156.100:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

All 1000 scanned ports on 192.168.156.101 are closed

Interesting ports on 192.168.156.254:
Not shown: 998 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Nmap done: 256 IP addresses (3 hosts up) scanned in 76.60 seconds
rabbit@rabbit-desktop:~$ ping -c 1 192.168.156.103
PING 192.168.156.103 (192.168.156.103) 56(84) bytes of data.
64 bytes from 192.168.156.103: icmp_seq=1 ttl=64 time=5.08 ms

--- 192.168.156.103 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 5.086/5.086/5.086/0.000 ms

```

---

### Post by rollin on 2010-08-22
> **uRock said:**
> If it is not coming from outside the LAN, then maybe it is a bad mouse?

I have run port scans against a ubuntu machine that had ufw enabled with the default settings and it could not detect the system was even there.

+1 On a default Ubuntu desktop installation with ufw enabled even nessus only finds low priority errors.

OP, there are lots of options to make the system as tight as you want but for a desktop it is unlikely you will need such actions. For obvious reasons Ubuntu servers with websites and more are in need of more security due to the open ports which an ubuntu desktop install does not have by default.

If you're really worried. Copy your files over to a usb and re-install the system without an internet connection and enable ufw prior to connecting to the net.

---

### Post by mr-woof on 2010-08-22
have you checked that remote desktop is not enabled?

---

### Post by actsofaith on 2010-08-22
> **uRock said:**
> Have you run nmap against your system to see if all ports are in fact closed? ```
nmap 192.168.1.0/24 
```Obviously you would need to change the address if you are not using the typical.

Here is the results of nmap against my own network. You will see that nmap sees my Wii, but can't find any ports and it doesn't even see the UFW enabled Netbook's 192.168.156.103 address that I pinged afterwards.
```
rabbit@rabbit-desktop:~$ nmap 192.168.156.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-22 14:35 PDT
Interesting ports on 192.168.156.100:
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

All 1000 scanned ports on 192.168.156.101 are closed

Interesting ports on 192.168.156.254:
Not shown: 998 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Nmap done: 256 IP addresses (3 hosts up) scanned in 76.60 seconds
rabbit@rabbit-desktop:~$ ping -c 1 192.168.156.103
PING 192.168.156.103 (192.168.156.103) 56(84) bytes of data.
64 bytes from 192.168.156.103: icmp_seq=1 ttl=64 time=5.08 ms

--- 192.168.156.103 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 5.086/5.086/5.086/0.000 ms

```
this is waht i get
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-22 17:53 EDT
Interesting ports on 192.168.1.1:
Not shown: 996 filtered ports
PORT   STATE  SERVICE
20/tcp closed ftp-data
21/tcp closed ftp
23/tcp closed telnet
80/tcp open   http

All 1000 scanned ports on 192.168.1.100 are filtered (724) or closed (276)

Interesting ports on 192.168.1.105:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Interesting ports on 192.168.1.107:
Not shown: 998 filtered ports
PORT      STATE SERVICE
80/tcp    open  http
49155/tcp open  unknown

Nmap done: 256 IP addresses (4 hosts up) scanned in 16.36 seconds
what can u make of all this? please & thanks

---

### Post by actsofaith on 2010-08-22
> **mr-woof said:**
> have you checked that remote desktop is not enabled?
yup. nothin to wrry about there.

---

### Post by OpSecShellshock on 2010-08-22
If this unusual activity occurs even when the computer isn't connected to the network, then I doubt it's the result of any unauthorized intrusions. When the pointer moves on its own, does it do things or does it just float around? When the browser closes on its own, what sort of content is being viewed at the time?

Of the IP addresses from the nmap scan, which is the device in question? You've got one device running as a web server and another running as an ssh server (at least that's how it looks given the ports that are open). What kinds of devices are connected to your network?

---

### Post by actsofaith on 2010-08-22
> **OpSecShellshock said:**
> If this unusual activity occurs even when the computer isn't connected to the network, then I doubt it's the result of any unauthorized intrusions. When the pointer moves on its own, does it do things or does it just float around? When the browser closes on its own, what sort of content is being viewed at the time?

Of the IP addresses from the nmap scan, which is the device in question? You've got one device running as a web server and another running as an ssh server (at least that's how it looks given the ports that are open). What kinds of devices are connected to your network?
hi OpSecShellshock, 
 thanks for replying, &yes my mouse has some unusual activities. When im moving it the cursor all of sudden does its own thing, sometimes slow, other times erratic, but each time different. What freaks me  out is when im not even touching the mouse pad and the cursor moves to certain points on the screen.With the browsers tho, they jusi disappear. At first i thought it could be the website, yet it happens at different times. also the right tab drop down menu appeared a couple of times out of the blue.btw  im in a home network using wifi.
btw i dont know if this is relevant but i have a dual boot with windows.
any leads will be v. appreciated

---

### Post by Jonny87 on 2010-08-22
On the idea of the mouse, have you got another mouse you can try for a while? If for no other reason but to rule out whether or not you have a faulty mouse?

> btw  im in a home network using wifi.
How is your wifi setup and connected? How many devices are on the WLAN (is it possible that someone else in the house is playing games with you)? 

When you tested it offline and got the same results, did you just disconnect the internet (ie. pulled out the dsl cable from the router) or did you turn of the router completely? If you were disconnected to the internet but still connected the WLAN then perhaps the possible intrusion is from a device connected to you WLAN.
Though from the previous post on the firewall being enabled then I would say that you machine is mostly likely secure enough. Though it might pay to check your wfii settings and make sure its all secure and as you expect.

Also just a thought on the web browser thing, have tried another browser? If not then I would suggest trying one (Konqueror for example) and see if you get the same or similar issues. Go to the same sites that you were going to with firefox when it had its trouble.

---

### Post by JBAlaska on 2010-08-23
Interesting ports on 192.168.1.105:
Not shown: 999 closed ports
PORT STATE SERVICE
**[COLOR="Red"]22/tcp open ssh[/COLOR]**
This port could allow remote access, close it unless your using it.

Interesting ports on 192.168.1.107:
Not shown: 998 filtered ports
PORT STATE SERVICE
80/tcp open http
**[COLOR="DarkOrange"]49155/tcp open unknown[/COLOR]**
Unless your using this port (for Bittorrent perhaps) you should close it as well.

---

### Post by Oxwivi on 2010-08-23
Is the mouse moving randomly? Try using a different surface if it's a laser mouse. Or if it's the old ball mouse, try opening it and cleaning the internals. This'll only help if the mouse isn't broken but acting up.

---

### Post by actsofaith on 2010-08-23
> **Jonny87 said:**
> On the idea of the mouse, have you got another mouse you can try for a while? If for no other reason but to rule out whether or not you have a faulty mouse?
yes i did that before when i thought it was the touch pad acting up, though the same thing kept happening. Mayb its a hardware problem.IDK. but if i dont figure somtin out ill have to take it to geek squad or something.


> **Jonny87 said:**
> 
How is your wifi setup and connected? How many devices are on the WLAN (is it possible that someone else in the house is playing games with you)? 
not many, the router is on a desktop comp which no1 really uses. I doubt any1 in my fam has that kind of comp skills to mess with me.

> **Jonny87 said:**
> 
When you tested it offline and got the same results, did you just disconnect the internet (ie. pulled out the dsl cable from the router) or did you turn of the router completely? If you were disconnected to the internet but still connected the WLAN then perhaps the possible intrusion is from a device connected to you WLAN.
 what i mean by offline is that i would lock the firewall, and the cursor will still keep moving. 

> **Jonny87 said:**
> 
Though from the previous post on the firewall being enabled then I would say that you machine is mostly likely secure enough. Though it might pay to check your wfii settings and make sure its all secure and as you expect. 
were on an open wifi, that is the only way for every1 to get connected to net without problems.

> **Jonny87 said:**
> Also just a thought on the web browser thing, have tried another browser? If not then I would suggest trying one (Konqueror for example) and see if you get the same or similar issues. Go to the same sites that you were going to with firefox when it had its trouble.
its happened to me on opera.

---

### Post by actsofaith on 2010-08-23
> **Oxwivi said:**
> Is the mouse moving randomly? Try using a different surface if it's a laser mouse. Or if it's the old ball mouse, try opening it and cleaning the internals. This'll only help if the mouse isn't broken but acting up.
hi
 i have a touch pad mouse, i tried a wireless mouse & still the same problem.:-|

---

### Post by actsofaith on 2010-08-23
> **JBAlaska said:**
> Interesting ports on 192.168.1.105:
Not shown: 999 closed ports
PORT STATE SERVICE
**[COLOR=Red]22/tcp open ssh[/COLOR]**
This port could allow remote access, close it unless your using it.

Interesting ports on 192.168.1.107:
Not shown: 998 filtered ports
PORT STATE SERVICE
80/tcp open http
**[COLOR=DarkOrange]49155/tcp open unknown[/COLOR]**
Unless your using this port (for Bittorrent perhaps) you should close it as well.

im not using any of these ports, & i dont have bittorrent. how could i block a port? keep it noob friendly
~thanks

---

### Post by actsofaith on 2010-08-23
> **OpSecShellshock said:**
> If this unusual activity occurs even when the computer isn't connected to the network, then I doubt it's the result of any unauthorized intrusions. When the pointer moves on its own, does it do things or does it just float around? When the browser closes on its own, what sort of content is being viewed at the time?

Of the IP addresses from the nmap scan, which is the device in question? You've got one device running as a web server and another running as an ssh server (at least that's how it looks given the ports that are open). What kinds of devices are connected to your network?
im not sure how to answer that, so this might sound off, but eth1 is the device that connects to the net.so other than my laptop wireless card there is no other devices.

---

### Post by cariboo on 2010-08-23
> **actsofaith said:**
> this is waht i get
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-22 17:53 EDT
Interesting ports on 192.168.1.1:
Not shown: 996 filtered ports
PORT   STATE  SERVICE
20/tcp closed ftp-data
21/tcp closed ftp
23/tcp closed telnet
80/tcp open   http

All 1000 scanned ports on 192.168.1.100 are filtered (724) or closed (276)

Interesting ports on 192.168.1.105:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Interesting ports on 192.168.1.107:
Not shown: 998 filtered ports
PORT      STATE SERVICE
80/tcp    open  http
49155/tcp open  unknown

Nmap done: 256 IP addresses (4 hosts up) scanned in 16.36 seconds
what can u make of all this? please & thanks

Your listing shows 4 different devices, 
[list]
[*]192.168.1.1, I assume is your router 
[*]192.168.1.100 seems to be a firewalled system
[*]192.168.1.105 has an openssh-server running 
[*]192.168.1.107 has a web server and something else running on port 49155
[/list]

---

### Post by actsofaith on 2010-08-23
> **cariboo907 said:**
> You listing shows 4 different devices, 
[LIST]
[*]192.168.1.1, I assume is your router
[*]192.168.1.100 seems to be a firewalled system
[*]192.168.1.105 has an openssh-server running
[*]192.168.1.107 has a web server and something else running on port 49155
[/LIST]

Right that makes sense. For one thing, i keep seeing the 192.168.1.105 as my active connections in firewall, also with some of the block addresses under destination. Should i  be concerned?:-s

---

### Post by cariboo on 2010-08-23
You should check to make sure they are all systems on your internal network. In Ubuntu, open a terminal and type:

```
ifconfig
```

the output should look something like this:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:da:4e:f4  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feda:4ef4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95371226 (95.3 MB)  TX bytes:3579712 (3.5 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

As you can see in the listing above, my ap address is 192.168.1.102.

On windows systems go to start->run and type cmd, and press enter, a command window (terminal) will open, at the prompt type:

```
ipconfig
```

The above command will list the ip address for that computer, the output should look something like this:

```
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : APLUS
        IP Address. . . . . . . . . . . . : 192.168.1.103
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
```

---

### Post by JK3mp on 2010-08-23
Wow. All this trouble. He's already stated that 1 he has the same problem with no connection to a network, so either way this can't be a remote attack. Correct? 2 He has checked his hardware(aka mouse). So now its narrowed to likely a software issue locally for the most part. I would suggest backing up(as I would hope you already have if you thought your system was hacked), and reinstalling Ubuntu. Bringing it up reinstalling everything and so on can be a pain but if this problem persists yet again let us know. For me it only takes about 2 hours to install, update, re add pictures/music/movies/documents, re-install software. For some it may take an hour or 2 more(possibly more on slow connection). But for the most part you'll spend more time trying to investigate and follow frantic leads and configs that it would take to get a fresh install back up. Plus IF you are infected or hacked in some kind of way usually a fresh install is the best way and sometimes only way to get rid of rootkits and so on. Best part of linux is when we break it can always hit the reset button(FOR FREE!). =)

---

### Post by actsofaith on 2010-08-23
> **JK3mp said:**
> Wow. All this trouble. *SHe's already stated that 1 She has the same problem with no connection to a network, so either way this can't be a remote attack. Correct? 2 *SHe has checked her hardware(aka(also known as) mouse). So now its narrowed to likely a software issue locally for the most part. I would suggest backing up(as I would hope you already have if you thought your system was hacked), and reinstalling Ubuntu. Bringing it up reinstalling everything and so on can be a pain but if this problem persists yet again let us know. For me it only takes about 2 hours to install, update, re add pictures/music/movies/documents, re-install software. For some it may take an hour or 2 more(possibly more on slow connection). But for the most part you'll spend more time trying to investigate and follow frantic leads and configs that it would take to get a fresh install back up. Plus IF you are infected or hacked in some kind of way usually a fresh install is the best way and sometimes only way to get rid of rootkits and so on. Best part of linux is when we break it can always hit the reset button(no duh!). =)
  wow for a moment i thought u wrote something substantial,&  ive already thought about reinstalling long b4 i came on here, but from what i can remeber taht took me a while, plus a couple of days to install drivers such as wireless card,etc. If nothing works ill prob wind up going to windows, although people  up to this point have been very helpful.

---

### Post by actsofaith on 2010-08-23
> **cariboo907 said:**
> You should check to make sure they are all systems on your internal network. In Ubuntu, open a terminal and type:

```
ifconfig
```the output should look something like this:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:da:4e:f4  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feda:4ef4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95371226 (95.3 MB)  TX bytes:3579712 (3.5 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```As you can see in the listing above, my ap address is 192.168.1.102.

On windows systems go to start->run and type cmd, and press enter, a command window (terminal) will open, at the prompt type:

```
ipconfig
```The above command will list the ip address for that computer, the output should look something like this:

```
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : APLUS
        IP Address. . . . . . . . . . . . : 192.168.1.103
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
```
k did those things, heres waht i cget 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:bb:96:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:55:84:f6  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe55:84f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:244719 errors:0 dropped:0 overruns:0 frame:456545
          TX packets:184550 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:335067983 (335.0 MB)  TX bytes:20502708 (20.5 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:378704 (378.7 KB)  TX bytes:378704 (378.7 KB)

. Could you tell me how to block unwanted ports using ubuntu code? i wont ask for much more. 
thanks you

---

### Post by Rumpletumbler on 2010-08-23
There's a lot to be gained by understanding what happened in my opinion. 

That being said to image it and redo it probably wouldn't be a bad idea and you can examine it at your leisure.

Too many do this / do thats in the forum in my opinion (without explanation) and sometimes when we're in over our heads just a little help goes a long way.

---

### Post by uRock on 2010-08-23
> **actsofaith said:**
>  Could you tell me how to block unwanted ports using ubuntu code? i wont ask for much more. 
thanks you
In Firestarter, click on the Policy tab and right click the Allow Inbound Service area like in the screenshot and add the rule for the port as well as doing the same for outbound traffic.

I do not know the commands to alter IP Tables, but I use GUFW which is a newer front end for IP Tables.

---

### Post by msandoy on 2010-08-24
This sounds to me like a hardware problem, have you tried booting up from a live CD. Does the mouse still move by itself? Also, be aware that some touchpads actually does not require you to physically touch them. It is sometimes enough that your fingers are hovering close to the surface while typing. Happens to me all the time, so I got myself an externalmouse and keyboard for my laptop since it is mostly used in one place.

---

### Post by alphaamanitin on 2010-08-24
When you say the problem kept occurring even when you were not connected to the net, how disconnected were you?  Are we talking about just disconnecting, or actually disabling your wireless card and/or unplugging ethernet cables?  

I have heard, no idea if they are just stories though, that sometimes just disabling your network card or disconnecting from a network is not enough if you have been compromised.  Is this true guys?

If you had these issues with everything unplugged and disabled than it does sound like a software/hardware issue.

AlphaA

---

### Post by JoshDN on 2010-08-24
If you are using an external mouse, is your touchpad mouse deactivated? The malfunctioning touchpad may be causing it even when using the external mouse.

---

### Post by JK3mp on 2010-08-24
> **actsofaith said:**
> wow for a moment i thought u wrote something substantial,&  ive already thought about reinstalling long b4 i came on here, but from what i can remeber taht took me a while, plus a couple of days to install drivers such as wireless card,etc. If nothing works ill prob wind up going to windows, although people  up to this point have been very helpful.

OOB wireless is usually well supported in ubuntu and drivers are generally easy to get on the go(though nvidia drivers suck). I don't really care for your lack of gratitude(or thats how its coming off), i only made a suggestion that I did not see anywhere you already tried. Either way I still don't see a fresh install taking as long as running through all the suggestions that everyone is giving. Plus as I stated its the best way to shake any infection(unless its brewing on your LAN which if you unplugged should have fixed). Yes they are trying to be helpful but so was i ;). A better attitude next time please. Good luck! :D

---

### Post by uRock on 2010-08-24
> **JK3mp said:**
> OOB wireless is usually well supported in ubuntu and drivers are generally easy to get on the go(though nvidia drivers suck). I don't really care for your lack of gratitude(or thats how its coming off), i only made a suggestion that I did not see anywhere you already tried. Either way I still don't see a fresh install taking as long as running through all the suggestions that everyone is giving. Plus as I stated its the best way to shake any infection(unless its brewing on your LAN which if you unplugged should have fixed). Yes they are trying to be helpful but so was i ;). A better attitude next time please. Good luck! :D
Not everyone wants to jump on a reinstall. I prefer to learn what went wrong, so I can fix it or figure out how to help others fix it.

And nVidia drivers work well for me. It is Plymouth that I does not work well with nVidia.

If you don't like someone's attitude, then by all means go to the next thread and help the grateful.

---

### Post by BkkBonanza on 2010-08-24
This really sounds like external interference with the mouse or touchpad. Check if you have any radio devices like mobile phones, cordless phones near by. Take the computer to another location at least 100m away and see if it still acts up. Random mouse movements (if they are random?) are not going to be caused by hackers. I'm assuming it doesn't "randomly" go and select a menu item and run a certain program and select files and delete them etc. If really just random then you have hardware faults or radio interference. I've seen cordless phones cause this type of thing before but it could be other devices.

---

### Post by actsofaith on 2010-08-25
> **JK3mp said:**
> OOB wireless is usually well supported in ubuntu and drivers are generally easy to get on the go(though nvidia drivers suck). I don't really care for your lack of gratitude(or thats how its coming off), i only made a suggestion that I did not see anywhere you already tried. Either way I still don't see a fresh install taking as long as running through all the suggestions that everyone is giving. Plus as I stated its the best way to shake any infection(unless its brewing on your LAN which if you unplugged should have fixed). Yes they are trying to be helpful but so was i ;). A better attitude next time please. Good luck! :D

hey 
ur response like the prior one is NOT necessary, as i made it obvious to u b4.  U sound like a noob, (or thats how its coming off) cuz the reinstall thing any1 with primal thinking could come up with it. dont waste my time with ur weak comebacks and smiley face whatevers.  keep it moving pls ur  jus too  lame.

---

### Post by actsofaith on 2010-08-25
hi thanks every1 for ur help, minus on exception. Im still in the same predicament,but now im thinking  its more of a hardware issue than anything else so, ill be looking into that 
thanks again,

---

### Post by endotherm on 2010-08-25
> **actsofaith said:**
> hi thanks every1 for ur help, minus on exception. Im still in the same predicament,but now im thinking  its more of a hardware issue than anything else so, ill be looking into that 
thanks again,
last time I saw somthing like that, the problem was with the motherboard. it would occasionally save up a few million mouse actions, and then release them all within the space of a few seconds (eg the mouse flew around the screen clicking everywhere loading a few hundred windows). I recall the user thinking it was a hack as well.

---

### Post by Jonny87 on 2010-08-25
> what i mean by offline is that i would lock the firewall, and the cursor will still keep moving. 
I wouldn't really call this offline as you are still connected to the network and if your UFW has open ports as I think I read earlier on then this would hardly eliminate the intrusion threat if they were using one of those ports. For this I would suggest turning off your wifi router for a bit. In my opinion this is the best method for eliminating an out side threat. And as you mentioned that you have an open wireless connection then I would say that its even more likely that a neighbor or passer by has picked up on that. 

I also wouldn't rule out the hardware problems, you've had a lot of intelligent people giving suggestions (I can say that as I seen their post in the past and I think some have even helped me at times) and it seems to be a common theme that it a hardware issue.

So here's what I see, your options are;

[LIST=1]
[*]You continue trouble shooting this seeking the solution.
[/LIST]
In my opinion this is always the 1st option as your better off learning for next time. Also others can learn from the forum posts. And myself and the others will continue to help with this.

      2. Re-install.

I wouldn't be so harsh on "JK3mp" for this idea. It's quite a valid suggestion, as he pointed out it can be quicker than going through this process of trying find out whats wrong and it will eliminate any threat. While I like to think of a re-install as the last option for fixing problems, it does have its place. And as JK3mp pointed out, its free with linux.
Its also quicker to get things back to normal that on windows.

If you have "/home" on a separate partition (I would suggest that you do next time round if you don't) then don't format it on the re-install but remount it as home, this will keep all your settings and files (ALWAYS BACK THEM UP THOUGH). Also you can back up the DEB's in > /var/cache/apt/archives then use them to re-install some packages if you have a poor connection.

Anyway I hope you find a solution sooner or later.

---

### Post by JK3mp on 2010-08-25
> **uRock said:**
> Not everyone wants to jump on a reinstall. I prefer to learn what went wrong, so I can fix it or figure out how to help others fix it.

And nVidia drivers work well for me. It is Plymouth that I does not work well with nVidia.

If you don't like someone's attitude, then by all means go to the next thread and help the grateful.

Nvidia drivers are a problem for me particularly but I think this is do to dual graphics. Was only suggesting fresh install as far as how quickly to get back up and running, educationally she can feel free to investigate it and thats just fine. And I will move on.

Best of luck actsoffaith and hopefully you will eventually find your problem.

---

### Post by uRock on 2010-08-25
If one uses GUFW and denies traffic both ways, then the PC will not communicate to the outside networking world. There is no reason to disable the network itself.

---

### Post by endotherm on 2010-08-25
> **uRock said:**
> Not everyone wants to jump on a reinstall. I prefer to learn what went wrong, so I can fix it or figure out how to help others fix it.

And nVidia drivers work well for me. It is Plymouth that I does not work well with nVidia.

If you don't like someone's attitude, then by all means go to the next thread and help the grateful.

I'm inclined to agree, with one major exception: security compromises. once you can confirm infection or infiltration, nothing short of a full rebuild will do. theres just no way to ever know it;s clean again.

---

### Post by uRock on 2010-08-25
> **endotherm said:**
> I'm inclined to agree, with one major exception: security compromises. once you can confirm infection or infiltration, nothing short of a full rebuild will do. theres just no way to ever know it;s clean again.
It will work well enough to trouble to find what went wrong, how and why, so that one can find out how to prevent the problem in the future. 

I have no problems with running a full install. I have a nice little script that will get all of my programs installed, all of the unwanted ones removed and settings back to normal in little over 35 minutes from time of inserting the LiveCD. Could be faster but my system is a little slow.

---

### Post by Jonny87 on 2010-08-25
> **uRock said:**
> If one uses GUFW and denies traffic both ways, then the PC will not communicate to the outside networking world. There is no reason to disable the network itself.

That may be true with default settings. But as I mentioned if she has open ports as mentioned on page two then it would do nothing. What I'm saying is that just merely enabling the firewall is not enough for trouble shooting.

If someone has hacked his system then who knows what they have done. And if that is to be true then a re-install is best solution to fix that.

If it were my system I would turn the router off all together and see I got the same result. If I had any suspicion of an intrusion I would instantly kill my network and re-install the system in question. All in all when dealing with wireless, security is a must.

If hard where is the problem then yes a re-install could be drastic if theres a fix. At the same time though a re-install could show if its a hardware problem. If he re-installed the system and had the same issues straight away then chances are its something to do with hardware.

---

### Post by JK3mp on 2010-08-25
> **Jonny87 said:**
>  If he re-installed the system and had the same issues straight away then chances are its something to do with hardware.

+1 Though i did not directly write this out as a plus for reinstalling it IS indeed a plus, as I said in my first post here to reinstall then if problem persists let us know. Would indeed narrow it to a hardware rather than software since I think for the most part we have narrowed down any kind of "hack attack" or external (mouse+keyboard). If hardware though I can't say Id really know for sure what it is if the problem persisted. I would be interested In if whether a reinstall would fix the problem so I'll be sure to check back and see if actsoffaith decides to reinstall as a LAST measure as she has obviously pointed out she wants it to be ...

---

### Post by cariboo on 2010-08-25
Shutting off networking by using either:

```
sudo service networking stop
```

or 

```
sudo /etc/init.d/networking stop
```

depending on what version you're using makes sure that no matter whether you're running  wired or wireless networking the networking daemon is stopped. The op can run that way for a couple of hours to see if the mouse problem reoccurs. 

When op finds what the problem is, the daemon can be restarted:

```
sudo service networking start
```

or

```
sudo /etc/init.d/networking start
```

---

### Post by TwoEars on 2010-08-26
> **uRock said:**
> It will work well enough to trouble to find what went wrong, how and why, so that one can find out how to prevent the problem in the future. 

I have no problems with running a full install. I have a nice little script that will get all of my programs installed, all of the unwanted ones removed and settings back to normal in little over 35 minutes from time of inserting the LiveCD. Could be faster but my system is a little slow.

You know, you could just take an image of your installed OS with everything setup, then just put the image back on when you're reinstalling.

---

### Post by rookcifer on 2010-08-26
He has an open SSH server on port 22 and an open HTTP server on port 80 and no one thinks that's weird?  I haven't followed this thread too closely, but I first would definitely find out who is running an ssh and http server and why.

---

### Post by OpSecShellshock on 2010-08-26
> **rookcifer said:**
> He has an open SSH server on port 22 and an open HTTP server on port 80 and no one thinks that's weird?  I haven't followed this thread too closely, but I first would definitely find out who is running an ssh and http server and why.

I thought it was weird, but it didn't seem like it would have been involved with the touchpad issue. Had that been indicative of a hijacked session it would definitely have been a bit more purposeful than what the OP described.

Of course, I'd say those servers running are a bit more pressing an issue than floating mouse pointers.

---

### Post by uRock on 2010-08-26
> **TwoEars said:**
> You know, you could just take an image of your installed OS with everything setup, then just put the image back on when you're reinstalling.
Last time I tried that t took about 10 DVDs and 3-4 hours, because if you are going to make a copy of a drive it has to be encrypted.

---

### Post by TwoEars on 2010-08-26
> **uRock said:**
> Last time I tried that t took about 10 DVDs and 3-4 hours, because if you are going to make a copy of a drive it has to be encrypted.

I'm talking about the software, judging from your post, you're only talking software terms. Software does not need to be encrypted. Settings, generally, take up a very small amount of space. How you've managed to end up with 10 DVDs worth of software and settings I'll never know, perhaps you've decided to run ```
sudo apt-get install *
```? :P

---

### Post by uRock on 2010-08-26
> **TwoEars said:**
> I'm talking about the software, judging from your post, you're only talking software terms. Software does not need to be encrypted. Settings, generally, take up a very small amount of space. How you've managed to end up with 10 DVDs worth of software and settings I'll never know, perhaps you've decided to run ```
sudo apt-get install *
```? :P
No, that was with using Windows. I was thinking your were talking about backing up everything, not just the programs. I don't really add/remove enough for that to save any time. The longest part of installing, for me, is the actual install process from the ISO. I have an old AMD CPU.

---

### Post by actsofaith on 2010-08-27
Oo man, the comments
im v. grateful for every1s input, good valid points to consider. 
> **endotherm said:**
> last time I saw somthing like that, the problem was with the motherboard. it would occasionally save up a few million mouse actions
 interesting nvr knew that, could be a possibility
> **uRock said:**
> If one  GUFW and denies traffic both ways, then the PC will not communicate to the outside networking world. There is no reason to disable the network itself.
 intuitively tried this,when i was workin with firestarter, then things got real quiet, &i couldnt go on the net, so i enabled it. but maybe a short hiatus fr. comp will clear things out.   im going to try cariboo9007 suggestion for disabling the network to my computer .t& see how  that goes 
> **Jonny87 said:**
> I wouldn't really call this offline as you are still connected to the network and if your UFW has open ports as I think I read earlier on then this would hardly eliminate the intrusion threat if they were using one of those ports. For this I would suggest turning off your wifi router for a bit. In my opinion this is the best method for eliminating an out side threat. And as you mentioned that you have an open wireless connection then I would say that its even more likely that a neighbor or passer by has picked up on that. 
no its not offline  technically,but i cant surf the net when its locked,  the ufw thing is nifty tool ive been using it alot, like whenever  im having problems , at one point i got this reading
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-26 22:46 EDT
Interesting ports on 192.168.1.1:
Not shown: 995 filtered ports
PORT     STATE  SERVICE
20/tcp   closed ftp-data
21/tcp   closed ftp
23/tcp   closed telnet
80/tcp   open   http
2869/tcp open   unknown

Interesting ports on 192.168.1.102:
Not shown: 977 closed ports
PORT      STATE    SERVICE
6/tcp     filtered unknown
144/tcp   filtered news
900/tcp   filtered unknown
1067/tcp  filtered instl_boots
1082/tcp  filtered unknown
1417/tcp  filtered timbuktu-srv1
1501/tcp  filtered sas-3
2196/tcp  filtered unknown
2608/tcp  filtered unknown
2701/tcp  filtered sms-rcinfo
3011/tcp  filtered unknown
4224/tcp  filtered xtell
4998/tcp  filtered maybe-veritas
5221/tcp  filtered unknown
5631/tcp  filtered pcanywheredata
5987/tcp  filtered unknown
8087/tcp  filtered unknown
9100/tcp  filtered jetdirect
10215/tcp filtered unknown
11111/tcp filtered unknown
32782/tcp filtered unknown
32784/tcp filtered unknown
62078/tcp open     iphone-sync

Interesting ports on 192.168.1.105:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 256 IP addresses (3 hosts up) scanned in 40.44 seconds

 i thought i post bc it was longest one i recorded.  i took a screenshot of my firewall at that time. What struck me odd was an .exe running but it could be becuase i fresh installed wine...

---

### Post by actsofaith on 2010-08-27
> **TwoEars said:**
> You know, you could just take an image of your installed OS with everything setup, then just put the image back on when you're reinstalling.
 sounds promising i might actually consider reinstalling, although one major setback is getting  my broadcom wireless device to work   with  ubuntu software. That itself took me days &  sheer chance to get a connection. would the image save me that step in the reinstall?

---

### Post by endotherm on 2010-08-27
> **actsofaith said:**
> sounds promising i might actually consider reinstalling, although one major setback is getting  my broadcom wireless device to work   with  ubuntu software. That itself took me days &  sheer chance to get a connection. would the image save me that step in the reinstall?
thats the idea. an image is a bit-for-bit exact copy of the hard disk partition you make it from, so assuming nothing goes wrong during creation or restore, everything will be identical down to exactly which files are fragmented.

---


---
title: "cannot connect to my server via WAN on any port"
date: 2010-05-15
forum: Server Platforms
---

### Post by Mistah_Transistah on 2010-05-15
first of all. when i fisrt signed up for this forums i accidently posted this same topic in the first place i found apropriate(network/wirless) and i just realised i didn't look hard enough so i marked my old post as solved, please admin delete that one. 

ubuntu server 10.04 LTS running ubuntu desktop on top(for my lack of skill)

ok nitty-gritty. i have been learning to use linux for a few months now and i like it but i cannot access my server through WAN on any ports, yes i have them all open and enabled and associated on my router properly. i even tryed turning off firewall on here and i have tryed a list of misc. things. is there something i am not doing that one might initialy do when first starting an ubuntu server?

---

### Post by Mistah_Transistah on 2010-05-18
Bump

---

### Post by NeddyDownUnder on 2010-05-18
Hi,

No one is replying because you have given no details of your setup at all. for example...:

What service are you trying to use? 
Have you tried to ping your server from the wan? 
Do you have a static ip? 
Are you using dyndns.com or some sort of similar service to direct to your server? 

Put up some specific details and then maybe someone can help you. :)

Cheers.

---

### Post by kevin11951 on 2010-05-18
if you have physical access to the server, post the contents of /etc/network/interfaces... its going to be hard because you will have to type it all out... sorry.

---

### Post by Mistah_Transistah on 2010-05-19
> **NeddyDownUnder said:**
> Hi,

No one is replying because you have given no details of your setup at all. for example...:

What service are you trying to use? 
Have you tried to ping your server from the wan? 
Do you have a static ip? 
Are you using dyndns.com or some sort of similar service to direct to your server? 

Put up some specific details and then maybe someone can help you. :)

Cheers.
right i see that, well you must understand i have only just had my first networking class tonight(intro so far) and growing up all i ever had to do was open the port and allow it on the firewall and that is consistant with what everyone says  when i attempt to look up my problem so i have to be missing something.  and yes i have tryed pinging it. within the second i ping it times out. of course when i attempt to connect on http via a web browser it either loads infinitly or fails to connect all together

> **kevin11951 said:**
> if you have physical access to the server,  post the contents of /etc/network/interfaces... its going to be hard  because you will have to type it all out... sorry. 
this is another problem in the works i cannot issue a static ip. i have been trying but every time i search for how to do this i get several different ways and none seem to work, but i have succeeded in making myself invisible in my lan.... and just loosing connection out all together...

one method says to do this to /etc/network/interface
```
[COLOR=blue]*auto eth0*[/COLOR]
[COLOR=blue]*iface eth0 inet static*[/COLOR]
[COLOR=blue]*address  192.168.0.5*[/COLOR]
[COLOR=blue]*netmask 255.255.255.0*[/COLOR]
[COLOR=blue]*network 192.168.0.0*[/COLOR]
[COLOR=blue]*broadcast 192.168.0.255*[/COLOR]
[COLOR=blue]*gateway  192.168.0.1*[/COLOR]

```
even trying to manipulate these numbers to match those which i need still does me no good...

since that did not work, i am working with this 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
address 192.168.1.110
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.0.255
gateway 192.168.1.1

```
i realize that dhcp will not make my ip static, but like i said i cannot successfully get a static ip issued.

---

### Post by NeddyDownUnder on 2010-05-20
I'm going to try to help, although I'm a little confused as to what you are trying to do... Are you trying to configure your Ubuntu server so that you can access it from the internet or are you trying to access the internet form your server? From looking at you /etc/network/interfaces file I'm assuming you can do neither right now... So either way the first thing to do is to get your computer onto the internet so you can browse the web etc... from the server. 

I suggest you make you /etc/network/interfaces file look like the one bellow. The below setup assumes your router's IP address is 192.168.1.1 and that your network is setup to allow IP address between 192.168.1.2 --> 192.168.1.255 . I have changed the IP address you were trying to use ( 192.168.1.110 ) because in many setups this will fall into the range your DHCP server uses or may use. I changed it to ( 192.168.1.175) as this is less likely to be in the DHCP range. But understand that this can be any ip address in the 192.168.1.* range that is not in the DHCP server's range and is not the address of the router or any other device that has a static IP on the LAN. 

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.175
	netmask 255.255.255.0
	gateway 192.168.1.1

```

Next you may need to edit the /etc/resolv.conf and enter a name server address. I normally just enter the router's ip address for this, but if you want I think you could also enter your ISP's DNS addresses if you like. I would just enter in this ( the address below should be your routers IP address)

/etc/resolv.conf
```
nameserver 192.168.1.1
```

Now restart you networking service with:

```
sudo /etc/init.d/networking restart
```

Hopefully now you can connect to the internet FROM your server.  After you have done that then you can start looking at setting up you server for access from the WAN... You could start with the link below but you probably have to do a bit of google-ing around as well to get your head around the service described below... Just remember that once you setup something like below that your server will be exposed to everyone which is not a great thing if you have not got it correctly setup to be secure... e.g. I only have one port open to my server from the WAN and that is  for SSH with a very long secure password and I tunnel other services through that... But that a whole different conversation, but is something I think you should probably understand before opening up services FROM you server to the internet.

[http://www.dyndns.com/services/dns/dyndns/howto.html]("http://www.dyndns.com/services/dns/dyndns/howto.html")

Good luck, let us know how it goes. Sorry it drags on a little but I'm trying to be clear as I can...

---

### Post by Mistah_Transistah on 2010-05-20
> **NeddyDownUnder said:**
> 

Good luck, let us know how it goes. Sorry it drags on a little but I'm trying to be clear as I can...

not at all a problem, i am not network or computer stupid i am just linux/ubuntu stupid and trying radical things because thats how you learn in the computer world. make radical changes and see what happens! =] 
first let me say i apritiate your kindness and decency! do you not realise you are suppose to be mean to people that are new on a given forum, especially when you are an experienced poster/troll? =] but thank you for not tareing me apart.

now it does look like finally i am making some progress.
all though i am still timing out on the human interface i am not getting the same error when i attempt to connect. and even more exciting i just pinged my machine and this time there was only 50% packet loss! we have partialy established a connection. what is the likely cause of 50% packet loss?

how do i prove that i have a static ip though? there is no ipconfig command like in windows. and my router only has a dhcp table... also does my router have to be set to static? i don't remember ever having to change that because i remember having static and dynamic addresses on the same network in the past.

thanks again!

ok i just answered my own question by connecting to 192.168.1.175 with http and succeeded so now the question still stands why can i not connect on the Wide end of things? and thank you for a beautifull static address! =]

---

### Post by arrrghhh on 2010-05-20
> **Mistah_Transistah said:**
> ok i just answered my own question by connecting to 192.168.1.175 with http and succeeded so now the question still stands why can i not connect on the Wide end of things? and thank you for a beautifull static address! =]

Firewall/Router?  ISP?

Make sure these things aren't blocking you.

---

### Post by NeddyDownUnder on 2010-05-20
> **Mistah_Transistah said:**
> 
how do i prove that i have a static ip though? there is no ipconfig command like in windows. 


ifconfig will give you details about your IP address and network interfaces...
```
user@ubuntu$ ifconfig
```

> **Mistah_Transistah said:**
>  
and my router only has a dhcp table... also does my router have to be set to static? i don't remember ever having to change that because i remember having static and dynamic addresses on the same network in the past.


You can have both static and dynamic on the same network, and in my experiences I have not had to alter any settings to allow static IPs. Just don't set static IPs in the DHCP range and ensure your static IPs are in the range allowed in the router. You should see the static IP pop up in the IP table when it's connected. Some routers have separate tables for static and dynamic IPs and some don't... 

> **Mistah_Transistah said:**
> what is the likely cause of 50% packet loss?

I'm not sure, I don't know enough about networking... Are you sure that you setup /etc/resolv.conf correctly? This is usually the source of my problems when setting up a static IP. Or is your network cable in bad condition / bad physical connection, I once remember a friend mentioning packet loss because of badly bent solid core cables...

---

### Post by Mistah_Transistah on 2010-05-21
hmmm should my network driver return fatal errors and missing file requests? :O
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
ssh stop/waiting
ssh start/running, process 4450
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

```

---

### Post by Mistah_Transistah on 2010-05-22
i got rid of some errors and now when i ping from my EV DO modem i get 100% packet circuit. but still i cannot connect on my Wide IP address any ideas anyone?

---

### Post by NeddyDownUnder on 2010-05-23
What's your setup? I'm assuming you can access the internet from your Ubuntu box, if you can't then this is your first port of call...

Next, how do you know what IP address to connect on from the net? Does your ISP provide you with a static IP? Or are you using a service such as Dyndns.com? (I don't know anything about EV DO modems or how this setup works with that type of service) If you are using a service such as Dyndns have you set it up correctly to allow the ports you are tying to use? Does your EV DO modem even have software to support this service? If not then you need to look at having your linux box sync with one of these services (Google it)... If your router does support this service have you double checked you router to make sure this service is setup correctly? Have you double checked that you have forwarded the correct ports to the correct IP address from your router? 

These are some of the things it could be... Unfortunately I don't know what else to do to help you out. Give all the things above a go and try Googleing any problems you run into and if you still can't get it to work them post back here with specific details of you setup and your problems and I or someone else will try to help...

Good Luck.

---

### Post by Mistah_Transistah on 2010-05-23
my EV DO modem is my sprint phone in tether mode. it's my only other address!

i was not using any particular dns servise before just automatic.
i am now using dyndns and yes i have it set to allow the types of services i am running.

and i just went to shieldsup to see how my ports are doing, and this is what i find:
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans  Serif][SIZE=-1][COLOR=#000066][FONT=courier new,courier][SIZE=3][COLOR=black]```

GRC Port Authority Report created on UTC: 2010-05-23 at 21:41:13

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    0 Ports Open
    0 Ports Closed
   26 Ports Stealth
---------------------
   26 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: FAILED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.


```why are all of my ports hiding? i have been all over the place looking for an answer. i turned off all firewalls. opened all ports on my router. i also ran shields up on other computers and recieved the same results, no matter what i do i am completely invisible... this would be a good thing if i was in the business of hiding but thats counter productive to runing a WEB server... any ideas???     
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by NeddyDownUnder on 2010-05-23
I just ran the same scan on my address:

```
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2010-05-23 at 23:25:12

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------
```

I don't have any services running in the range above and I don't have any firewall active so the above is correct. As far as I know a Stealth port is the same as an unused non-firewalled one. What services are you running? What ports do you expect to have services on? When you say that you have opened all ports on your router do you mean that you have forwarded all ports to your server? If your router has a DMZ setting you could try putting your server in the DMZ temporarily to see if you can get access to it like that. However I would not suggest leaving it in the DMZ as it's an unnecessary security risk. 

From you posts below I'm assuming you have a second computer on the network. Can you connect to services on your server from the other computer on the LAN? 

Lastly, how do you have your internet connection setup? Is you phone tethered to your router? You say you now use dyndns now, did you configure your router to work with this service? Please write a direct response to these last two questions as I am still unclear about how you actually have your LAN setup and how it connects to the internet.

---

### Post by Mistah_Transistah on 2010-05-23
> **NeddyDownUnder said:**
> I just ran the same scan on my address:

```
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2010-05-23 at 23:25:12

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------
```I don't have any services running in the range above and I don't have any firewall active so the above is correct. As far as I know a Stealth port is the same as an unused non-firewalled one. What services are you running? What ports do you expect to have services on? When you say that you have opened all ports on your router do you mean that you have forwarded all ports to your server? If your router has a DMZ setting you could try putting your server in the DMZ temporarily to see if you can get access to it like that. However I would not suggest leaving it in the DMZ as it's an unnecessary security risk. 

From you posts below I'm assuming you have a second computer on the network. Can you connect to services on your server from the other computer on the LAN? 

Lastly, how do you have your internet connection setup? Is you phone tethered to your router? You say you now use dyndns now, did you configure your router to work with this service? Please write a direct response to these last two questions as I am still unclear about how you actually have your LAN setup and how it connects to the internet.
LAMP and FTP server is all which of course looks for 80 and 443; and 21. i asked my isp if they have any blocks on these ports or services and they said no and even tryed to assist me, but they are less educated... lol
yes all of the ports required are forwarded, i havn't messed with DMZ because of how insecure it looks.

yes i have been always able to connect to these services in lan no problem at all.

no i tethered my laptop to my phone, otherwise i wouldn't be able to test my WAN access.

and yes i have configured the DNS settings in my router properly.

also this is there deffenition for a stealth port:

>  [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans  Serif][SIZE=-1][COLOR=#000070]A "Stealth" port is one that completely ignores and  simply "drops" any incoming packets without telling the sender whether  the port is "Open" or "Closed" for business. When all of your system's  ports are stealth (and assuming that your personal firewall security  system doesn't make the mistake of "counter-probing" the prober), your  system will be completely opaque and invisible to the random scans which  continually sweep through the Internet. [/COLOR][/SIZE][/FONT]
 [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans  Serif][SIZE=-1][COLOR=#000070]Even if this machine had previously been scanned and  logged by a would-be intruder, a methodical return to this IP address  will lead any attacker to believe that your machine is turned off,  disconnected, or no longer exists. You couldn't ask for anything better.  Your personal firewall or NAT router protected system is acting like a  black hole for TCP/IP packets. That's very cool. [/COLOR][/SIZE][/FONT]


---

### Post by NeddyDownUnder on 2010-05-23
So you bridge the connection on your laptop to your network? Maybe your laptop is blocking the ports? 

I'm sorry but I don't know how much I can help, there are so many variables in your setup... And I'm not an expert... It has to be some problem with how you have your LAN setup or how your laptop shares the connection. I would try at least putting your server in the DMZ for a minute just to see if you get a connection. 

Hopefully some with more knowledge might be able to chime in to this post and give you some help...

---

### Post by Mistah_Transistah on 2010-05-24
i am just going to keep googleing, you don't understand what a basic home network looks like, nor comprehend that in order to connect on WAN you have to establish a connection from another network which is all the laptop is doing

---

### Post by NeddyDownUnder on 2010-05-24
> **Mistah_Transistah said:**
> i am just going to keep googleing, you don't understand what a basic home network looks like, nor comprehend that in order to connect on WAN you have to establish a connection from another network which is all the laptop is doing

I was trying to help you... I'm sorry I wasted my time. I would also like to suggest that it is in fact you who does not understand networking...  I have an Ubuntu home server which I can administer and access from the WAN, you do not... :P  and I've only been using Ubuntu and Linux for two months... Enough said.

---

### Post by Mistah_Transistah on 2010-05-24
my friend, i apologise for my sudden rage, i do very much apritiate your help. and i have good news to announce. i was looking over the bios of my modem once more and found a policy in the firewall settings which i overlooked a million and a half times, i turned this particular policy off and now i am able to access my DSL modem from WAN... but now the question is..... how do i make it look at my server and not my modem?

---


---
title: "how do i change the permission of the /var/www folder"
date: 2009-08-03
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-08-03
i'm trying to host a website. I new at this

I installed LAMP, and it seems to be working fine.

I want to start adding content to the site, but i cannot change any thing in the /var/www folder.

how do i change the permissions of this folder?

---

### Post by SoftwareExplorer on 2009-08-03
Ok, you have a few options:

1.```
gksudo nautilus
```
and put files in that way. You may have to go to properties for the content files and make sure that they are owned by 'www-data'.

2.Make a link that the server 'owns' that points to a folder you own. This way you can change it easily still.

Tell me what you want to do and I'll try to help you through it.

If you want to set up a name like yourwebsite.with-linux.com, for free, I can help you with that, too.

---

### Post by slakkie on 2009-08-03
man chmod
man chown

Good luck

---

### Post by rhythmiccycle on 2009-08-03
> If you want to set up a name like yourwebsite.with-linux.com, for free, I can help you with that, too.

how do i do that?

---

### Post by rhythmiccycle on 2009-08-03
the computer i'm using is also the web server.
(i don't know if thats a good idea, but i'm trying it out. The site isn't meant to have much traffic)

> man chmod
man chown

how exactly do i use this code?

like this:

```

man chmod /var/www

```

then

```

man chown /var/www

```

and then i can change things in that folder? is that how it works?

---

### Post by Sepanderi on 2009-08-03
> **rhythmiccycle said:**
> how exactly do i use this code? like this:...is that how it works?

No, "man" gives you the manual pages of the command, so you should just try to type "man chmod" in the terminal and then press enter. You can scroll the manual page with arrow keys and exit by pressing Q. Man pages come in handy with almost every command. :)

---

### Post by SoftwareExplorer on 2009-08-03
> **rhythmiccycle said:**
> how do i do that?

First, do you have a static ip? If you havn't bought one specifically it's usually dynamic. We can still make it work if it's dynamic though.

---

### Post by rhythmiccycle on 2009-08-03
> Originally Posted by SoftwareExplorer
do you have a static ip? 

when i  enter 
 ```
ifconfig | grep inet
```
it says:
> 
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb7:76e9/64 Scope:Link
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host


and i can see my site from a computer on my LAN. using:
192.168.1.4

but, when my friend tried it from another network, they could see that site.

so i guess its dynamic. (not really sure though)

---

### Post by chapa on 2009-08-03
Hi Actually you will need to go through and make sure you have a static assigned to server. I used the following:
sudo nano /etc/network/interfaces

-In the screen you may see this:
auto eth0
  iface eth0 inet dhcp

_You need to change the inet dhcp to inet static and use the following to define the IP information:
auto eth0
  iface eth0 inet static
address 192.168.1.100
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

Obviously you will use your IP address and router/ gateway setting to your local network.

Close the nano editor (dont forget to overwrite the directory and save your changes)

then restart the network:

sudo /etc/init.d/networking restart

Once you do that you should be set with static IP address

---

### Post by rhythmiccycle on 2009-08-03
chapa,

when i open /etc/network/interfaces

(i like gedit bettet than nano)

it says:

> 
auto lo
iface lo inet loopback


so your telling me, i should delete that and replace it with

> 
auto eth0
iface eth0 inet static
address 192.168.1.100
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


just like that (cut and paste)

then save it??

> Obviously you will use your IP address and router/ gateway setting to your local network.

this is all new to me, none of it is obvious to me (yet)

---

### Post by chapa on 2009-08-03
Ummm... no. You need to use setting from your local network. For instance:

address 192.168.1.100 [COLOR=Red]Is the address I gave this linux box that is in the same subnet as my router/gateway[/COLOR]

gateway 192.168.1.254 [COLOR=Red]My routers address[/COLOR]

netmask 255.255.255.0 [COLOR=Red]Class C network, most common network.[/COLOR]

network 192.168.1.0 [COLOR=Red]Beginning IP subnet range[/COLOR]

broadcast 192.168.1.255                      [COLOR=Red]End or broadcasting IP subnet range

[COLOR=Black]If you are not too familiar with networking stuff you can look on this site:[/COLOR][/COLOR][COLOR=Black]
[www.practicallynetworked.com]("http://www.practicallynetworked.com")[/COLOR]

However this is stuff you need to read about yourself there is no real way of explaining network stuff in a short posting ;-)

I, by the way, am very new at this as well.

Oops I forgot, I really dont know why your network interface card is only stating it is a loopback? perhaps the driver did not install or your network cable is unplugged. Mine shows the following:

lamp@lamp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:18:00:00:00
    inet addr:192.168.1.100  
    Bcast:192.168.1.255  
    Mask:255.255.255.0
    inet6 addr: fe00::000:00ff:f001:f002/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:45486 errors:0 dropped:0 overruns:0 frame:0
        TX packets:26094 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:28038652 (28.0 MB)  TX bytes:7353920 (7.3 MB)
        Interrupt:17 Base address:0x8800

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:25 errors:0 dropped:0 overruns:0 frame:0
        TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:2278 (2.2 KB)  TX bytes:2278 (2.2 KB)

You can see I have my network interface defined BEFORE my loopback.

---

### Post by SoftwareExplorer on 2009-08-03
When you have a network address like 192.168.*.* it means that You have network address translation. It means your router has an address on the Internet which is the one you see if you go to somewhere like whatismyip.com. That address is referred to as your external address. Then the various computers behind your router have their own internal addresses. Sometimes your router's address is set to one number by your ISP and it never changes. That's what I meant by having a static IP. Other times it changes whenever your router restarts or automatically whenever your ISP wants. That's what I meant by dynamic. 
If your address is dynamic it can change from day to day, so people would need a way to tell what your external address is right when they wanted to access your website. That's where a program like inadyn comes in. It sends a message every minute or so to a server on the Internet with its external address. This server is the server a web browser asks to convert a name like example.com to an address made of numbers (in this case it's your external address).
So, 
```
sudo apt-get install inadyn
```


What is NAT? Once someones request get to the router, how will your router know where to send it? Well, instead of your actual computer having an address on Internet, everyone on the Internet talks to your computer by your router's address. Inside your router everyone has addresses like 192.168.*.* to tell different computers hooked up to the router apart. In fact, the addresses that start with 192.168 are not used on the Internet, they are only used inside of (or behind, if thats how you look at it) NAT. Then when you want to go on the internet, your router can translate the messages between it's address and your computer's 'internal' address, as long as you start the connection. But when someone else starts the connection, your router doesn't know what computer to send it to. That's where port forwarding comes in. It basically makes a rule for you router to follow that says, all traffic marked as port 80 should go to the computer 192.168.specific.address. Ok, so we just have to set up port forwarding. 
One problem though: often routers are set up to give computers connected to them the lowest number of address available. But that can change what internal address your computer has from day to day depending on what computer connected to your router first. So we have two options: one is to tell your computer what it's internal address will be and make sure that no other computers will accidentally use it, or, second, have your router assign the same address to the same piece of network hardware. Then it can send port 80 to the same address, and the computer will have the same internal address all the time, so it will get to the correct place.

Edit: > **chapa said:**
> 
However this is stuff you need to read about yourself there is no real way of explaining network stuff in a short posting ;-)
Well said chapa, no wonder I couldn't seem to make this post much shorter

---

### Post by SoftwareExplorer on 2009-08-03
rhythmiccycle, I wouldn't use /etc/network/interfaces, I would use the GUI instead. First go to 192.168.0.1 or 192.168.1.1 in your web browser. (depends on your router, you want to get into the control panel for it). Look for a section on DHCP and limit the range addresses it gives out so that it is not giving away the static one we want to set up for your server. Then We'll use the network applet to set the static IP up on your computer.

Edit:We are in the server section, so If you don't have a GUI then you'll have to use the file, but the GUI would mean less likelihood of errors and I can coach you through it.
Edit 2:You can go to the router control panel on any computer on your network, it doesn't have to be the server.

---

### Post by chapa on 2009-08-03
Much better said than what I could do... Many thanks SoftwareExplorer... But I am sorta lost on a comment you made.... You can install GUI on server?... Really? I dont want to change the subject but if someone were to do this... how would someone go about to do this and is it possible to log on the server with windows with like a remote desktop connection and see the GUI? Wow this will be really cool if it is possible...

---

### Post by SoftwareExplorer on 2009-08-03
By the way, unless you specifically set it up, you probably have a dynamic internal address. It especially looks that was from the address you posted earlier. You may or may not have a static external address, but usually an ISP will charge a monthly fee for a static external address, but we can get around that and do it for free. :D

---

### Post by SoftwareExplorer on 2009-08-03
> **chapa said:**
> Much better said than what I could do... Many thanks SoftwareExplorer... But I am sorta lost on a comment you made.... You can install GUI on server?... Really? I don't want to change the subject but if someone were to do this... how would someone go about to do this and is it possible to log on the server with windows with like a remote desktop connection and see the GUI? Wow this will be really cool if it is possible...

Well, you can always install the ubuntu-desktop package on the server install to get a desktop and then login. However, if you don't have a screen that might be of no use. On the other hand, I have read that you can forward X sessions over ssh, but I haven't figured out how to do that yet.
BTW:One of the machine at school that I setup is full-blown desktop with compiz and full blown server...Ahh the wonders of Linux and package management. It seems to make your computer's software capable of morphing.

---

### Post by SoftwareExplorer on 2009-08-03
> **SoftwareExplorer said:**
> Well, you can always install the ubuntu-desktop package on the server install to get a desktop and then login. However, if you don't have a screen that might be of no use. On the other hand, I have read that you can forward X sessions over ssh, but I haven't figured out how to do that yet.


Looking at [COLOR="Red"][this]("http://ubuntuforums.org/showthread.php?t=1229518")[/COLOR], it sounds like it's possible. I'll have to read up on X forwarding.

---

### Post by rhythmiccycle on 2009-08-04
> **SoftwareExplorer said:**
> rhythmiccycle, I wouldn't use /etc/network/interfaces, I would use the GUI instead. First go to 192.168.0.1 or 192.168.1.1 in your web browser. (depends on your router, you want to get into the control panel for it). Look for a section on DHCP and limit the range addresses it gives out so that it is not giving away the static one we want to set up for your server. Then We'll use the network applet to set the static IP up on your computer.


i went to 192.168.1.1, but i don't see any DHCP, but under "Basic Settings" and then under "Internet IP Address"

there is a pair of radio buttons "Get Dynamically From ISP" and "Use Static IP Address"

then under "Use Static IP Address" there are 3 sets of textboxes that have IP's
1) IP Address, set to 72,227,184,36
2) IP Subnet Mask, set to 255.255.248.0
3) Gateway IP Address, set to 72.227.184.1

please see the attached jpeg.

are these the setting i need to change to make my ip static.

note: my overall goal is to simply host a small low traffic web site from my home pc.

---

### Post by SoftwareExplorer on 2009-08-04
Those setting look they are for your routers external address, not you computers internal address. If you computer's internal address is dynamic, it gets assigned the address from a program on the router that is called a DHCP server. So, no that's not the right setting. I see a router model number in the screenshot, I'll research where to find the correct setting.

---

### Post by SoftwareExplorer on 2009-08-05
Ok, so I looked at your screenshot of your router page more and I think I know where you need to look. LAN (**L**ocal **A**rea **N**etwork) Setup is probably where you can change the Dynamic internal address server (DHCP server) settings. The dynamic DNS section I see probably means we can have your router update the domain server with your external address automatically, and that way we don't have to mess with configuring inadyn.

When you go into the LAN setup part, you are looking either for something like assigning addresses by MAC or for DHCP server settings.

---

### Post by SoftwareExplorer on 2009-08-05
OK, I found your router's manual online.

First, we need to find your servers MAC address. This address is specified in the hardware when it was manufactured and no other network device has it, basically it is unique. Run ```
ifconfig | grep HWaddr
``` and look for your hardware device. If it is connected with ethernet, it's probably something like eth0 or eth1. If it's wireless, it's probably something like wlan0. When you find the correct section, there should be a 'HWaddr' listed it would be something like 00:5e:7c:40:08:10. Write it down.


OK, for the next step.
Go to your router's page again. In the side bar under the Advanced section, click LAN setup.
In the 'address reservation' section, click add.
Choose an IP address from the router&#8217;s LAN subnet, such as 192.168.1.X, with x representing whatever custom number between 2 and 254 you choose.
In the IP Address box, type the IP address to assign to the  server.
Type the 'HWaddr'/MAC address that you wrote down earlier.
Click Apply.
Disconnect your server from your router and then reconnect it.
Congratulations, you now have a static internal IP address for your server.


OK, now to set it up so when someone who is on the Internet side of your router requests to see a web page, it gets to the server.

Go to your routers configuration page.
In the sidebar under the advanced section, Go to Port forwarding/Port triggering.
Select port forwarding in the 'please select service type' section.
Look in the service and Game box to see if there is Apache, HTTP, or web server.
[COLOR="Blue"]If there is,
select it and Put the address you picked earlier in the Server IP address box. Click the add button.[/COLOR]
**------or-------**
[COLOR="Purple"]If not there is not,
click add custom service. Give the service a name. (Apache, for instance) Put 80 in both the starting and ending port boxes. Put in the internal IP address you picked earlier in the server IP address box. Click apply.[/COLOR]

OK, so now people out on the Internet can request web pages now.


One last thing to do:
Set it up so your website has a name that stays up to date with your (probably) dynamic external IP address.
In the advanced section go to Dynamic DNS
The select service provider box will show you what websites are compatible with your router. Pick one and go their website and sign up. (I use afraid.org). Turn on the use dynamic dns checkbox. Fill out the rest of the details and click apply. (sorry I can't be more specific, but i think that it is different for different dynamic dns services.)

---

### Post by rhythmiccycle on 2009-08-06
thank you so much for all your help SoftwareExplorer,

i did all the steps you said.

i choose the domain "maliszesky.dyndns.org"

There is one (hopefully the last) problem:
when i go to that site (maliszesky.dyndns.org), it takes me to the router setting (i.e "192.168.1.1")

I don't want that.

"192.168.1.2" takes computers on my network to the "localhost" on my server.

i want "maliszesky.dyndns.org" to  go to the "localhost" (i.e. /var/www on my server), not the router setting.

i attached some screen shoots.

i'm so close to getting this to work!!!!

---

### Post by SoftwareExplorer on 2009-08-06
I forgot to tell you, most routers don't handle it very well when a request comes from the internal network, uses the external address, and then needs to go back in. Try looking at your website from a proxy or from a different connection. Your website is probably already working, but from where you are you can't see that. I tried the address, but the connection timed out. Most likely your computer was  off.

However, if thats not the case, try this test: (you can do it from any computer on your network)
You can also check to see if dyndns is working by Clicking System -> Admistration-> Network tools and going to the Lookup tab. Put in your domain name. It will give you the address listed for that name. Go to somewhere like whatismyip.com and compare numbers. If they match, it's going to the correct place. (Your router)

---

### Post by rhythmiccycle on 2009-08-06
i called a friend and had them go to the site, and it seems to be working!!!

SoftwareExplorer you are my savior, thank you so much for all your help.  you even went so far as to read the manual to my router. Its people like you who make the world a better place.

---

### Post by SoftwareExplorer on 2009-08-07
> **rhythmiccycle said:**
> i called a friend and had them go to the site, and it seems to be working!!!
I just checked, and I can confirm it works.
> **rhythmiccycle said:**
> SoftwareExplorer you are my savior, thank you so much for all your help.  you even went so far as to read the manual to my router. Its people like you who make the world a better place.
Your welcome. I was trying to do the same thing six months ago both at home and for a server for my school. I was having the same problem in two places. I just couldn't figure out the router and proxy thing until dmizer helped me on these forums. So I was glad to help because I was trying to do the exact same thing a few months ago. It pretty cool to be able to have your own website for free.  And it sure is a nice feeling helping someone to do it to.  :P

---


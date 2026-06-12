---
title: "How to Internet on Ubuntu...?"
date: 2011-02-16
forum: Server Platforms
---

### Post by Its_Rishi on 2011-02-16
i have two systems in both systems there i installed ubuntu 10.10
i need to know how to share an internet connection over the two systems at a time...?

---

### Post by volkswagner on 2011-02-16
Please explain your current network setup.  Do you have a router?  Do you have Cable, DSL, dialup?

Does the pc connected to the internet use the network card or usb to modem?  If it used the Network card to connect, and you have no router, does this machine have a second network card installed?

---

### Post by Neo@Matrix on 2011-02-16
What hardware do You use for connection to the internet?
How do U tend to share the connection?Wired or wireless?

---

### Post by Its_Rishi on 2011-02-16
> **volkswagner said:**
> Please explain your current network setup.  Do you have a router?  Do you have Cable, DSL, dialup?

Does the pc connected to the internet use the network card or usb to modem?  If it used the Network card to connect, and you have no router, does this machine have a second network card installed?
yeah i have a broadband modem and i use DSL 
well i connect the internet through the network card to modem for both the systems

---

### Post by Its_Rishi on 2011-02-16
> **Neo@Matrix said:**
> What hardware do You use for connection to the internet?
How do U tend to share the connection?Wired or wireless?
i use a broadband wired modem through LAN to connect to internet

---

### Post by rvchari on 2011-02-16
> **Its_Rishi said:**
> i have two systems in both systems there i installed ubuntu 10.10
i need to know how to share an internet connection over the two systems at a time...?

option 1: if your DSL broadband connection is through a router, check if you router has additional port. if you have that then connect the 2 pc to the router. the net connection can be shared. if you dont have an additional port then check if you can get a splitter to accomodate another port.

option 2: allocate an ip address to your primare computer, something related to the same family as your broadband connection. (192.168.X.1 must be your router IP, so allocate your computer IP as 192.168.X.50 or something like that)
after you do this, connect to this computer from your 2nd computer through auto dhcp, this should allocate an auto IP in relation to your primary family.
your problem should be solved...

(i am not a typical networking / hardware guy but i solved my problem like this....
i use ubuntu on my laptop and can easily connect to my office server that runs windows....

---

### Post by Its_Rishi on 2011-02-16
> **rvchari said:**
> option 1: if your DSL broadband connection is through a router, check if you router has additional port. if you have that then connect the 2 pc to the router. the net connection can be shared. if you dont have an additional port then check if you can get a splitter to accomodate another port.

option 2: allocate an ip address to your primare computer, something related to the same family as your broadband connection. (192.168.X.1 must be your router IP, so allocate your computer IP as 192.168.X.50 or something like that)
after you do this, connect to this computer from your 2nd computer through auto dhcp, this should allocate an auto IP in relation to your primary family.
your problem should be solved...

(i am not a typical networking / hardware guy but i solved my problem like this....
i use ubuntu on my laptop and can easily connect to my office server that runs windows....
But how to setup auto DHCP...?

---

### Post by rvchari on 2011-02-16
simply select network from places menu. ur other computer will be listed there. when you claick on that, it may prompt for a username and password. type in ur username and password for that pc and make this remember password forever (else u ll have to do this every now and then. if there is security issue, then do it everytime u connect.)

else to to start > system > preferences > network connections. u can do it from there too....

this is what i love in ubuntu... u can juggle around and everything is displayed on whats happening !!!

---

### Post by Its_Rishi on 2011-02-16
> **rvchari said:**
> simply select network from places menu. ur other computer will be listed there. when you claick on that, it may prompt for a username and password. type in ur username and password for that pc and make this remember password forever (else u ll have to do this every now and then. if there is security issue, then do it everytime u connect.)

else to to start > system > preferences > network connections. u can do it from there too....

this is what i love in ubuntu... u can juggle around and everything is displayed on whats happening !!!
well im confused and can't find wat u said at there...

---

### Post by rvchari on 2011-02-16
u r now connected to your 1st computer and are using the net from there, when you connect the two computers and open the network from the 2nd (places > network ) do u see the 1st computer ? if u do then u need not do anythng, just click on that computer and connect with your passowrd and name. if u dont then go to ubuntu start button > system > preferences > network connections
the window will open, now go to eth0 or auto eth0 which ever ur connection may be and click on edit button.
you will have the options for IPV4. check if auto DHCP is enabled. (this is something like TCP/IP properties we click and edit while on windows, get me? )

---

### Post by Its_Rishi on 2011-02-17
> **rvchari said:**
> u r now connected to your 1st computer and are using the net from there, when you connect the two computers and open the network from the 2nd (places > network ) do u see the 1st computer ? if u do then u need not do anythng, just click on that computer and connect with your passowrd and name. if u dont then go to ubuntu start button > system > preferences > network connections
the window will open, now go to eth0 or auto eth0 which ever ur connection may be and click on edit button.
you will have the options for IPV4. check if auto DHCP is enabled. (this is something like TCP/IP properties we click and edit while on windows, get me? )
at places>network i don't see the first computer at there
and there is no eth and auto eth0 at system > preferences > network connections in both systems :(

---

### Post by rvchari on 2011-02-17
tyr to go to connect to server > choose custom location and give the ip address of the 1st computer. i havent tried this and at present am at home and i dont have another computer running ubuntu !!! but this should work i have a gutt feeling

---

### Post by Its_Rishi on 2011-02-17
> **rvchari said:**
> tyr to go to connect to server > choose custom location and give the ip address of the 1st computer. i havent tried this and at present am at home and i dont have another computer running ubuntu !!! but this should work i have a gutt feeling
it doesn't accepting ip address and asks me to enter the name even after entering also no use

---

### Post by rvchari on 2011-02-17
i think the connection has to be through a switch and cant be connected directly.... that must be the crux of ur problem. as i said i am not a hardware guy, i love ubuntu and tweak it to my level refering to forum posts and issuing my commands.

one difference is i connect through a switch.

---

### Post by rvchari on 2011-02-17
for a more detailed info...
follow these links... am sure it will enlighten you on solving ur problem.

a) [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
b)[http://ubuntuforums.org/archive/index.php/t-147971.html](http://ubuntuforums.org/archive/index.php/t-147971.html)

option 2 is the one that might bo of interest to u even though option 1 is a more comprehensive approach shown

---

### Post by volkswagner on 2011-02-17
> **Its_Rishi said:**
> yeah i have a broadband modem and i use DSL 
well i connect the internet through the network card to modem for both the systems

If both computers are able to connect to your modem at the same time, your modem must also include a router.

Is it true, your modem has more than one port to connect to? (If this is true that is all you should need to connect to the Internet from either machine.)

Both machines are running Ubuntu 10.10, are they each desktop version or are any server version (with no GUI)?


Next you will need to make sure each machine has a network card that drivers are loaded, and can get an ip address from your router.

The following will tell you about what type of network card is attached.
```
lspci
```

The following will tell you if the NIC is recognized and if an ip address has been issued.
```
ifconfig
```

Before we proceed with actions, it is best to know what we are dealing with.

---

### Post by Its_Rishi on 2011-02-18
> **volkswagner said:**
> If both computers are able to connect to your modem at the same time, your modem must also include a router.
 
Is it true, your modem has more than one port to connect to? (If this is true that is all you should need to connect to the Internet from either machine.)
 
Both machines are running Ubuntu 10.10, are they each desktop version or are any server version (with no GUI)?
 
 
Next you will need to make sure each machine has a network card that drivers are loaded, and can get an ip address from your router.
 
The following will tell you about what type of network card is attached.
```
lspci
```
 
The following will tell you if the NIC is recognized and if an ip address has been issued.
```
ifconfig
```
 
Before we proceed with actions, it is best to know what we are dealing with.
 Yes my modem has 4 ports and one wifi(wlan) compatibity and in the both computers there is only ubuntu 10.10 maverick version none of then have server installed in it...

---

### Post by rvchari on 2011-02-18
rishi,
i use the same service provider that you use and instead of beating around the bush getting things configured, you can simply fit a wi-fi pci card on one of ur pc and connect thru wi-fi. whenever i have guests at home (with their resp laptops) we all connect at once and everything is fine... this is a straight forward solution irrespective of OS we use.

but to connect, you can always have a long cable with RJ 45 jack and connect to the router. so internet can be accessed from both pc.

what you may do further will enable you to congigure your home network (making one as a server and other as client) that can be done after you follow the links that i had posted earlier.

---

### Post by Its_Rishi on 2011-02-20
> **rvchari said:**
> Rishi,
i use the same service provider that you use and instead of beating around the bush getting things configured, you can simply fit a wi-fi pci card on one of ur pc and connect thru wi-fi. whenever i have guests at home (with their resp laptops) we all connect at once and everything is fine... this is a straight forward solution irrespective of OS we use.

but to connect, you can always have a long cable with RJ 45 jack and connect to the router. so internet can be accessed from both pc.

what you may do further will enable you to configure your home network (making one as a server and other as client) that can be done after you follow the links that i had posted earlier.
Sorry for my late posting...
As i cannot effort the wi-fi pci card i do already have and connect my systems by long RJ 45 jack cable to the router from the both pc's
and iam exactly asking that how to make one pc as the server and the other as client...?
thats what iam exactly asking to connect my both pc's internet mutually...!

---

### Post by rvchari on 2011-02-20
you need a switch to connect the two computers. direct rj45 jack interconnect may not work for your internal LAN (its only then that you can connect for internet sharing)
get a switch and connect the 2 pcs to the switch. link the internet router to the switch

---

### Post by Its_Rishi on 2011-02-20
> **rvchari said:**
> you need a switch to connect the two computers. direct rj45 jack interconnect may not work for your internal LAN (its only then that you can connect for internet sharing)
get a switch and connect the 2 pcs to the switch. link the internet router to the switch
Ofcourse i connected the both pc's to the modem which has four pc's sharing capacity and wi-fi...

---

### Post by volkswagner on 2011-02-20
> **Its_Rishi said:**
> iam exactly asking that how to make one pc as the server and the other as client...?
thats what iam exactly asking to connect my both pc's internet mutually...!



I don't understand where this thread is going.

What are you trying to do?

Are both machines currently able to connect to the Internet?
If not, did you run any of the commands in my earlier post?

What type of client server situation are you looking for?  Do you just want to share files?  Do you want the server to control access to the internet for the client (filter, router, proxy server)?

---

### Post by Its_Rishi on 2011-02-20
> **volkswagner said:**
> I don't understand where this thread is going.

What are you trying to do?

Are both machines currently able to connect to the Internet?
If not, did you run any of the commands in my earlier post?

What type of client server situation are you looking for?  Do you just want to share files?  Do you want the server to control access to the internet for the client (filter, router, proxy server)?
Yes the both computers connect to internet seperatly(one is on and the other is off)
I need to share not only files but also internet for the both computers at a time...

---

### Post by volkswagner on 2011-02-20
> **Its_Rishi said:**
> Yes the both computers connect to internet seperatly(one is on and the other is off)
I need to share not only files but also Internet for the both computers at a time...

What does this mean?  "One is off" does this mean it is not working or you have internet disabled for security reasons.

Your router/modem should be the device to share your Internet.  Please give specifics what you want to do, so we can help.

I have asked once, and I'll ask again.... "Do you want/need the first machine to control Internet to the second, if so why?  Why can't you allow your router to do the Internet sharing?

---

### Post by rvchari on 2011-02-20
> **Its_Rishi said:**
> Ofcourse i connected the both pc's to the modem which has four pc's sharing capacity and wi-fi...

rishi,
dont get confused....
the router u use to access the internet cannot act as a switch.
with that you can connect upto 4 pcs over ethernet lan and wi-fi will make many others connect.

that much for internet access.

you primarily wanted one pc to be connected to that router and other pc to be connected to the 1st pc so that you can have local lan access to share files and folders and at the same time use that to surf net (internet sharing) for this you just cant connect 2 pc thru rj45, u need a switch. get me ?

i hope i understood you right.

sm i right volkswagner ?

---

### Post by volkswagner on 2011-02-20
> **rvchari said:**
> rishi,
dont get confused....
the router u use to access the internet cannot act as a switch.
with that you can connect upto 4 pcs over ethernet lan and wi-fi will make many others connect.

that much for internet access.

you primarily wanted one pc to be connected to that router and other pc to be connected to the 1st pc so that you can have local lan access to share files and folders and at the same time use that to surf net (internet sharing) for this you just cant connect 2 pc thru rj45, u need a switch. get me ?

i hope i understood you right.

sm i right volkswagner ?

I never heard of a router with multiple ports, not being able to act as a switch.

---


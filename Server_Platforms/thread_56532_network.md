---
title: "network"
date: 2005-08-12
forum: Server Platforms
---

### Post by pcd927 on 2005-08-12
I just got Linux and I am very satisfied but I don’t know my ip address to make a network can somebody please help me out 
I am using a cable modem connected to a router

---

### Post by amohanty on 2005-08-12
to get network information, at the terminal type:
ifconfig

Can you access the network, you know browse the net etc. ???
AM

---

### Post by pcd927 on 2005-08-12
[QUOTE=amohanty]to get network information, at the terminal type:
ifconfig

Can you access the network, you know browse the net etc. ???
AM[/QUOTE]
 Well I can't when I was installing ubuntu it asked me something something about the network( I just clicked "cofigure it later") and now I can't access the internet or connect to the other computers, I am very new to linux and haven't used it prior to today. If it concers you i have a linksys brondband router model: BEFW11S4
and moterola surfboard cable modem
thanks. :)

---

### Post by amohanty on 2005-08-12
Can you use the router and cable modem to browse the net using some other machine?

If yes it means your stuff is configured, now to the ubuntu machine:
Goto:
Applications->Systems Tools->Network Tools

A dialog will pop up. Now if your NIC was recognized by Ubuntu (search in the forums for anybody having problems with your NIC make, your modem. If you cannot find anything, it will usually mean that everything works fine _usually_) then in the drop down box in the 'Devices' tab you should be able to see eth0. Select it, and click the Configure button. THen based on whether you are using DHCP or you have a static IP set it up and you should be ready to go.

If no, I suggest you first make sure that you are able to connect to the network with your router and modem, then go back to step 1.


HTH
AM

---

### Post by pcd927 on 2005-08-13
like I said I'm new to ubuntu and I don't know how to set it up 
oh and how do you get the ip address

---

### Post by dorris on 2005-08-14
[QUOTE=pcd927]like I said I'm new to ubuntu and I don't know how to set it up 
oh and how do you get the ip address[/QUOTE]
 this is definitely not a thread for servers, but anyways, heres the quick info

to retrieve your ip information, type in terminal window
```
ifconfig
```
ifconfig is a great tool to view/edit wired interfaces.
but if no ip has yet been assigned, it won't show any IP address.
perhaps ifconfig ethx would also be suitable to specify which interface to loot at.
To configure the interfaces graphically on hoary, click
System->Administration->networking tools, follow instructions!
to do it manually:
change IP on ethx
```
ifconfig ethx xxx.xxx.xxx.xxx netmask xxx.xxx.xxx.xxx up
```
add a dns server, edit /etc/resolv.conv
and add a line such as ```
nameserver 196.25.1.1
```
to add a route, in particular a default gateway
```
route add default gw xxx.xxx.xxx.xxx
```

and that should be it, great using the text based for on-the-fly changes, the graphical manager edits the file /etc/networking/interfaces , which stores details, so its automatically configured on boot, obviously it can also be done manually with ease
eg, my file contains the following to configure my wired interface.
```
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.11
```

Good luck, but seriously, I should not have needed to answer this question, google is your friend!
If you going to get into linux, I seriously recommend googling a lot more, and it seems like you haven't even attempting to click around and see what gnome can configure for you.
this is a friendly community and will generally help with anything you need, but it is much more benefical  to try solve problems for yourself, you will learn a lot more that way.
also visit the "Absolute beginner talk" thread, 
I recommend before you go any further, go through every option in the Application launcher and see what it does!!

---

### Post by pcd927 on 2005-08-28
Okay I solved half the problem I was using kubuntu but it said I was using ubuntu :oops:. Therefore, I installed ubuntu the network works but I cannot go to other sites.
Please help me

---

### Post by gruepig on 2005-08-29
I think this thread really belongs on the networking forum.  Re-post your question there and include the contents of the files /etc/network/interfaces and /etc/resolv.conf and the output of '/sbin/ifconfig -a' and '/sbin/route -n', and I'll try to help.

---


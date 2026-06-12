---
title: "4 Questions about Setting up Static IP address for my Server"
date: 2009-04-07
forum: Server Platforms
---

### Post by redonwhite on 2009-04-07
Hello,

I have a fresh install of ubuntu 8.10 server edition with LAMP and SSH installed.  This will be a headless server once i have a static IP configured so i have no GUI.  Just command line.  I am trying to configure a static IP address on my server.  Im following the directions from this site.

[http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/](http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/)

I have a couple questions...(some are silly i know) ;)

First.---You have to open and edit some things in a text editor and i was wondering how do i open the file.  For example on the Links How to i need to edit /etc/network/interfaces.  Do i need to type anything in front of that before running the command to bring it up in a text editor?

Second.---Once I'm able to open a file in a text editor how do i go about Editing and then Saving the file?  I have never had to do this in Command line before.

Third.---On the step where I edit the /etc/network/interfaces the writer says i need to input this code in at the bottom of the file and in place of where it says iface eth0 inet dhcp i assume.  Am i doing good so far?
```
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
```
He says I will need to change the three lines to reflect my own network setup.  As for the first line, IP address, can i make this number up.  Or is it a number i need to get from my router.  Or is it a number i need to make up and then input it into my router.

Forth(LAST ONE I SWEAR!):p---On the DNS part of the "how to".  Am I suppose to just add those two lines he posted to the file.  He says that the above is an example using the OpenDNS server.  Im not familiar with the OpenDNS server.  Is this preinstalled on Ubuntu server 8.10?

THANK YOU for for any help you can give.  If there is any more information i can give to better help you help me just ask.  Thanks! ):P

---

### Post by cariboo on 2009-04-08
For ease of use I would suggest using nano. To edit /etc/network/interfaces you would type at the prompt:

```
sudo nano /etc/network/interfaces
```

this will open the file for editing. At the bottom of the window you will a list of the commands. Press Ctrl+the letter of the command you want to execute. See Screenshot

As far as the ip address is concerned it has to be in the same netblock as your router. In the screensreenshot you can see the ip address of my gateway is 192.168.1.1, the ip address of the server should be anywhere between 192.168.1.2 and 192.168.1.254. I used 192.168.1.200 as that is outside the range of addresses that my router assigns via dhcp. You will also have to change the dhcp to static.

In the example you linked to the author suggested using Opendns for your dns addresses, you can use the dns addresses in the example or use the dns addresses provided by your isp. You will have to access the the management interface on your router, and from there you should be able to find out what the gateway and dns addresses are.

I have a Linksys WRT54GS, to access the managment interface. in Firefox I type in the address bar:

```
https://192.168.1.1
```

Depending on your router make and model it may be different. Check the documentation that came with the router.

Jim

---

### Post by andrewc6l on 2009-04-08
Here are some answers :-)

1 & 2. You can use the text editor nano to edit files from the command line.
```
sudo nano /etc/network/interfaces
```
will edit /etc/network/interfaces. When you're done, Ctrl-X will then prompt you if you want to save changes.

3. You can make the IP address up. You will want to configure your router so it doesn't give out that IP address. (Often, you can change the DHCP setup in the router so it assigns a range like 192.168.1.0-192.168.1.32. If that's the case, you could safely pick 192.168.1.33 or higher for your static IP address). The gateway has to be the address of your router. Netmask should be 255.255.255.0 if both your static IP and your DHCP addresses are in the same 192.168.1.xxx range.

4. The DNS server is something you get from your ISP. If you are configured for DHCP, you can type ```
nslookup google.com
```
The "Server:" line will tell you what your DNS address is.

---

### Post by EXCiD3 on 2009-04-08
> **redonwhite said:**
> Hello,

I have a fresh install of ubuntu 8.10 server edition with LAMP and SSH installed.  This will be a headless server once i have a static IP configured so i have no GUI.  Just command line.  I am trying to configure a static IP address on my server.  Im following the directions from this site.

[http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/](http://www.ghacks.net/2009/03/30/configure-static-ip-address-in-ubuntu-server-810/)

I have a couple questions...(some are silly i know) ;)

First.---You have to open and edit some things in a text editor and i was wondering how do i open the file.  For example on the Links How to i need to edit /etc/network/interfaces.  Do i need to type anything in front of that before running the command to bring it up in a text editor?
[/quote
Use nano from the command-line. It works like such:
```
nano /etc/network/interfaces
```
It will open up the file in a text editor that is text based for you. :)

> 
Second.---Once I'm able to open a file in a text editor how do i go about Editing and then Saving the file?  I have never had to do this in Command line before.

Edit like normal, Ctrl-X will save it. Might want to google the nano controls so you can use some of the other options as well.

[quote]
Third.---On the step where I edit the /etc/network/interfaces the writer says i need to input this code in at the bottom of the file and in place of where it says iface eth0 inet dhcp i assume.  Am i doing good so far?
```
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
```He says I will need to change the three lines to reflect my own network setup.  As for the first line, IP address, can i make this number up.  Or is it a number i need to get from my router.  Or is it a number i need to make up and then input it into my router.

This will depend on how your home network is setup. Presumably you are using a router which will give out 192.168.1.X ip addresses. A static IP means that the last IP is ALWAYS the same number. What you might want to do instead of having the server get a static IP, is to leave the configuration alone and have the router always give that computer's mac address a static IP. Saves time in configuration considerably. The IP will have to be from 1 to 255. Typically most routers are 192.168.1.1 so you should set it on the other end of the spectrum, say 192.168.1.250 instead. Netmask will configure the subnet of the IP address, which should stay as 255.255.255.0 for you. Gateway should point to the router's IP address, which most likely will be 192.168.1.1 for you.

> 
Forth(LAST ONE I SWEAR!):p---On the DNS part of the "how to".  Am I suppose to just add those two lines he posted to the file.  He says that the above is an example using the OpenDNS server.  Im not familiar with the OpenDNS server.  Is this preinstalled on Ubuntu server 8.10?

THANK YOU for for any help you can give.  If there is any more information i can give to better help you help me just ask.  Thanks! ):P
OpenDNS won't be preinstalled because it is a free online DNS service. Instead of using your ISP's DNS servers which are often crappy and go down, you can use their reliable servers for DNS resolution instead. Typically you will just set this in your router instead as well. Check out more about OpenDNS here: [http://www.opendns.com/](http://www.opendns.com/)

Hope that helps explain some stuff, please feel free to ask more questions. :D

---

### Post by redonwhite on 2009-04-08
To all of you.  THANK YOU!! =D> 

I just have a few more questions about DNS.  I now see a few different options as far as DNS goes.  I was able to access my router through the browser and noticed on the set up page there are three spots towards the bottom and for an address.  Each spot is labeled "static DNS".  Then the other thing i noticed is under the DDNS tab on my routers access page.  When i click on the DDNS tab i am sent to a page where it says DDNS service.  then in the box next to it, it says disabled.  When i click the drop down box i have two options.  DynDNS.org and TZO.  Should i select one of these?

Thanks for your help again!

---

### Post by EXCiD3 on 2009-04-08
You don't have to worry about DDNS, what you can do with that is have a free domain from DynDNS.org setup that points to your home network so that you can access it from home later on. Might be something you should look into if you are interested. It's really handy.

The three spots are where you put the OpenDNS servers. Usually you only use two from there. If you leave them blank then it won't be using OpenDNS but your ISP's DNS servers.

---

### Post by redonwhite on 2009-04-08
> **EXCiD3 said:**
> You don't have to worry about DDNS, what you can do with that is have a free domain from DynDNS.org setup that points to your home network so that you can access it from home later on. Might be something you should look into if you are interested. It's really handy.

The three spots are where you put the OpenDNS servers. Usually you only use two from there. If you leave them blank then it won't be using OpenDNS but your ISP's DNS servers.

Okay just so i have this straight.  I should take those two numbers from OpenDNS. 208.67.222.222, and  208.67.220.220.  Input them into the server as explained in the link.  Then is it necessary to input them into the router as well? 
Thanks for your help.  :guitar:

---

### Post by EXCiD3 on 2009-04-08
Actually, don't even bother with putting them into your server. Setup your entire network to use OpenDNS by putting them into your router. OpenDNS is much more reliable than any ISP's DNS servers and works much better so why not go the extra step and have your entire network use it? I have always used OpenDNS and never had any troubles. I think you will really like it. Of course, you can remove them if you don't like it for some reason.

The DNS servers are just there so that you can specify if your ISP requires it or if you want to use something different from what your ISP provides automatically. I suggest using OpenDNS for sure, but there is nothing saying you have to. Your server will work just fine without it.

---

### Post by redonwhite on 2009-04-08
> **EXCiD3 said:**
> Actually, don't even bother with putting them into your server. Setup your entire network to use OpenDNS by putting them into your router. OpenDNS is much more reliable than any ISP's DNS servers and works much better so why not go the extra step and have your entire network use it? I have always used OpenDNS and never had any troubles. I think you will really like it. Of course, you can remove them if you don't like it for some reason.

The DNS servers are just there so that you can specify if your ISP requires it or if you want to use something different from what your ISP provides automatically. I suggest using OpenDNS for sure, but there is nothing saying you have to. Your server will work just fine without it.


I see.  I added them to the lines on my server.  I think i will test them out on the server for a bit and then if i like them ill put them on my router too. :p .  I didnt delete the other "servernames" on that list when inputing the OpenDNS "servernames".  Does that matter?  All and all i should have static IP address on my server now right? haha.  I would have been lost with out your replies.  Thanks!

---

### Post by EXCiD3 on 2009-04-08
Yep everything should work alright for you. You probably won't notice opendns if you server is running headless. The only time it will be noticeable is if you put say "ubuntu" in your address bar without the .com because OpenDNS will return a search result page for you. You might be able to get to sites silghtly faster with it though. If you need anything else, don't hesitate to ask. I'm always on IM as well if you get stuck on something. Cheers! :)

---

### Post by redonwhite on 2009-04-08
> **EXCiD3 said:**
> Yep everything should work alright for you. You probably won't notice opendns if you server is running headless. The only time it will be noticeable is if you put say "ubuntu" in your address bar without the .com because OpenDNS will return a search result page for you. You might be able to get to sites silghtly faster with it though. If you need anything else, don't hesitate to ask. I'm always on IM as well if you get stuck on something. Cheers! :)

Greatness.  Thank you so much!  Now i can begin my Jinzora adventure without my IP changing every time i try and SSH into my server hehe.  ;)  Thanks again everyone!  Problem SOLVED!.  ):P

---


---
title: "Apache Newbie and Port 80"
date: 2006-03-25
forum: Server Platforms
---

### Post by Simian on 2006-03-25
Yesterday I set up an apache web server over a lan (I think). i am able to type the ip of the server into another linux box (or non linux) and view the test html pages that I put there.

i am only able to do this over the lan with a non public ip address, 192.168.2.102

I was told on Freenode #kubuntu that i need send all traffic from port 80 to 192.168.2.102 That is where I am completely lost.

Could someone please walk me through this process. I would be eternally grateful. :)

---

### Post by Simian on 2006-03-25
I'm looking at portforward.com and selected linksys BEFW11S4. But now it is asking me 'Please select the program you are forwarding ports for from the list below'

Well I don't know? I just want users to access my web pages through the internet.

---

### Post by localzuk on 2006-03-25
On your router you need to use a feature called 'port forwarding'. This is usually very simple to set up (on mine I just state the port and destination ip - and that is it).

Take a look at the instructions for your router.

---

### Post by localzuk on 2006-03-25
The site you reference has this page:

[http://portforward.com/english/routers/port_forwarding/Linksys/BEFW11S4/Easy_File_Sharing_Web_Server.htm](http://portforward.com/english/routers/port_forwarding/Linksys/BEFW11S4/Easy_File_Sharing_Web_Server.htm)

It provides info for setting up some sort of server in windows. The bit you want is the lower part - setting up the router part.

---

### Post by Simian on 2006-03-25
Thanks localzuk, for taking the time to find that infomation for me. I followed the tutorial step by step but there was one part that i couln't do for some reason:

Put a dot into the Block WAN Request Disable radio button
Click the Apply button near the bottom of the page.

i did that but when i clicked apply nothing happend? It is driving me crazy because i am positive that that is what's standing in my way.

i don't suppose that you or anyone else can think why i can't disable 'Block Wan requests' ?

---

### Post by peanut butter on 2006-03-25
i shoulden't matterfor your use but that is odd

---

### Post by Simian on 2006-03-25
ok i've managed to disable 'Block wan requests' by adding  192.168.2.102 address to DMZ (I have no idea what i'm doing but it worked).

But when i enter my ip address into my browser i still jsut get some info about my router.

i should mention that i don't have a static ip. someone at Freenode #kubuntu said that i don't need one.

---

### Post by peanut butter on 2006-03-25
did u select both tcp and udp to forwardbecauseits not fowaarding then.

also u might want to use dyndns.org to get an eisier hostname

---

### Post by peanut butter on 2006-03-25
ok ihave the same router as u so i made a screenshot of the applacations and gameing section of mine.
notice you will have to change your ip to static and set it to 192.168.1.102 or like me to 192.168.1.120 so there arent any conflicts. btw. you must check the enable box and say save settings.

---

### Post by Simian on 2006-03-25
thanks peanut butter, i have done everything right with the router (I think) maybe my problem is with apache. i just started using it yesterday so maybe the is some configuration thing that i'm supposed to do.
Do you know apache at all?
lol i feel like i'm clutching at straws now...

---

### Post by localzuk on 2006-03-25
It could still be your router. In order to log into your router, do you just visit the ip address of it or do you specify a different port.

Eg. 192.168.1.1 or 192.168.1.1:8080?

---

### Post by peanut butter on 2006-03-25
your isp might block port 80 try a different one like 90 or something
which isp do u have?

---

### Post by Simian on 2006-03-26
localzuk: To log in I just enter it's IP address without specifying a port

peanut butter: I have tried forwarding all traffic from port 8080 to 192.168.2.103 (my IP) as well.

My ISP is BT Broadband

---

### Post by localzuk on 2006-03-26
The problem is that your router is serving its administration software on port 80 so you cannot just forward the data.

Is there a way, on the router, for you to change the port that the admin software is served on? If not, you should edit the apache configuration file to use a different port, other than 80 and set up forwarding on the router for that.

BT don't block port 80 traffic so that should be fine.

---

### Post by Simian on 2006-03-26
I've looked everywhere on the router setup page and can't see an option for changing the port that it uses, (but that doesn't mean that it's not there)

I'll take a look at the apache config file (/etc/apache/httpd.conf i think) wish me luck](*,) lol

---

### Post by peanut butter on 2006-03-26
which version of the router do u have (
itsays on the bottom)?

---

### Post by Simian on 2006-03-26
version 4

---

### Post by peanut butter on 2006-03-26
ill figure out how to get itto work but as far as i remember i just fowarded the portsand itworked. if u dont have any special settings i would just reset it and foward port 80. what happened before was ifi went thru the internet it would foward it to the correct computer.
did u check the enable checkbox by the foward?

---

### Post by localzuk on 2006-03-27
How can it forward the port 80 if the admin software on the router itself runs on port 80?

---

### Post by peanut butter on 2006-03-27
the admin software runson port 80 of the ip 192.168.1.1 but when you foward ports its going to your public ip address dont ask me how they do thatbut it just does.

---

### Post by localzuk on 2006-03-28
That is understandable - however the user mentions that when he tries the public IP it still shows him the admin software - which indicates that there is something different. (My router does the same thing, however I can turn it on/off and change the port the admin software runs on).

---

### Post by webfoot0 on 2006-03-28
[QUOTE=Simian]thanks peanut butter, i have done everything right with the router (I think) maybe my problem is with apache. i just started using it yesterday so maybe the is some configuration thing that i'm supposed to do.
Do you know apache at all?
lol i feel like i'm clutching at straws now...[/QUOTE]

Hi There are a number of points:
1 If from a second machine on your LAN you can see the pages on the Apache Server by entering [http://192.168.xxx.yyy](http://192.168.xxx.yyy) (the address of the machine running the server) then Apache is working correctly.
2 If you are connecting through a router with a DMZ set for the apache server machine then to see the pages you should enter the public address which your router has obtained from your ISP in the address bar of your browser.
3 Be aware that if either the local server address OR the address of the machine running Apache are allocated by DHCP then further steps will be required for regular connections from the Internet.

Keith
===================================

Hope im not telling granny to suck eggs.

---

### Post by Simian on 2006-03-29
It has just occurred to me that the problem might be my adsl modem. I believe that it is also a router. Now my wireless router plugs into my modem/router. When I type the public IP address I get the setup page of my modem/router, not the wireless router.
I would have mentioned this earlyer but until now I have always thought of it as just a modem and my wireless router as THE router. In fact there are two routers.
So do any of you think this is where the problem lies?

---

### Post by ehazlett on 2006-03-29
you may also check to make sure your router admin software is running on a different port.  mine runs on 80 by default, thus it could override and take all http requests.  change your router admin to listen on a port like 8080, and try to hit your web server.

---

### Post by Simian on 2006-04-01
Just to let you guys know that I changed my old modem and wireless router for a modem/router(wireless)/firewall and it was forwarding port 80 traffic within minutes of setting it up.

Thanks for all your help and making this a great comunity to be a part of :)

---


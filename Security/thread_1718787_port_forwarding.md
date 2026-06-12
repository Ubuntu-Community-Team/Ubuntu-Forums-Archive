---
title: "port forwarding"
date: 2011-03-31
forum: Security
---

### Post by josephmills on 2011-03-31
Hi there I have been struggling trying to set up my QSee H.264 Network Embedded DVR model QS408 (Here is a PDF with the manual [www.q-see.com/files/manuals/QS408-Manualweb.pdf](www.q-see.com/files/manuals/QS408-Manualweb.pdf)
)
MY router is a gigaset SX762 
the router is set to ppoe 

I am running ubuntu 10.10 and use opera,firefox and chromium for my browsers 

Here are the troubles that I have been having 
1) I can not remote view the dvr 
2) Some how the passwoed to the router has changed from admin to ?
3) I had it all set up. When I went to my ip for the dvr box my browser says IT WORKS! but there is no data bring transfered 

first thing I did was set up my  wireless
then  
Here is a step by step list of things that I did 
1) connected the cat5 cable to the router from the dvr in slot #1
2) went to the computer then checked my Connection information 
3) set the dvr box's settings dhcp and the port to 8080 and 2000
4) went back to computer and loged into my router and this is where I thin that I messed up but I set the port forwarding option to utp and tcp for both port 8080 and 2000 
5) took down all the fire walls 
6) went back to the computer and typed in the ip for the dvr box and got the IT WORKS message 


that was yesterday 
today I tried to talk to my internet provider and see how much a staic ip would cost me. First it would cost a lot more and second if I did that then they need to bring in a new router and it will only have one port on it and I cant hook up any of my other computers to it and it has no wifi. Then they went on to tell me that I would not be able to get into my router because they provide 24 hour support and they will do the work for me. And that they do that for all of there business accounts So I told them that I had to think about it and call them back. I thought at this point that I would try to fix it again my self and now I cant even log into my routers account. So here I am with a nice dvr box that I cant view or hook up to my computer to watch my store. Could some one please help me with this one thanks

---

### Post by cariboo on 2011-03-31
You should be able to reset your router and start from scratch.

---

### Post by josephmills on 2011-03-31
thank you for that I will do I total for got that I d do that thank you again. is there any way that I could set up my router or internet to be ddns instead of pppoe or do I need another router?

---

### Post by spynappels on 2011-04-01
DDNS and PPOE are two completely different things. PPOE is the type of connection you have to the Internet, while DDNS is a service which runs on many routers which tells DynDNS (or other No IP type services) what your public IP is at regular intervals.

You will probably need to set a static IP on the DVR rather than a DHCP lease as the address of a DHCP lease can change on reboot and break your port forwarding rules, unless you have reserved IP DHCP. Static IP is normally easier.

When you went to the DVR IP and got the It Works message, you were probably accessing the standard Apache page on port 80, but you say the DVR sends data on either port 2000 or 8080, so when going to the IP from a browser, you need to make sure you specify a port also like [http://your-ip-here:8080](http://your-ip-here:8080)

---

### Post by BkkBonanza on 2011-04-01
Are you trying to access your PVR from outside your LAN (on the internet)?

It sounds like you are doing it within your LAN.
If the PVR is inside your LAN then you don't use port forwarding at all.
You just connect to the correct local IP and port.

If you are trying to connect from outside then you do need port forwarding and also to configure the DHCP in your router to assign a "static lease" to the PVR (by MAC address)(see page 73 of the [router manual]("http://gigaset.com/medias/sys_master/A31008-M707-R121-3-7619_en_GBR_IRL.pdf")). 

Both settings require you get admin access to the router. Usually there is a reset button to reset everything. Again, check the manual about reseting (though you may have problems re-configuring if you have no access to what the settings are now and don't know much about that stuff).

---

### Post by josephmills on 2011-04-01
cool guys thanks for all the help I will be going over to the store now and will keep you up to date also I might post the ip if any one would like to see the camera. damn when it rains it pours My car has a flat so I have to ride my bike. will post in hour or so once again thank you for all the help talk to you soon

---

### Post by josephmills on 2011-04-01
ok after a long and wet bike ride I am here and about to reset the modem wish me luck and once again thanks guys

---

### Post by josephmills on 2011-04-01
I got to work!!!!!!!!!!!!!!!!!!!!!  After working on it for about 4 hours I got it. I am going to work on a video tutorial and will post a link. Once again thank you all so much.:D and if you would like to "see" send a message

---

### Post by josephmills on 2011-04-01
> **spynappels said:**
> DDNS and PPOE are two completely different things. PPOE is the type of connection you have to the Internet, while DDNS is a service which runs on many routers which tells DynDNS (or other No IP type services) what your public IP is at regular intervals.

You will probably need to set a static IP on the DVR rather than a DHCP lease as the address of a DHCP lease can change on reboot and break your port forwarding rules, unless you have reserved IP DHCP. Static IP is normally easier.

When you went to the DVR IP and got the It Works message, you were probably accessing the standard Apache page on port 80, but you say the DVR sends data on either port 2000 or 8080, so when going to the IP from a browser, you need to make sure you specify a port also like [http://your-ip-here:8080](http://your-ip-here:8080)

I am brand new to all of this, but you made grey water turn clear thank you so much!!!!

---

### Post by josephmills on 2011-04-01
there is a bonanza on a cariboo and its totally spynappnapious thanks again you guys

---

### Post by josephmills on 2011-04-02
> **josephmills said:**
> there is a bonanza on a cariboo and its totally spynappnapious thanks again you guys
[http://www.youtube.com/watch?v=8bVDQ4rVrM4](http://www.youtube.com/watch?v=8bVDQ4rVrM4)

---


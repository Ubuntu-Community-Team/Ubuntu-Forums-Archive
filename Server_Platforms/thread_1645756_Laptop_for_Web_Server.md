---
title: "Laptop for Web Server"
date: 2010-12-15
forum: Server Platforms
---

### Post by micha8l on 2010-12-15
Hey, I've been wondering if a Laptop could be used as a web server, asI'm wanting to run LAMP (Zend Server) on it, but I'm not sure if it could take heavy traffic (50 - 100 concurrent connections).

Toshiba Tecra A10-104 Specification:
type : [Intel® Centrino® 2 with vPro technology]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_02105076401&cc=GB") featuring [Intel® Core 2 Duo Processor]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_02105071001&cc=GB&contentType=0")P8400, Intel® GM45 Express chipset and Intel® WiFi Link 5100                                
                                                          clock speed : 2.26 GHz                              
                                                          front side bus : 1066 MHz                              
                                                          2nd level cache : 3 MB                              

                                                                                standard : 2,048 MB                              
                                                          maximum expandability : 8,192 MB                              
                                                          technology : DDR2 RAM (800 MHz)                                

topology : international V.92 modem                                
                                                          speed : 56 Kbps data and 14.4 Kbps fax                                
                                                          topology : Gigabit Ethernet LAN                                
                                                          speed : 10BASE-T/100BASE-TX/1000BASE-T                                

Could someone give me an idea on how much traffic this could take, or point me to a web app that could compute this?

Kind Regards
Mike

---

### Post by elico on 2010-12-16
well sure your computer can run this server with no problem but most of the problem is with the internet connection speed and not the machine.
50-100 connections is not that heavy duty for this machine as long as it configured correctly.

---

### Post by R.Bucky on 2010-12-17
Just remember that if your hdd dies, your entire config is dead. Also, it is likely that your laptop's 2.5" hdd spins at 5400RPM, not the 7200 or 10000 that servers operate at. It is fine for a temporary situation, but you need a dedicated box that can always be on, regardless of your laptop activity.

---

### Post by The Real Dave on 2010-12-18
It depends on what you what it for. If you're sharing photos with your family and friends it's overkill, however, if you're starting the next facebook you're barking up the wrong tree. 

Will users be downloading video, or other large content, browsing regular site content (blogs for example), or uploading and sharing their own stuff? How popular do you expect it to be?

For something that isn't getting massive traffic (50-100 isn't very big, depending on what those connections are doing) a laptop will make a fine web server. The HDD might be a bit on the slow side, but you could replace it with an SSD of a suitable size, or, if you preferred, upgrade your RAM to it's maximum, which could allow most of the site to be served from the RAM, depending on the site type.


Laptops, even powerful ones like your's, also draw a lot less power than a regular desktop, and a small town less than a full blown, dual quad core, 10K SSCIs server :) Be aware that laptops tend to get quite hot, and cooling could be an issue. You may want to raise it, so it recieves better airflow, or even use a laptop cooler.

---

### Post by HermanAB on 2010-12-19
Look at it this way: A modern laptop is 100 times faster than a high end server from 15 years ago and things worked fine then...

---


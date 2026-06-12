---
title: "Wydarr's Travels in UNRLiliput, LinuxBrobdingnag and KubuntuLaputa"
date: 2009-05-21
forum: Testimonials &amp; Experiences
---

### Post by Wydarr on 2009-05-21
I have been using Ubuntu for the past two years, as my only OS (figured I'd go all the way or no way at all). This here is both a testimonial and a let's say cry for help (Anyone willing to help me with any of the below issues, please PM me and I will be forever in debt.) 

The main problem with Linux / Ubuntu is, in my opinion as a beginner, the initial setup of the box that you are using, which in many cases can be very painful (Kinda like a natural birth after hemorrhoid surgery). 
For example, as of now, I have at home three computers: My desktop and my wife's laptop (Dell Inspiron 1501), both running Kubuntu 9.04, and an Asus Eee which currently runs Ubuntu Netbook Remix. On one hand, I understand the frustration of a beginner user running Ubuntu. For example, here's a list of problems that require(d) fixing at one time or another during the past three weeks when I switched to Kubuntu and when I installed the UNR:

Laptop: 

- Cannot connect to wireless router if the router doesn't broadcast the SSID.
- After every restart I need to type in the network passkey and eventually I got like 7 connections in the network manager, with the same name (With the router broadcasting the SSID this time). Then, imagine that the passkey is some 20 characters long, with caps and symbols, and imagine trying to coach you wife over the phone on how to do this. 
- The internet connection was extremely laggy. Thought it was IPv6, but eventually figured out that one of my provider's DNS servers has been down for some time. If I edit /etc/resolv.conf to disable it, after every restart the configuration resets itself, even if I use chmod 000 on it. Solved it by using manual DNS in network management. Which only works on the laptop until I need to re-setup the connection (see previous bullet).
- The bottom panel simply disappeared. It required deleting the plasma profile to reset it to original and customize the desktop all over again. Which had to be done when I got home (major matrimonial disturbance :) )
- Firefox requiring frequent restarts (the video window is just greyed out and won't play) I know it's not Ubunutu's fault, but I can't help being pissed. Plus, the amount of memory FF is using keeps growing, and growing, and growing... until you need to kill the beast. 

Desktop:
The desktop runs pretty much smooth. Except for the fact that if I open a movie and leave it on pause and try to play music in Amarok, when it says f*&^ off ALSA, I'm using pulse audio. If it's the other way around, I have to close Amarok to be able to watch a movie.

The Eee on the other hand takes the cake. 
I've tried Ubuntu-eee, Xubuntu, eeeUbuntu and finally settled for UNR. 
It took me two days (or about 6-7 hours of reading, downloading, experimenting, redoing,) to set up the functionality of the custom buttons (CPU Scaling, BT and Wi-Fi on and off - the Wifi button still isn't working properly, Cpu Fan, and the lot), and for the past 4 (four) days, I'm trying to make a blasted BT GPS device (Nokia LD-3W) to work with the notebook (I'm still at the point of understanding what is the difference between bluez, bluetooth and bluesman and why different tools for interrogating the device yield results that vary widely (hcitool, hidd, smptool and the lot). 
Did I mention that the gpsdrive application does not fit the screen (In fullscreen it's a full one inch wider), that during the installation of xubuntu the install manager did not fit the screen and I had to navigate blind or that all the youtube videos are choppy and unintelligible.
Oh... and the process of creating a full disk encryption.... has in my lame, noobish, beginner opinion more to do with magic than with computers :)

For now this is it :) I think it's a shame that it's the little things that leave me with a significant amount of frustration towards using Linux / Ubuntu. This is mainly because the information is scattered, contradictory, not vetted well enough and... did I say scattered? I am well aware of the benefits of using Linux, I am taking as much advantage as I can of them, but I find hard dealing with the fact that the little things take so much time to solve. 
As of now, I am planning to dedicate myself to putting what little experience I have in writing what I've learned (when trying to solve the problems I've encountered) so that the path for those who are confronted with the same issues, is shorter and less difficult. 

Thanks for reading this rant, and I deeply appreciate any feedback, good or bad.

---

### Post by ukripper on 2009-05-21
I've never had these many problems with ubuntu or any other linux distro. I might be the lucky one.

---

### Post by lancest on 2009-05-22
No problems at all here on 3 notebooks. Wireless works without a hitch.

---

### Post by Peter09 on 2009-05-22
I have three notebooks - 2 work OK, one is a problem. Its intermittent, sometimes it will connect sometimes not -  I keep an external USB device ready just in case. Had this problem on it since Intrepid, now on Karmic.

You have only to look in these forums to see that wireless connectivity is still a problem. Its also the case the often the problem is not with the driver but the supporting apps. 

There is a current problems with DHCP and Network Manager for some users.

---

### Post by lancest on 2009-05-22
Place I go Vista has big problems connecting. It never works! Seen it happen at least 5 times. Good thing I always use Linux. Wireless problems happen on Windows too.

---


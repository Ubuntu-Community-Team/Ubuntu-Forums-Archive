---
title: "virtual desktop server ??? Is it the solution ???"
date: 2008-12-05
forum: Server Platforms
---

### Post by luay on 2008-12-05
I'm managing a cyber cafe including games and on-line games so I have to update each pc's every couple of days am using xp sp2 pro to my client pc's as u can imagine I remote  desktop from my server to update each pc's its not easy and take a lot of time, so I decided to build another server to control on this and to make my work more easiest, anyway after searched I found Virtual machine application under ubuntu server or virtual box or any kind of virtual (desktop utilization) so if I change my server to this specification : 
    Asus P5Q Motherboard                          
   Pentium E7200-2MB C2D Processor

   1GB Kingston DDR 2 800MHz RAM x 2 unit

   4 unit Seagate ES Hard disk 500GB – 16MB Buffer

   Cooler Master 550Watt Real Power – Power Supply

   Cooler Master Casing + 2 Fans + CDROM HOLDER

   Asus EN7200GS 256MB Display Card

   Samsung DVD-Writer

   Intel Pro 1000Mbps8390MT Network Adapter x2units


and change my switch to : 
   DGS-1224T 10/100/1000Mbps Smart Gigabit

   24-Port 10/100/1000 Switch,

   48Gbps Switching capacity,

   8K MAC Address Table


and for client change the network card to this network :
   Intel Pro 1000Mbps8390MT Network Adapter

if its possible to built that server as ubuntu server and use any kind of virtual application over Xp sp2 pro OS and send one  OS to all my pc's client and I can update that system once and it will update all clients simultaneously and I will reduce the time and cost for update also the game's license's copy windows license etc.. 
I've found many solution just like what I want, one of them ( took off all hard disk from clients and use same server as I mentioned before using linux host server and build any system and send  it to all clients), but the problem was the cost of that application and my cyber cafe cannot afford that, so I decided to build my own server .
Now I'm familiar with ubuntu server and ubuntu desktop also with virtual box and virtual machine etc.. 
and I know the deferences between them also I've found video on youtube explain same what I need but unfortunately the video not complete and here is the link for that video :
[http://www.youtube.com/watch?v=ai0ZZXTuHxM](http://www.youtube.com/watch?v=ai0ZZXTuHxM)
[http://www.youtube.com/watch?v=H2GhVmRS15U&feature=related](http://www.youtube.com/watch?v=H2GhVmRS15U&feature=related)
[http://www.youtube.com/watch?v=fXQTBY-iklw&feature=related](http://www.youtube.com/watch?v=fXQTBY-iklw&feature=related)
[http://www.youtube.com/watch?v=usRGizhC8ig&feature=related](http://www.youtube.com/watch?v=usRGizhC8ig&feature=related)
[http://www.youtube.com/watch?v=IRacpaV_2BM&feature=related](http://www.youtube.com/watch?v=IRacpaV_2BM&feature=related)

My question is does ubuntu server will solve my problem ???
If does, Is the virtual box will work or what ???
suppose I build my ubuntu server and virtual box(Xp sp2 Pro) and install all the games and on-line game how can I send that system to each client? Cause all the explaining I've found until this part okay!! I build the virtual and everything okay what will happen after that how can I send that system to Pc's?? how does it function?? also how can I control the time to each Pc's I'm using (antamedia server monitor) 
any help with be appreciated...  also if there is another suggest please tell me about it..

---

### Post by hyper_ch on 2008-12-05
I don't think ubuntu will help you solve much

(1) you still require a valid licence for all the xp installs and games and stuff (of course you can chose not to get that but that could and will put you in legal troubles)

(2) virtualization demands higher hardware to performe equally... also 3d applications may or may not work. VmWare now supports up to directx 9c - I have not tried yet.

(3) with online games that require an authentication. If you just load one virtual image to all workstatitions it will always have the same ID (if any is required) and hence only 1 may connect...

---


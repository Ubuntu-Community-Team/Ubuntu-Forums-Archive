---
title: "100mb Connections bring Gigabit connections to a crawl"
date: 2014-11-26
forum: Server Platforms
---

### Post by tp427 on 2014-11-26
I'm having a problem that is detailed below.  To simplify the issue here is a simple test the exibits the same problem. 

Setup:
Ubuntu 14.04 server (Gigabit Ethernet) ip 172.16.0.9
Ubuntu 14.04 desktop (Gigabit Ethernet) ip 172.16.0.100
Ubuntu 14.04 desktop (100mb Ethernet) ip 172.16.0.101
All three are connected to a Gigabit Ethernet switch

Desktop 1 - Run iperf -s
Desktop 2 - Run iperf -s

In two ssh terminals
Ubuntu Server - run iperf -s 172.16.0.100 -P 20
Ubuntu Server - run iperf -s 172.16.0.101 -P 20

The expected behavior would be for the server to upload at 800+mb/s to the gigabit machine and 94+mb/s to the 100mb machine.  What happens is the server will upload at 900+mb/s until I start the upload to the 100mb machine.  Then the throughput of the gigabit machine drops to anywhere from <1mb/s to 20mb/s and the 100mb machine stays at 94mb/s.  If I add more connections to the 100mb machine, the throughput of the gigabit machine keeps dropping.

 Once the 100mb connections are cancelled, the gigabit machine downloads at the expected 900+mb/s.  I added several more gigabit machines and get the same result anytime I introduce a 100mb machine into the equation.  If I have more than one 100mb machine, all 100mb machines download at full speed, but the gigabit machines barely move. 

If I reverse the test and have the server do the downloading, I get the expected results of 800+mb/s from gigabit machine and 94+mb/s from the 100mb machine.  If the 100mb machine is on a different subnet then the gigabit machine then everything works at full speed in both directions.

It appears that the server uploading files (or iperf test) to mixed 100mb and gigabit machines is the problem, but I think I must be missing something.  This is a major problem when the server is acting as a router because the same thing happens (see below).  I did some other tests and if the 100mb machines have to write the download to disk, as expected the throughput drops to around 60mb/s (due to slow hdd), but the gigabit machines then download at full speed.  So I'm thinking it has something to do with saturating the 100mb machine brings the throughput of the whole network down.  

Any ideas?
_____________________________________________________________________________________
I've got a networking/server problem that I am having trouble figuring  out. I use this setup for testing. At first I thought it was a routing  problem so I got rid of the router. Here's the setup:

Ubuntu 14.04 server
Gigabit Switch (default settings)
3 Ubuntu desktops (2 with gigabit ethernet and 1 with 100mb Ethernet)

The server is set up as a standard install with apache2. I have a 1gb  file sitting on it and I download it from the other computers via wget.  Everything is on the same subnet with no router involved. I download the  1gb file from the two gigabit computers and the throughput is over  400mb/s each, which is fine. Then I start the download from the 100mb  computer and rather than getting 300+mb/s on the gigabit computers and  around 94mb/s on the 100mb computer, all three drop to less than 100mb/s  for a total through put of less than 300mb/s. Doing the same test but  using two servers and isolating the 100mb and gigabit machine so they  don't download from the same server, it works as expected and I get  800+mb/s and 94mb/s.

Occasionally, I can get all three to download at full speed (2 gigabit  computers at over 400mb/s and the 100mb at around 94mb/s) but if I then  add a few more connections from the 100mb machine then it will drop all  three to below 100mb every time. Most of the time the 100mb computer  gets 94mb and the others drop to 10mb/s-20mb/s.  All ports on computers  and switch light up the appropriate color (green for gigabit and yellow  for 100mb).  Also, simply starting 10-15 wget downloads on the 100mb  machine and then starting a few on one of the gb machines will cause the  gb machine to download at 15-20mb/s and the 100mb machine at 94mb.  As  soon as I cancel the 100mb machines connections, the gb machines jump  back to where they should be, 400mb/s with two going and 950mb/s with  one going.

I tried using two servers on different a subnet then the computers doing  the download and having an Ubunutu router do the routing.  I had the  two gigabit computers connect to the one gigabit server and the 100mb  computer connect to the other one gigabit server and had the same  problem.  Unless I missed something, I believe I tried everything I can  think of to rule out hardware as the problem.  The only common element  is Ubuntu server/desktop on every machine. So the traffic passing  through an Ubuntu router has the same problem as an Ubuntu server that  is simply serving up files.

The same problem persists in simply setting up iperf on two servers on  different subnet.  If I try downloading to two computers on the lan from  the wan with iperf and 1 connection to each, I get around 500mb/s and  91mb/s on the gigabit machine and 100mb machine respectively.  If I then  run iperf but use around 15 or more connection on the 100mb machine,  the throughput drops to 94mb/s on the 100mb machine and 1mb/s - 10mb/s  on the gigabit machine.  Running iperf in the opposite direction and  uploading files from the lan to the wan, it works as expected and I get  800mb/s and 94 mb/s.

I have tried the following to rule out sources of the problem:

*tried using a BSD router and a Ubuntu linux router
*Swapped out server for another server running same OS (tried apache2 and lighttpd on both)
*Swapped out switch three times (Netgear gs748t, dell powerconnect 2716,  and a cheap netgear wnr3500l router, but only using the switch ports,  no routing  
*Tried multiple combinations of 8 different computers (all running  Ubuntu 14.04) half have gigabit Ethernet and the other half have 100mb  
*tried using ssh for the downloads  
*tried using scp for the downloads  
*tried different sized files for downloads (1MB, 12MB 50MB, etc)  

Any help would be greatly appreciated.

---


---
title: "Snort protecting range of IPs"
date: 2010-09-11
forum: Security
---

### Post by noway2 on 2010-09-11
I have been using snort for little more than a year now and would like to upgrade things to better protect my expanding network.  I currently have a range of public IP addresses running two servers on two separate IP addresses in my range.  

I am running snort on one of the servers.  Both servers are connected to the modem's bridge, currently no router in between and should be seeing all network traffic.  I have a router on a third IP that is the gateway to the "home" network and would like to protect this too.  I have been reading up on the HOME_NET variable and IP range definitions and it looks like if I specify the range with the CIDR mask that snort should be monitoring the entire network range.

When I attempt to test this feature by running either a port scan or nikto against my servers it will alert against the machine (IP) that is running snort, but not the other IPs in the range.

I currently have HOME_NET set to my range (base network IP/mask) and EXTERNAL_NET set to !HOME_NET.  Should snort be picking up the IP range and if so what am I getting wrong in the configuration?

---

### Post by noway2 on 2010-09-11
I had a bit of inspiration an used TCPDUMP to watch for packets on one server while running NMAP on the other.  It appears that only the device being addresses is seeing any traffic.  This says that either the Ethernet card can't enter promiscuous mode or the cable modem has a switching device on its output rather than a simple bridge.

Does anyone have any ideas or suggestions or will I have to run snort on both servers.  If I do this, I think I should still be able to log all the data into one MySQL database and monitor it in one location.

---

### Post by bodhi.zazen on 2010-09-12
I can not tell from your post, but you need to put snort in a location it can listen to all servers. This depends on your network / subnets and if you are using a switch (as oposed to a hub). Some switches have monitoring ports.

---

### Post by noway2 on 2010-09-12
Thank you for the response.  Sorry for being unclear, the situation was a little unclear to me too.  I am using a cable modem for my ISP service.  It is "business" class service and I have a /29 public IP subnet.  The cable modem has 4 Ethernet jacks on the back of it and I assumed that they would act as a basic hub and all traffic would repeat on each of those ports.  I was reading that a lot of cable modems with multiple outputs provide switch function on the outputs so that the connections will effectively be point-point.  This makes sense in that it would reduce the collision rate if you run multiple subnets.  I don't believe it has any form of monitoring port.

Currently my network is set up to use three of the IPs.  I have two public servers, one for a home based business and one as a personal project and business backup.  I then used a third one for the home "lan" which is behind a router.  The servers are dual homed in that they use the public interface as the gateway and have a private LAN connection for administration.  This way I can keep critical applications like phpmyadmin on the LAN interface only, but can still back-door into them via SSH.

Ideally, I would like to run snort on one of the servers and run two instances one on the LAN net and one on the public block.  In order to do this, the interface would need to see all of the traffic, as you pointed out.  Currently it doesn't and I suspect that this is because the modem is acting as a switch.

I think I am going to have to reconfigure the network physical arrangement somehow, but I am not entirely certain how I can create a node that will see all of the traffic.  Perhaps I could put a switch on th output of the modem and create a VLAN that has the entire /29 block and connect one of the servers to that as a stealth port?  I have a Cisco Catalyst 2950 switch but I am still a novice at IOS and it would take me a while to learn how to configure it.  I also have an old repeater hub that might do the trick, but I almost hate to use it.  

Ultimately, the trick is to get all of the traffic on one wire for the entire IP range which is kind of anti what most people want to do with switching.

---

### Post by bodhi.zazen on 2010-09-12
You may need to deploy snort at several locations and log to a central server or configure a box between your internet connection and first router. Perhaps a switch with a monitoring port.

Your system sounds complex.

---

### Post by OpSecShellshock on 2010-09-12
Yeah, I was just going to suggest the same. You can deploy multiple sensors and have them send events to a central server where your viewing console is hosted. If you've got a hardware firewall or two between the internet and your devices, you'll probably be better served by putting the sensor on the LAN side of the firewall, otherwise you're going to generate events for traffic that's not actually getting to your devices (and as such creating stress/wasting time investigating non-threatening traffic).

In order to be processed, all traffic is going to have to go through a sensor at some point prior to getting where it needs to go. Unfortunately, that's the best I can offer since my professional experience with Snort has all been on the incident handling side, so I've never been privy to the specifics of architecture and deployment.

---

### Post by noway2 on 2010-09-15
Sorry for the delay in responding, I have been a little short on free time the last few days.

Bodhi, yeah it has become a bit of a Frankenstein of a setup.  My wife wanted to start a small on-line business and I made setting up and running a server my hobby.  I got lucky when a local data center went out of business and gave away some equipment and I also found a source of refurbished commercial grade equipment.  

On the weekend, I decided to try and learn enough IOS to set up the Cisco Catalyst switch.  It turns out that it has a really nice feature in that you can set a port as what is called a SPAN port, or monitoring port.  You can assign any port of your choice to mirror either the inbound, outbound, or both traffic from any other port or range of ports.  The monitor port will then copy this data to that port without interfering with the data stream.  I then added a $15 NIC card to the computer and defaulted it to non-addressed but active in promiscuous mode and told Snort to monitor that card.

After giving the logs a little time to collect, I noticed that it is successfully monitoring traffic for all of the IP blocks. I have even been able to tell that my wife picked up a tracking cookie and was using the Xbox yesterday as well as picking up that someone was running a couple PING variants against both machines.

I had been using an older version of snort that had gone EOL on the rules so I took this opportunity to upgrade snort.  I had to give it some time to see what kind of alerts I was getting and had to pare back on it a bit because I was getting alerts on timestamps and header sizes on just about every transaction.

As OpSecShellshock pointed out, it is seeing traffic and making alerts on all of the traffic and that it would be less noisy, and possibly more effective to have it scan based on what makes it through the fire wall instead of at the input.  I will either need to get a hardware based firewall and just open the ports for the servers or run Snort on both and use a common monitoring.

---

### Post by bodhi.zazen on 2010-09-15
Perfect. You may be able to change the location of the cisco switch, put it after your router / firewall rather then in front.

---


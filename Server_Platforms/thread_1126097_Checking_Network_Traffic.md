---
title: "Checking Network Traffic"
date: 2009-04-15
forum: Server Platforms
---

### Post by spynappels on 2009-04-15
Hi Guys,

  I am using Ubuntu Servers to host a webapp (LAMP setup) and I have a problem with one specific server. It seems to crash the firewall at intervals, and it seems to do this by generating a lot of traffic, which overloads the f/w. All internet connectivity on the whole network is then lost until that server is rebooted.

  I have disabled hamachi as this may have been the problem partially, didn't play nice with Samba and network master browser, but yesterday apparently it was generating a large amount of traffic so that the router was running at 98%CPU, which again stopped when the server was rebooted.

  What I don't get is why so much traffic is being generated, at times when this happens there may not even be external access, only local clients may be connected.

  I was looking at using tcpdump to check what the traffic actually is, but I have one or two questions. Firstly, how much of the system resources does it use? Will it noticeably slow the server down? Secondly, what is the syntax to run tcpdump continuously for say a week and dump the results into txt files of say 1 MB each, and how do I specify the names of the text file? The man pages are not terribly helpful on this score.

  I appreciate any help you can give me.

  Regards,
         Stefan.

---

### Post by ikonia on 2009-04-15
this may sound silly - but what makes you think it's the physical volume of the traffic that's causing the problem

1.) setup sar for overall system monitoring

2.) review your logs - see if anything else is causing load that can drop a box eg: I've just had two boxes that where under ssh attack look for other options

3.) look at tools like ntop to monitor the traffic on your box, and as you say tcpdump, I advise you to monitor tcpdump real time rather than log to a file - as it will log a LOT of data on a busy box which can put io load on the box (see point 1 about monitoring the boxes overall workings).

4.) look again at your firewall rules, make sure there is not a silly rule in there that's causing you the issue, eg: put's a specific range in a routing loop

5.) you mention your running things like samba - look at the application log files, it's quite possible a non network issue is dropping your box

6.) look at the network card / switch configuration, ethtool/mii-tool etc etc make sure your card is not flapping or overloaded.

---

### Post by spynappels on 2009-04-15
Thanks for your answer. The problem is not that the box is dropping, it is the Corporate Firewall that is crashing (I'm told) and I have no access to this firewall. Neither is it set up to log anything (?) but as it is outside my control, I have no way of checking it. I've just been told that my server is generating a huge amount of traffic, and I want to check if there is really so much traffic being sent out on my NIC. If there is not, I want to see what is going out so I can tell them to take a running jump next time they tell me I'm causing problems. The server runs as normal albeit possibly a bit more slowly at times.

---

### Post by ikonia on 2009-04-15
if there is no logging on their firewall how can they tell your machine is hitting it that hard ?

if there is no logging on the network how can they tell your machine is causing a lot of traffic.

set your iptables to log with something like ulog if your machine has the power for it, so you can see better what's going on over a long period of time.

---

### Post by spynappels on 2009-04-15
You would probably not believe it, but a 3rd party consultant is called to look at the problem, he logs in to the firewall and sees what is happening and rings me and tells me my server is generating traffic. I can't call him a bluffer without having some evidence of my own to back up what I say.

 I just want to be able to call up a log and see what is going in and out on the NIC at a given time. I have loads of storage, so fairly verbose logging is fine.

 If I can do this using IP tables, great, but I will need a walkthrough or something to help me. Else TCPdump will probably do what I want, but I cannot afford for server performance to be compromised too much.

---

### Post by ikonia on 2009-04-15
tcpdump and snoop will be fine, they won't cause that much of a big deal on your performance.

If the guy logging in is telling you your box is causing a lot of traffic, no problem, the questions are

1.) how do you know this - what leads you to think this ?
2.) is it too much traffic for the firewall ? if so what sort of levels are we talking about
3.) are they coming from one specific source in the headers, or all over the place (obviously they come from your server, but through your server, not from it)
4.) what type of data is being sent ?

if he is saying "it's your box" it should be easy for him to answer these 4 questions and give you more info to look at your box in better detail.

---

### Post by wirelessmonkey on 2009-04-15
tcpdump, wireshark, and iftop will be your best friends.

---


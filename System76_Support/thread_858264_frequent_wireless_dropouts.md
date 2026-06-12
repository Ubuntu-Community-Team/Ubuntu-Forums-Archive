---
title: "frequent wireless dropouts"
date: 2008-07-13
forum: System76 Support
---

### Post by hodad on 2008-07-13
Tom,

Since I upgraded to 8.04 about 2 months ago, I have been experiencing internet dropouts every couple of minutes.  I have to power down/up the wireless router to get back up.

Had a Linksys Wireless G for about a year with only occasional problems.   After noticing the problem after the upgrade, I went to Office Depot for something, and mentioned the problem to their computer guy. He said that  he'd heard about people having the same problem with Linksys/Linux, and my particular ISP.  He suggested upgrading to a D-Link  DIR-615 wireless. Didn't help.

The problem is annoying, especially when I try and attend a monthly webinar that I need to listen in on.  I dropped out ten times during the hour long seminar (would have been even more often, but I spent a good part of that hour in the "reboot" process).

Have tried keeping Ubuntu updated, and have gone thru all of the relevant settings in the wireless router itself. All of the network settings in "Networking Tools" seem to be right. I also got the ISP (Sopris Surfers) to test my link end-to-end, right up to my wireless router; tested strong.

After researching other postings in the Forums, I've seen a couple of other people with the same problem, though no suggestions on what to do.

Could there be another networking driver or something that I could try installing to try and solve this?  Is there a hidden network setting I can access? Seems to be a problem with 8.04, since I was OK before upgrade.

I have a Pangolin Value, mdl FL91, running 64 bit 8.04.

Thanks in advance for your help.

---

### Post by thomasaaron on 2008-07-14
Please post the output of this command...
```
lspci | grep -i wireless
```
...so I can see which wireless card you have.

Also, after the next disconnect, immediately run this command.
```

cat /var/log/daemon.log > ~/Desktop/daemon.txt
```

(It will create a text file on your desktop. You can just attach the text file to this thread.)

---

### Post by Pethegreat on 2008-07-14
I will also be looking for an answear to the same problem. Before I reformatted and re-installed ubuntu I had no problem with wireless. Now I am getting a similar problem that the OP is having. I had an app on the old install(it was on the laptop when I got it) that allowed me to see wireless connection and connect to them, but that feature has vanished.

---

### Post by hodad on 2008-07-17
Tom,
Sorry about delay, wanted to try a few more ideas on how to solve it.

I noticed that the dropouts are frequent when using "OnSync" application, which the webinar operates under.  I just tried the webinar link this morning again, and it dropped out in 2 minutes.  However, I immediately was able to use Google to search for OnSync support w/o rebooting the wireless router; which tells me its a problem with OnSync.  

I left them a message on their support line.

Nonetheless, I logged some of the stuff you asked me to.   Got no messages from the "daemon" command, as you can see.

Thanks for the help.  I guess I'll see what (if anything) they can tell me about how to solve the problem.  Let me know if you are interested in their answer.


********************

*-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               

       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:16:d4:de:db:3c 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: wmaster0 
       version: 02 
       serial: 00:1c:bf:19:cf:42 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.199 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g 


*-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:16:d4:de:db:3c 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: wmaster0 
       version: 02 
       serial: 00:1c:bf:19:cf:42 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.199 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g 

************************

*-laptop:~$ sudo pccardctl ident 
sudo: unable to resolve host *-laptop 
*-laptop:~$ 

cat /var/log/daemon.log > ~/Desktop/daemon.txt
*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt

*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt

*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt

*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt

*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt

*-laptop:~$ 

*-laptop:~$ sudo cat /var/log/daemon.log > ~/Desktop/daemon.txt

sudo: unable to resolve host *-laptop

[sudo] password for *: 

*-laptop:~$

---

### Post by osx424242 on 2008-07-21
> **hodad said:**
> 
*-laptop:~$


Is "*-laptop" really the name of your computer, or just something you inserted for this forum?  If it is really your computer's name, I'd recommend changing it (to only include alphanumeric characters) and trying again.  Using special characters like '*' and '-' just seems like _asking_ for trouble :)  Especially the '*', who knows what that will expand to if a program uses it for any sort of filename!

> **hodad said:**
> 
*-laptop:~$ cat /var/log/daemon.log > ~/Desktop/daemon.txt


On the off chance you see this before Thomas Aaron replies: this command won't return anything in your Terminal window.  What it will do, is create a file called "daemon.txt" on your Desktop.  You should run this command again the next time your network drops out; after you re-connect, reply to this thread and attach the file (start a new reply, scroll down, click "Manage Attachments," click the first "Browse," go to your Desktop folder, and select "daemon.txt") daemon.txt to this thread.
[You could also try attaching the 'daemon.txt' that should already be on your Desktop, rather than waiting until your next Internet dropout]

---

### Post by darkknight045 on 2008-07-22
I'm sure the * is just to hide his user name.  During a standard ubuntu install when you enter your name it will automatically generate a name for the computer ie:

Name:John Smith
Computer Name: john-laptop or john-desktop

---

### Post by thomasaaron on 2008-07-22
> "OnSync" application, which the webinar operates under. I just tried the webinar link this morning again, and it dropped out in 2 minutes. However, I immediately was able to use Google to search for OnSync support w/o rebooting the wireless router; which tells me its a problem with OnSync.


Actually, I was kind of considering the above quote as an affirmation that the issue was solved. If onsync is the problem, it should probably be reported to them.

---

### Post by thinman1189 on 2008-07-23
I just got a new serp and I was just on digg and pidgin when all of a sudden it was trying to connect to my network, then failed and couldn't see any networks. Took a restart to work again. Weird thing was, when it was still connecting I couldn't digg up anything but I could go to new sites and refresh, but pidgin wouldn't work. Not sure if it's related or not, if not and it happens again I'll start a new thread.

I had taken a ufw update about 20mins before the problems occurred, but last I checked ufw isn't enabled.

---


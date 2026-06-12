---
title: "Can't get Internet in Windows XP in VirtualBox"
date: 2019-07-08
forum: Virtualisation
---

### Post by dora5 on 2019-07-08
I tried to post this in VirtualBox's forum but got some weird error message about urls (the post doesn't have any).  I have attached my VirtualBox log files, though possibly only Oracle would make any use of them - but they're not accepting my post today.   No, I really want the Internet in VirtualBox next week!   

I am running Virtualbox 6.0 on Ubuntu 18.04, and installed Windows XP service pack 2 from my install CD.   I have googled it to death and tried many instructions and suggestions but can't connect to the Internet.   I tried it in Virtual Box 5 and can't get it to work there either.   I have uninstalled and reinstalled a number of times, making sure to completely remove the virtual drive and all VirtualBox files.   


Internet works perfectly in Ubuntu.


I installed Guest Additions.   


I changed the driver to Intel PRO/1000 MT Desktop.  I shared the downloads folder with VirtualBox, and I installed the driver.   


I turned off the Windows XP firewall.  






I have tried both Nat and Bridged Adapter.


In Bridged Adapter I don't get the options I'm supposed to get; the only name available to me is eno1 and I can't change it, and nothing else appears in the dropdown box.   That has not changed across multiple uninstalls and reinstalls and virtualbox 5.2 and 6.0.   Google won't tell me what the bleep eno1 even means.


In Bridged adapter I set Promiscuous mode to allow all.


In settings, Network, I have cable connected and enable network adapter checked.


I tried fooling with the MAC address in virtualbox settings, network, and have used the setting that is there, the one I got when it reset, and the MAC address that corresponds with my computer.   


I have not seen a set of instructions that tell how to set up the internet connection inside of Windows XP, though some instructions say to set up Internet connection or network inside of Windows XP.   I've tried running through the basic Internet setup, choosing connect directly to Internet.   When I tried to connect through a network, next it wanted to know what network.    Under Internet Gateway I see Internet Connection  Connected Internet Connection, and under LAN or High-Speed Internet I see a single icon with Local Area Connection 2 Connected  Intel(R) PRO/1000 MT Deskto...    One set of instructions said I should see several things but the image that shows what I should see was missing.   


When I double click on Properities on the Local area connection icon, it says it's status is connected.  It is set to obtain an IP address and DNS server address automatically.   And doesn't show any specific IP address.   


It seems to be sending and receiving packets, though, so I opened a command window inside of Windows XP VM, and pinged google.com   It successfully pings Google.com.   


Pinging google.com [172.217.2.238] with 32 bytes of data;   TTL is 54 all four times.  cip


So I tried ipconfig


Connection to austin.rr.com which is my ISP


IP address 192.168.0.9
(Ip address of my computer is 192.168.0.2 and the modem is 192.168.0.1)
subnet mask what it should be
Default gateway 192.168.0.1


So the specific problems are:  Internet Explorer can't reach the Internet, and I can't activate Windows on account of allegedly no Internet connection.   


Mind, I've only rebooted that VM umpteen times.    When I have the same problem in Windows 7, not in VirtualBox, where I can obviously connect to the Internet but my browsers can't, rebooting solves the problem.


I see that you want my log files.   There are no instructions on where to find the log files, not even on your own web site's page that describes the log files.   Therefore I copied and pasted several log files into a text file and then zipped it, and have attached it.  Or, I tried to attach it.  It says I have to be a member for a day before I can "post urls".    !!!!!!!!!!!!!!!!! I don't think so!    But if you'd like me to copy and paste anything in particular from the log file...

---

### Post by dora5 on 2019-07-08
This appears to be solved.  A discussion elsewhere claimed that if one can ping, one has internet, which in my experience isn't necessarily true.  But the article claimed that Internet Explorer in Windows XP can't access modern web pages.  Not even google.com?   I installed a very old version of 32 bit Chrome and connected with the Internet without a problem.  I had to whatever my edition of Windows by phone, however.  I don't know if that's ability to connect with the internet or the web address has changed over the years.

---

### Post by uRock on 2019-07-08
I used to work product support for a major company. We were flooded with calls the day they rolled out their new website. I pointed quite a few people towards Ubuntu during that period. Management wasn't happy about me recommending a "foreign" operating system.

---


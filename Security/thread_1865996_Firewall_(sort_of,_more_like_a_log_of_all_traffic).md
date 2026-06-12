---
title: "Firewall (sort of, more like a log of all traffic)"
date: 2011-10-20
forum: Security
---

### Post by pizza-is-good on 2011-10-20
I have Firestarter installed, great for using a network that you don't trust.

What I am looking for is an application that will monitor all traffic in and out of the computer, give me details as to what it is about, and allow me to block them. 

I know something like this exists, but my searches haven't given me good results.

Oh, and if it works on Windows as well as in Ubuntu that is a plus.

Thanks!

~pizza

---

### Post by Dangertux on 2011-10-21
> **pizza-is-good said:**
> I have Firestarter installed, great for using a network that you don't trust.

What I am looking for is an application that will monitor all traffic in and out of the computer, give me details as to what it is about, and allow me to block them. 

I know something like this exists, but my searches haven't given me good results.

Oh, and if it works on Windows as well as in Ubuntu that is a plus.

Thanks!

~pizza

As far as monitoring traffic  you have a few options on Linux. Wireshark or tcpdump to monitor your network traffic though it's not going to hold your hand you will need to be able to analyze the packets yourself. It also won't do anything about anything by itself.

If you want something that analyzes and intelligently blocks traffic you're getting into an IPS in which case I would look into Snort Inline mode. Which will protect both Linux and windows machines.

Hope that helps.

---

### Post by bodhi.zazen on 2011-10-21
The advantage of snort, it will filter through all the thousands of packets you receive and alert you to those you should pay attention to.

tcpdump and wireshark will capture them all, but you will then need to search trough them.

---

### Post by SparTacux on 2011-10-22
The problem with Firestarter is that it only logs blocked traffic plus you have to have it running in sudo mode to view the details in the events column. It does write to your log files which can be viewed with the log file viewer but tends to write the blocked traffic details to quite a number of different log files. There are ways to configure the output from firestarter to write logs to a unique Firestarter.log file  to make things clearer but it still only writes the blocked traffic to such a file.

A better solution is to use GUFW instead and set the GUFW preferences for high logging. This will log all traffic in and out of your computer to the UFW.log file which again can be viewed in Log File Viewer. You will see traffic that has been blocked or allowed to pass through your Firewall.
 
If your modem supports SYSLOG forwarding of it's Firewall output ( if it has a Firewall  ) you can also pick up the SYSLOG data from a computer on your network and see all traffic in and out of your modem to the internet itself. 

Another handly tool is to load the system monitor panel app and configure it to monitor network activity on your computer. Right click on the panel and select add to panel and then select system monitor. Then configure it to monitor network activity using red lines for outgoing traffic and green lines for incoming traffic. 

If you download nmap onto another computer on your network then probe the ports on your computer from that you will see the UFW logs start to get very busy blocking incoming traffic from the computer with nmap installed on it. Your system monitor panel app will also go haywire with incoming activity.

Another good one is to type netstat -ntuc in the terminal. This will give you live feedback on connections out of your computer.

That should be good for starters.

---

### Post by The Cog on 2011-10-22
If you just want to get a feel for what traffic is going on, you might like etherape. It gives a real-time picture of your node and all the other nodes it's conversing with, using coloured lines with a thichness that changes as the traffic level changes. No logging though - just a real-time overview. It really depends on how much detail you want to wade through.

---


---
title: "Unwanted TCP FIN scans of Unknown Cause"
date: 2012-10-26
forum: Security
---

### Post by 151rby on 2012-10-26
I  have a System76 Pangolin Performance (Panp8), and I'm running Ubuntu 11.04, 64-bit.

My computer has apparently been the target of incoming TCP-FIN scans, and also did at least one outbound scan. My network administrator banned my computer from the wifi network because of it. He says my computer's the only one on the network exhibiting the behavior. I really want to figure out the cause, but I have a huge amount of homework right now, and at this very moment the most important thing is for me to just prevent it from happening because I need the internet to do my homework. I have Uncomplicated Firewall, but I don't really know how it works; is there a way that I can use it to block or prevent such scans? Is there something I can do with my system or network settings to make it stop? I will be extremely grateful for any help!

Now, if you know a way I can just make the scans stop regardless of their cause, then please feel free to answer without bothering to read the rest of this post. But maybe more details are necessary, so here is the firewall log report the admin sent me: 

10/25/2012 10:41:11  **TCP FIN Scan** 74.114.28.200, 80->> 192.168.2.37, 59562 (from WAN Inbound)   Meebo
10/25/2012 10:41:11  **TCP FIN Scan** 207.200.81.7, 80->> 192.168.2.37, 40283 (from WAN Inbound)   Netscape Communications Corp
10/25/2012 10:41:11  **TCP FIN Scan** 74.125.225.69, 80->> 192.168.2.37, 51341 (from WAN Inbound)   Google
10/25/2012 10:41:11  **TCP FIN Scan** 174.132.95.10, 80->> 192.168.2.37, 46657 (from WAN Inbound)   Theplanet.com internet services
10/25/2012 10:41:11  **TCP FIN Scan** 64.236.85.82, 80->> 192.168.2.37, 41429 (from WAN Inbound)   AOL transit data network
10/25/2012 10:41:11  **TCP FIN Scan** 23.21.54.230, 80->> 192.168.2.37, 40730 (from WAN Inbound)   Amazon
10/25/2012 10:41:11  **TCP FIN Scan** 67.132.183.64, 80->> 192.168.2.37, 57262 (from WAN Inbound)   Akamai technologies
10/25/2012 10:41:11  **TCP FIN Scan** 199.117.103.72, 80->> 192.168.2.37, 39606 (from WAN Inbound)   Akamai technologies
10/25/2012 10:36:21  **TCP FIN Scan** 208.81.191.110, 80->> 192.168.2.37, 54965 (from WAN Inbound)   Meebo
10/25/2012 10:36:21  **TCP FIN Scan** 74.125.225.176, 80->> 192.168.2.37, 35835 (from WAN Inbound)   Google
10/25/2012 10:36:21  **TCP FIN Scan** 74.125.225.89, 80->> 192.168.2.37, 41008 (from WAN Inbound)   Google
10/25/2012 10:36:21  **TCP FIN Scan** 54.243.110.233, 80->> 192.168.2.37, 39518 (from WAN Inbound)   Amazon.com
10/25/2012 10:36:21  **TCP FIN Scan** 199.38.164.155, 80->> 192.168.2.37, 34961 (from WAN Inbound)   X Plus One
10/25/2012 10:36:21  **TCP FIN Scan** 208.81.191.113, 80->> 192.168.2.37, 51972 (from WAN Inbound)   Meebo
10/25/2012 10:21:41  **TCP FIN Scan** 208.81.191.110, 80->> 192.168.2.37, 54295 (from WAN Inbound)   Meebo
10/25/2012 10:21:41  **TCP FIN Scan** 69.171.234.21, 80->> 192.168.2.37, 44825 (from WAN Inbound)   Facebook (I don't even have a Facebook account)
10/25/2012 10:21:41  **TCP FIN Scan** 67.132.183.9, 80->> 192.168.2.37, 35936 (from WAN Inbound)   Akamai Technologies
10/25/2012 10:21:41  **TCP FIN Scan** 167.8.226.13, 80->> 192.168.2.37, 38467 (from WAN Inbound)   Gannett Co Inc
10/25/2012 10:21:41  **TCP FIN Scan** 168.143.84.74, 80->> 192.168.2.37, 44154 (from WAN Inbound)   NTT America Inc
10/25/2012 10:21:41  **TCP FIN Scan** 64.236.85.88, 80->> 192.168.2.37, 48464 (from WAN Inbound)   AOL Transit Data Network
10/25/2012 10:21:41  **TCP FIN Scan** 75.98.35.20, 80->> 192.168.2.37, 44010 (from WAN Inbound)   Legolas Media
10/25/2012 10:21:41  **TCP FIN Scan** 174.132.95.10, 80->> 192.168.2.37, 45758 (from WAN Inbound)   Theplanet.com
10/25/2012 10:21:41  **TCP FIN Scan** 54.243.166.54, 80->> 192.168.2.37, 59490 (from WAN Inbound)   Amazon.com
10/25/2012 10:21:41  **TCP FIN Scan** 69.172.216.55, 80->> 192.168.2.37, 45381 (from WAN Inbound)   Saferoute Incorporated
10/25/2012 10:21:41  **TCP FIN Scan** 74.125.225.89, 80->> 192.168.2.37, 40278 (from WAN Inbound)   Google
10/25/2012 10:21:41  **TCP FIN Scan** 64.94.107.18, 80->> 192.168.2.37, 40790 (from WAN Inbound)   Intermap Network Services Corporation
10/25/2012 10:21:41  **TCP FIN Scan** 50.16.195.154, 80->> 192.168.2.37, 36605 (from WAN Inbound)   Amazon
10/25/2012 10:21:41  **TCP FIN Scan** 74.125.225.90, 80->> 192.168.2.37, 47767 (from WAN Inbound)   Google
10/25/2012 10:21:41  **TCP FIN Scan** 67.132.183.42, 80->> 192.168.2.37, 58683 (from WAN Inbound)   Akamai Technologies
10/25/2012 10:21:41  **TCP FIN Scan** 205.217.176.11, 80->> 192.168.2.37, 57381 (from WAN Inbound)   Savvis
10/25/2012 10:21:41  **TCP FIN Scan** 208.71.123.131, 80->> 192.168.2.37, 57039 (from WAN Inbound)   24/7 Real Media
10/25/2012 10:21:41  **TCP FIN Scan** 67.132.183.65, 80->> 192.168.2.37, 50760 (from WAN Inbound)   Akamai Technologies
10/25/2012 10:21:41  **TCP FIN Scan** 67.132.30.137, 80->> 192.168.2.37, 46285 (from WAN Inbound)   Qwest Communications
10/25/2012 10:09:12  **TCP FIN Scan** 192.168.2.37, 52621->> 107.22.232.230, 80 (from WAN Outbound)Amazon

The right-hand column (Google, Meebo, etc) was added by me after I did a bunch of lookups on whois.domaintools.com. I am so confused. Why in the world am I being TCP FIN scanned from IPs owned by Google and Amazon and Meebo and various media companies? At the time it happened, I do actually think I was on a website where I was logged into Meebo and the chat bar was open; could these actually be "legitimate" harmless scans performed as part of Meebo's chat service? Another thing I noticed was that all of the scans came from a port 80, and when my computer did an outbound scan, the scan was sent to a port 80. This makes me wonder if it's just being done by one person who is spoofing various IPs, because what are the chances all those different computers would be using the same port to scan me/get scanned by me? Or, could someone be spoofing my IP and MAC addresses on the network, and if so how could I find out?

Also, I would like to know, is there a log on my computer that I can check which will tell of any such scans that have recently occurred?

I ran chkrootkit and rkhunter, and neither detected any rootkits, but chkrootkit said: 
The following suspicious files and directories were found:  
/usr/lib/jvm/.java-1.6.0-openjdk.jinfo /usr/lib/pymodules/python2.7/.path /usr/lib/firefox-addons/extensions/globalmenu@ubuntu.com/chrome/.mkdir.done

And rkhunter gave "warnings" for the following:
/usr/bin/mail
/usr/bin/bsd-mailx

Rkhunter also said that "Checking if syslog remote logging is allowed" was "Not Allowed". I have no idea whether any of this is relevant to my problem. Yes, go ahead and laugh at my ignorance.

---

### Post by Doug S on 2012-10-27
Hi and welcome to Ubuntu forums.
It is late in my time zone, so I'll be brief. I can give further help tomorrow.
Also, this subject is fairly advanced, and this thread would be better in the "security" forum.
 
I suspect that your issue is a false positive for FIN scan.
Note that it isn't possible for those inbound packets to be destined to your computer if your computer didn't create the original outbound connection. The WiFi network router NAT table seems to be remembering the mapping. Of course, and as you mention, it could be someone on your LAN spoofing your IP address.
 
The admin says your computer is the only one showing the behaviour, but is your computer the only linux box on your LAN? I see a definate "signature" difference for partially closed TCP connections on my LAN depending on if the client is a windows box or a MAC or a linux box.
 
For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. With routers in the route it can and does result in computers and/or routers getting out of sync, where something thinks the connection is still open and something else thinking it is closed and has forgotten about it.
 
Now, how can we prove if your situation is a false positive or not? My suggestion is to politely ask your admin to allow you back on the sub net, and to continue to monitor these "FIN scan" things. If your admin is reluctant, suggest to be allowed for just enough time to gather some data. Use a packet sniffer (i.e. tcpdump or wireshark if you prefer) and log every packet coming and going from your computer. Then you can go back and correlate the Admin's file with your tcpdump file. The question being are these merely lingering packets for partially closed TCP sessions?
I would suggest to use this command:```
sudo tcpdump -n -nn -tttt -i eth1 >somefile.txt
```You will have to change eth1 to your interface. Watch the file size.
Edit: Note: be aware of, and adjust for, any clock difference between your computer and the admin's computer.

---

### Post by 151rby on 2012-10-27
> **Doug S said:**
> this subject is fairly advanced, and this thread would be better in the "security" forum. Oops. I assumed it belonged in this section because, well, I'm an absolute beginner :) Is there some way I can move it?
 
> **Doug S said:**
> Now, how can we prove if your situation is a false positive or not? My suggestion is to politely ask your admin to allow you back on the sub net, and to continue to monitor these "FIN scan" things. If your admin is reluctant, suggest to be allowed for just enough time to gather some data. Use a packet sniffer (i.e. tcpdump or wireshark if you prefer) and log every packet coming and going from your computer. Then you can go back and correlate the Admin's file with your tcpdump file. The question being are these merely lingering packets for partially closed TCP sessions?
I would suggest to use this command:```
sudo tcpdump -n -nn -tttt -i eth1 >somefile.txt
```You will have to change eth1 to your interface. Watch the file size.Thank You!!! You are now my hero. Now, when it's time to turn off my computer, what command should I use to stop tcpdump? And when I turn my computer on and start tcpdump logging again, if I use the same "somefile.txt" in the command, will it overwrite the old somefile.txt, or just add to it?

---

### Post by oldos2er on 2012-10-27
Moved to Security Discussions.

---

### Post by Lars Noodén on 2012-10-27
If you want to stop tcpdump as invoked above, press ctrl-C or just turn off the computer.  

The redirect (>) will overwrite the file it is pointed at.  So if you want to save the file, use a new file name or copy the file to a backup before using the redirect again.  Or you can append to the file with >> when you start tcpdump again.  The files can be large so you might want separate files for the separate days.  

```

echo A > /tmp/x
cat /tmp/x
echo B >> /tmp/x
cat /tmp/x
echo C > /tmp/x
cat /tmp/x

```

---

### Post by Doug S on 2012-10-27
@151rby: You wouldn't have been expected to know that this thread might get better exposure to subject matter experts on the "security" forum. I was more hoping to get the attention of a helpful moderator.
 
@oldos2er: Thanks.
 
Oh, when I scroll down to check something, I see Lars answered your question, I guess I didn't refresh this page before replying. As an addition, on my network I actually use this:```
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600
```To create seperate files each 10 minutes. I cann't recall for sure, but I think some library might be needed for the cool date and time in the file name part to work. I always have the compiler (build-essentail) installed so I have the library. Then I use wireshark from another computer with a GUI to actually look at the file (I only use server editions of Ubuntu), if required.
 
For your case, I suggest to use grep to extract the parts you want / need for your correlation work. For example, say you wanted to investigate this line (I mean a similar line from when both tcpdump and your admin scan thing are both acquired at the same time):```
10/25/2012 10:36:21 **TCP FIN Scan** 208.81.191.113, 80->> 192.168.2.37, 51972 (from WAN Inbound) Meebo
```noting that there are actually a few "Meebo" sessions. Suggest this:```
grep "192\.168\.2\.37\.51972" somefile.txt | more
```or```
grep "192\.168\.2\.37\.51972" somefile.txt >m51972.txt
```and then look at m51972.txt with an editor or something. If you did this in another terminal session, you wouldn't even have to stop your tcpdump command while you do it.

---

### Post by OpSecShellshock on 2012-10-27
The external IP addresses are communicating on port 80. These are almost certainly just regular http responses, given port 80 on the external side and random high ports on yours. I really don't think you're getting scanned. Most likely it's existing http connections being closed, as described above.

As for why there are so many of them in such a short time, that's just the nature of websites these days, especially if you don't block scripts and ads. Any site that has a Facebook follow or like button will make a request to Facebook. Akamai is a very large content delivery network which serves and hosts a lot of static media content for other parties' sites. And of course you can't get away from Google no matter where you are. It's well within normal browsing session parameters to just go to one or two websites but make requests out to that many domains in such a short time.

False positives from FIN scan alerts have been a known issue with some firewalls/routers for a while now.

---

### Post by 151rby on 2012-10-27
You are all awesome! I'm 99% sure that this issue is now solved, but I won't know for sure until it happens again and the admin sends me the new firewall log. To mark it solved now would feel like tempting fate.

---

### Post by 151rby on 2012-10-29
Oh, one more little thing. When I look at the tcpdump log to find times when there were lingering packets from closed TCP sessions, what exactly will I be looking for, text-wise?

---

### Post by Doug S on 2012-10-29
You will want to follow the whole TCP session. You will want to see the initial "SYN packet from you, a SYN ACK packet back from whoever, the session guts, then there should be a FIN and a FIN-ACK. However we suspect the close sequence might have issues, you might see extra trailing packets. Somewhere in the end stuff should be packets with time stamp correlation with what your admin gives you.
Post here (edit out the meat in the middle of the session) if you have troubles, and we will help to interprete. If you edit out the middle contents, you should be able to get the posting down to very few lines, say 20 or 30.
 
While not the best example, here is an example from my network:```
Example session from WAN side:
2012-10-28 23:56:00.888728 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [[COLOR=red]S[/COLOR]], seq 2541980324, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2012-10-28 23:56:00.929348 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]S[/COLOR].], seq 3533071615, [COLOR=red]ack[/COLOR] 2541980325, win 14300, options [mss 1430,nop,nop,sackOK], length 0
2012-10-28 23:56:00.931196 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [.], ack 1, win 17160, length 0
2012-10-28 23:56:00.932499 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [P.], seq 1:416, ack 1, win 17160, length 415
2012-10-28 23:56:01.007696 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [.], ack 416, win 15008, length 0
2012-10-28 23:56:01.012072 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [.], seq 1:1431, ack 416, win 15008, length 1430
2012-10-28 23:56:01.015768 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [.], seq 1431:2861, ack 416, win 15008, length 1430
2012-10-28 23:56:01.019165 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [.], ack 2861, win 17160, length 0
2012-10-28 23:56:01.020087 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [.], seq 2861:4291, ack 416, win 15008, length 1430
2012-10-28 23:56:01.020307 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [P.], seq 4291:4488, ack 416, win 15008, length 197
2012-10-28 23:56:01.021258 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [P.], seq 4488:4834, ack 416, win 15008, length 346
2012-10-28 23:56:01.023866 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [.], ack 4488, win 17160, length 0
2012-10-28 23:56:01.213782 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [.], ack 4834, win 16814, length 0
2012-10-28 23:57:07.633842 IP 173.180.45.4.52663 > 74.125.129.95.80: Flags [[COLOR=red]R[/COLOR].], seq 416, ack 4834, win 0, length 0
2012-10-29 00:00:00.994144 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 3533076449, [COLOR=red]ack[/COLOR] 2541980740, win 15008, length 0
2012-10-29 00:00:01.371140 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:02.127023 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:03.639065 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:06.663162 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:12.711409 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:22.711640 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:32.711819 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
2012-10-29 00:00:42.712091 IP 74.125.129.95.80 > 173.180.45.4.52663: Flags [[COLOR=red]F[/COLOR].], seq 0, [COLOR=red]ack[/COLOR] 1, win 15008, length 0
Example session from LAN side:
2012-10-28 23:56:00.888713 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [S], seq 2541980324, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2012-10-28 23:56:00.929360 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [S.], seq 3533071615, ack 2541980325, win 14300, options [mss 1430,nop,nop,sackOK], length 0
2012-10-28 23:56:00.931183 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [.], ack 1, win 17160, length 0
2012-10-28 23:56:00.932484 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [P.], seq 1:416, ack 1, win 17160, length 415
2012-10-28 23:56:01.007704 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [.], ack 416, win 15008, length 0
2012-10-28 23:56:01.012087 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [.], seq 1:1431, ack 416, win 15008, length 1430
2012-10-28 23:56:01.015783 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [.], seq 1431:2861, ack 416, win 15008, length 1430
2012-10-28 23:56:01.019153 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [.], ack 2861, win 17160, length 0
2012-10-28 23:56:01.020101 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [.], seq 2861:4291, ack 416, win 15008, length 1430
2012-10-28 23:56:01.020319 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [P.], seq 4291:4488, ack 416, win 15008, length 197
2012-10-28 23:56:01.021270 IP 74.125.129.95.80 > 192.168.111.100.52663: Flags [P.], seq 4488:4834, ack 416, win 15008, length 346
2012-10-28 23:56:01.023855 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [.], ack 4488, win 17160, length 0
2012-10-28 23:56:01.213769 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [.], ack 4834, win 16814, length 0
2012-10-28 23:57:07.633834 IP 192.168.111.100.52663 > 74.125.129.95.80: Flags [R.], seq 416, ack 4834, win 0, length 0
Related Firewall log entries:
Oct 29 00:00:00 doug-64 kernel: [1082841.420960] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31594 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:01 doug-64 kernel: [1082841.797935] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31595 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:02 doug-64 kernel: [1082842.553817] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31596 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:03 doug-64 kernel: [1082844.065862] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31597 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:06 doug-64 kernel: [1082847.089958] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31598 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:12 doug-64 kernel: [1082853.138205] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31599 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:22 doug-64 kernel: [1082863.138437] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31600 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:32 doug-64 kernel: [1082873.138624] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31601 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0
Oct 29 00:00:42 doug-64 kernel: [1082883.138888] GW MAC:IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=74.125.129.95 DST=173.180.45.4 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=31602 PROTO=TCP SPT=80 DPT=52663 WINDOW=15008 RES=0x00 ACK FIN URGP=0

```The Microsoft computer at 192.168.111.100 issues a TCP RESET (MAC's tend to use FIN). The router forwards the packet and terminates the TCP session. For whatever reason, the other end continues to try to close the session for another few minutes. There ends up being 9 incoming packets that my router/firewall doesn't know how to deal with. (As a side note: The extra traffic would probably have been less if I used "REJECT" instead of "DROP" in my router / firewall rule set.)
Note that in this example, the LAN never sees the extra packets, and the first one is 2 minutes and 53 seconds later. I don't know what will happen in your case, but this could present a challenge for the correlation attempts.

---

### Post by Lars Noodén on 2012-10-29
Also, you might want to make sure that you are using NTP or OpenNTP to sync the clocks and that you are using the same time server pool as your network admin is.  If the clocks are off by even a few seconds that can make matching the logs much harder on a busy network.

---

### Post by 151rby on 2012-11-04
Alright, so now the admin is asking me how he can tell that they're false positives. I certainly don't want to have to send him log excerpts every single time some false positives happen. I'm going to suggest that he use a packet sniffer, and look at context such as the ports used and the owners of the external IP addresses. Are there any particular firewalls I could recommend that are more friendly to Linux machines? And are there any other things in general I should recommend to him?

---

### Post by Doug S on 2012-11-04
I was wondering how you were doing on this issue.
 
It should be sufficient for you to do the correlation we talked about earlier. Even if you do not get the actual extra packets at your computer, as in my example in posting #10 above, it should be good enough to prove the issue is just TCP half closed issues.
 
A root key point to make to your admin, supported by the correlation data you give, is that the admin router seems to be recalling that the so called external "FIN Scan" packets are destined for your computer. That is only possible if your computer started the connection in the first place.
 
It should also be sufficient to go through this process once only, and not have to repeat it everytime there is a false positive.

---

### Post by 151rby on 2013-02-20
This issue is solved! It's been solved for a while now, but I've just been too preoccupied with school and work and stuff. Thanks to all who helped!

---


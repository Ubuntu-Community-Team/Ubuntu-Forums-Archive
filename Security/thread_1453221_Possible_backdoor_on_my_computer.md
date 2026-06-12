---
title: "Possible backdoor on my computer"
date: 2010-04-13
forum: Security
---

### Post by jsvidyad on 2010-04-13
Hi!!

   I was looking at my firewall(firestarter) logs. It shows that a program named Master's Paradise has been trying to make connections to outside from my computer on port 3129. A google search revealed that it is a backdoor for windows machines. Why would I have something like this on my machine? Is this something I need to be worried about?? Or is some legitimate program using port 3129 and the firewall log is still showing it as Master's Paradise?

Thank you in advance for your help.

---

### Post by lisati on 2010-04-13
Unless you've done something to open up the port and have your computer react when the request comes in, and as long as the attempts are coming from the outside, you'll be safe.

You might want to have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by unspawn on 2010-04-13
Resolving ports using static port mappings like those in /etc/services may cause mismatches. If you don't run a mcrsft machine then this probably isn't Master's Paradise, if you do then investigate by running diagnostic tools (even though Master's Paradise was thing from the previous millennium AFAIK).

---

### Post by jsvidyad on 2010-04-13
Hi!!

    My computer is trying to make a connection to the outside on that port. Its an outgoing connection that firestarter has blocked. Before, I used to allow all outgoing connections and disallowed all incoming connections. Now, I have restricted outgoing connections to just some programs and the firestarter logs show that an outgoing connection has been blocked on port 3129 and the log gives the name of the program as Master's Paradise. Now, from what I could understand from the net, that is a backdoor for windows machines. How can I get a windows backdoor installed on my system? Is this  a false alarm? i have had firestarter give me false alarms regarding a trojan named gate-crasher some time ago.

---

### Post by lisati on 2010-04-13
> **jsvidyad said:**
> Hi!!

    [COLOR="Red"]My computer is trying to make a connection to the outside on that port. [/COLOR]It's an outgoing connection that firestarter has blocked.

Sorry about that, I misread your initial post.

---

### Post by jsvidyad on 2010-04-13
I am using ubuntu 9.10 64 bit. Master's Paradise is a windows backdoor from the late 1990s. I thought that it might be a false alarm from firestarter. But, the problem is that I couldn't find a legitimate program which uses the same port(3129).

---

### Post by jsvidyad on 2010-04-13
Hello,

  Can someone help me with this issue??

---

### Post by jsvidyad on 2010-04-13
I found on the internet that 3129 is a netport discovery port. Can some one please tell me what program uses this??

---

### Post by OpSecShellshock on 2010-04-13
What is it trying to connect to? A destination IP might give you an idea of what it is by looking at where it's headed. Alternatively you could try netstat. I'm not exactly sure which flags to use with netstat to show you which process is using the port, but someone on the boards probably can.

Alternatively you could just allow the connection and see what happens. Either you do have something malicious, which means you'll be reinstalling anyway, or you don't, which means allowing the connection is harmless.

---

### Post by dgw on 2010-04-13
Do you have Wine installed?

---

### Post by a.walker on 2010-04-13
Run the following command from terminal and post the output here.

```
sudo netstat -ntulp 
```

---

### Post by CharlesA on 2010-04-13
Using netstat will tell you what is trying to access that port.

Also: Bumping yer thread muliple times within 24 hours is frowned upon here. The security subforum isn't really *that* busy, as to need constant bumps.

---

### Post by jsvidyad on 2010-04-13
Hi!!!


   I am using wine. But, I scanned my wineprefix using clamav and it doesn't show any issues. 

I ran "sudo netstat -ntulp" and the output is given below:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1813/cupsd      
tcp        0      0 0.0.0.0:58938           0.0.0.0:*               LISTEN      4435/skype.real 
tcp6       0      0 ::1:631                 :::*                    LISTEN      1813/cupsd      
udp        0      0 127.0.0.1:41571         0.0.0.0:*                           4435/skype.real 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1168/avahi-daemon: 
udp        0      0 0.0.0.0:39338           0.0.0.0:*                           1168/avahi-daemon: 
udp        0      0 0.0.0.0:58938           0.0.0.0:*                           4435/skype.real 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3822/dhclient

---

### Post by cdenley on 2010-04-13
That actually lists listening processes on your system. Since you said it is an outgoing connection, that won't help us, although I wouldn't be surprised if it was related to skype. What will help us is if you give us the destination IP for the traffic. If your computer is attempting to make a connection, there is probably something listening for that connection, and we may be able to identify it. A whois lookup with the IP can also sometimes be informative.

---

### Post by jsvidyad on 2010-04-13
The firewall log didn't show the destination IP. It gave just the source IP, that's the IP of my computer.

---

### Post by cdenley on 2010-04-13
> **jsvidyad said:**
> The firewall log didn't show the destination IP. It gave just the source IP, that's the IP of my computer.

Then that is kind of useless. Doesn't give us much information to work with. Perhaps someone who is familiar with firestarter can help you find this information.

---

### Post by jsvidyad on 2010-04-13
Hello,

 I found the destination IP for that firewall event. It is 186.87.179.68

---

### Post by cdenley on 2010-04-13
It was TCP not UDP, right? There is no server listening on that port. Either the blocked connection attempt would have failed anyway, it was some sort of p2p traffic, or the IP was re-assigned to someone else (it appears to be dynamically assigned). The IP is from an ISP in Colombia.

---

### Post by jsvidyad on 2010-04-13
Hi!!!

   I noticed that there is some program trying to connect to that IP address by trying different ports. It tries to connect to that IP by trying ports starting from 1. Is that typical of a trojan/backport?

   I am attaching the relevant lines from the firewall log below:

Time:Apr 13 12:27:14 Direction: Unknown In: Out:wlan0 Port:1 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Tcpmux
Time:Apr 13 12:27:17 Direction: Unknown In: Out:wlan0 Port:2 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:20 Direction: Unknown In: Out:wlan0 Port:3 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:23 Direction: Unknown In: Out:wlan0 Port:4 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:26 Direction: Unknown In: Out:wlan0 Port:5 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:29 Direction: Unknown In: Out:wlan0 Port:6 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:32 Direction: Unknown In: Out:wlan0 Port:7 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Echo
Time:Apr 13 12:27:35 Direction: Unknown In: Out:wlan0 Port:8 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:38 Direction: Unknown In: Out:wlan0 Port:9 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Discard
Time:Apr 13 12:27:41 Direction: Unknown In: Out:wlan0 Port:10 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:44 Direction: Unknown In: Out:wlan0 Port:11 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Systat
Time:Apr 13 12:27:47 Direction: Unknown In: Out:wlan0 Port:12 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:50 Direction: Unknown In: Out:wlan0 Port:13 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Daytime
Time:Apr 13 12:27:53 Direction: Unknown In: Out:wlan0 Port:14 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:27:56 Direction: Unknown In: Out:wlan0 Port:15 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Netstat
Time:Apr 13 12:27:59 Direction: Unknown In: Out:wlan0 Port:16 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 13 12:28:02 Direction: Unknown In: Out:wlan0 Port:17 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Qotd
Time:Apr 13 12:28:05 Direction: Unknown In: Out:wlan0 Port:18 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:Msp
Time:Apr 13 12:28:08 Direction: Unknown In: Out:wlan0 Port:19 Source:192.168.1.2 Destination:Dynamic-IP-1868717968.cable.net.co Length:44 TOS:0x00 Protocol:TCP Service:Chargen
Time:Apr 13 12:28:11 Direction: Unknown In: Out:wlan0 Port:20 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:FTP
Time:Apr 13 12:28:14 Direction: Unknown In: Out:wlan0 Port:21 Source:192.168.1.2 Destination:186.87.179.68 Length:44 TOS:0x00 Protocol:TCP Service:FTP
Time:Apr 13 12:31:13 Direction: Unknown In: Out:wlan0 Port:44444 Source:192.168.1.2 Destination:186.87.179.68 Length:65535 TOS:0x00 Protocol:UDP Service:Unknown

---

### Post by cdenley on 2010-04-13
That looks like a port scan. Are you sure you didn't do that with "network tools"? If you run this command during the portscan, it should reveal what process is performing it.
```

sudo netstat -tunp

```

---

### Post by jsvidyad on 2010-04-13
Yes, I actually did a port-scan of that IP address from Network-Tools.

---

### Post by cdenley on 2010-04-13
> **jsvidyad said:**
> Yes, I actually did a port-scan of that IP address from Network-Tools.

If you're filtering outbound traffic, a port scan won't tell you too much. When I first scanned that IP, it had port 21 open, although I couldn't get a response, and a DNS server. Probably a linksys home router. The second time I scanned it, I got nothing. That seems like just another IP, nothing special or suspicious.

---

### Post by jsvidyad on 2010-04-13
Do you know of any legitimate program that uses port 3129? I saw on the web that IANA has assigned that port to netport discovery. What is that?

Also, I disallow all incoming connections. Is it necessary also to filter outbound connections?? I previously used to allow all outbound connections without any restriction. That was the default setting of firestarter(all incoming connections blocked and all outgoing connections allowed). Is this default setting good enough from the point of view of security? Or should outgoing connections be restricted too?

---

### Post by cdenley on 2010-04-13
I've never heard of anything using 3129, but there is pleny of software that can be configured to use any port.

Generally, you don't need to worry about outgoing connections. Anything that generates traffic would have been installed by you. The only scenario where it would benefit you to filter outgoing traffic is if you install malware. A better solution would be not to install malware. Install only from trusted, verified sources, such as the ubuntu repos.

---

### Post by jsvidyad on 2010-04-13
Is there some way to find out exactly which program is trying to connect to that IP address?

---

### Post by OpSecShellshock on 2010-04-13
> **jsvidyad said:**
> Is there some way to find out exactly which program is trying to connect to that IP address?

Allow it to connect and then see what process is using it.

---

### Post by jsvidyad on 2010-04-13
I usually install only programs from ubuntu and medibuntu repos. The only exceptions I have made are when I installed mathematica and maple. I installed those as root. I got the installation material from my office. So, it would be surprising if there was any malware on it.

Anyway, what do you suggest?? Should I re-install my OS or not?

---

### Post by cdenley on 2010-04-14
> **jsvidyad said:**
> I usually install only programs from ubuntu and medibuntu repos. The only exceptions I have made are when I installed mathematica and maple. I installed those as root. I got the installation material from my office. So, it would be surprising if there was any malware on it.

Anyway, what do you suggest?? Should I re-install my OS or not?

I still think that was probably a p2p connection attempt from something like skype. The only way to trace that back to a process that I can think of is to run "sudo netstat -tunp" when it is trying to connect.

---


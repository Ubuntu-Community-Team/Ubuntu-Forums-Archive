---
title: "Random TCP ports keep opening and closing, is my system compromised?"
date: 2016-12-11
forum: Security
---

### Post by koda2 on 2016-12-11
I have noticed that on my computer, random TCP ports open for a second, and then close immediately. This keeps happening as long as I am connected to the internet.

For example, one local NMAP scan for 65535 ports would give this output:

> 
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0014s latency).
Not shown: 65533 closed ports
PORT      STATE SERVICE
3852/tcp  open  sse-app-config
9648/tcp  open  unknown
57084/tcp open  unknown


And then after a second, if I do the same command again, I get:

> Nmap scan report for localhost (127.0.0.1)
Host is up (0.0014s latency).
Not shown: 65532 closed ports
PORT      STATE SERVICE
3077/tcp  open  orbix-loc-ssl
8158/tcp  open  unknown
48321/tcp open  unknown
55390/tcp open  unknown

And then when once again I do it, I receive:

> Nmap scan report for localhost (127.0.0.1)
Host is up (0.0016s latency).
Not shown: 65534 closed ports
PORT      STATE SERVICE
13926/tcp open  unknown
41695/tcp open  unknown


Even when I am not browsing or anything, this still happens.

What is causing all of this? How can I stop this from happening?

---

### Post by ian-weisser on 2016-12-11
Take a look at which applications are binding to which ports using
```
sudo netstat -tulpn
```

---

### Post by koda2 on 2016-12-12
There are a bunch of UDP ports ran locally by avahi-daemon & minissdpd and nothing else. I ran the command many times, and I get the same output. But those random TCP ports keep occurring.

Could these two applications be causing the problem somehow?

---

### Post by cogset on 2016-12-13
> **ian-weisser said:**
> Take a look at which applications are binding to which ports using
```
sudo netstat -tulpn
```

If what the OP is saying is the same thing that I've seen sometimes, that would not be possible: the ports close almost instantly, by the time the scan is finished there's nothing to look at.

Interestingly, I've also noted that scanning (as in scanning the machine from itself) with the -A flag always returns all ports closed, whilst -sT occasionally reports this random ports briefly opened.

---

### Post by Habitual on 2016-12-13
```
PORT      STATE SERVICE
13926/tcp open  unknown
41695/tcp open  unknown                      

```
Try in terminal> 
```
lsof -p <pid>
``` 
where <pid> is in the first columns shown.

This should tell you what files and processes have port 13926 and 41695 "open".

Also
```
sudo netstat -plnt | grep LISTEN
``` will show you either support for or against 
this "random" argument.
5th column will show your foreign connections.

I suspect ubuntu updates and open browser tab actions running, or something innocuous.

---

### Post by koda2 on 2016-12-15
> **Habitual said:**
> ```
PORT      STATE SERVICE
13926/tcp open  unknown
41695/tcp open  unknown                      

```
Try in terminal> 
```
lsof -p <pid>
``` 
where <pid> is in the first columns shown.

This should tell you what files and processes have port 13926 and 41695 "open".

Also
```
sudo netstat -plnt | grep LISTEN
``` will show you either support for or against 
this "random" argument.
5th column will show your foreign connections.

I suspect ubuntu updates and open browser tab actions running, or something innocuous.


For the first command, the ports open and close so instantly that it is  useless to see what files and processes have that specific port open,  the command simply returns nothing.

I also tried > sudo netstat -plnt | grep LISTEN several times, but at each time, it returns nothing. 

If no file and process are using these ports, then what is? I am terribly confused.

---

### Post by Habitual on 2016-12-15
Sorry, I am unable to diagnose any further.
I suspect all these "random" ports being reported are above > 1024 and that means
does not require root.

I suggest utilizing tcpdump to sniff and capture-to-file say, 10,000 packets and 
then that can be analyzed further by someone who's good at it.
You need forensics.

Have a look at 
[http://www.thegeekstuff.com/2010/08/tcpdump-command-examples](http://www.thegeekstuff.com/2010/08/tcpdump-command-examples)

Something like
```
sudo tcpdump -w sniff.pcap -i eth0 -c 10000 -A
```
Your Network Interface may not be eth0, so check using 
```
ifconfig
``` and examine the left column for your interface label/identifiers.

I'd suggest clamAV, so if it is not installed, open a terminal and issue:
```
sudo apt-get install clamav && sudo freshclam && exit
```
Now, as your usual self, issue this command:
```
clamscan -ir $HOME --log=$HOME/sniff.scan
```
This scan will do 2 things, scan and report on screen the same result it writes to sniff.scan

sniff.pcap is for the evidence
sniff.scan is for you to examine.
Infectioins will be shown.
clamAV has no "clean" routine, quarantine or delete.

You have a router? Any Open Access Points?

Please let us know.
Please, if you use the GUI version of clamAV, don't enable PUA and only scan your $HOME, for now.

---

### Post by koda2 on 2016-12-15
I have three updates:


1) These random TCP ports open and close instantly EVEN without an internet connection.

2) These ports are always in the 1600-60000 range.

3) I ran both chkrootkit and rkhunter, and nothing suspicious was found.

Can someone provide some insight or a hypothesis as to why this is happening, that is, what is causing these random TCP ports to open and close in the split of a second even when there is no network connection?

---

### Post by kpatz on 2016-12-15
When you're doing the nmap scans, are you scanning your network interface (or IP address on the network interface), either wired or wireless, or are you scanning localhost (127.0.0.1)?

What's the nmap command you're running?

Do you have more than one computer?  Have you tried doing the scan from another computer over the network?

There are services that may bind to localhost to talk to another service, and you may be scanning the ports when they open momentarily, but that should only happen on the lo interface, not an ethernet or wireless interface.

---

### Post by koda2 on 2016-12-17
> **kpatz said:**
> When you're doing the nmap scans, are you scanning your network interface (or IP address on the network interface), either wired or wireless, or are you scanning localhost (127.0.0.1)?

What's the nmap command you're running?

Do you have more than one computer?  Have you tried doing the scan from another computer over the network?

There are services that may bind to localhost to talk to another service, and you may be scanning the ports when they open momentarily, but that should only happen on the lo interface, not an ethernet or wireless interface.

I have scanned both using my IP and through localhost, the same thing happens each time.

I use> nmap localhost -p 0-65535 but I replace 'localhost', as is stated above, with my IP too and the same result occurs.

And yes, I have ran the scan from another network and the outcome is the same as if I was performing it from my own computer, that is, random TCP ports are opening and closing.

---

### Post by cogset on 2016-12-19
Out of curiosity, I' ve scanned again my computer from itself using ```
sudo nmap -sT -f -vv --reason  --version-intensity 9  -T normal -p 1-65535 192.168.x.xxx
```
 and as usual random highly numbered ports appear to be briefly open
 ```
Initiating Connect Scan at 20:03 Scanning 192.168.x.xxx [65535 ports]
 Discovered open port 59640/tcp on 192.168.x.xxx
 Completed Connect Scan at 20:03, 1.02s elapsed (65535 total ports)
 Nmap scan report for 192.168.x.xxx
 Host is up, received localhost-response (0.00019s latency).
 Scanned at 2016-12-18 15:10:35 CET for 1s
 Not shown: 65534 closed ports Reason: 65534 conn-refused 
  PORT      STATE SERVICE REASON
 59640/tcp open  unknown syn-ack
``` 

I was  running a tshark capture on the same interface: after looking at the capture file using wireshark, there's no trace at all of that port.  

When  trying again the same scan, a different port will be reported as "open  unknown syn-ack" and also  then never seen by tshark. 

 If scanning with ```
sudo nmap -A -f -vv --reason  --version-intensity 9  -T normal -p 1-65535 192.168.x.xxx
``` no port will ever be open ```
All 65535 scanned ports on 192.168.x.xxx are closed because of 65535 resets
``` 

  Anyone that  can figure out this?

---

### Post by kpatz on 2016-12-19
Does the same thing happen if you don't have wireshark running?

---

### Post by Habitual on 2016-12-19
I get the syn-ack also, high ports too, using 
```
sudo nmap -sT -f -vv --reason  --version-intensity 9  -T normal -p 1-65535 192.168.1.3
```
<snipped fluff>

Found using this is more of what I'd expect. 
Use ```
sudo \nmap -sT -f -vv --version-intensity 5  -T Insane -p 1-65535 192.168.1.3
```

Normal vs. Insane.
Age old question, maybe it's an Easter Egg? (wut? could happen)

And you start out on a high port connecting to standard daemon ports, so I guess maybe syn-ack is expected?
I didn't count, but are there only even numbered results in your test? (All results / 2?)
I rebooted my machine and router and now the output is completely different.
```
sudo \nmap -sT -f -vv --version-intensity 5  -T Normal -p 1-65535 192.168.1.3
...
Starting Nmap 6.40 ( http://nmap.org ) at 2016-12-19 18:11 EST
Initiating ARP Ping Scan at 18:11
Scanning 192.168.1.3 [1 port]
Completed ARP Ping Scan at 18:11, 0.43s elapsed (1 total hosts)
Nmap scan report for 192.168.1.3 [host down]
Read data files from: /usr/bin/../share/nmap
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 0.51 seconds
           Raw packets sent: 2 (56B) | Rcvd: 0 (0B)
```

Hope that helps?

---

### Post by cogset on 2017-02-21
> **kpatz said:**
> Does the same thing happen if you don't have wireshark running?  Why would wireshark (or tshark, for that matter) affect this? Isn't it just a passive monitoring tool, meaning it should not open any port or send any packet ?

---

### Post by cogset on 2017-02-21
> **Habitual said:**
>    Age old question, maybe it's an Easter Egg? (wut? could happen)  I'd find it strange, but anything is possible.  > **Habitual said:**
> And you start out on a high port connecting to standard daemon ports, so I guess maybe syn-ack is expected? I didn't count, but are there only even numbered results in your test? (All results / 2?) I rebooted my machine and router and now the output is completely different.  But I don't think I have anything listening, as I've removed stuff such as bluetooth, avahi, ssh and so on. As for the even numbered ports, no, it also finds odd numbered ports on occasion - neither rebooting the pc or the router seems to have a part in this.   I don't think the router should even be considered, as I've disabled anything in it that could arbitrarily open a port on my pc - of course ,unless it's doing something behind my back.

---

### Post by ventrical on 2017-02-24
> **koda2 said:**
> I have three updates:


1) These random TCP ports open and close instantly EVEN without an internet connection.

2) These ports are always in the 1600-60000 range.

3) I ran both chkrootkit and rkhunter, and nothing suspicious was found.

Can someone provide some insight or a hypothesis as to why this is happening, that is, what is causing these random TCP ports to open and close in the split of a second even when there is no network connection?


I have my network up and:

```
ventrical@ventrical-MS-7798:~$ nmap localhost -p 0-65535 

Starting Nmap 7.01 ( https://nmap.org ) at 2017-02-24 19:35 EST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000075s latency).
All 65536 scanned ports on localhost (127.0.0.1) are closed

Nmap done: 1 IP address (1 host up) scanned in 2.10 seconds
ventrical@ventrical-MS-7798:~$ 

```

but I am on a router.

 I am curious if you were to scan your ports using Shields Up by

[www.grc.com](www.grc.com)

and see if there are any ports open.

What version of Ubuntu are you running?

Regards..

Mt Theory:You installed something from USC (or elsewhere) which has a depend to have those ports open , most likely from a virtual machine service or process that loads at startup..
Regards..

---

### Post by kevdog on 2017-02-26
I take it you don't have a firewall in place on your setup.  Not saying a firewall is impenetrable, however that's a sure way to limit access to open ports -- both inbound and outbound.

---

### Post by cogset on 2017-03-06
It's not clear to me at this point if the last two replies were intended for me (I suspect not), in any case I do have a firewall in place with a default deny incoming/allow outgoing policy and no services listening that I'm aware of.

---

### Post by bashiergui on 2017-03-09
Try an nmap FIN scan by using the -U switch. A closed port will send you a RST. And try a SYN scan with the -s switch. If you get the same results with all these types of scans then the ports are more likely to really be open. 

Use "watch" with netstat to see if these ports appear and disappear. ```
sudo watch netstat -tulpn
``` I'd use ```
sudo top -b -n9 > top.txt
``` to see the processes opening the ports dumped into a text file. The -n9 will give you 9 iterations of the top refreshes. You can look for the pids that might match up with your nmap results if top and nmap run simultaneously. Or instead of top run ```
watch ps aux >> processes.txt
``` for a giant list of all the processes over & over.

---

### Post by cogset on 2017-04-07
I've noted in the meantime that a scan with -sF always reports all ports closed, even when  -sT finds something open.

---

### Post by Habitual on 2017-04-07
I suspect MCAST/BCAST traffic.

---


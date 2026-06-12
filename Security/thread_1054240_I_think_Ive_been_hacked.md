---
title: "I think Ive been hacked"
date: 2009-01-29
forum: Security
---

### Post by engineuity on 2009-01-29
Hi, 
  As my title says, I think Ive been hacked. I have a connection to my computer that is eating my bandwidth. I can see it on my system monitor, but I do not know how to tell who or what is downloading from me. I would like to add this IP to my iptables config, but I do not know how to determine the connection.

Thanks

Edit:
The connection is on my WAN. I have dd-wrt flashed onto my router. I will check if I can find an IP address through there as well.

---

### Post by e1mer on 2009-01-29
If you open a bash shell and 'sudo netstat -t' you can see which
hosts have TCP connections opened to your server.

Sometimes the hosts are listed as nnn.nnn.nnn.nnn:port and 
sometimes they are listed as nnn-nnn-nnn-nnn.stuff:port

I use the domain dossier at centralops.net/co to look and see
if the IP is something reasonable.
(web crawling through your pages) or unfriendlys.

Sometimes I just don't care:
 iptables -A INPUT -s 201.151.0.0/16 -j DROP
cut off the ability for more than 65 thousand IP
addresses in Mexico from seeing my computer.

---

### Post by SIGTERMer on 2009-01-29
are you running server software such as openssh? block port forwarding on your router or change the default port the daemons listens to. that might help.

---

### Post by timcredible on 2009-01-29
are you running frostwire or something similar?

---

### Post by engineuity on 2009-01-29
I am running sshd, but I was never able to connect from outside my network. I have a fios modem/router connected to my flashed linksys

Im pretty sure the only service I run on that box are mediatomb and sshd. It basically just serves as my media server (currently headless but runs gnome).

I tried nestat, but all of the connections point to localhost and the machine I am using through ssh.

Im not sure what frostwire is, but if it is a P2P software then no.

This is frustrating, system-monitor is showing a 800kb/s - 1mb/s output

Edit: I also dropped Mexico, but the connection is still running full speed

---

### Post by Dr Small on 2009-01-29
Try running:
```
netstat -ta
```

And look for any foreign IPs connecting to the system.

---

### Post by engineuity on 2009-01-29
```
sudo netstat -ta
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 *:43858                 *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:6010          *:*                     LISTEN     
tcp        0      0 *:41691                 *:*                     LISTEN     
tcp        0      0 *:43932                 *:*                     LISTEN     
tcp        0      0 motown:ssh              studio:60925            ESTABLISHED
tcp        0      0 localhost:6010          localhost:35732         ESTABLISHED
tcp        0      0 motown:ssh              studio:36832            ESTABLISHED
tcp       96      0 localhost:55741         localhost:6010          ESTABLISHED
tcp        0      0 motown:45390            prat.canonical.com:www  ESTABLISHED
tcp        0      0 localhost:6010          localhost:55741         ESTABLISHED
tcp        0      0 localhost:35732         localhost:6010          ESTABLISHED
tcp        0      0 motown:ssh              studio:44946            ESTABLISHED
tcp        0      0 localhost:6010          localhost:55742         ESTABLISHED
tcp        0      0 localhost:55742         localhost:6010          ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:6010          [::]:*                  LISTEN     


```
prat.canonical.com:www

That was the only foreign IP I could tell. And I believe that is cause of the system update I am trying.

Edit:
Studio is the machine I am using to access the media box.

---

### Post by Dr Small on 2009-01-29
Well, other than studio, canonical and localhost, I don't see any incoming connections.

---

### Post by wickedbadawesome on 2009-01-29
where are you getting the information from that is telling you about the 1mbs traffic coming from your computer?

---

### Post by engineuity on 2009-01-29
I tried getting some updates on 'studio' and they were downloading exceptionally slow. ~23kb/s and Im used to ~1mb/s. I checked my router status page and it showed WAN activity uploading at about 800kb/s. 
I pulled up gnome-system-monitor on both of my boxes and motown seems to be the big offender, but I cannot trace why.

---

### Post by engineuity on 2009-01-29
I just tried unmounting my media disks, but the connection is still going strong. Now Im really not sure whats going on. Id hate to reinstall without knowing what was wrong in the first place.

---

### Post by wickedbadawesome on 2009-01-29
Not a solution but unplug motown from the network, isolate it - see if the attacker if there is one goes after the other machine on your network, it is possible that it is just something screwed up on that machine. you need to find out what port it is on as well. which ports are open from the router that go back to that machine. Close them if you can. Do some packet sniffin as well - you can see what is being sent that way - i imagine this will take some time but, its worth it to track down the problem and you will learn alot in the meantime i imaigne..

---

### Post by engineuity on 2009-01-29
Is it possible that my box has become a zombie and using DoS on my network? I disconnected the router from the internet and checked my connections again and the speeds jumped up to 2mb/s, but didnt seem to be going anywhere. Each time I reboot, the "process" starts back up and goes right back to the state before I rebooted.

Its like the box is just flooding my network.

---

### Post by wickedbadawesome on 2009-01-29
Are you hosting any torrent files on that machine?  - oh did you netstat on the motown machine or on the other machine? i know stupid question but still

---

### Post by engineuity on 2009-01-29
> **wickedbadawesome said:**
> Not a solution but unplug motown from the network, isolate it - see if the attacker if there is one goes after the other machine on your network, it is possible that it is just something screwed up on that machine. you need to find out what port it is on as well. which ports are open from the router that go back to that machine. Close them if you can. Do some packet sniffin as well - you can see what is being sent that way - i imagine this will take some time but, its worth it to track down the problem and you will learn alot in the meantime i imaigne..

I closed the ports on my router already, I only opened 21 and 22. I will try to do some packet sniffing

---

### Post by engineuity on 2009-01-29
> **wickedbadawesome said:**
> Are you hosting any torrent files on that machine?  - oh did you netstat on the motown machine or on the other machine? i know stupid question but still

No torrent hosting, and I ran netstat from motown.

---

### Post by wickedbadawesome on 2009-01-29
> **engineuity said:**
> I tried getting some updates on 'studio' and they were downloading exceptionally slow. ~23kb/s and Im used to ~1mb/s. I checked my router status page and it showed WAN activity uploading at about 800kb/s. 
I pulled up gnome-system-monitor on both of my boxes and motown seems to be the big offender, but I cannot trace why.

> **engineuity said:**
> ```
sudo netstat -ta
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 *:43858                 *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:6010          *:*                     LISTEN     
tcp        0      0 *:41691                 *:*                     LISTEN     
tcp        0      0 *:43932                 *:*                     LISTEN     
tcp        0      0 motown:ssh              studio:60925            ESTABLISHED
tcp        0      0 localhost:6010          localhost:35732         ESTABLISHED
tcp        0      0 motown:ssh              studio:36832            ESTABLISHED
tcp       96      0 localhost:55741         localhost:6010          ESTABLISHED
tcp        0      0 motown:45390            prat.canonical.com:www  ESTABLISHED
tcp        0      0 localhost:6010          localhost:55741         ESTABLISHED
tcp        0      0 localhost:35732         localhost:6010          ESTABLISHED
tcp        0      0 motown:ssh              studio:44946            ESTABLISHED
tcp        0      0 localhost:6010          localhost:55742         ESTABLISHED
tcp        0      0 localhost:55742         localhost:6010          ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:6010          [::]:*                  LISTEN     


```
prat.canonical.com:www

That was the only foreign IP I could tell. And I believe that is cause of the system update I am trying.

Edit:
Studio is the machine I am using to access the media box.

Im a little suspicious of all of your localhost connections. is it possible that something is disguised as localhost

---

### Post by engineuity on 2009-01-29
I googled ports 35732 and 55741 and they seem to map to phpmyadmin. I dont remember explicitly installing it, but I vaguely remember it being a dependency of something, mediatomb maybe?

---

### Post by bodhi.zazen on 2009-01-29
:lolflag:

I find this command to be VERY helpful :

```
sudo lsof -i -n -P
```

ports are confusing at first.

Incoming ports use specific ports, ssh uses 22 by default for example.

Outgoing ports are pseudo-random, so if you are using firefox it will use an outgoing port of say 35732 to connect to port 80 (http) or 443 (https) on the server .

You are best closing all apps that use the network, then looking at the network activity.

If you wish to analyze the activity further you will need to look at a packet sniffer such as snort or wireshark.

---

### Post by engineuity on 2009-01-29
```
 sudo lsof -i -n -P
COMMAND    PID       USER   FD   TYPE DEVICE SIZE NODE NAME
portmap   4126     daemon    4u  IPv4  14063       UDP *:111 
portmap   4126     daemon    5u  IPv4  14070       TCP *:111 (LISTEN)
rpc.statd 4148      statd    5r  IPv4  14113       UDP *:932 
rpc.statd 4148      statd    7u  IPv4  14121       UDP *:34032 
rpc.statd 4148      statd    8u  IPv4  14124       TCP *:58860 (LISTEN)
avahi-dae 4685      avahi   14u  IPv4  14997       UDP *:5353 
avahi-dae 4685      avahi   15u  IPv4  14998       UDP *:45142 
sshd      4714       root    3u  IPv6  15057       TCP *:22 (LISTEN)
sshd      4714       root    4u  IPv4  15059       TCP *:22 (LISTEN)
cupsd     4757       root    2u  IPv4  15151       TCP 127.0.0.1:631 (LISTEN)
rpc.mount 4971       root    6u  IPv4  15477       UDP *:35604 
rpc.mount 4971       root    7u  IPv4  15482       TCP *:53679 (LISTEN)
dhclient  5771       root    5w  IPv4  25423       UDP *:68 
sshd      5835       root    3r  IPv4  25517       TCP 192.168.2.202:22->192.168.2.201:60272 (ESTABLISHED)
sshd      5842 engineuity    3u  IPv4  25517       TCP 192.168.2.202:22->192.168.2.201:60272 (ESTABLISHED)

```

I forgot I have an nfs running on that box...

There is no printer, I can disable cupsd.
Other than that I dont see anything out of the ordinary. I just connected the box back to the network and will try to do some packet sniffing. I just installed snort

---

### Post by engineuity on 2009-01-29
```

Run time prior to being shutdown was 203.667781 seconds
Frag3 statistics:
        Total Fragments: 0
      Frags Reassembled: 0
               Discards: 0
          Memory Faults: 0
               Timeouts: 0
               Overlaps: 0
              Anomalies: 0
                 Alerts: 0
     FragTrackers Added: 0
    FragTrackers Dumped: 0
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 0
     Frag Nodes Deleted: 0
===============================================================================
Stream5 statistics:
            Total sessions: 679
              TCP sessions: 679
              UDP sessions: 0
             ICMP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
TCP StreamTrackers Created: 679
TCP StreamTrackers Deleted: 679
              TCP Timeouts: 0
              TCP Overlaps: 0
       TCP Segments Queued: 679
     TCP Segments Released: 679
       TCP Rebuilt Packets: 674
         TCP Segments Used: 679
              TCP Discards: 138293
      UDP Sessions Created: 0
      UDP Sessions Deleted: 0
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 0
===============================================================================
Final Flow Statistics
,----[ FLOWCACHE STATS ]----------
Memcap: 10485760 Overhead Bytes 32800 used(%1.841679)/blocks (193114/695)
Overhead blocks: 1 Could Hold: (45392)
IPV4 count: 694 frees: 0
low_time: 1233264861, high_time: 1233264920, diff: 0h:00:59s
    finds: 145515 reversed: 50196(%34.495413) 
    find_success: 144821 find_fail: 694
percent_success: (%99.523073) new_flows: 694
 Protocol: 6 (%99.979384)
   finds: 145485
   reversed: 50181(%34.492216)
   find_success: 144806
   find_fail: 679
   percent_success: (%99.533285)
   new_flows: 679
 Protocol: 17 (%0.020616)
   finds: 30
   reversed: 15(%50.000000)
   find_success: 15
   find_fail: 15
   percent_success: (%50.000000)
   new_flows: 15


===============================================================================

Snort received 148194 packets
    Analyzed: 144841(97.737%)
    Dropped: 3350(2.261%)
    Outstanding: 3(0.002%)
===============================================================================
Breakdown by protocol:
      TCP: 144811     (99.979%)         
      UDP: 30         (0.021%)          
     ICMP: 0          (0.000%)          
      ARP: 0          (0.000%)
    EAPOL: 0          (0.000%)
     IPv6: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
     FRAG: 0          (0.000%)          
    OTHER: 0          (0.000%)
  DISCARD: 0          (0.000%)
InvChkSum: 0          (0.000%)
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
HTTP Inspect - encodings (Note: stream-reassembled packets included):
    POST methods:                   0         
    GET methods:                    1358      
    Post parameters extracted:      5         
    Unicode:                        0         
    Double unicode:                 0         
    Non-ASCII representable:        0         
    Base 36:                        0         
    Directory traversals:           0         
    Extra slashes ("//"):           14        
    Self-referencing paths ("./"):  0         
    Total packets processed:        94704     
===============================================================================
Snort exiting
```
I have some output from snort, but Im not sure what Im looking for.

---


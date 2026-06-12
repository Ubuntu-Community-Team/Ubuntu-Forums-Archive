---
title: "proftpd maximum login attempts"
date: 2009-02-24
forum: Security
---

### Post by krooked on 2009-02-24
Hello,
Last night I was fortunate enough to load up a connection monitor and notice someone sending thousands of packets to brute force my FTP. I didnt think this was possible since i have 
> # set max number of login attempts
MaxLoginAttempts 3

in my proftpd.conf file.
Is this not the right config parameter to limit someone from sending thousands of packets in a brute force manor, or have they got away around this? 
I like using proftpd and wouldnt like to have a "which ftp program is better" arguement, but if there are security tips i could definetely use those.

---

### Post by redroad55 on 2009-02-24
Try looking here :   [http://ubuntuforums.org/showthread.php?t=1071799]("http://ubuntuforums.org/showthread.php?t=1071799")

---

### Post by brian_p on 2009-02-24
> **krooked said:**
> 

Is this not the right config parameter to limit someone from sending thousands of packets in a brute force manor, . . . . . 

No. It allows three attempts at a password after connecting to the daemon. Then the daemon closes the connection. Another connection can be made, of course.

And so the dance continues. You have strong passwords so you are always the leader. If you are worried (but why should you be?) fail2ban is a package some people install.

---

### Post by bodhi.zazen on 2009-02-24
You can add a "simple" rule to iptables, blacklist the offending IP address, or use something such as fail2ban.

---

### Post by Gouki on 2009-02-24
> **bodhi.zazen said:**
> You can add a "simple" rule to iptables, blacklist the offending IP address, or use something such as fail2ban.

I don't know what's the state of fail2ban these days, but the version I used on 8.04 Backports had several bugs that prevented me from using it.

I ended up with DenyHosts.

---

### Post by bodhi.zazen on 2009-02-24
+1 , I have used denyhosts as well.

Now I use a few rules in iptables, once you learn the rules for iptables it is easier then either denyhosts or fail2ban (imo).

---

### Post by krooked on 2009-02-24
hey thanks. ill look for some info on ip tables to figure out how it works and i could permaban these people. yeah i keep my password for the users i allow super long so i wanst worried when i saw the user and pass combonations i was being sent, i just didnt want even the slightest worries of it being remotely possible to gain access.

---

### Post by bodhi.zazen on 2009-02-24
I wrote an overview on iptables here :

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by krooked on 2009-02-25
that guide was very helpful and i read through the whole thing. i am going to start on a table right now.

---

### Post by krooked on 2009-02-25
After some playing i got iptables setup by adding 
> pre-up iptables-restore < /etc/iptables.txt
which should load my iptables everytime i turn on the computer

then added 
> iptables -A blacklist -d <Bad_IP_1> -j DROP
for the 2 ip's i didnt want anything to do with, they look to be properly added into my blocklist Chain.

> iptables -A INPUT -p tcp -m state --state NEW -m recent --set -j ACCEPT
iptables -A INPUT -p udp -m state --state NEW -m recent --set -j ACCEPT
iptables -A INPUT -m recent --update --seconds 300 --hitcount 4 --rttl -j DROP
which is supposed to stop an "SSH or other connections" brute force attack, i wasnt sure what i needed to customize in this command, and from what i cal tell this will basically set a counter for login attempts and if it hits 4 then it drops packets from that user, im guessing for only this instance of iptables


> iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
which is supposed to be Http protection(for 5 requests within 30 minutes?)

My question is does the ssh brute force command protection also protect from an ftp attack, the command seems to include all udp and tcp input requests so i would think that is true.
Also i was concerned about other programs since this isnt a standalone server, will the packets for a game or messaging clients begin to be dropped if they are refreshed too fast?
Besides those 2 concerns i do not believe there is anything else that needs to be done to relieve my concerns as my passwords are healthy and limited to only select accounts for ftp/ssh. any comments/suggestions will be appreaciated.

---

### Post by bodhi.zazen on 2009-02-25
Glad you found it helpful.

The "best" way is to test, test, test.

The same rules for ssh should apply to ftp. 

I found Apace (http) needed more liberal rules.

If you "break" those rules (for ssh) the offending IP address will be blacklisted for 300 seconds (5 minutes) which is sufficient to stop brute force attempts (it will take a long, long time if they wait for 5 minutes), yet allow vaild traffic (if a user makes a mistake) after a 5 minute "time out".

I hope that helps, I am not an expert on iptables by any means and most of what I know is by trial and error (mostly error, lol).

---

### Post by krooked on 2009-02-25
ok thanks that clarifies alot. yes right now i am trying trial by myself by specifying a block to my laptop on the same network for incoming and outgoing packets but it doesnt seem to be working. It gives me two options 1) specifying a block for 192.168.1.X is going wrong
> sudo iptables -A blacklist -d 192.168.1.4 -j DROP
2) the iptables arent being loaded correctly at boot and none of these rules are being applied, is it normal to have to restore from a file to play with the iptables, or if my network/interfaces file correctly imported them should they already be configurable/viewable (iptables -L currently returns blank tables until a restore > file)

im going to bed and will have to continue this playing tommorow. I thank all who have helped as i feel much better and love learning new programs in linux.

---

### Post by Wush.S.H on 2009-02-25
For beginners, perhaps firestarter is a good choose to set up iptables rule.

---

### Post by bodhi.zazen on 2009-02-25
> **Wush.S.H said:**
> For beginners, perhaps firestarter is a good choose to set up iptables rule.

IMO firestarter is not so good, and for the task of the OP firestarter will not work at all (firestarter is very basic and will not limit the number of connection attempts nor automatically black list offending IP addresses).

If you would like, as a new user, I suggest ufw which comes with a gui front end, gufw.

The other option is guarddog. What is nice about guarddog is that it comes with very nice built in help.

But, IMHO, iptables will do what the OP is asking and takes about as long to learn as guarddog.

---

### Post by krooked on 2009-02-25
yes i have no problem learning ip tables, i already understand much of it as i have had alot of networking tasks in the past and already understood much of what it was doing. now its just implementing that config file that should be setup properly into my system so everything works together seamlessly as well as learning the syntax of commands in iptables.

---

### Post by bodhi.zazen on 2009-02-25
To keep your settings you have two options.

first, and IMO more complex, you write a script. The second is to use iptables-save and iptables-restore.

There is some additional information if you use network manager on the ubuntu wiki page :

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

personally what I do is :

```
sudo mkdir /root/etc

sudo -c bash "iptables-save > /root/etc/iptables"
```Then to restore add this to /etc/rc.local :

```
iptables-restore < /root/etc/iptables
```

There is also this thread (some if it is a bit old)

[http://ubuntuforums.org/showthread.php?t=299300](http://ubuntuforums.org/showthread.php?t=299300)

---

### Post by krooked on 2009-02-25
i actually was able to get away with
> su
iptables-save > /etc/iptables.rules

and appending to my /etc/network/interfaces
> pre-up iptables-restore < /etc/iptables.rules


upon restart it now loads up my iptables, which look like this
> Chain INPUT (policy ACCEPT 14 packets, 838 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   35  4372 blacklist  all  --  any    any     anywhere             anywhere            
    9  1347 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: ' 
    8   468 ACCEPT     tcp  --  any    any     anywhere             anywhere            state NEW limit: avg 30/min burst 5 
    5  1404 DROP       all  --  any    any     anywhere             anywhere            recent: UPDATE seconds: 300 hit_count: 4 TTL-Match name: DEFAULT side: source 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state NEW recent: SET name: DEFAULT side: source 
    8  1662 ACCEPT     udp  --  any    any     anywhere             anywhere            state NEW recent: SET name: DEFAULT side: source 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 44 packets, 4667 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   44  4667 blacklist  all  --  any    any     anywhere             anywhere            

Chain blacklist (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     87.106.246.117       anywhere            
    0     0 DROP       all  --  any    any     217.199.164.48       anywhere            
    0     0 DROP       all  --  any    any     anywhere             217.199.164.48      
    0     0 DROP       all  --  any    any     anywhere             87.106.246.117   

A blacklist addition from a second test pc stopped my connections 
> iptables -A blacklist -s 192.168.1.6 -j DROP
iptables -A blacklist -s 192.168.1.6 -j DROP
i then removed it and moved on
> iptables -D blacklist #

i ran an attack against myself in the network and it succeeded in dropping my packets, one line out of many shown in /var/log/debug
> Feb 25 11:51:36 krooked-desktop kernel: [ 1201.699789] iptables denied: IN=eth0 OUT= MAC=XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX SRC=192.168.1.1 DST=192.168.1.4 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=137 LEN=58 

although this completely cut off my internet for a few minutes, because it started dropping to and from my router, which was successful in a way because it triggered a drop, although i will need to test outside the network with some brute force attacks to really see if i can trigger the rules for dropping packets properly while still maintaining a connection.

I dont really have any questions or problems right now about this, i do this post mainly to add conclusive steps for others to reference in the future. If you see something wrong with this please let me know.

---

### Post by shadowhacker on 2009-02-26
I'm not sure if it's applicable in your case as well, but I've also had a bunch of brute force attempts in the past. I have strong passwords too, but I still didn't like the extra network traffic being generated.

I solved my issue by forwarding an undisclosed port externally to 21 on my LAN. I also did the same with the passive ports. This way not only does a user need a Username and password, they also need the specific port I'm running on. I love that trusty old Cisco 806.

---

### Post by krooked on 2009-02-26
ive heard of changing from the standard ports but that can still be found with a simple nmap. are you talking of something different? ive noticed some addresses seem to hide what ports they are using.

if this is so, i could use a point in the right direction, ill figure out what your talking about and see if it will help in my case.

---

### Post by bodhi.zazen on 2009-02-26
IMO changing the port helps with ssh and ftp as it eliminates the script kiddies who write scripts to target the default ports.

It is not great and as you say you can be port scanned, but either you will see the port scan (you do use snort ?) or the attacker is sophisticated and hides the scan in some way, in which case changing the port does not really help much.

This is similar to not responding to ping requests and what not.

---


---
title: "OpenVPN connections allowed on port 53100 even though port blocked by UFW"
date: 2020-08-14
forum: Server Platforms
---

### Post by kazarrwahoo on 2020-08-14
Hi. I have been testing the firewall and security of my ubuntu server 20.04 on VMWare Workstation (linux mint host). I had SSH and OpenVPN configured and working. OpenVPN is configured to use port 53100. SSH and OpenVPN were both working when I enabled UFW. I was then unable to connect to SSH until I added the appropriate firewall rules. However I am still able to connect to OpenVPN server, even though I didn't add a rule to allow in/out of udp on port 53100. This puzzled me. So I added a rule denying udp and tcp for port 53100 but I can still connect to openVPN server. 

My question is how do I block this port in UFW so no incoming openVPN connections can occur? 
```

steve@ubuntuerver:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
2235/udp                   DENY        Anywhere                  
2235/tcp                   ALLOW       Anywhere                  
53100/udp                  DENY        Anywhere                  
53100/tcp                  DENY        Anywhere  



```

I can't figure out how to run netstat -tunip from SSH client (it doesn't return results which are meaningful to me). I have ran it within the server and it says 53100 udp associated with 7902/openvpn. 

I would be very gratful if someone could help. Perhaps I am misunderstanding how to use the firewall?

---

### Post by darkod on 2020-08-14
ufw is only a frontend of iptables. Check iptables output instead of relying only on ufw.
```
sudo iptables -L -n -v
```

If you post the output here in CODE tags we can help review it.

It could also be a case if you have multiple NICs on the server and the firewall is blocking traffic on one but you are connecting from the other. Again, iptables would show detailed related to NIC name too. Lets see the output...

---

### Post by The Cog on 2020-08-14
It may be important that OpenVPN was active when you enabled ufw. ssh uses a new source port for each connection, but OpenVPN may well re-use the same ports over and over. In this case, OpenVPN re-connnecting will just look like a continuation of the same connection (one that was permitted before ufw started), not a new connection. ufw will deny new connections but it allows existing ones to continue. You may have to wait until the connection state tracking times out and forgets the old connection. From memory, I think this might be 5 or 15 minutes but I'm not sure.

---

### Post by darkod on 2020-08-14
Good point. Or simply restart the openvpn service on the server, that way it will close all connections and start again fresh.

---

### Post by kazarrwahoo on 2020-08-14
Thank you so much everyone- This is my first post and I'm blown away at support (-:

I queried the iptables suggested by darkod- the output is-
<CODE>
```
:~$ sudo iptables -L -n -v
[sudo] password for steve: 
Chain INPUT (policy DROP 4 packets, 144 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   26  5192 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53100
12274 1125K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
12274 1125K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  564 35164 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   360 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   360 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   360 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    8  1347 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    7   451 ACCEPT     all  --  *      *       10.8.0.0/24          0.0.0.0/0           
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
18043 8462K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
18043 8462K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   21  1598 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   21  1598 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   21  1598 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           sudo systemctl stop [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
sudo systemctl start [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
   21  1598 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    4   972 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
  550 33832 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   10   360 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  100  7938 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
11606 1082K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
  568 35404 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
  568 35404 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
sudo systemctl stop [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
sudo systemctl start [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  100  7938 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
17922 8452K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
   21  1598 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   240 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
   10   360 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
  554 34804 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
  554 34804 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           sudo systemctl stop [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
sudo systemctl start [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e

Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   240 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
   17  1358 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:2235
    4   240 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:2235

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
</CODE>
I have restarted the service as follows-
<CODE>
sudo systemctl stop [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
sudo systemctl start [EMAIL="openvpn-server@server.servic"]openvpn-server@server.servic[/EMAIL]e
</CODE>
I checked and I could not connect to openvpn whist service was stopped- I could connect once service started.

The current status of UFW is-
<CODE>
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
2235/udp                   DENY IN     Anywhere                  
2235/tcp                   ALLOW IN    Anywhere
</CODE>
```


Thanks again everyone

---

### Post by darkod on 2020-08-15
The above output is what I hate about ufw. It creates so much unnecessary "noise" in the iptables, it is often hard to troubleshoot.

In your place I would simply use iptables directly, not ufw.

Anyway, you seem to have an entry in the INPUT chain that allows all UDP traffic. The very first line entry:
```
Chain INPUT (policy DROP 4 packets, 144 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   26  5192 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53100
```

Because it is the first entry that allows all UDP traffic without taking into account there might be other rules below that would block that traffic.

To delete this rule from iptables it would be something like:
```
sudo iptables -D INPUT -p udp --dport 53100 -j ACCEPT
```

After that check again if it shows in the iptables output. If it doesn't, try connecting by openvpn and it should not allow you.

---

### Post by The Cog on 2020-08-15
Darkod is right. ufw generates an awful lot of "noise" rules. What it is doing here could be done in less than ten lines. But that very first rule is the one that allows OpenVPN to come in. 

The rule is before any of the usual ufw rules. So I don't think it's been written by ufw. I think maybe OpenVPN wrote it as part of its startup script. Which does make me wonder - why try to block OpenVPN when you could just turn it off? Anyway, it would be interesting to delete that rule (darkod posted the command), then see if it returns when you stop and start OpenVPN. I think it will reappear. Remember that ufw is just an iptables rule writing front end and it is perfectly possible for other things to also write iptables rules as well, with possible conflicts of interest.

I prefer the output of "sudo iptable save" or  "sudo iptables -t filter -S" to the listing format used above, but it's personal prference - same info.

> Or simply restart the openvpn service on the server, that way it will close all connections and start again fresh. 
I disagree. OpenVPN is using a single known UDP port. There is no way for iptables/conntrack to know OpenVPN is starting a "new connection". It's just resuming the conversation. You should be able to verify this by installing conntrack and watching the tracking table.

---

### Post by kazarrwahoo on 2020-08-15
Thanks darkod that did the trick. I am opening this server up to the internet and was worried that firewall wasn't effective.

Thanks so much for all the help

---

### Post by burbigo3 on 2020-08-15
I had the same issues and all these answers helped me, it works great for me now

---

### Post by SeijiSensei on 2020-08-15
I don't know how you have OpenVPN configured. In my case I use simple [static-key]("https://openvpn.net/community-resources/static-key-mini-howto/") arrangements. Even if someone could connect to the server, (which in my case they cannot since access to the port OVPN listens on is limited to my home office IP), they still can''t do anything without the proper key.

---

### Post by kazarrwahoo on 2020-08-16
The COG you were right- the entry allowing connections on 53100 is back. I had suspected that this problem relates to the script openvpn-ubuntu-install.sh

On looking at the script (I won't post the entire script unless anyone wants me to), Ican find the following code segments which seem to be relavent-

```

# Install a firewall in the rare case where one is not already available
    if ! systemctl is-active --quiet firewalld.service && ! hash iptables 2>/dev/null; then
        if [[ "$os" == "centos" || "$os" == "fedora" ]]; then
            firewall="firewalld"
            # We don't want to silently enable firewalld, so we give a subtle warning
            # If the user continues, firewalld will be installed and enabled during setup
            echo "firewalld, which is required to manage routing tables, will also be installed."
        elif [[ "$os" == "debian" || "$os" == "ubuntu" ]]; then
            # iptables is way less invasive than firewalld so no warning is given
            firewall="iptables"
        fi
    fi

```
Logic tells me (though I'm noob) that for some reason the code sets firewall = "iptables". 

Then code creates a service to add persistent entries in iptables-

```

        # Create a service to set up persistent iptables rules
        iptables_path=$(command -v iptables)
        ip6tables_path=$(command -v ip6tables)
        # nf_tables is not available as standard in OVZ kernels. So use iptables-legacy
        # if we are in OVZ, with a nf_tables backend and iptables-legacy is available.
        if [[ $(systemd-detect-virt) == "openvz" ]] && readlink -f "$(command -v iptables)" | grep -q "nft" && hash iptables-legacy 2>/dev/null; then
            iptables_path=$(command -v iptables-legacy)
            ip6tables_path=$(command -v ip6tables-legacy)
        fi
        echo "[Unit]
Before=network.target
[Service]
Type=oneshot
ExecStart=$iptables_path -t nat -A POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to $ip
ExecStart=$iptables_path -I INPUT -p $protocol --dport $port -j ACCEPT
ExecStart=$iptables_path -I FORWARD -s 10.8.0.0/24 -j ACCEPT
ExecStart=$iptables_path -I FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
ExecStop=$iptables_path -t nat -D POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to $ip
ExecStop=$iptables_path -D INPUT -p $protocol --dport $port -j ACCEPT
ExecStop=$iptables_path -D FORWARD -s 10.8.0.0/24 -j ACCEPT
ExecStop=$iptables_path -D FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT" > /etc/systemd/system/openvpn-iptables.service
        if [[ -n "$ip6" ]]; then
            echo "ExecStart=$ip6tables_path -t nat -A POSTROUTING -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to $ip6
ExecStart=$ip6tables_path -I FORWARD -s fddd:1194:1194:1194::/64 -j ACCEPT
ExecStart=$ip6tables_path -I FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
ExecStop=$ip6tables_path -t nat -D POSTROUTING -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to $ip6
ExecStop=$ip6tables_path -D FORWARD -s fddd:1194:1194:1194::/64 -j ACCEPT
ExecStop=$ip6tables_path -D FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT" >> /etc/systemd/system/openvpn-iptables.service
        fi
        echo "RemainAfterExit=yes
[Install]
WantedBy=multi-user.target" >> /etc/systemd/system/openvpn-iptables.service
        systemctl enable --now openvpn-iptables.service

```

It seems to me this is the code that messes things up- any thoughts? 
So I've back up my VM and have decided to modify the openvpn-ubuntu-install.sh file so to forget messing around with IPTables because it thinks I don't have a firewall (the code is redundant given I do have a firewall). I will post my results to this thready later.

---

### Post by kazarrwahoo on 2020-08-16
Sorry everyone I seem to be having trouble wrapping code <Code> </Code>. I will look at noob help and see if I can fix (-:

---

### Post by deadflowr on 2020-08-16
> **kazarrwahoo said:**
> Sorry everyone I seem to be having trouble wrapping code <Code> </Code>. I will look at noob help and see if I can fix (-:

Try with brackets like
[noparse]```
 
```[/noparse]

Fixed the post for you.

A nice code tag primer here:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by kazarrwahoo on 2020-08-16
It worked :D

I'm modified the script and commented out the code blocks that are redundant (I will leave the if statement that incorrectly determines my system not have a current firewall which is enabled to the owner as it is over my head) given that I know I have UFW installed and enabled. 
The step I took to 'reset' system was-
[LIST=1]
[*]uninstalled openVPN using the original openvpn-ubuntu-install.sh script.
[*]inspected the iptables- the rogue entry at top allowing connects to 53100 (against ufw rules below) was gone. If not it should be removed
[*]I removed the ufw rule allowing 53100/udp
[/LIST]

I modified the script removing the relevant code blocks (I will attach it to this thready). I ran the script again, not forgetting to make the script executable beforehand. The installation looked the same as it did prior to changing it. Everything is working. No connections allowed until I add new rule to ufs allowing 53100/udp. 

Thanks all.

---

### Post by kazarrwahoo on 2020-08-16
I can't figure out how to attach the file LOL. Any tips- the file doesn't appear after I upload it. The script is 

```
#!/bin/bash
#
# [https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)
#
# Copyright (c) 2013 Nyr. Released under the MIT License.


# Detect Debian users running the script with "sh" instead of bash
if readlink /proc/$$/exe | grep -q "dash"; then
    echo 'This installer needs to be run with "bash", not "sh".'
    exit
fi

# Discard stdin. Needed when running from an one-liner which includes a newline
read -N 999999 -t 0.001

# Detect OpenVZ 6
if [[ $(uname -r | cut -d "." -f 1) -eq 2 ]]; then
    echo "The system is running an old kernel, which is incompatible with this installer."
    exit
fi

# Detect OS
# $os_version variables aren't always in use, but are kept here for convenience
if grep -qs "ubuntu" /etc/os-release; then
    os="ubuntu"
    os_version=$(grep 'VERSION_ID' /etc/os-release | cut -d '"' -f 2 | tr -d '.')
    group_name="nogroup"
elif [[ -e /etc/debian_version ]]; then
    os="debian"
    os_version=$(grep -oE '[0-9]+' /etc/debian_version | head -1)
    group_name="nogroup"
elif [[ -e /etc/centos-release ]]; then
    os="centos"
    os_version=$(grep -oE '[0-9]+' /etc/centos-release | head -1)
    group_name="nobody"
elif [[ -e /etc/fedora-release ]]; then
    os="fedora"
    os_version=$(grep -oE '[0-9]+' /etc/fedora-release | head -1)
    group_name="nobody"
else
    echo "This installer seems to be running on an unsupported distribution.
Supported distributions are Ubuntu, Debian, CentOS, and Fedora."
    exit
fi

if [[ "$os" == "ubuntu" && "$os_version" -lt 1804 ]]; then
    echo "Ubuntu 18.04 or higher is required to use this installer.
This version of Ubuntu is too old and unsupported."
    exit
fi

if [[ "$os" == "debian" && "$os_version" -lt 9 ]]; then
    echo "Debian 9 or higher is required to use this installer.
This version of Debian is too old and unsupported."
    exit
fi

if [[ "$os" == "centos" && "$os_version" -lt 7 ]]; then
    echo "CentOS 7 or higher is required to use this installer.
This version of CentOS is too old and unsupported."
    exit
fi

# Detect environments where $PATH does not include the sbin directories
if ! grep -q sbin <<< "$PATH"; then
    echo '$PATH does not include sbin. Try using "su -" instead of "su".'
    exit
fi

if [[ "$EUID" -ne 0 ]]; then
    echo "This installer needs to be run with superuser privileges."
    exit
fi

if [[ ! -e /dev/net/tun ]] || ! ( exec 7<>/dev/net/tun ) 2>/dev/null; then
    echo "The system does not have the TUN device available.
TUN needs to be enabled before running this installer."
    exit
fi

new_client () {
    # Generates the custom client.ovpn
    {
    cat /etc/openvpn/server/client-common.txt
    echo "<ca>"
    cat /etc/openvpn/server/easy-rsa/pki/ca.crt
    echo "</ca>"
    echo "<cert>"
    sed -ne '/BEGIN CERTIFICATE/,$ p' /etc/openvpn/server/easy-rsa/pki/issued/"$client".crt
    echo "</cert>"
    echo "<key>"
    cat /etc/openvpn/server/easy-rsa/pki/private/"$client".key
    echo "</key>"
    echo "<tls-crypt>"
    sed -ne '/BEGIN OpenVPN Static key/,$ p' /etc/openvpn/server/tc.key
    echo "</tls-crypt>"
    } > ~/"$client".ovpn
}

if [[ ! -e /etc/openvpn/server/server.conf ]]; then
    clear
    echo 'Welcome to this OpenVPN road warrior installer!'
    # If system has a single IPv4, it is selected automatically. Else, ask the user
    if [[ $(ip -4 addr | grep inet | grep -vEc '127(\.[0-9]{1,3}){3}') -eq 1 ]]; then
        ip=$(ip -4 addr | grep inet | grep -vE '127(\.[0-9]{1,3}){3}' | cut -d '/' -f 1 | grep -oE '[0-9]{1,3}(\.[0-9]{1,3}){3}')
    else
        number_of_ip=$(ip -4 addr | grep inet | grep -vEc '127(\.[0-9]{1,3}){3}')
        echo
        echo "Which IPv4 address should be used?"
        ip -4 addr | grep inet | grep -vE '127(\.[0-9]{1,3}){3}' | cut -d '/' -f 1 | grep -oE '[0-9]{1,3}(\.[0-9]{1,3}){3}' | nl -s ') '
        read -p "IPv4 address [1]: " ip_number
        until [[ -z "$ip_number" || "$ip_number" =~ ^[0-9]+$ && "$ip_number" -le "$number_of_ip" ]]; do
            echo "$ip_number: invalid selection."
            read -p "IPv4 address [1]: " ip_number
        done
        [[ -z "$ip_number" ]] && ip_number="1"
        ip=$(ip -4 addr | grep inet | grep -vE '127(\.[0-9]{1,3}){3}' | cut -d '/' -f 1 | grep -oE '[0-9]{1,3}(\.[0-9]{1,3}){3}' | sed -n "$ip_number"p)
    fi
    # If $ip is a private IP address, the server must be behind NAT
    if echo "$ip" | grep -qE '^(10\.|172\.1[6789]\.|172\.2[0-9]\.|172\.3[01]\.|192\.168)'; then
        echo
        echo "This server is behind NAT. What is the public IPv4 address or hostname?"
        # Get public IP and sanitize with grep
        get_public_ip=$(grep -m 1 -oE '^[0-9]{1,3}(\.[0-9]{1,3}){3}$' <<< "$(wget -T 10 -t 1 -4qO- "http://ip1.dynupdate.no-ip.com/" || curl -m 10 -4Ls "http://ip1.dynupdate.no-ip.com/")")
        read -p "Public IPv4 address / hostname [$get_public_ip]: " public_ip
        # If the checkip service is unavailable and user didn't provide input, ask again
        until [[ -n "$get_public_ip" || -n "$public_ip" ]]; do
            echo "Invalid input."
            read -p "Public IPv4 address / hostname: " public_ip
        done
        [[ -z "$public_ip" ]] && public_ip="$get_public_ip"
    fi
    # If system has a single IPv6, it is selected automatically
    if [[ $(ip -6 addr | grep -c 'inet6 [23]') -eq 1 ]]; then
        ip6=$(ip -6 addr | grep 'inet6 [23]' | cut -d '/' -f 1 | grep -oE '([0-9a-fA-F]{0,4}:){1,7}[0-9a-fA-F]{0,4}')
    fi
    # If system has multiple IPv6, ask the user to select one
    if [[ $(ip -6 addr | grep -c 'inet6 [23]') -gt 1 ]]; then
        number_of_ip6=$(ip -6 addr | grep -c 'inet6 [23]')
        echo
        echo "Which IPv6 address should be used?"
        ip -6 addr | grep 'inet6 [23]' | cut -d '/' -f 1 | grep -oE '([0-9a-fA-F]{0,4}:){1,7}[0-9a-fA-F]{0,4}' | nl -s ') '
        read -p "IPv6 address [1]: " ip6_number
        until [[ -z "$ip6_number" || "$ip6_number" =~ ^[0-9]+$ && "$ip6_number" -le "$number_of_ip6" ]]; do
            echo "$ip6_number: invalid selection."
            read -p "IPv6 address [1]: " ip6_number
        done
        [[ -z "$ip6_number" ]] && ip6_number="1"
        ip6=$(ip -6 addr | grep 'inet6 [23]' | cut -d '/' -f 1 | grep -oE '([0-9a-fA-F]{0,4}:){1,7}[0-9a-fA-F]{0,4}' | sed -n "$ip6_number"p)
    fi
    echo
    echo "Which protocol should OpenVPN use?"
    echo "   1) UDP (recommended)"
    echo "   2) TCP"
    read -p "Protocol [1]: " protocol
    until [[ -z "$protocol" || "$protocol" =~ ^[12]$ ]]; do
        echo "$protocol: invalid selection."
        read -p "Protocol [1]: " protocol
    done
    case "$protocol" in
        1|"") 
        protocol=udp
        ;;
        2) 
        protocol=tcp
        ;;
    esac
    echo
    echo "What port should OpenVPN listen to?"
    read -p "Port [1194]: " port
    until [[ -z "$port" || "$port" =~ ^[0-9]+$ && "$port" -le 65535 ]]; do
        echo "$port: invalid port."
        read -p "Port [1194]: " port
    done
    [[ -z "$port" ]] && port="1194"
    echo
    echo "Select a DNS server for the clients:"
    echo "   1) Current system resolvers"
    echo "   2) Google"
    echo "   3) 1.1.1.1"
    echo "   4) OpenDNS"
    echo "   5) Quad9"
    echo "   6) AdGuard"
    read -p "DNS server [1]: " dns
    until [[ -z "$dns" || "$dns" =~ ^[1-6]$ ]]; do
        echo "$dns: invalid selection."
        read -p "DNS server [1]: " dns
    done
    echo
    echo "Enter a name for the first client:"
    read -p "Name [client]: " unsanitized_client
    # Allow a limited set of characters to avoid conflicts
    client=$(sed 's/[^0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ_-]/_/g' <<< "$unsanitized_client")
    [[ -z "$client" ]] && client="client"
    echo
    echo "OpenVPN installation is ready to begin."
    # Install a firewall in the rare case where one is not already available
    # if ! systemctl is-active --quiet firewalld.service && ! hash iptables 2>/dev/null; then
    #    if [[ "$os" == "centos" || "$os" == "fedora" ]]; then
    #        firewall="firewalld"
    #        # We don't want to silently enable firewalld, so we give a subtle warning
    #        # If the user continues, firewalld will be installed and enabled during setup
    #        echo "firewalld, which is required to manage routing tables, will also be installed."
    #    elif [[ "$os" == "debian" || "$os" == "ubuntu" ]]; then
    #        # iptables is way less invasive than firewalld so no warning is given
    #        firewall="iptables"
    #    fi
    # fi
    read -n1 -r -p "Press any key to continue..."
    # If running inside a container, disable LimitNPROC to prevent conflicts
    if systemd-detect-virt -cq; then
        mkdir /etc/systemd/system/openvpn-server@server.service.d/ 2>/dev/null
        echo "[Service]
LimitNPROC=infinity" > /etc/systemd/system/openvpn-server@server.service.d/disable-limitnproc.conf
    fi
    if [[ "$os" = "debian" || "$os" = "ubuntu" ]]; then
        apt-get update
    #   omnit the firewall variable (hopefully this is the one!)
    #    apt-get install -y openvpn openssl ca-certificates $firewall
        apt-get install -y openvpn openssl ca-certificates
    elif [[ "$os" = "centos" ]]; then
        yum install -y epel-release
        yum install -y openvpn openssl ca-certificates tar $firewall
    else
        # Else, OS must be Fedora
        dnf install -y openvpn openssl ca-certificates tar $firewall
    fi
    # following code redundant
    # If firewalld was just installed, enable it
    # if [[ "$firewall" == "firewalld" ]]; then
    #    systemctl enable --now firewalld.service
    # fi
    # Get easy-rsa
    easy_rsa_url='https://github.com/OpenVPN/easy-rsa/releases/download/v3.0.7/EasyRSA-3.0.7.tgz'
    mkdir -p /etc/openvpn/server/easy-rsa/
    { wget -qO- "$easy_rsa_url" 2>/dev/null || curl -sL "$easy_rsa_url" ; } | tar xz -C /etc/openvpn/server/easy-rsa/ --strip-components 1
    chown -R root:root /etc/openvpn/server/easy-rsa/
    cd /etc/openvpn/server/easy-rsa/
    # Create the PKI, set up the CA and the server and client certificates
    ./easyrsa init-pki
    ./easyrsa --batch build-ca nopass
    EASYRSA_CERT_EXPIRE=3650 ./easyrsa build-server-full server nopass
    EASYRSA_CERT_EXPIRE=3650 ./easyrsa build-client-full "$client" nopass
    EASYRSA_CRL_DAYS=3650 ./easyrsa gen-crl
    # Move the stuff we need
    cp pki/ca.crt pki/private/ca.key pki/issued/server.crt pki/private/server.key pki/crl.pem /etc/openvpn/server
    # CRL is read with each client connection, while OpenVPN is dropped to nobody
    chown nobody:"$group_name" /etc/openvpn/server/crl.pem
    # Without +x in the directory, OpenVPN can't run a stat() on the CRL file
    chmod o+x /etc/openvpn/server/
    # Generate key for tls-crypt
    openvpn --genkey --secret /etc/openvpn/server/tc.key
    # Create the DH parameters file using the predefined ffdhe2048 group
    echo '-----BEGIN DH PARAMETERS-----
MIIBCAKCAQEA//////////+t+FRYortKmq/cViAnPTzx2LnFg84tNpWp4TZBFGQz
+8yTnc4kmz75fS/jY2MMddj2gbICrsRhetPfHtXV/WVhJDP1H18GbtCFY2VVPe0a
87VXE15/V8k1mE8McODmi3fipona8+/och3xWKE2rec1MKzKT0g6eXq8CrGCsyT7
YdEIqUuyyOP7uWrat2DX9GgdT0Kj3jlN9K5W7edjcrsZCwenyO4KbXCeAvzhzffi
7MA0BM0oNC9hkXL+nOmFg/+OTxIy7vKBg8P+OxtMb61zO7X8vC7CIAXFjvGDfRaD
ssbzSibBsu/6iGtCOGEoXJf//////////wIBAg==
-----END DH PARAMETERS-----' > /etc/openvpn/server/dh.pem
    # Generate server.conf
    echo "local $ip
port $port
proto $protocol
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
auth SHA512
tls-crypt tc.key
topology subnet
server 10.8.0.0 255.255.255.0" > /etc/openvpn/server/server.conf
    # IPv6
    if [[ -z "$ip6" ]]; then
        echo 'push "redirect-gateway def1 bypass-dhcp"' >> /etc/openvpn/server/server.conf
    else
        echo 'server-ipv6 fddd:1194:1194:1194::/64' >> /etc/openvpn/server/server.conf
        echo 'push "redirect-gateway def1 ipv6 bypass-dhcp"' >> /etc/openvpn/server/server.conf
    fi
    echo 'ifconfig-pool-persist ipp.txt' >> /etc/openvpn/server/server.conf
    # DNS
    case "$dns" in
        1|"")
            # Locate the proper resolv.conf
            # Needed for systems running systemd-resolved
            if grep -q '^nameserver 127.0.0.53' "/etc/resolv.conf"; then
                resolv_conf="/run/systemd/resolve/resolv.conf"
            else
                resolv_conf="/etc/resolv.conf"
            fi
            # Obtain the resolvers from resolv.conf and use them for OpenVPN
            grep -v '^#\|^;' "$resolv_conf" | grep '^nameserver' | grep -oE '[0-9]{1,3}(\.[0-9]{1,3}){3}' | while read line; do
                echo "push \"dhcp-option DNS $line\"" >> /etc/openvpn/server/server.conf
            done
        ;;
        2)
            echo 'push "dhcp-option DNS 8.8.8.8"' >> /etc/openvpn/server/server.conf
            echo 'push "dhcp-option DNS 8.8.4.4"' >> /etc/openvpn/server/server.conf
        ;;
        3)
            echo 'push "dhcp-option DNS 1.1.1.1"' >> /etc/openvpn/server/server.conf
            echo 'push "dhcp-option DNS 1.0.0.1"' >> /etc/openvpn/server/server.conf
        ;;
        4)
            echo 'push "dhcp-option DNS 208.67.222.222"' >> /etc/openvpn/server/server.conf
            echo 'push "dhcp-option DNS 208.67.220.220"' >> /etc/openvpn/server/server.conf
        ;;
        5)
            echo 'push "dhcp-option DNS 9.9.9.9"' >> /etc/openvpn/server/server.conf
            echo 'push "dhcp-option DNS 149.112.112.112"' >> /etc/openvpn/server/server.conf
        ;;
        6)
            echo 'push "dhcp-option DNS 176.103.130.130"' >> /etc/openvpn/server/server.conf
            echo 'push "dhcp-option DNS 176.103.130.131"' >> /etc/openvpn/server/server.conf
        ;;
    esac
    echo "keepalive 10 120
cipher AES-256-CBC
user nobody
group $group_name
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem" >> /etc/openvpn/server/server.conf
    if [[ "$protocol" = "udp" ]]; then
        echo "explicit-exit-notify" >> /etc/openvpn/server/server.conf
    fi
    # Enable net.ipv4.ip_forward for the system
    echo 'net.ipv4.ip_forward=1' > /etc/sysctl.d/30-openvpn-forward.conf
    # Enable without waiting for a reboot or service restart
    echo 1 > /proc/sys/net/ipv4/ip_forward
    if [[ -n "$ip6" ]]; then
        # Enable net.ipv6.conf.all.forwarding for the system
        echo "net.ipv6.conf.all.forwarding=1" >> /etc/sysctl.d/30-openvpn-forward.conf
        # Enable without waiting for a reboot or service restart
        echo 1 > /proc/sys/net/ipv6/conf/all/forwarding
    fi
    # this if block redundant
#################################################################################################################
    # if systemctl is-active --quiet firewalld.service; then
        # Using both permanent and not permanent rules to avoid a firewalld
        # reload.
        # We don't use --add-service=openvpn because that would only work with
        # the default port and protocol.
    #    firewall-cmd --add-port="$port"/"$protocol"
    #    firewall-cmd --zone=trusted --add-source=10.8.0.0/24
    #    firewall-cmd --permanent --add-port="$port"/"$protocol"
    #    firewall-cmd --permanent --zone=trusted --add-source=10.8.0.0/24
        # Set NAT for the VPN subnet
    #    firewall-cmd --direct --add-rule ipv4 nat POSTROUTING 0 -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to "$ip"
    #    firewall-cmd --permanent --direct --add-rule ipv4 nat POSTROUTING 0 -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to "$ip"
    #    if [[ -n "$ip6" ]]; then
    #        firewall-cmd --zone=trusted --add-source=fddd:1194:1194:1194::/64
    #        firewall-cmd --permanent --zone=trusted --add-source=fddd:1194:1194:1194::/64
    #        firewall-cmd --direct --add-rule ipv6 nat POSTROUTING 0 -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to "$ip6"
    #        firewall-cmd --permanent --direct --add-rule ipv6 nat POSTROUTING 0 -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to "$ip6"
    #    fi
#    else
        # Create a service to set up persistent iptables rules
#        iptables_path=$(command -v iptables)
#        ip6tables_path=$(command -v ip6tables)
        # nf_tables is not available as standard in OVZ kernels. So use iptables-legacy
        # if we are in OVZ, with a nf_tables backend and iptables-legacy is available.
#        if [[ $(systemd-detect-virt) == "openvz" ]] && readlink -f "$(command -v iptables)" | grep -q "nft" && hash iptables-legacy 2>/dev/null; then
#            iptables_path=$(command -v iptables-legacy)
#            ip6tables_path=$(command -v ip6tables-legacy)
#        fi
#        echo "[Unit]
# Before=network.target
# [Service]
# Type=oneshot
# ExecStart=$iptables_path -t nat -A POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to $ip
# ExecStart=$iptables_path -I INPUT -p $protocol --dport $port -j ACCEPT
# ExecStart=$iptables_path -I FORWARD -s 10.8.0.0/24 -j ACCEPT
# ExecStart=$iptables_path -I FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
# ExecStop=$iptables_path -t nat -D POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to $ip
# ExecStop=$iptables_path -D INPUT -p $protocol --dport $port -j ACCEPT
# ExecStop=$iptables_path -D FORWARD -s 10.8.0.0/24 -j ACCEPT
# ExecStop=$iptables_path -D FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT" > /etc/systemd/system/openvpn-iptables.service
#        if [[ -n "$ip6" ]]; then
#            echo "ExecStart=$ip6tables_path -t nat -A POSTROUTING -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to $ip6
# ExecStart=$ip6tables_path -I FORWARD -s fddd:1194:1194:1194::/64 -j ACCEPT
# ExecStart=$ip6tables_path -I FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
# ExecStop=$ip6tables_path -t nat -D POSTROUTING -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to $ip6
# ExecStop=$ip6tables_path -D FORWARD -s fddd:1194:1194:1194::/64 -j ACCEPT
# ExecStop=$ip6tables_path -D FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT" >> /etc/systemd/system/openvpn-iptables.service
#        fi
#        echo "RemainAfterExit=yes
# [Install]
# WantedBy=multi-user.target" >> /etc/systemd/system/openvpn-iptables.service
#        systemctl enable --now openvpn-iptables.service
#    fi
################################################################################################################################################

    # If SELinux is enabled and a custom port was selected, we need this
    if sestatus 2>/dev/null | grep "Current mode" | grep -q "enforcing" && [[ "$port" != 1194 ]]; then
        # Install semanage if not already present
        if ! hash semanage 2>/dev/null; then
            if [[ "$os_version" -eq 7 ]]; then
                # Centos 7
                yum install -y policycoreutils-python
            else
                # CentOS 8 or Fedora
                dnf install -y policycoreutils-python-utils
            fi
        fi
        semanage port -a -t openvpn_port_t -p "$protocol" "$port"
    fi
    # If the server is behind NAT, use the correct IP address
    [[ -n "$public_ip" ]] && ip="$public_ip"
    # client-common.txt is created so we have a template to add further users later
    echo "client
dev tun
proto $protocol
remote $ip $port
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
auth SHA512
cipher AES-256-CBC
ignore-unknown-option block-outside-dns
block-outside-dns
verb 3" > /etc/openvpn/server/client-common.txt
    # Enable and start the OpenVPN service
    systemctl enable --now [email]openvpn-server@server.servic[/email]e
    # Generates the custom client.ovpn
    new_client
    echo
    echo "Finished!"
    echo
    echo "The client configuration is available in:" ~/"$client.ovpn"
    echo "New clients can be added by running this script again."
else
    clear
    echo "OpenVPN is already installed."
    echo
    echo "Select an option:"
    echo "   1) Add a new client"
    echo "   2) Revoke an existing client"
    echo "   3) Remove OpenVPN"
    echo "   4) Exit"
    read -p "Option: " option
    until [[ "$option" =~ ^[1-4]$ ]]; do
        echo "$option: invalid selection."
        read -p "Option: " option
    done
    case "$option" in
        1)
            echo
            echo "Provide a name for the client:"
            read -p "Name: " unsanitized_client
            client=$(sed 's/[^0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ_-]/_/g' <<< "$unsanitized_client")
            while [[ -z "$client" || -e /etc/openvpn/server/easy-rsa/pki/issued/"$client".crt ]]; do
                echo "$client: invalid name."
                read -p "Name: " unsanitized_client
                client=$(sed 's/[^0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ_-]/_/g' <<< "$unsanitized_client")
            done
            cd /etc/openvpn/server/easy-rsa/
            EASYRSA_CERT_EXPIRE=3650 ./easyrsa build-client-full "$client" nopass
            # Generates the custom client.ovpn
            new_client
            echo
            echo "$client added. Configuration available in:" ~/"$client.ovpn"
            exit
        ;;
        2)
            # This option could be documented a bit better and maybe even be simplified
            # ...but what can I say, I want some sleep too
            number_of_clients=$(tail -n +2 /etc/openvpn/server/easy-rsa/pki/index.txt | grep -c "^V")
            if [[ "$number_of_clients" = 0 ]]; then
                echo
                echo "There are no existing clients!"
                exit
            fi
            echo
            echo "Select the client to revoke:"
            tail -n +2 /etc/openvpn/server/easy-rsa/pki/index.txt | grep "^V" | cut -d '=' -f 2 | nl -s ') '
            read -p "Client: " client_number
            until [[ "$client_number" =~ ^[0-9]+$ && "$client_number" -le "$number_of_clients" ]]; do
                echo "$client_number: invalid selection."
                read -p "Client: " client_number
            done
            client=$(tail -n +2 /etc/openvpn/server/easy-rsa/pki/index.txt | grep "^V" | cut -d '=' -f 2 | sed -n "$client_number"p)
            echo
            read -p "Confirm $client revocation? [y/N]: " revoke
            until [[ "$revoke" =~ ^[yYnN]*$ ]]; do
                echo "$revoke: invalid selection."
                read -p "Confirm $client revocation? [y/N]: " revoke
            done
            if [[ "$revoke" =~ ^[yY]$ ]]; then
                cd /etc/openvpn/server/easy-rsa/
                ./easyrsa --batch revoke "$client"
                EASYRSA_CRL_DAYS=3650 ./easyrsa gen-crl
                rm -f /etc/openvpn/server/crl.pem
                cp /etc/openvpn/server/easy-rsa/pki/crl.pem /etc/openvpn/server/crl.pem
                # CRL is read with each client connection, when OpenVPN is dropped to nobody
                chown nobody:"$group_name" /etc/openvpn/server/crl.pem
                echo
                echo "$client revoked!"
            else
                echo
                echo "$client revocation aborted!"
            fi
            exit
        ;;
        3)
            echo
            read -p "Confirm OpenVPN removal? [y/N]: " remove
            until [[ "$remove" =~ ^[yYnN]*$ ]]; do
                echo "$remove: invalid selection."
                read -p "Confirm OpenVPN removal? [y/N]: " remove
            done
            if [[ "$remove" =~ ^[yY]$ ]]; then
                port=$(grep '^port ' /etc/openvpn/server/server.conf | cut -d " " -f 2)
                protocol=$(grep '^proto ' /etc/openvpn/server/server.conf | cut -d " " -f 2)
# nothing here to remove (redundant)################################################################################################################
            #    if systemctl is-active --quiet firewalld.service; then
            #        ip=$(firewall-cmd --direct --get-rules ipv4 nat POSTROUTING | grep '\-s 10.8.0.0/24 '"'"'!'"'"' -d 10.8.0.0/24' | grep -oE '[^ ]+$')
            #        # Using both permanent and not permanent rules to avoid a firewalld reload.
            #        firewall-cmd --remove-port="$port"/"$protocol"
            #        firewall-cmd --zone=trusted --remove-source=10.8.0.0/24
            #        firewall-cmd --permanent --remove-port="$port"/"$protocol"
            #        firewall-cmd --permanent --zone=trusted --remove-source=10.8.0.0/24
            #        firewall-cmd --direct --remove-rule ipv4 nat POSTROUTING 0 -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to "$ip"
            #        firewall-cmd --permanent --direct --remove-rule ipv4 nat POSTROUTING 0 -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to "$ip"
            #        if grep -qs "server-ipv6" /etc/openvpn/server/server.conf; then
            #            ip6=$(firewall-cmd --direct --get-rules ipv6 nat POSTROUTING | grep '\-s fddd:1194:1194:1194::/64 '"'"'!'"'"' -d fddd:1194:1194:1194::/64' | grep -oE '[^ ]+$')
            #            firewall-cmd --zone=trusted --remove-source=fddd:1194:1194:1194::/64
            #            firewall-cmd --permanent --zone=trusted --remove-source=fddd:1194:1194:1194::/64
            #            firewall-cmd --direct --remove-rule ipv6 nat POSTROUTING 0 -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to "$ip6"
            #            firewall-cmd --permanent --direct --remove-rule ipv6 nat POSTROUTING 0 -s fddd:1194:1194:1194::/64 ! -d fddd:1194:1194:1194::/64 -j SNAT --to "$ip6"
            #        fi
            #    else
            #        systemctl disable --now openvpn-iptables.service
            #        rm -f /etc/systemd/system/openvpn-iptables.service
            #    fi
#######################################################################################################################################################
                if sestatus 2>/dev/null | grep "Current mode" | grep -q "enforcing" && [[ "$port" != 1194 ]]; then
                    semanage port -d -t openvpn_port_t -p "$protocol" "$port"
                fi
                systemctl disable --now [email]openvpn-server@server.servic[/email]e
                rm -rf /etc/openvpn/server
                rm -f /etc/systemd/system/openvpn-server@server.service.d/disable-limitnproc.conf
                rm -f /etc/sysctl.d/30-openvpn-forward.conf
                if [[ "$os" = "debian" || "$os" = "ubuntu" ]]; then
                    apt-get remove --purge -y openvpn
                else
                    # Else, OS must be CentOS or Fedora
                    yum remove -y openvpn
                fi
                echo
                echo "OpenVPN removed!"
            else
                echo
                echo "OpenVPN removal aborted!"
            fi
            exit
        ;;
        4)
            exit
        ;;
    esac
fi
```

---

### Post by kazarrwahoo on 2020-08-16
Thanks deadflower :p

---


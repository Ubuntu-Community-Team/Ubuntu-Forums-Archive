---
title: "share internet connection to clint from  server"
date: 2011-07-19
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-07-19
:(Thanks for the help from you all  :(, now am back to the same issue internet connection sharing using NAT .I use the following command it work for me for an hours ..
```

sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
```

```
sudo iptables-save | sudo tee /etc/iptables.sav
```Edit /etc/rc.local and add the following lines before the "exit 0" line: 
```
iptables-restore < /etc/iptables.sav
``````
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```After restarting my server NAT is not working .client system can ping to  my server through the server's eth1 ip but Internet is not accessible to the client pcs .I think its my fault but I cant rectify what is the issue ..please any give me your configuration ....and also I wish to implement the attached structure in my institution if it any wrong on there please suggest me to change .......

---

### Post by Rakeshvijayan on 2011-07-19
structure wish to implement

---

### Post by Rakeshvijayan on 2011-07-20
Hmmm am alone here ok 



```
echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n" DEPMOD=/sbin/depmod MODPROBE=/sbin/modprobe  EXTIF="eth0" INTIF="eth1" #INTIF2="eth0" echo "   External Interface:  $EXTIF" echo "   Internal Interface:  $INTIF"  #====================================================================== #== No editing beyond this line is required for initial MASQ testing ==  echo -en "   loading modules: " echo "  - Verifying that all kernel modules are ok" $DEPMOD -a echo "----------------------------------------------------------------------" echo -en "ip_tables, " $MODPROBE ip_tables echo -en "nf_conntrack, "  $MODPROBE nf_conntrack echo -en "nf_conntrack_ftp, "  $MODPROBE nf_conntrack_ftp echo -en "nf_conntrack_irc, "  $MODPROBE nf_conntrack_irc echo -en "iptable_nat, " $MODPROBE iptable_nat echo -en "nf_nat_ftp, " $MODPROBE nf_nat_ftp echo "----------------------------------------------------------------------" echo -e "   Done loading modules.\n" echo "   Enabling forwarding.." echo "1" > /proc/sys/net/ipv4/ip_forward echo "   Enabling DynamicAddr.." echo "1" > /proc/sys/net/ipv4/ip_dynaddr  echo "   Clearing any existing rules and setting default policy.."  iptables-restore <<-EOF *nat -A POSTROUTING -o "$EXTIF" -j MASQUERADE COMMIT *filter :INPUT ACCEPT [0:0] :FORWARD DROP [0:0] :OUTPUT ACCEPT [0:0] -A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT  -A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT -A FORWARD -j LOG COMMIT EOF  echo -e "\nrc.firewall-iptables v$FWVER done.\n"
```



This script help to share the connection but after restart the server it  not allow to share ,so I am force to run the script againg```
sudo sh nat.sh
```I think last command for start this script at boot time is not work for me ```
[If ping responds, make our new script bootable so we don't have to run the script every time we restart. 

[LIST]
[*][CODE]sudo cp nat.sh /etc/init.d/ sudo ln -s /etc/init.d/nat.sh /etc/rc2.d/S95masquradescript
```
[/LIST]
As  a final test, restart your computer and test to see if you still have  the same functionality. If so then congratulations! If not then make  sure you followed the above correctly so the script is bootable. /CODE]

---


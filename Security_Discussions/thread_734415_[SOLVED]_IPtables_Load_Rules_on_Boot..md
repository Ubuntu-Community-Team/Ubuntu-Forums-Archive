---
title: "[SOLVED] IPtables Load Rules on Boot."
date: 2008-03-24
forum: Security Discussions
---

### Post by EMCGFX on 2008-03-24
I have boot problem whenever I due this for my firewall rules.

First I save it to:
```
sh -c "iptables-save > /etc/iptables.rules"
```

Then I add this two lines to my /etc/network/interfaces file.
```
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.rules
```

After that, whenever I restart my Ubuntu. It says network interfaces FAILED. Does any one know what is the deal with this ? Btw, I use Ubuntu 7.10 stable right now. Each time I need to use vi to remove this two lines and reboot. Then it boots fine, but my rules are not loaded on boot ;-( Any help would be great. Thanks a lot.

My iptables.rules file:
```
#!/bin/bash

iptables -F
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -N LOGNDROP

## Allow loopback port
iptables -I INPUT 1 -i lo -j ACCEPT

## Allowing Established Sessions
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Blocking Traffic
iptables -A INPUT -j DROP

## Logging and Blocking
iptables -A INPUT -j LOGNDROP
iptables -A LOGNDROP -p tcp -m limit --limit 5/min -j LOG --log-prefix "Denied TCP: " --log-level 7
iptables -A LOGNDROP -p udp -m limit --limit 5/min -j LOG --log-prefix "Denied UDP: " --log-level 7
iptables -A LOGNDROP -p icmp -m limit --limit 5/min -j LOG --log-prefix "Denied ICMP: " --log-level 7
iptables -A LOGNDROP -j DROP

## Save firewall rules
sh -c "iptables-save > /etc/iptables.rules"
```

Btw, I had the same problem when I was trying out Ubuntu 8.04 Alpha 6. :confused:

:x

---

### Post by Sam Lars on 2008-03-24
Well it looks like the script is overwriting itself with that last command?
I have mine set up to load as a service from /etc/init.d

---

### Post by EMCGFX on 2008-03-24
QUOTE, I have mine set up to load as a service from /etc/init.d

How would I due that ?


QUOTE, Well it looks like the script is overwriting itself with that last command?

You mean this command >
## Save firewall rules
sh -c "iptables-save > /etc/iptables.rules"

---

### Post by Sam Lars on 2008-03-24
Here's what I have for my /etc/init.d/firewall
```
#!/bin/bash

RETVAL=0

# To start the firewall
start() {
	echo -n "Iptables rules creation: "
	/etc/firewall.bash
	RETVAL=0
}

# To stop the firewall
stop() {
	echo -n "Removing all iptables rules: "
	/etc/flush_iptables.bash
	RETVAL=0
}

case $1 in
	start)
		start
		;;
	stop)
		stop
		;;
	restart)
		stop
		start
		;;
	status)
		/sbin/iptables -L
		/sbin/iptables -t nat -L
		RETVAL=0
		;;
	*)
		echo "Usage: firewall (start|stop|restart|status)"
		RETVAL=1
esac

exit
```

And that points to this file, /etc/firewall.bash

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe iptable_filter
modprobe iptable_nat

# Remove all rules and chains
iptables -F
iptables -X
iptables-restore /home/user/firewall

# End message
echo " [End iptables rulesetting]"
```

And that points to my firewall configuration in /home/user/firewall, like what you have already.

I'm sure there are different/simpler ways of doing this but I just found instructions for this and it works well for me.

---

### Post by tech0007 on 2008-03-24
Hi.  I had mine starting load from /etc/rc.local.  Is that ok? If not, can I copy what you posted above? 

Thanks!

---

### Post by EMCGFX on 2008-03-24
> **tech0007 said:**
> Hi.  I had mine starting load from /etc/rc.local.  Is that ok? If not, can I copy what you posted above? 

Thanks!

:lolflag: of course you can copy! If you could not he would not of posted it. This is linux world bratha, everything is free and open unlike windows :)

---

### Post by EMCGFX on 2008-03-24
@Sam Lars, Thanks. But I prefer my way, and you are right it is looping at last command will try removing it. LOL I can't belive I did not realize that in the first place, I guess I am blind.

---

### Post by cdenley on 2008-03-25
/etc/rc.local is loaded after the network, so there would be a few seconds with no firewall protection. For /etc/init.d, it depends on the sequence number you use with update-rc.d when you install the script. The network pre-up method is probably best.

---

### Post by The Cog on 2008-03-25
Your file is the wrong format for iptables-restore. The rules you posted are a shell script, but iptables-save and iptables-restore use a different file format. In fact, that last line in the script ensures that if you ever run the file as a shell script, it will overwrite itself with the iptables-save format.

I suggest you either:

1) Use **iptables-save > /etc/iptables.rules** to save the config and **iptables-restore < /etc/iptables.rules** to restore it. This requires that some other mechanism (by hand perhaps) configures the running rules that then get saved.

or 2)
Forget iptables-save and iptables-restore and just use a shell script like the one you posted. Note that your** iptables -F **on the first line ensures that the rules are cleared immediately before re-entering them, so there is no daner of building up lots of duplicate entries.

P.S. Personally, I have settled on option 1 for now, because iptables-restore and iptables-save between them lose any comment lines that I might wish to put in the config file. Of course, you could always just use iptables-restore, and edit that file by hand when you want to make firewall changes. This is my personal second preference, despite warnings in the manual that say not to edit the file by hand.

---

### Post by EMCGFX on 2008-03-26
It says I have an error when I am trying to restore the rules.

root@home:~# iptables-restore < /etc/iptables.rules 
iptables-restore: line 3 failed

and any line I comment out gives next line error, exp: line 4 failed... and so on.

my rules:
```
#!/bin/bash

iptables -F
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

## Allow loopback port
iptables -I INPUT 1 -i lo -j ACCEPT

## Allowing Established Sessions
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Blocking Traffic
iptables -A INPUT -j DROP
```

---

### Post by Sam Lars on 2008-03-26
As The Cog said, that file is not the right format to use with direct iptables commands like that.
Here's what mine looks like:

```
# Generated by iptables-save v1.3.6 on Fri Feb  1 21:09:02 2008
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
#Localnet
-A INPUT -s 192.168.1.0/22 -j ACCEPT
#Spammers
-A INPUT -s 61.57.137.54 -j DROP
#FTP,Apt-cache
-A INPUT -p tcp -m multiport --dports 20,21,3000:3010 -j ACCEPT 
-A INPUT -p tcp -m multiport --dports 6881:6889 -j ACCEPT 
-A INPUT -p udp -m multiport --dports 6881:6889 -j ACCEPT 
-A INPUT -p udp -m multiport --sports 6881:6889 -j ACCEPT
-A INPUT -p tcp -m multiport --sports 6881:6889 -j ACCEPT
#-A INPUT -s 192.168.1.0/255.255.255.0 -p tcp -m multiport --dports 135,139,445,3142,4000,4002,31416,2049,111,22 -j ACCEPT 
#-A INPUT -s 192.168.1.0/255.255.255.0 -p udp -m multiport --dports 135,137,138,139,445,2049,3142,4000,4002,111 -j ACCEPT 
-A INPUT -j LOG 
-A INPUT -j DROP 
-A OUTPUT -j ACCEPT 
COMMIT
# Completed on Fri Feb  1 21:09:02 2008
```

---

### Post by EMCGFX on 2008-03-26
Tryed that same probelm, wont boot. Here is my /etc/network/interfaces files

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iptables-restore < /etc/iptables.rules
```

I've also tried this, did not work:
```
  pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules
```

---

### Post by Sam Lars on 2008-03-26
Does it still give you the error in line X error?
What happened when you tried those pre-up post-down lines?  Did you do those lines exactly?  In your initial post, both used a <, just want to make sure.

---

### Post by cdenley on 2008-03-27
Why are you editing /etc/network/interfaces? Why are you piping a bash script to iptables-restore? You should only pipe files to iptables-restore which are created with the output of iptables-save. Network pre-up scripts should go in /etc/network/if-pre-up.d. Post-down scripts go in /etc/network/if-post-down.d.

---

### Post by EMCGFX on 2008-03-27
OK, I fixed it ;-) The problem was completely different :lolflag:

Here is my original /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet
```

Here is the file after I've edited it.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
```

Now I've tried using this line bellow withouth any luck, my system was stoped booting all the time. I've saved rules properly too, nothing helped:
```
pre-up iptables-restore < /etc/iptables.rules
```

It worked only when I un-comment this line:
```
iface eth0 inet dhcp
```

By default it was commented :confused:



So now, this is what I did complete description for new people who need it. NOTE: For all of this steps root access needed, so use sudo -i to loging.

1. You can ether create a script or type in the rules manually into the firewall. I've created a script, for easy integration of rules next time, or whenever I edit it.

My iptables firewall rules, I called it "iptables.rules.sh"
```
#!/bin/bash

## Flash all rules from firewall
iptables -F

## Allow all traffic by default
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

## Allow established sessions
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Block all incoming traffic
iptables -A INPUT -j DROP

## Allow local loopback
iptables -I INPUT 1 -i lo -j ACCEPT
```

2. Go to your terminal window, and type this commands. Replace "dir" with your path to the file. This makes your script executable.
```
chmod +x /dir/iptables.rules.sh
```

3. Execute your "iptables.rules.sh" by typing. Again, replace "dir" with your file path.
```
/dir/iptables.rules.sh
iptables-save > /etc/iptables.rules
```

4. Edit your /etc/network/interfaces file:
```
gedit /etc/network/interfaces
```

and add this lines to your file, it should look something simular to this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
```

Note this line bellow, if's commented with # un-comment it. Otherwise, you might have problems like me with booting. It looks like not everyone as me have the same problem. Un-commenting this helped me booting correctly and loading my firewall rules ;-)
```
iface eth0 inet dhcp
```

Recovery in case you have problems booting into your ubuntu.
1. On boot click ESC when you see grab counter.
2. Choose to boot into recovery mode.
3. When you see command line where you can type, simply type
```
vi /etc/network/interfaces
```
4. Then you should see your added line:
```
pre-up iptables-restore < /etc/iptables.rules
```
5. Remove it, by moving to it with arrows and using Backspace to delete it.
6. Press Shift+: (symbol, it should be right besides your L button)
7. then type letter "w" without quotes and ENTER to write to file.
8. Press Shift+: (again), but this time type letter "q" for exiting vi.
9. Type ether reboot or halt (halt is for shut down your pc).
10. When you reboot, you should be able to boot properly into your ubuntu. You can type "sudo iptables -L" to check if your rules loaded.

Anyways, this is how I did it ;-) Thank you everyone for helping :guitar: *Now I am off to writing some more advanced rules for my firewall, hehe*

---

### Post by DigitalDuality on 2008-05-14
> **EMCGFX said:**
> OK, I fixed it ;-) The problem was completely different :lolflag:

Here is my original /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet
```

Here is the file after I've edited it.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
```

Now I've tried using this line bellow withouth any luck, my system was stoped booting all the time. I've saved rules properly too, nothing helped:
```
pre-up iptables-restore < /etc/iptables.rules
```

It worked only when I un-comment this line:
```
iface eth0 inet dhcp
```

By default it was commented :confused:



So now, this is what I did complete description for new people who need it. NOTE: For all of this steps root access needed, so use sudo -i to loging.

1. You can ether create a script or type in the rules manually into the firewall. I've created a script, for easy integration of rules next time, or whenever I edit it.

My iptables firewall rules, I called it "iptables.rules.sh"
```
#!/bin/bash

## Flash all rules from firewall
iptables -F

## Allow all traffic by default
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

## Allow established sessions
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Block all incoming traffic
iptables -A INPUT -j DROP

## Allow local loopback
iptables -I INPUT 1 -i lo -j ACCEPT
```

2. Go to your terminal window, and type this commands. Replace "dir" with your path to the file. This makes your script executable.
```
chmod +x /dir/iptables.rules.sh
```

3. Execute your "iptables.rules.sh" by typing. Again, replace "dir" with your file path.
```
/dir/iptables.rules.sh
iptables-save > /etc/iptables.rules
```

4. Edit your /etc/network/interfaces file:
```
gedit /etc/network/interfaces
```

and add this lines to your file, it should look something simular to this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
```

Note this line bellow, if's commented with # un-comment it. Otherwise, you might have problems like me with booting. It looks like not everyone as me have the same problem. Un-commenting this helped me booting correctly and loading my firewall rules ;-)
```
iface eth0 inet dhcp
```

Recovery in case you have problems booting into your ubuntu.
1. On boot click ESC when you see grab counter.
2. Choose to boot into recovery mode.
3. When you see command line where you can type, simply type
```
vi /etc/network/interfaces
```
4. Then you should see your added line:
```
pre-up iptables-restore < /etc/iptables.rules
```
5. Remove it, by moving to it with arrows and using Backspace to delete it.
6. Press Shift+: (symbol, it should be right besides your L button)
7. then type letter "w" without quotes and ENTER to write to file.
8. Press Shift+: (again), but this time type letter "q" for exiting vi.
9. Type ether reboot or halt (halt is for shut down your pc).
10. When you reboot, you should be able to boot properly into your ubuntu. You can type "sudo iptables -L" to check if your rules loaded.

Anyways, this is how I did it ;-) Thank you everyone for helping :guitar: *Now I am off to writing some more advanced rules for my firewall, hehe*

lets say i did an iptables save into a file and i simply want this file to be restored upon every single boot.

would adding that pre-up iptables-restore < /etc/iptables.rules to /etc/network/interfaces in the appropriate place  do the trick? Or did i under complicate you're entire post?

---


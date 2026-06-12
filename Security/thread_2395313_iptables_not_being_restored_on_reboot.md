---
title: "iptables not being restored on reboot"
date: 2018-06-29
forum: Security
---

### Post by sniper8752 on 2018-06-29
I noticed that when I reboot my machine, iptables are NOT being restored.  I had thought that it was doing it before.  Is this something that needs to be manually configured and setup?

---

### Post by &amp;KyT$0P# on 2018-06-29
> **sniper8752 said:**
> Is this something that needs to be manually configured and setup?
Yes it does.  You could try installing and using the [FONT=Courier New]iptables-persistent[/FONT] package

---

### Post by sniper8752 on 2018-06-29
It looks like I already have it installed.

---

### Post by &amp;KyT$0P# on 2018-06-29
So after setting up your iptables how you want, run this command -
```
sudo netfilter-persistent save
```
Does that get your iptables being restored on reboot?

---

### Post by Doug S on 2018-06-30
Because I have some other related stuff to do, my iptables rule set is part of a script. I run it at start up this way, via the /etc/network/interfaces file:
```
# interfaces file for smythies.com 2016.01.30
#       attempt to set local DNS herein, as the method
#       used with the old 12.04 server no longer works.
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR="#FF0000"]pre-up /home/doug/init/doug_firewall[/COLOR]
dns-nameservers 127.0.0.1

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

# Local network interface (uses built in ethernet port)
auto enp2s0
iface enp2s0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```The server is 16.04. This method will not work (I think) with netplan and 18.04

---

### Post by sniper8752 on 2018-07-04
> **halogen2 said:**
> So after setting up your iptables how you want, run this command -
```
sudo netfilter-persistent save
```
Does that get your iptables being restored on reboot?
This did not work.

---

### Post by cariboo on 2018-07-04
> **sniper8752 said:**
> This did not work.

This reply doesn't help, at least post the error message you are getting.

---

### Post by sniper8752 on 2018-07-04
There was no error that popped up.  Is there a log that would maybe have some errors?
I also tried adding this to my interfaces file, but it did not do any of this:
```
pre-up ipset restore < /etc/ipset.up.rules
pre-up iptables-restore < /etc/iptables/rules.v4

```

---

### Post by &amp;KyT$0P# on 2018-07-05
> **sniper8752 said:**
> Is there a log that would maybe have some errors?
What does this command show? -
```
systemctl status netfilter-persistent
```

---

### Post by sniper8752 on 2018-07-07
```
&#9679; netfilter-persistent.service - netfilter persistent configuration   Loaded: loaded (/lib/systemd/system/netfilter-persistent.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2018-07-04 18:49:29 MDT; 2 days ago
  Process: 486 ExecStart=/usr/sbin/netfilter-persistent start (code=exited, status=1/FAILURE)
 Main PID: 486 (code=exited, status=1/FAILURE)


Jul 04 18:49:27 server systemd[1]: Starting netfilter persistent configuration...
Jul 04 18:49:28 server netfilter-persistent[486]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start
Jul 04 18:49:29 server netfilter-persistent[486]: run-parts: /usr/share/netfilter-persistent/plugins.d/15-ip4tables exited with return code 2
Jul 04 18:49:29 server netfilter-persistent[486]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start
Jul 04 18:49:29 server systemd[1]: netfilter-persistent.service: Main process exited, code=exited, status=1/FAILURE
Jul 04 18:49:29 server systemd[1]: Failed to start netfilter persistent configuration.
Jul 04 18:49:29 server systemd[1]: netfilter-persistent.service: Unit entered failed state.
Jul 04 18:49:29 server systemd[1]: netfilter-persistent.service: Failed with result 'exit-code'.



```

---

### Post by Doug S on 2018-07-08
> **sniper8752 said:**
> I also tried adding this to my interfaces file, but it did not do any of this:
```
pre-up ipset restore < /etc/ipset.up.rules
pre-up iptables-restore < /etc/iptables/rules.v4

```Suggest that you make one script to run that stuff, and add something like this to that script:
```
echo "doug_firewall $FWVER done..." >> /dev/kmsg
```And then check for that flag statement:
```
doug@DOUG-64:~$ [COLOR="#FF0000"]dmesg | grep doug_firewall[/COLOR]
[4191333.763562] doug_firewall 2.07 done...
[4191547.715773] doug_firewall 2.07 done...

```Based on another of your postings, I am assuming your computer is 16.04. I don't think this method works on 18.04.

---

### Post by sniper8752 on 2018-07-08
so it'd look something like this: ```
pre-up sh script.sh
```?

what is /dev/kmsg? It looks like it just logs dropped packets. 
Why won't it work on 18?

---

### Post by Doug S on 2018-07-09
> **sniper8752 said:**
> so it'd look something like this: ```
pre-up sh script.sh
```?No, it would something like the example I already gave in a previous reply. Specifically, the full path and name of the script.

> **sniper8752 said:**
> what is /dev/kmsg? It looks like it just logs dropped packets.a circle buffer for kernel messages. By putting a message there, as a flag, we can later (as long as soon enough that the ring buffer hasn't gone through a complete cycle) check that it actually ran.

> **sniper8752 said:**
> Why won't it work on 18?It is my understanding that the pre-up (and post-up) directives don't work with netplan, which is used on 18.04. I don't know for certain, as I have stayed with 16.04 for now.

---

### Post by mike4ubuntu on 2018-08-27
so then, netfilter-persistent.service basically doesn't work in 18.04?  Is anybody working of fixing this?  Is there a bug ticket opened on it?

---

### Post by &amp;KyT$0P# on 2018-08-27
> **mike4ubuntu said:**
> so then, netfilter-persistent.service basically doesn't work in 18.04?
It works for me in 18.04.  I have no idea why OP's netfilter-persistent is failing with exit status 2, nor even how an exit status of 2 could be produced.

> Is anybody working of fixing this? Is there a bug ticket opened on it?
How do you know it's a bug in netfilter-persistent?

---

### Post by mike4ubuntu on 2018-08-27
there seems to be something wrong during boot with netfilter-persistent.  It won't start durint the boot process, but then after the boot, I can start it from the command ok.  Might be another systemd race condition.  The sequence below is repeatable after a re-boot every time.

```

root@server:/etc/iptables# systemctl status netfilter-persistent
&#9679; netfilter-persistent.service - netfilter persistent configuration
   Loaded: loaded (/lib/systemd/system/netfilter-persistent.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2018-08-27 19:14:17 EDT; 6min ago
  Process: 878 ExecStart=/usr/sbin/netfilter-persistent start (code=exited, status=1/FAILURE)
 Main PID: 878 (code=exited, status=1/FAILURE)

Aug 27 19:14:16 server systemd[1]: Starting netfilter persistent configuration...
Aug 27 19:14:16 server netfilter-persistent[878]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start
Aug 27 19:14:17 server netfilter-persistent[878]: run-parts: /usr/share/netfilter-persistent/plugins.d/15-ip4tables exited with return code 1
Aug 27 19:14:17 server netfilter-persistent[878]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start
Aug 27 19:14:17 server netfilter-persistent[878]: run-parts: /usr/share/netfilter-persistent/plugins.d/25-ip6tables exited with return code 1
Aug 27 19:14:17 server systemd[1]: netfilter-persistent.service: Main process exited, code=exited, status=1/FAILURE
Aug 27 19:14:17 server systemd[1]: netfilter-persistent.service: Failed with result 'exit-code'.
Aug 27 19:14:17 server systemd[1]: Failed to start netfilter persistent configuration.
root@server:/etc/iptables# systemctl start netfilter-persistent
root@server:/etc/iptables# systemctl status netfilter-persistent
&#9679; netfilter-persistent.service - netfilter persistent configuration
   Loaded: loaded (/lib/systemd/system/netfilter-persistent.service; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2018-08-27 19:20:50 EDT; 2s ago
  Process: 5583 ExecStart=/usr/sbin/netfilter-persistent start (code=exited, status=0/SUCCESS)
 Main PID: 5583 (code=exited, status=0/SUCCESS)

Aug 27 19:20:50 server systemd[1]: Starting netfilter persistent configuration...
Aug 27 19:20:50 server netfilter-persistent[5583]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start
Aug 27 19:20:50 server netfilter-persistent[5583]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start
Aug 27 19:20:50 server systemd[1]: Started netfilter persistent configuration.

```

---

### Post by macnux on 2018-08-29
On CentOS, you can save rules like this:
```
$ iptables-save > /etc/sysconfig/iptables
```
Or on CentOS 7, you can save them like this:
```
$ service iptables save
```
On Debian based distros, you can use  iptables-persistent like this:
First, install it:
```
$ apt-get install iptables-persistent
```
To save rules:
```
$ netfilter-persistent save
```
To restore rules:
```
$ netfilter-persistent reload
```
You can learn more about iptables firewall rules from this tutorial [Linux iptables firewall]("https://likegeeks.com/linux-iptables-firewall-examples/")

Hope that helps!

---

### Post by mike4ubuntu on 2018-08-31
yes, those commands work for netfilter-persistent for me too.  However, the problem is when the system reboots.  netfilter-persistent service is supposed to automatically reload the rules on reboot startup.  However, the netfilter-persistent service fails to start in system startup (see my previous post for errors).  However, after the system has started, I can manually start the netfilter-persistent service fine.  There seems to be a race condition or some other related error in startup for that service.  There is probably a dependency for the service that has not completed before netfilter-persistent service tries to start, so it fails.  That's why if you wait after the system has been completely started, and you log in, and start the netfilter-persistent service just fine.

---

### Post by mike4ubuntu on 2018-09-05
I tracked the problem down to /usr/share/netfilter-persistent/plugins.d/15-ip4tables.  This script has a "set -e" that causes the script to abort as soon as there is a problem.  Apparently, the iptables-restore command fails, probably because of some kind of race condition during startup.  So I commented out the "set -e" and added this code at the iptables-restore:
```

        for i in {1..5}; do
            echo -e "DEBUG(${0}.15-ip4tables): load_rules, in loop cnt ${i}...${1}"
#            /sbin/iptables-restore < /etc/iptables/rules.v4 2> /dev/null
            /sbin/iptables-restore < /etc/iptables/rules.v4 2> /var/log/iptables-error.log
            if [ $? -ne 0 ]; then
                echo "ERROR($0): iptables-restore FAILED, iteration $i"
                rc=1
                sleep 5
            else
                echo "INFO($0): iptables-restore SUCCEEDED,"
                rc=0
                break
            fi
        done

```
this seemed to work, and it normally processes 2 or 3 iterations through the loop before the iptables-restore succeeds.  However, this way, the rules do get loaded.

---


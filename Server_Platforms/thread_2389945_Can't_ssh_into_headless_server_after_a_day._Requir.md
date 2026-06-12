---
title: "Can't ssh into headless server after a day. Requires restart."
date: 2018-04-23
forum: Server Platforms
---

### Post by jstaker7 on 2018-04-23
I'm running Ubuntu 16.04 and set up my system to run headless with port forwarding. I can ssh into the machine just fine, but after a day or two (the exact interval seems inconsistent) I can no longer ssh in; the ssh request times out and doesn't seem to be be communicating with the system.

Things I've tried:
1) Plugged monitor into machine to see if I could use the computer normally, but nothing comes up on the screen. I think this is because the computer was started headless and Xorg times out after a while after reboot.
2) Appended to a log using cron. This ruled out that the system itself froze since the log continued to get updated even after the system quit responding to ssh. 
3) The system still sounds like it's running and not powered down, so I don't think this is a sleep/hibernation issue (although I don't exactly know what the computer sounds like in sleep mode, if the fans can still be running, etc.)
4) Looked at system logs and nothing seemed out of place.
5) Ensured that the ip address did not change between between when ssh worked and when it didn't

Any ideas on why this is happening or ideas on how to debug this?

---

### Post by TheFu on 2018-04-24
Welcome to the forums.

[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) might help.
Ubuntu server doesn't need any X11 stuff, so I doubt that is an issue.  OTOH, if you loaded a desktop version, I don't know what it expects.

Never rule out obvious problems. Could it be the network cable or switch port or router causing the issue?

---

### Post by wildmanne39 on 2018-04-24
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-04-24
Can a server be called "headless" if a graphic UI (xorg) is installed?

But anyway, none of my servers from 10.04, 12.04, 14.04, 16.04 and 18.04 have ever randomly stopped responding to SSH and I have almost a dozen running at any point in time.

I have a firewall enabled but it allows SSH for specific IP addresses to get through.
I also have fail2ban enabled but I never get auto-banned due to never giving bad credentials.

I guess your best bet is to look at the logs and look for anything that resembles an SSH deny or if the sshd service shuts down.  I know you looked at the system logs but also examine them to see if you can identify good SSH connections.

Could also run a script in crontab that checks the status of the sshd service and output to log with a timestamp so if it does shutdown, you can tell when it does.

LHammonds

---

### Post by jstaker7 on 2018-04-25
Thanks for the help thus far; after digging more into the logs, I noticed some interesting things in kern.log.

For most of the time I see this. Almost looks like it renews the connection every 3600 seconds:
```
Apr 19 19:01:48 computer_name NetworkManager[873]: <info>  [1524189708.6542] dhcp4 (enp30s0): state changed bound -> bound
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9536]   address local_ip_address.7
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9536]   plen 24 (255.255.255.0)
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9537]   gateway local_ip_address
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9537]   server identifier local_ip_address.1
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9537]   lease time 3600
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9537]   nameserver '75.75.75.75'
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9537]   nameserver '75.75.76.76'
Apr 19 19:25:57 computer_name NetworkManager[873]: <info>  [1524191157.9538] dhcp4 (enp30s0): state changed bound -> bound
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2008]   address local_ip_address.7
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2009]   plen 24 (255.255.255.0)
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2009]   gateway local_ip_address
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2009]   server identifier local_ip_address
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2009]   lease time 3600
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2009]   nameserver '75.75.75.75'
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2010]   nameserver '75.75.76.76'
Apr 19 19:49:44 computer_name NetworkManager[873]: <info>  [1524192584.2010] dhcp4 (enp30s0): state changed bound -> bound
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7801]   address local_ip_address.7
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7801]   plen 24 (255.255.255.0)
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7802]   gateway local_ip_address
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7802]   server identifier local_ip_address
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7802]   lease time 3600
Apr 19 20:17:09 computer_name NetworkManager[873]: <info>  [1524194229.7802]   nameserver '75.75.75.75'

```

But after a while, this happens:
```
Apr 20 14:13:41 computer_name NetworkManager[873]: <info>  [1524258821.0448] dhcp4 (enp30s0): state changed bound -> bound
Apr 20 15:13:42 computer_name NetworkManager[873]: <info>  [1524262422.9119] dhcp4 (enp30s0): state changed bound -> expire
Apr 20 15:13:42 computer_name NetworkManager[873]: <info>  [1524262422.9457] dhcp4 (enp30s0): canceled DHCP transaction, DHCP client pid 1155
Apr 20 15:13:42 computer_name NetworkManager[873]: <info>  [1524262422.9458] dhcp4 (enp30s0): state changed expire -> done

```

Then this repeats for a while:
```
Apr 20 16:27:58 computer_name NetworkManager[873]: <info>  [1524266878.5512] device (enp30s0): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 20 16:27:58 computer_name NetworkManager[873]: <info>  [1524266878.5514] manager: NetworkManager state is now DISCONNECTED
Apr 20 16:27:58 computer_name NetworkManager[873]: <info>  [1524266878.5516] policy: disabling autoconnect for connection 'Wired connection 1'.
Apr 20 16:27:58 computer_name NetworkManager[873]: <warn>  [1524266878.5518] device (enp30s0): Activation: failed for connection 'Wired connection 1'
Apr 20 16:27:58 computer_name NetworkManager[873]: <info>  [1524266878.5527] device (enp30s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6028] policy: auto-activating connection 'Wired connection 1'
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6042] device (enp30s0): Activation: starting connection 'Wired connection 1' (496a9407-8de6-3e9f-b8ef-cec3122af9fe)
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6044] device (enp30s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6047] manager: NetworkManager state is now CONNECTING
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6054] device (enp30s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6062] device (enp30s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6067] dhcp4 (enp30s0): activation: beginning transaction (timeout in 45 seconds)
Apr 20 16:32:58 computer_name NetworkManager[873]: <info>  [1524267178.6086] dhcp4 (enp30s0): dhclient started with pid 17819
Apr 20 16:33:43 computer_name NetworkManager[873]: <warn>  [1524267223.5166] dhcp4 (enp30s0): request timed out
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5167] dhcp4 (enp30s0): state changed unknown -> timeout
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5344] dhcp4 (enp30s0): canceled DHCP transaction, DHCP client pid 17819
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5344] dhcp4 (enp30s0): state changed timeout -> done
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5349] device (enp30s0): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5353] manager: NetworkManager state is now DISCONNECTED
Apr 20 16:33:43 computer_name NetworkManager[873]: <warn>  [1524267223.5358] device (enp30s0): Activation: failed for connection 'Wired connection 1'
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5366] device (enp30s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5403] policy: auto-activating connection 'Wired connection 1'
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5418] device (enp30s0): Activation: starting connection 'Wired connection 1' (496a9407-8de6-3e9f-b8ef-cec3122af9fe)
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5421] device (enp30s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5424] manager: NetworkManager state is now CONNECTING
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5431] device (enp30s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5439] device (enp30s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5444] dhcp4 (enp30s0): activation: beginning transaction (timeout in 45 seconds)
Apr 20 16:33:43 computer_name NetworkManager[873]: <info>  [1524267223.5465] dhcp4 (enp30s0): dhclient started with pid 17825
Apr 20 16:34:28 computer_name NetworkManager[873]: <warn>  [1524267268.5160] dhcp4 (enp30s0): request timed out
Apr 20 16:34:28 computer_name NetworkManager[873]: <info>  [1524267268.5161] dhcp4 (enp30s0): state changed unknown -> timeout
Apr 20 16:34:28 computer_name NetworkManager[873]: <info>  [1524267268.5502] dhcp4 (enp30s0): canceled DHCP transaction, DHCP client pid 17825
Apr 20 16:34:28 computer_name NetworkManager[873]: <info>  [1524267268.5503] dhcp4 (enp30s0): state changed timeout -> done

```

Then finally outputs this (then nothing after this):
```
Apr 20 16:34:37 computer_name NetworkManager[873]: <info>  [1524267277.5269] manager: NetworkManager state is now DISCONNECTED
Apr 20 16:34:47 computer_name kernel: [193438.362397] igb 0000:1e:00.0 enp30s0: igb: enp30s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0633] device (enp30s0): link connected
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0638] device (enp30s0): state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0652] policy: auto-activating connection 'Wired connection 1'
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0664] device (enp30s0): Activation: starting connection 'Wired connection 1' (496a9407-8de6-3e9f-b8ef-cec3122af9fe)
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0667] device (enp30s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0668] manager: NetworkManager state is now CONNECTING
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0675] device (enp30s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0683] device (enp30s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0688] dhcp4 (enp30s0): activation: beginning transaction (timeout in 45 seconds)
Apr 20 16:34:48 computer_name NetworkManager[873]: <info>  [1524267288.0708] dhcp4 (enp30s0): dhclient started with pid 17840
Apr 20 16:34:56 computer_name NetworkManager[873]: <info>  [1524267296.0472] device (enp30s0): link disconnected (deferring action for 4 seconds)
Apr 20 16:34:56 computer_name kernel: [193446.453632] igb 0000:1e:00.0 enp30s0: igb: enp30s0 NIC Link is Down
Apr 20 16:34:59 computer_name kernel: [193449.477917] igb 0000:1e:00.0 enp30s0: igb: enp30s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Apr 20 16:34:59 computer_name NetworkManager[873]: <info>  [1524267299.1793] device (enp30s0): link connected
Apr 20 16:35:06 computer_name NetworkManager[873]: <info>  [1524267306.3153] device (enp30s0): link disconnected (deferring action for 4 seconds)
Apr 20 16:35:06 computer_name kernel: [193456.721193] igb 0000:1e:00.0 enp30s0: igb: enp30s0 NIC Link is Down
Apr 20 16:35:09 computer_name kernel: [193459.665480] igb 0000:1e:00.0 enp30s0: igb: enp30s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Apr 20 16:35:09 computer_name NetworkManager[873]: <info>  [1524267309.3673] device (enp30s0): link connected
Apr 20 16:35:31 computer_name NetworkManager[873]: <info>  [1524267331.3135] device (enp30s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr 20 16:35:31 computer_name NetworkManager[873]: <info>  [1524267331.3142] device (enp30s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr 20 16:35:31 computer_name NetworkManager[873]: <info>  [1524267331.3146] device (enp30s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 20 16:35:31 computer_name NetworkManager[873]: <info>  [1524267331.3148] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 20 16:35:31 computer_name NetworkManager[873]: <info>  [1524267331.3208] device (enp30s0): Activation: successful, device activated.
Apr 20 16:35:33 computer_name NetworkManager[873]: <warn>  [1524267333.5055] dhcp4 (enp30s0): request timed out
Apr 20 16:35:33 computer_name NetworkManager[873]: <info>  [1524267333.5055] dhcp4 (enp30s0): state changed unknown -> timeout
Apr 20 16:35:33 computer_name NetworkManager[873]: <info>  [1524267333.5389] dhcp4 (enp30s0): canceled DHCP transaction, DHCP client pid 17840
Apr 20 16:35:33 computer_name NetworkManager[873]: <info>  [1524267333.5390] dhcp4 (enp30s0): state changed timeout -> done
Apr 20 16:36:42 computer_name NetworkManager[873]: <info>  [1524267402.8927] dhcp6 (enp30s0): activation: beginning transaction (timeout in 45 seconds)
Apr 20 16:36:42 computer_name NetworkManager[873]: <info>  [1524267402.8948] dhcp6 (enp30s0): dhclient started with pid 17901
Apr 20 16:36:42 computer_name NetworkManager[873]: <info>  [1524267402.8963] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 20 16:36:42 computer_name NetworkManager[873]: <info>  [1524267402.8965] policy: set 'Wired connection 1' (enp30s0) as default for IPv6 routing and DNS
Apr 20 16:36:42 computer_name NetworkManager[873]: <info>  [1524267402.8967] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9983]   valid_lft 60
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9984]   preferred_lft 30
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9984]   address 2601:1c0:5a01:76c0::6
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9984]   nameserver '2001:558:feed::1'
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9984]   nameserver '2001:558:feed::2'
Apr 20 16:36:52 computer_name NetworkManager[873]: <info>  [1524267412.9984] dhcp6 (enp30s0): state changed unknown -> bound, event ID="23:07:5d:68|1510077280"
Apr 20 16:36:53 computer_name NetworkManager[873]: <info>  [1524267413.0048] dhcp6 (enp30s0): state changed bound -> unknown
Apr 20 16:36:53 computer_name NetworkManager[873]: <info>  [1524267413.0082] dhcp6 (enp30s0): state changed unknown -> expire
Apr 20 16:36:53 computer_name NetworkManager[873]: <info>  [1524267413.0090] dhcp6 (enp30s0): canceled DHCP transaction, DHCP client pid 17901
Apr 20 16:36:53 computer_name NetworkManager[873]: <info>  [1524267413.0091] dhcp6 (enp30s0): state changed expire -> done

```

I can't be sure, but I think the times in the log coincide with when I lost ssh access. I don't really understand what all this is telling me, but seeing things like "expire" and "timeouts" seem promising. Is there anything in what I've provided out of the ordinary and might explain why I lose ssh access?

---

### Post by SeijiSensei on 2018-04-25
First thing I'd check is the hardware.  Use a different Ethernet cable, and connect to it a different port on the router.

---

### Post by TheFu on 2018-04-25
Definitely check the cables and switch port.  Try a different one.

On the DHCP server (router?), you can usually change the lease period.  3600 seconds is only 1 hour.  For a home, perhaps 1 week would make more sense?

---

### Post by LHammonds on 2018-04-25
Ah, so when you cannot connect via SSH, you also cannot ping it or access any of the services?

Like SeijiSensei said, swap the cable is the easiest test, then move to different port in the switch.  You might have a 2nd cable to swap as well if you use a patch panel.  If you have a second Ethernet NIC on the server, then switch to it and re-config your network settings.

LHammonds

---

### Post by jstaker7 on 2018-05-28
Sorry for the long delay -- it actually took that long before the error happened again. Somewhat frustrating to have inconsistent behavior for debugging. Oh well.

These last few weeks things appeared fine, but I kept a monitor plugged in just in case, so that I could open things up locally to help with debugging when the error happened again. 

Yesterday my router was acting up and my internet/wifi seemed to be having issues across all my devices. I rebooted the router and everything went back to normal -- except I could no longer ssh into my box.

I turned on the monitor and checked logs, and nothing seemed out of place. The internet on the box was very weird, though. Some sites (like google searches) were working, but most gave a connection error.

After a lot of searching and trial and error I couldn't restore network connectivity. 

Finally, in the terminal I simply ran "dhclient" and everything was restored! Any ideas on what this means? Is something not restarting/renewing itself like it should? Can I simply run "dhclient" every day in crontab and forget about it?

---

### Post by TheFu on 2018-05-28
Have you considered setting up static IPs and forgetting DHCP?  After all, if it isn't a laptop or tablet, why deal with DHCP at all?

Did I miss the swapped cables and switch port testing or was that not done?

---


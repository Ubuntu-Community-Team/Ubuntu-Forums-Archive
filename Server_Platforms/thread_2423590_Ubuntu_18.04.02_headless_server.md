---
title: "Ubuntu 18.04.02 headless server"
date: 2019-07-25
forum: Server Platforms
---

### Post by XBMC old School on 2019-07-25
I have a home server that host smb shares for backups, has ssh installed on it.   month ago it went dead on the network, no ssh access, no smb shares, but the box shows up as connected to router.  when i jump on it, it shows that everything is running?  I'm totally clueless how to figure this thing out.

---

### Post by wildmanne39 on 2019-07-25
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-07-25
How are you addressing this box? By name or IP address? If by name, where are the name->address mappings stored? Do you have a local DNS server or using /etc/hosts?

How does this machine get an IP address? Via DHCP or does it have a static configuration? Any server should have a static IP or have a "reservation" in the router's DHCP server.

If you log on to the machine at the console and run "ip addr" do you get the expected address?

---

### Post by XBMC old School on 2019-07-25
I have an IP reservation on the router, have not delved into DNS

---

### Post by LHammonds on 2019-07-26
Is the server's firewall blocking access?

```
ufw status
```

---

### Post by TheFu on 2019-07-26
I read that Samba removed SMBv1 as available recently. 
a) Unix systems really should be using NFS, not SMB/CIFS.
b) Windows systems are really the only ones that still need samba.  Which version of the SMB protocol do each of your other systems require?

Using network storage for backups doesn't mitigate crypto-malware. In fact, all the backups are likely at risk if you do this.  Network backups really need to be "pulled" by the server, not "pushed" to the server by each client.  But having backups is so much better than NOT having them, regardless of where you are today.

Samba creates logs for every client connection in /var/log/samba/ ... take a look there for any issues. 

As for network issues, we need some facts to help.
* which ubuntu release?  The last 3 LTS releases have each changed the way network configs are handled.
* **ip a **output, please.
* **route -n** output, please.

My wired network troubleshooter - it isn't for 18.04, so you'll need to change some commands, but they might still work:
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
and for ssh connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

When posting output, please include the EXACT commands and "relevant" parts of the output if it is long.  Also, wrap it in code tags so it looks the same here as it does in a terminal.  If it isn't lined up the same, then you didn't get the code-tags right.  It is a copy/paste. Nobody is asking anyone to insert tabs or spaces. If it doesn't line up, the code tags are wrong.   Adv Edit (#)

---

### Post by XBMC old School on 2019-07-26
> **TheFu said:**
> I read that Samba removed SMBv1 as available recently. 
a) Unix systems really should be using NFS, not SMB/CIFS.
b) Windows systems are really the only ones that still need samba.  Which version of the SMB protocol do each of your other systems require?

Using network storage for backups doesn't mitigate crypto-malware. In fact, all the backups are likely at risk if you do this.  Network backups really need to be "pulled" by the server, not "pushed" to the server by each client.  But having backups is so much better than NOT having them, regardless of where you are today.

Samba creates logs for every client connection in /var/log/samba/ ... take a look there for any issues. 

As for network issues, we need some facts to help.
* which ubuntu release?  The last 3 LTS releases have each changed the way network configs are handled.
* **ip a **output, please.
* **route -n** output, please.

My wired network troubleshooter - it isn't for 18.04, so you'll need to change some commands, but they might still work:
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
and for ssh connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

When posting output, please include the EXACT commands and "relevant" parts of the output if it is long.  Also, wrap it in code tags so it looks the same here as it does in a terminal.  If it isn't lined up the same, then you didn't get the code-tags right.  It is a copy/paste. Nobody is asking anyone to insert tabs or spaces. If it doesn't line up, the code tags are wrong.   Adv Edit (#)

Shares are not visible to either Windows 10 or ubuntu

server & desktop is 18.04.02

The server is running and connected, i disabled ufw and was able to SSH into it.

---

### Post by LHammonds on 2019-07-29
> **XBMC old School said:**
> The server is running and connected, i disabled ufw and was able to SSH into it.
If disabling the firewall allowed you to connect via SSH, then you need to look at your firewall rules.

My guess is that you have SSH enabled in the firewall for a specific IP or subnet and the subnet or IP changed and thus your access rules no longer apply.

You are able to connect via SSH now but are you able to connect to the shares too?  If not, then there is yet another issue at play.

LHammonds

---

### Post by SeijiSensei on 2019-07-29
You say this server is running on your home network. Is it exposed to the Internet? If not, why do you need a firewall at all? 

I've run servers in my home office for decades without a firewall.  I do have a means of connecting to my home network in emergencies via SSH to an arbitrary "high" port on a virtual server I manage. It forwards the traffic over an OpenVPN connection to a desktop machine on the network. My servers have never been compromised.

---

### Post by XBMC old School on 2019-07-29
Now ssh is "fixed",  I still haven't been able to get the server visible on the network and the smb shares available

---

### Post by Morbius1 on 2019-07-29
> Shares are not visible to either Windows 10 or ubuntu
What exactly do you mean by "visible"? Do you mean "discoverable"?

If you mean that opening explorer and clicking on "Network" in Win10 does not display your servers host name that is to be expected because Win10 disables smb1 on the client side and without it it cannot discover hosts by their netbios names.

The Linux client will have the same issue depending on which version you are running.

If your server has a fixed ip address can't you just connect to it directly:

**Win10** **Explorer**: \\192.168.0.100
**Ubuntu Nautilus**: smb://192.168.0.100

---

### Post by XBMC old School on 2019-07-30
Ya i punch the address in from ubuntu &amp; windows10 and nothing comes up, I wonder if it is because i might have removed the browseable flag, hmm.&nbsp;

> **Global parameters**

 [global]
server string = %h %v
server role = standalone server
map to guest = Bad User
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
max protocol = SMB3
protocol = SMB3
dns proxy = No
usershare allow guests = Yes
panic action = /usr/share/samba/panic-action %d
idmap config * : backend = tdb

But it shouldn't matter if i plug in the exact address, maybe im missing a netbios name

---

### Post by Morbius1 on 2019-07-31
You've posted the [gloabal] section. What about the rest.

Why not just post the output of the following:
```
testparm -s
```

---


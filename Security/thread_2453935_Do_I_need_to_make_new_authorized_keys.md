---
title: "Do I need to make new authorized_keys?"
date: 2020-11-19
forum: Security
---

### Post by pqwoerituytrueiwoq on 2020-11-19
yesterday i a raspberry pi i setup for my mom was not working right, upon logging to it everything was segfaulting and i noticed last logging was from a foreign ip, clearly it was comprised
the only thing remotely sensitive on it was the ~/.ssh/authorized_keys file
here is a snip from my auth.log file
```

Nov  2 06:34:48 radio sshd[3301]: Accepted password for pi from 190.211.254.116 port 53766 ssh2
Nov  2 06:34:48 radio sshd[3301]: pam_unix(sshd:session): session opened for user pi by (uid=0)
Nov  2 06:34:49 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/grep -E ^pi: /etc/shadow
Nov  2 06:34:49 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:34:49 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:35:39 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/usr/bin/id -g
Nov  2 06:35:39 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:35:39 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:35:39 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/usr/bin/whoami
Nov  2 06:35:39 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:35:39 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:35:49 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/mount -o remount,rw /
Nov  2 06:35:49 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:35:49 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:35:59 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/sh -c sed '#/lib/libxml.so#' /etc/ld.so.preload > /etc/ld.so.preload
Nov  2 06:35:59 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:35:59 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:36:09 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/usr/bin/killall -9 libxml_CP
Nov  2 06:36:09 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:36:09 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:36:09 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/rm /lib/libxml.so
Nov  2 06:36:09 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:36:09 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:36:19 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/rm -R /var/libxml_CP
Nov  2 06:36:19 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:36:19 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:36:29 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/mkdir /var/libxml_CP
Nov  2 06:36:29 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:36:29 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:36:39 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/chmod 777 -R /var/libxml_CP
Nov  2 06:36:39 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:36:39 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:37:50 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/sbin/iptables -I INPUT -p tcp --dport 40018 -j ACCEPT
Nov  2 06:37:50 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:37:50 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:38:05 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/sbin/iptables-save
Nov  2 06:38:05 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:38:05 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:38:20 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/sbin/iptables -S
Nov  2 06:38:20 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:38:20 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:39:25 radio sudo:       pi : TTY=pts/0 ; PWD=/home/pi ; USER=root ; COMMAND=/bin/ss -tulpn
Nov  2 06:39:25 radio sudo: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Nov  2 06:39:25 radio sudo: pam_unix(sudo:session): session closed for user root
Nov  2 06:40:06 radio sshd[3301]: pam_unix(sshd:session): session closed for user pi

```
it appears the attacker did this multiple times

---

### Post by EuclideanCoffee on 2020-11-19
You should take the following steps.

1. Backup your data. Sanitize it for possible malware or bad data you wish to keep off your device.
2. Remove Pi from network.
3. Change credentials to network access ports, such as gateways and other IoT devices.
4. Check logs of your gateway, IoT devices, and computers connected to this network.
5. Reformat your Pi and change passwords.
6. Assess if you need to purchase a new gateway (router).

---

### Post by DuckHook on 2020-11-19
Though I'm not nearly as knowledgeable as EuclideanCoffee in security matters, in answer to your question:

If it were me, yes, I would make new keys and nuke the old ones.

Although a bad actor having access to the public key should not be a deal breaker, it would still rub me the wrong way. But then, it's not a major pain for me to change keys. I run a SOHO and have no enterprise&#8209;level commitments. If your keys are used extensively among many machines/applications, this is a much bigger hurdle.

---

### Post by TheFu on 2020-11-19
Do you have lots of friends in Panama that need ssh access into the r-pi?  Could they be using a VPN with an exit node in Panama?

Changing keys is the least of the problems.
I'd wipe the storage, re-image the OS, lock down the OS from outside access off the LAN, except ssh-keys from my home public IP and only for ssh.  I'd put ssh onto a non-standard port - probably using the router's port-translation capability.  Then I'd only allow password-based connections from the LAN where the PI sits.

There is much you haven't shared.  This could be a teaching thread for others - how to secure ssh and block all other access.

Don't allow the entire world the ability to connect to services they don't have any need to connect into.  
Block everyone and whitelist only the places you KNOW need access and only to the specific services they need.  
Say your home and work IP subnets, assuming they are different from the PI's LAN.

Don't allow password-based connections from outside the LAN. Don't allow direct root access without a password except on the LAN and don't allow remote root access ... except from extremely specific locations .... perhaps 3 in the world.
Step 4: Lock down the sshd_config on the ssh server
```
   $ ssh username@remote
   $ sudoedit /etc/ssh/sshd_config
```
     Change line with:
```
  PasswordAuthentication yes
```
   to 
```
  PasswordAuthentication **no**
```

At the end of the file, add:
```
  Match Address 192.168.22.0/24,172.16.0.0/12,10.0.0.1/8
      PasswordAuthentication yes
```
Change the subnets above for the LAN where the sshd runs.  This has nothing to do with remote client LANs over the internet. It needs to be at the trailing end of the file.

Install fail2ban to block brute force password attempts:
```
sudo apt install fail2ban
```

Setup ufw to block access by default, except for ssh from your IP and rate limit connections.
```
  $ sudo ufw enable
  $ sudo ufw default deny
  $ sudo ufw allow from {IP_SUB/net} to any port 22 proto tcp
  $ sudo ufw limit 22/tcp
```

There's much more that can be done for ssh security, but those are the main things that came to mind today.

If you secure ssh, almost anything else you need to do on that subnet is possible through an ssh-tunnel.

---

### Post by pqwoerituytrueiwoq on 2020-11-20
@TheFu what additional info would you like, i made a backup of the card before i wiped it with a non-eol install (guessing raspbian headless from q4 of 2014)
i do not even recall what the password even was on this install
i can upload almost every file on the sd card well not the ~/Music folder that was setup for mpd cause copyright reasons, aside form that is is just wifi login, ddns token/domain, and the authorized_keys file

---

### Post by TheFu on 2020-11-20
IF you don't know how they got into the system, then doing the same thing over again is useless. They will just be right back.
What mitigations beyond "starting over" did you have planned?
What other services were open?  If you're running WordPress with 50 addons and a theme created by Joe in Yukon who dabbles in php themes? Perhaps those are the initial ways they go into the system before ssh?

Doing the same thing and expecting different results won't prevent this from happening again.

BTW, we've all been hacked - well - I have.  I've posted about those experiences here a few times over the years. Each was because I was stupid in some way, though the bluetooth hack really wasn't my fault. I blame Canonical for that one because it was a brand new install under 24 hrs old, freshly patched less than 1 day before, I never turned on BT, yet was still hacked. Can't blame me for that. The moral of that story is NEVER trust bluetooth.  I remove it from my systems and have processes setup to keep removing it weekly when some dependency re-adds it.  Why does QEMU have a bluetooth dependency? Really?!!

---

### Post by pqwoerituytrueiwoq on 2020-11-20
only open service was ssh for remote management so that when my mom calls me i can look into it (running a few local only services, one was a lamp timer, overkill: rpi as a lamp timer)
rather they got in via a password guess or a flaw n a old version of ssh ssh flaw is unknown (assuming the install was eol)
should have disabled password login
i have disabled remote management for the time being, once i get everything running i am gonna make a backup before enabling it

"WordPress with 50 addons" that probably would not run very well on a rpi model A+ (700Mhz;256MB RAM; usb wifi)

---

### Post by TheFu on 2020-11-20
> **pqwoerituytrueiwoq said:**
>  
"WordPress with 50 addons" that probably would not run very well on a rpi model A+ (700Mhz;256MB RAM; usb wifi)

People run complete NextCloud instances on r-pi v2 and v3 quite nicely.

Passwords alone for authentication over the internet is a massive security failure, including for websites. Leaving default usernames and default passwords is even worse. ;)  Any javascript that we are tricked into running on our browsers can scan our LAN for devices, then try default logins for each.

---

### Post by EuclideanCoffee on 2020-11-20
Simply use RSA instead of login, do not allow root access remotely, and force users with access to login into an elevated account once they sign-in. Push your SSH traffic on a different port, like 23 (not literally).

Here's a good intro: [https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-18-04)

---

### Post by pqwoerituytrueiwoq on 2020-11-20
i never allow root, well i have one box where i do, but that is limited  to a single local ip, and only the root account on that box can use that  key

it has never been public on port 22, it was on a 4 digit port number

@TheFu
not using a version 2 board, this is one of the original boards, the single core 700Mhz cpu 
```
cat /proc/cpuinfo 
processor    : 0
model name    : ARMv6-compatible processor rev 7 (v6l)
BogoMIPS    : 697.95
Features    : half thumb fastmult vfp edsp java tls 
CPU implementer    : 0x41
CPU architecture: 7
CPU variant    : 0x0
CPU part    : 0xb76
CPU revision    : 7

Hardware    : BCM2835
Revision    : 0012
Serial        : 00000000c3f95f7a
Model        : Raspberry Pi Model A Plus Rev 1.1
```

---


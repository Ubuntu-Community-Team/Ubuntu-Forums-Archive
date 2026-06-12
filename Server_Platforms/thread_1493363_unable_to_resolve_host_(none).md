---
title: "unable to resolve host (none)"
date: 2010-05-25
forum: Server Platforms
---

### Post by dr_pardee on 2010-05-25
[COLOR=#000000][FONT=Times][FONT=arial]I just built out an Ubuntu Server 10.04.



My problem is setting the hostname. I cloned the machine, then normally on the clone, I would change the /etc/hostname and /etc/hosts file.


However, when I do this, upon restart, I get the message, "init hostname main process (some process number) terminated with status 1"
Then, when the machine finally boots, the hostname is set to (none). Literally has braces like: user@(none):


I've tried: sudo hostname machine_name but it says can't resolve hostname (none).


I've Google'd around a lot but can't get it. It may have something to do with 10.04? I have been using 9.04, 9.10 with no problems.

Thanks,
Eric

[COLOR=#000000][FONT=Times][FONT=arial]eric@(none):~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface

# Had this set to dhcp but a friend suggested making this NIC static to solve this issue

#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 10.70.70.1
gateway 10.70.70.250
netmask 255.255.255.0
network 10.70.70.0
broadcast 10.70.70.255

auto eth1
iface eth1 inet static
address 10.60.60.1
gateway 10.60.60.250
netmask 255.255.255.0
network 10.60.60.0
broadcast 10.60.60.255


eric@(none):~$ sudo hostname fserver
sudo: unable to resolve host (none)

eric@(none):~$ cat /etc/hostname 
[COLOR=#000000][FONT=Times][FONT=arial][COLOR=#000000][FONT=Times][FONT=arial]fserver[/FONT][/FONT][/COLOR][/FONT][/FONT][/COLOR]

eric@(none):~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1 [COLOR=#000000][FONT=Times][FONT=arial][COLOR=#000000][FONT=Times][FONT=arial][COLOR=#000000][FONT=Times][FONT=arial][COLOR=#000000][FONT=Times][FONT=arial]fserver[/FONT][/FONT][/COLOR][/FONT][/FONT][/COLOR][/FONT][/FONT][/COLOR][/FONT][/FONT][/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
[/FONT][/FONT][/COLOR]


[/FONT][/FONT][/COLOR]

---

### Post by arrrghhh on 2010-05-25
Hrm... all my 'fixes' aren't working for me, so I keep editing my post sorry.

I'll go back to my original recommendation - instead of rebooting, try to restart the hostname service.  You'll have to use the new upstart manager, which I haven't quite sorted out yet.  Kinda miss my basic init.d scripts...


I've also been reading this can seriously break sudo.  Are you able to do any other commands using sudo, or is that broken as well?

---

### Post by dr_pardee on 2010-05-25
I tried, with no luck:
eric@(none):/etc$ sudo service hostname restart
sudo: unable to resolve host (none)
restart: Unknown instance: 

eric@(none):/etc$ sudo /etc/init.d/hostname restart
sudo: unable to resolve host (none)
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service hostname restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart hostname
start: Job failed to start

Then I was reading about Upstart and tried, with no luck:
eric@(none):/etc$ sudo initctl restart hostname
sudo: unable to resolve host (none)
initctl: Unknown instance: 

So I tried, with no luck:
eric@(none):/etc$ sudo initctl start hostname
sudo: unable to resolve host (none)
initctl: Job failed to start

Looking at the log, I see the message I see when I boot:
eric@(none):/etc$ tail /var/log/syslog
...
May 25 16:38:28 (none) init: hostname main process (1319) terminated with status 1
May 25 16:43:14 (none) init: hostname main process (1572) terminated with status 1
May 25 16:48:20 (none) init: hostname main process (1619) terminated with status 1
May 25 16:49:54 (none) init: hostname main process (1629) terminated with status 1

---

### Post by capscrew on 2010-05-25
i know you said this was a server install -- but to be sure.  Does it have any desktop components installed?  I ask this because this is suspect with respect to your concerns```
# The primary network interface

# Had this set to dhcp but a friend suggested making this NIC static to solve this issue

#auto eth0
#iface eth0 inet dhcp
```

When you have dhcp supply the hostname you run into just these types of errors.  See [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/537978").  When you comment out the /etc/interfaces file for eht0 DHCP you have not shut off the dhcp3 client.

---

### Post by dr_pardee on 2010-05-25
This is server install, no Desktop components installed that I'm aware of.

I did not know that you can not comment out eth0. I stripped that out and still have the problem. The comment about my friend's suggestion was added to the post only, not really in interfaces file.

---

### Post by dr_pardee on 2010-05-25
On second thought, it wasn't the sudoers file... Sorry all.

In my hostname I had pw_t1_inhouse

I guess you can't have underscores in the hostname. Previously I've never had this problem.

---

### Post by capscrew on 2010-05-25
> **dr_pardee said:**
> This is server install, no Desktop components installed that I'm aware of.

I did not know that you can not comment out eth0. I stripped that out and still have the problem. The comment about my friend's suggestion was added to the post only, not really in interfaces file.

I never said that you can't comment out the interface.  What I'm saying is that if you have setup dhcp, commenting out those lines will not make the dhcp client stop.

The question to you is -- What is the dhcp client doing in your system right now?

---

### Post by capscrew on 2010-05-25
Pretty strange.  Glad you found it.

---

### Post by davst825 on 2010-09-30
I'm having this problem above, though I don't have a hostname with underscores in it. How exactly did you solve this?

---

### Post by dr_pardee on 2010-09-30
davst825: Unfortunately I solved it by changing the hostname with underscores to dashes... Strange anomaly. What hostname are you using?

---

### Post by farazhussain on 2010-11-21
> **dr_pardee said:**
> On second thought, it wasn't the sudoers file... Sorry all.

In my hostname I had pw_t1_inhouse

I guess you can't have underscores in the hostname. Previously I've never had this problem.

This seems to be the problem I was having. I was getting a "hostname main process (nr) terminated with status 1" error at startup (but no other issues).

It was still irritating me though. I read your post and changed my hostname from "my_laptop" to "my-laptop" and that message disappeared. 

So, thanks for this post.

---


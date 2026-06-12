---
title: "Unknown interface ens ..... but its not true !"
date: 2016-09-09
forum: Server Platforms
---

### Post by bob_jones2 on 2016-09-09
Let me start by saying I'm not a noob, I've configured new network interfaces with Ubuntu a gazillion times.    So I'm putting this one down as possibly yet another bug (or "feature") of 16.04LTS.

So, here's the evidence :
```
$ dmesg | fgrep ens
[    2.650580] vmxnet3 0000:13:00.0 ens224: renamed from eth2
$ ifconfig -a | fgrep ens224
ens224    Link encap:Ethernet  HWaddr 00:90:10:cf:11:4c
```

So, ens224 is there !

So, as usual, I add the following to /etc/network/interfaces :

```
auto ens224
iface ens160 inet static
        address 10.20.30.94
        netmask 255.255.255.224
        network 10.20.30.64
        broadcast 10.20.30.95
```

And that's where the fun stars .......

$ sudo systemctl restart networking   
(N.B. I've also tried rebooting "just incase")

```

Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.
Sep 09 15:23:54 px3 systemd[1]: Starting Raise network interfaces...
Sep 09 15:23:54 px3 sh[4529]: Unknown interface ens224
Sep 09 15:23:54 px3 ifup[4535]: Unknown interface ens224
Sep 09 15:23:54 px3 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Sep 09 15:23:54 px3 systemd[1]: Failed to start Raise network interfaces.
Sep 09 15:23:54 px3 systemd[1]: networking.service: Unit entered failed state.
Sep 09 15:23:54 px3 systemd[1]: networking.service: Failed with result 'exit-code'.
```

---

### Post by darkod on 2016-09-09
I assume the "iface ens160" is a typo?

Just out of curiocity, does lshw show the same interface?
```
sudo lshw -short | grep network
```

---

### Post by bob_jones2 on 2016-09-09
"I assume the "iface ens160" is a typo?"

Allright, you win !  ;-)

What's that saying about a second pair of eyes ?

I'll just go quietly put on my dunce cap and stand in the corner crying !

---

### Post by darkod on 2016-09-09
Mark the thread as solved first. ;) (if it is)

Jokes aside, it helps others. You can do that in Thread Tools above the first post.

---

### Post by bob_jones2 on 2016-09-09
"UP BROADCAST RUNNING MULTICAST " .... says it all really.  :(

Will do & thanks again eagle eyes !

---


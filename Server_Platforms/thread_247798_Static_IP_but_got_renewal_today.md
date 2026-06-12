---
title: "Static IP but got renewal today"
date: 2006-08-31
forum: Server Platforms
---

### Post by Kurdt on 2006-08-31
Hi, i had setup an static ip to an ubuntu computer, 2.6.15-26-386 like this in /etc/network/interfaces

```
auto eth0
iface eth0 inet static
address 192.168.1.51
netmask 255.255.255.0
gateway 192.168.1.120

```

The static ip lasted a week, today it renew to 192.168.1.8 (the dhcp server gave it)

What did i do wrong ? maybe the line auto eth0 is wrong? what should i change to have a static ip to last forever?

Thanks

---

### Post by jimm on 2006-08-31
Hi,

Did you reboot or do a /etc/init.d/networking restart after you assigned the static IP address?

Thanks,
James

---

### Post by Kurdt on 2006-08-31
Yes, that's why it worked -a week until renewal-

---

### Post by Kurdt on 2006-08-31
I just noticed that the static IP, lasted EXACTLY ONE WEEK, i did the change to set a static ip exactly in time and day last week.

---

### Post by chipyoung on 2006-08-31
I'll give it a shot.

Could it be that your router is set for a IP lease of 1 week.  I know the default time on my router is 1 day.  Do you have any other wireless PC's on this lan?  Maybe when your lease expires the IP address is given to another device on your network.

Hope that helps.

Chip

---

### Post by Kurdt on 2006-08-31
Mmm... that might be true, as i have no access to the router (ISP restricted) i will have to make a support request to them, and tell you :)

Thanks

---

### Post by dragze on 2006-08-31
Hi, ok i might have misunderstood somewhere, but the ip u gave in ur nic config is a local area ip and your last post you mentioned you do not have access to your router cause it is ISP restricted. is it an ISP's onsite router or something??

Cheers.

---

### Post by Kurdt on 2006-09-01
it's onsite.

There is no way to force ubuntu not to use dhcp?
I am having trouble trying to contact tech support with necessary knowledge to understand the problem...

---

### Post by Iowan on 2006-09-01
I have a Ubuntu server with a static address (but then, it is also the DHCP server).  I'd have thought the static settings would work, but I'm not sure what would happen if you picked a static address that is inside the DHCP range of the router. As **chipyoung** mentioned, the router may have reassigned your static IP when the lease expired... but then you should be seeing address conflicts with whoever got the DHCP address 192.168.1.51.

---

### Post by Kurdt on 2006-09-03
Well, I spoofed ubuntu mac address with the old server who was using .51 addreess, but did not work :( lasted 2 days and it got renewal... :confused: I don't know what to do now...

I have 3 more computer with static addresses (1 FreeBSD 2 Windows) like .5X and they give me no problems...

What could happen if i disable dhcpclient or sort? :(  help please, everytime the address change i leave without service the entire office.

**.5x is outside dhcp's router range**

---

### Post by Kurdt on 2006-09-04
Hi, i read this thread [http://www.ubuntuforums.org/showthread.php?t=227585](http://www.ubuntuforums.org/showthread.php?t=227585) and i did that to give it a try, how do i disable dhclient3 at startup?

maybe this works... i hope.
Thanks

---

### Post by gruepig on 2006-09-05
> **Kurdt said:**
> Hi, i had setup an static ip to an ubuntu computer, 2.6.15-26-386 like this in /etc/network/interfaces

```
auto eth0
iface eth0 inet static
address 192.168.1.51
netmask 255.255.255.0
gateway 192.168.1.120

```

The static ip lasted a week, today it renew to 192.168.1.8 (the dhcp server gave it)

What did i do wrong ? maybe the line auto eth0 is wrong? what should i change to have a static ip to last forever?

Thanks

Okay ... if you set 'iface eth0 inet static', that means eth0 should be configured statically according to the address parameters you assign. It should not be using dhcp at all.  Your /etc/network/interfaces file looks fine (at least the bit you've posted).

Check 'ifconfig -a' and 'route -n' (if you're not sure how to interpret them, post the output).  

Check to see if you have a dhcp client running (it seems you do): 'ps aux | grep dhc' or  'pgrep dhc'.  If you do, you'll want to stop the dhcp client process with 'sudo kill process_number' (process number is in the second column of ps output) or 'sudo pkill process_name' (process name is likely dhclient3).

Then 'sudo ifdown eth0' to take down the eth0 interface and 'sudo ifup eth0' to bring it back up.  Run 'ifconfig -a', 'route -n', and 'ps aux | grep dhc' again.  Your IP should be 192.168.1.51 and no dhclient processes should be running.

---

### Post by Kurdt on 2006-09-06
I killed dhclient 2 days ago and got no renewal until then, so, i hope this is fixed now, i still don't know how to disable dhcp at startup...

Thanks!

---


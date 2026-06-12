---
title: "DHCP Server, Remaining Addresses?"
date: 2012-11-28
forum: Server Platforms
---

### Post by jlacroix on 2012-11-28
I can't seem to find any information on this so I figured I'd ask here. I have a DHCP server running, and it works great. But every now and then, I'd like to check how many address leases remain. I can't seem to find an easy way to do that. Is there any command whatsoever that will say something like "you have X leases remaining"? I know I can go into the leases file and count them, but it shows leases even after they expire and the file can become quite large.

---

### Post by papibe on 2012-11-29
Hi jlacroix.

I don't know if you can do exactly that, but the next best thing would be to see the list of the current leases:
```
more /var/lib/dhcp3/dhcpd.leases
```
Hope it helps.
Regards.

---

### Post by jlacroix on 2012-11-29
> **papibe said:**
> Hi jlacroix.

I don't know if you can do exactly that, but the next best thing would be to see the list of the current leases:
```
more /var/lib/dhcp3/dhcpd.leases
```
Hope it helps.
Regards.
Thank you. That is what I was referring to, it seems to include expired leases. I was hoping there would be a command to just show the remaining number. If nothing else, perhaps it's possible to write a BASH script.

---

### Post by Catalyph on 2012-11-30
If that is the only DHCP server on the network then
nmap -sP 192.168.1.0/24
 
Also this script was created by a user:
[http://ubuntuforums.org/showthread.php?t=926487](http://ubuntuforums.org/showthread.php?t=926487)

---

### Post by jlacroix on 2012-11-30
> **Catalyph said:**
> If that is the only DHCP server on the network then
nmap -sP 192.168.1.0/24
 
Also this script was created by a user:
[http://ubuntuforums.org/showthread.php?t=926487](http://ubuntuforums.org/showthread.php?t=926487)
Great idea in regards to nmap. However, I am confused by the output. It says that I have 256 addresses and three are used. However, my range in the dhcp config is set to .200 through 250.

---

### Post by Catalyph on 2012-11-30
Then
 
nmap -sP 192.168.1.200-250

---

### Post by jlacroix on 2012-11-30
> **Catalyph said:**
> Then
 
nmap -sP 192.168.1.200-250
Thank you, but that one doesn't seem to work at all. 

However, I looked up the nmap man page to find out what that's actually doing, and it doesn't appear to be what I need. It appears to be telling me how many hosts are online, not how many leases dhcp handed out.

I had an issue some months ago where I had no available IP addresses at all. I only have under 10 hosts. It's hard for me to believe that I can actually run out of 50 addresses between 10 machines, when the leases are set to expire in a week. To monitor this, I'd like to find a command to tell me how many leases are currently active. That way, if there is anything funny going on, I can see it.

---

### Post by darkod on 2012-11-30
I know this is not answering your question, but since there don't seem to be too many answers, I fail to see why do you need this so much.

First, with only 10 hosts there is virtually no way to run out of 50 leases. Especially if those hosts are wired. Even when alternating between wired and wi-fi clients, the 50 leases should be fine.

If you have so many clients accessing the network for short periods and taking up a lease, why don't you lower the lease time to 1 or 2 days for example. With long term clients that wouldn't make a difference, the lease will simply get renewed. With short term clients the lease taken will be freed after 2 days and available for other clients.

If you have clients accessing the network for very short time and never coming back, having a 7d lease time will keep that lease allocated for a week, which is pointless.

---

### Post by jlacroix on 2012-11-30
> **darkod said:**
> I know this is not answering your question, but since there don't seem to be too many answers, I fail to see why do you need this so much.

First, with only 10 hosts there is virtually no way to run out of 50 leases. Especially if those hosts are wired. Even when alternating between wired and wi-fi clients, the 50 leases should be fine.

If you have so many clients accessing the network for short periods and taking up a lease, why don't you lower the lease time to 1 or 2 days for example. With long term clients that wouldn't make a difference, the lease will simply get renewed. With short term clients the lease taken will be freed after 2 days and available for other clients.

If you have clients accessing the network for very short time and never coming back, having a 7d lease time will keep that lease allocated for a week, which is pointless.
I have it set to a day now.

I am asking about this because it's been on my mental list for a while and I am now getting around to investigating it. I was under the impression that the dhcp server was simply never releasing IPs. At the time, I solved it by deleting the leases file. I've done that a few times since. 

I ask mainly because this is a handy thing to have. Being able to easily check this is not out of the question. As powerful as Linux is, I am actually completely baffled that there isn't a command for the dhcp server to give you a readout of available addresses, or even just a numerical value of how many leases remain. Even Windows has this.

Even though I only have a few machines, I am studying to be certified and to take this knowledge to a company some day, and it's a good thing to know how to do.

---

### Post by darkod on 2012-11-30
I agree it would be a very useful information, even better if you can get it by issuing only few commands.

But so far there doesn't seem to be a way, and my google search also returns nothing...

---

### Post by jlacroix on 2012-11-30
> **darkod said:**
> I agree it would be a very useful information, even better if you can get it by issuing only few commands.

But so far there doesn't seem to be a way, and my google search also returns nothing...
I think it's conceivable to write a bash script to parse the number available, but I'm not quite good enough to do that just yet...

---


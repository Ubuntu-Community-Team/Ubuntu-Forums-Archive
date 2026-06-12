---
title: "My router has been hacked"
date: 2008-04-19
forum: Security Discussions
---

### Post by blastus on 2008-04-19
My router has been hacked. This morning I checked my router's DHCP client list as I haven't checked it in a number of days. The following device in the list was a cause for concern...

IP Address = 172.28.4.96
Host Name = Macintosh
MAC Address = 00:1E:C2:XX:XX:XX

I put the XX's in there. The problem is that I don't own any network devices that start with 00:1E:C2. This device appears to be a MacBook based on this address? This is what was in my router logs...

```
04/18/2008  22:03:42 sending ACK to 172.28.4.96

04/18/2008  22:03:40 sending ACK to 172.28.4.96

04/18/2008  22:03:37 sending OFFER to 172.28.4.96

04/18/2008  22:03:29 sending OFFER to 172.28.4.96

04/18/2008  22:03:21 sending OFFER to 172.28.4.96

04/18/2008  22:03:08 sending OFFER to 172.28.4.96

04/18/2008  22:03:05 sending OFFER to 172.28.4.96

04/18/2008  22:03:04 sending OFFER to 172.28.4.96
```

I don't understand how my wireless could have been hacked as I am using WPA2-AES encryption with a secure 63-character PSK generated from GRC + MAC address filtering only on the wireless side. I also have a secure password with the maximum allowable length for my router as well generated from GRC.

Here's the biggest issue of all, I turned OFF wireless on my router a few days ago and am just using a wired connection. I don't know if the hack was from wireless or from the Internet. How can I tell and what can I do about this?

---

### Post by ATLANT3AN-UK on 2008-04-19
As much as I hate wireless and refuse to ever use it from a security perspective with the security you described it would be extremely hard to hack your wireless connection even to the point where I would say its publicly not possible with known techniques but of course who knows what could be done in the private world.

It cannot be from the internet as the host would not have anything to do with DHCP, the attacker uses your connection they don't act like a machine on your network unless physically plugged in which is only possible in your case wirelessly, so a safe bet would be it was when you had it set on wireless.

If you are that worried about it, I would suggest formatting your machine and setting fresh router passwords if you have not done so already and stick with wired as I do, although those wireless settings should stop 99.9% of all hackers even attempting to crack your network.

ATLANT3AN :)

---

### Post by floke on 2008-04-19
Of course you could always enable MAC filtering in your router settings and add the MAC address to it, which will block the device with that address.

---

### Post by blastus on 2008-04-19
[QUOTE=ATLANT3AN-UK]As much as I hate wireless and refuse to ever use it from a security perspective with the security you described it would be extremely hard to hack your wireless connection even to the point where I would say its publicly not possible with known techniques but of course who knows what could be done in the private world.[/QUOTE]

I agree with you completely about the wireless security. What's very strange about this is that I have MAC address filtering on on the wireless side and only the MAC address of my laptop is allowed in. I know that MAC address filtering provides absolutely no security but I think the MAC address of that foreign machine would have had to have been spoofed to the MAC address of my laptop--but it clearly wasn't. This leads me to believe there is a bug in the router.

[QUOTE=ATLANT3AN-UK]It cannot be from the internet as the host would not have anything to do with DHCP, the attacker uses your connection they don't act like a machine on your network unless physically plugged in which is only possible in your case wirelessly, so a safe bet would be it was when you had it set on wireless.[/QUOTE]

Thanks for clearing that one up :) 

I have noticed some strange things about the router. Sometimes the DHCP client list is not up-to-date, i.e. sometimes some or all of my machines drop off the list even though they are actively connected and using the network. Sometimes I click Refresh and my computers are on the list, then click refresh a second later and there are NO computers on the list. I turned OFF wireless because I needed a high bandwidth connection to my network from my laptop.

[QUOTE=ATLANT3AN-UK]If you are that worried about it, I would suggest formatting your machine and setting fresh router passwords if you have not done so already and stick with wired as I do, although those wireless settings should stop 99.9% of all hackers even attempting to crack your network.ATLANT3AN :)[/QUOTE]

The only conclusion I can come to is that this router has some kind of bug (exploit) that allowed this happen wirelessly. Nothing else makes sense and that 00:1E:C2 address looks like a wireless Apple device. I don't like this router because I can't log or track much of anything with it...the log history is very small. I can't, for example, hook into it and be notified when new clients attach to the network.

What I'm going to do is get a switch and use my desktop as a gateway/router because I really need a gigabyte network anyway. That way I can totally track everything. Maybe I'll figure out how to hook up the router to my gateway (so I guess it will have 3 network cards in it) and setup some kind of honeypot. It would be cool to make it so that every web page a client tries to access goes to a web page that tells them they are busted or something like that. :)

---

### Post by blastus on 2008-04-19
> **floke said:**
> Of course you could always enable MAC filtering in your router settings and add the MAC address to it, which will block the device with that address.

But I did have MAC address filtering on on the wireless side and I know it worked before because I tested before. I think there is a bug in this router because only the MAC address of my laptop has ever been allowed in wirelessly. I don't have any other wireless devices except my laptop.

---

### Post by tturrisi on 2008-04-20
Your log doe NOT show the router was hacked.  It just shows that someone became aware that your wlan exists and attempted to connect to it.  The router ack'd the user & sent a dhcp offer.  However, the user did not have the passkey and could not connect.

All APs will send dhcp offers IF dhcp is enabled in the router, it a client sends a request to connect, even if mac address filtering is used and even if ssid broadcast is disabled.

Someone could easily get your WPA passkey IF the passkey is a word that exists in a dictionary or is a first or last name.

172.0.0.0 to 172.255.255.255 are private ip addresses used ONLY for local networks, just like the 192.168.x.x and 10.x.x.x addresses.  That 172.x.x.x address was assigned to the comp. by the mac operating system at boot.

---

### Post by blurg on 2008-04-20
Presumably if you are only ever letting your laptop connect to the router you don't need dhcp? Just set up your computer and the router with static ip.

---

### Post by Chayak on 2008-04-20
You were not hacked.  What your log is showing is  wireless device trying to authenticate to the router.

The way wireless authentication works is a client sends a connection request to the access point.  The access point sends an encrypted challenge to the client and the client (if it has the correct key) decrypts it and sends a reply.  If that succeeds then the client will be able to use the AP

What is looks like is your router sent an ACK back to a client to tell it that it had recieved the request then it sent an OFFER to authenticate which it did not reply to so it was sent again.    Nothing authenticated so no hack was done.

What this is most likely is a mac with it's airport on and configured to auto connect.  It probably tried to authenticate against every wifi point it detected.  That or the owner was just clicking down the list to see if he/she could connect to one.

You might consider turning off your SSID broadcast.  It won't show up in AP lists that way and you'll have to manually enter the name to configure something to connect to it but it'll keep the vast majority of people from trying not to say that someone who knows how to find it won't but it just makes it a little harder.

---

### Post by blastus on 2008-04-20
> **tturrisi said:**
> Your log doe NOT show the router was hacked.  It just shows that someone became aware that your wlan exists and attempted to connect to it.  The router ack'd the user & sent a dhcp offer.  However, the user did not have the passkey and could not connect.

All APs will send dhcp offers IF dhcp is enabled in the router, it a client sends a request to connect, even if mac address filtering is used and even if ssid broadcast is disabled.

Someone could easily get your WPA passkey IF the passkey is a word that exists in a dictionary or is a first or last name.

172.0.0.0 to 172.255.255.255 are private ip addresses used ONLY for local networks, just like the 192.168.x.x and 10.x.x.x addresses.  That 172.x.x.x address was assigned to the comp. by the mac operating system at boot.

Ok that makes sense, but in the router under DHCP it says that these are the devices that are *connected* to my network. Maybe it's just really bad wording but to me, if you are connected to a network and have an IP address, you are on the network and can see other machines on that network.

The 172.x.x.x address range is configured in my router. I changed it from the default 192.168.x.x.

---

### Post by blastus on 2008-04-20
> **Chayak said:**
> You were not hacked.  What your log is showing is  wireless device trying to authenticate to the router.

The way wireless authentication works is a client sends a connection request to the access point.  The access point sends an encrypted challenge to the client and the client (if it has the correct key) decrypts it and sends a reply.  If that succeeds then the client will be able to use the AP

What is looks like is your router sent an ACK back to a client to tell it that it had recieved the request then it sent an OFFER to authenticate which it did not reply to so it was sent again.    Nothing authenticated so no hack was done.

What this is most likely is a mac with it's airport on and configured to auto connect.  It probably tried to authenticate against every wifi point it detected.  That or the owner was just clicking down the list to see if he/she could connect to one.

You might consider turning off your SSID broadcast.  It won't show up in AP lists that way and you'll have to manually enter the name to configure something to connect to it but it'll keep the vast majority of people from trying not to say that someone who knows how to find it won't but it just makes it a little harder.

That means then that the DHCP client list is not useful for determining who is actually connected to your network--you have to scour through the router log to determine who is actually on the network! I think I have seen this before in the router logs when I tested connecting with my laptop with an invalid PSK. This is a huge problem because the log on this router doesn't keep history for a very long period of time.

Perhaps the DHCP client list should have been split into two categories; 1. the list of clients actually connected to the network (for wireless clients that means actually authenticated), and 2. the list of clients that tried to connect to the network but failed because of authentication. That would contain much more practical information.

I did at one point disable SSID broadcast but it just makes it a little harder to connect as there are other access points around here where there is no SSID. I have since gotten a new router to handle gigabyte wired connections but I'm not using wireless at this point.

---

### Post by picopir8 on 2008-04-21
Rather than using MAC filtering, I recommend the honey pot approach.  Set up static IPs or static DHCP for all your network devices and then use DHCP to assign an IP to any unknown device.  Lock down that pool of IPs so that the unauthorized devices can not do anything, but because they are on your network you will now be able to log the activity better.  Of course if you notice many repeat offenders, then you could block their MAC address.  Though I do not like to use MAC address filtering on a global level because someone can easily spoof an approved device and gain access.  Since they look like an approved device it is more difficult to detect their presence.  However, most people looking for a quick hack wont take the time to sniff for valid MAC addresses.  Let them in early to learn their behavior (particular port accesses at particular times) and then implement rules across the entire network that would prevent similar behavior should they spoof an approved device.

---

### Post by blastus on 2008-04-22
> **picopir8 said:**
> Rather than using MAC filtering, I recommend the honey pot approach.  Set up static IPs or static DHCP for all your network devices and then use DHCP to assign an IP to any unknown device.  Lock down that pool of IPs so that the unauthorized devices can not do anything, but because they are on your network you will now be able to log the activity better.  Of course if you notice many repeat offenders, then you could block their MAC address.  Though I do not like to use MAC address filtering on a global level because someone can easily spoof an approved device and gain access.  Since they look like an approved device it is more difficult to detect their presence.  However, most people looking for a quick hack wont take the time to sniff for valid MAC addresses.  Let them in early to learn their behavior (particular port accesses at particular times) and then implement rules across the entire network that would prevent similar behavior should they spoof an approved device.

I guess my only concern about using static IP addresses based on MAC address is that it is very easy for a wireless device to discover the MAC address of a wireless device that is on your network. Isn't that the first thing an attacker would do to get on a wireless network; sniff the air and determine the MAC address or MAC addresses of the device(s) connected to the wireless network and then spoof one of those addresses?

---

### Post by netlogic on 2008-04-23
Mac address filtering doesn't do anything. 
Someone can just listen to the broadcast, copy and paste your mac address.
Also, you didn't get hacked. :)
Be glad.

---


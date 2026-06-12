---
title: "Unnecessary dns queries"
date: 2010-07-18
forum: Security
---

### Post by linuxyogi on 2010-07-18
Hi, I connect to the internet using an adsl modem in bridged mode.
I use firestarter to configure the firewall.
All incoming ports are blocked. (I confirmed that at grc.com)
Outgoing is permissive by default.

Now, the problem is lately I started noticing the LED indicators on the modem which generally blinks when there is some data transfer takes place, blinking unnecessarily.

My first thought was that ubuntu is checking for updates. 
I opened etherape just to check. But what I saw was really strange. Etherape was showing an exceptionally high number of DNS queries to numerous nodes.

Next I opened terminal & started nethogs to check if any app ia accessing the internet but there was none.

Then I opened firestarter to check its log.
There log was really getting flooded by entries. (A few of them "serious" according to firestarter)
Also there's a place in firestarter called "active connections". It was empty too.

I ran a scan using rkhunter. Nothing strange there too.

I fail to understand what's causing all these dns queries.

Please help.

---

### Post by movieman on 2010-07-18
Is it some kind of reverse DNS lookup? If someone's trying to connect to your system then it might be trying to look up their hostname so it can log the attempted connection.

---

### Post by linuxyogi on 2010-07-18
> **movieman said:**
> Is it some kind of reverse DNS lookup? If someone's trying to connect to your system then it might be trying to look up their hostname so it can log the attempted connection.

Well, when I start etherape first the ip appears then it changes to a name.
They look like ----- 1234.xyz.abcd.net
What lookup is that?

I guess attempts are being made to connect to my PC otherwise why is the protocol telnet showing up in the etherape protocol window?
Other frequently appearing protols are -----------
microsoft-ds
udp-unknown
ms-sql-s
telnet
loc-srv
tcp-unknown
icmp

Previously I used to use DNS Advantage DNS service & the google dns service. Now I am using my ISP's DNS but these things haven't stopped.

One more thing, is there any method in Ubuntu which enables NAT? My adsl modem, when configured in PPPOe mode offers this feature. I saw this feature in fedora some years back. I guess it was in fedora's integrated firewall.

---

### Post by lisati on 2010-07-18
Do you have any server software or Windows machines running on your home network that could have caught something untoward? Just a thought :)

---

### Post by linuxyogi on 2010-07-18
> **lisati said:**
> Do you have any server software or Windows machines running on your home network that could have caught something untoward? Just a thought :)

Server software ... meaning? I am using Ubuntu 10.04 Desktop & my old PC is running Hardy. Thats it.

No, there are no windows machine here. 

Thanks.

---

### Post by lisati on 2010-07-18
> **linuxyogi said:**
> Server software ... meaning? I am using Ubuntu 10.04 Desktop & my old PC is running Hardy. Thats it.

No, there are no windows machine here. 

Thanks.
Just a hunch on my part which apparently was incorrect. 

By "server software" I mean stuff that might work behind the scenes to host a web site or deal with email, and not having a Windows machine hooked up reduces the chance of malware doing something "naughty" to virtually zero.

<side note>If you choose to check the "black list" link in my sig, it might prove interesting.</side note>

---

### Post by linuxyogi on 2010-07-18
> **lisati said:**
> 
<side note>If you choose to check the "black list" link in my sig, it might prove interesting.</side note>

Hi, I visited the link in your signature & found that my IP was listed in some of the RBLs.
I don't have a static ip.

Can this be a cause for worry?

It was written there -----
"Listing in any of the above does not necessarily mean you are a spammer.
It could simply mean that another user of your ISP and/or ESP has been misbehaving."

So, in such a case do I need to do anything or leave it as it is?

Thanks again.

---

### Post by noway2 on 2010-07-18
On one of your (linux) machines, run the TCPDUMP command for a few seconds.  You will probably see traffic for ARP packets from your machines talking to each other, as well as if any applications are trying to "phone home".

As far as being on the 'black lists', it is likely that your IP range has been black listed because it is not static.  While this is slowly becoming a thing of the past, traditionally 'users' who are the bulk of the dynamic IP pool don't run their own mail servers.  Hence, by virtue of being a dynamic IP, it would be unexpected to have mail originate from your IP without passing through a valid SMTP server.

---

### Post by OpSecShellshock on 2010-07-18
> **noway2 said:**
> On one of your (linux) machines, run the TCPDUMP command for a few seconds.  You will probably see traffic for ARP packets from your machines talking to each other, as well as if any applications are trying to "phone home".

As far as being on the 'black lists', it is likely that your IP range has been black listed because it is not static.  While this is slowly becoming a thing of the past, traditionally 'users' who are the bulk of the dynamic IP pool don't run their own mail servers.  Hence, by virtue of being a dynamic IP, it would be unexpected to have mail originate from your IP without passing through a valid SMTP server.

Yeah. Every ISP that provides IP address space for home use is on one blacklist or another simply due to all the bots and/or spoofed headers out there. Checking those lists probably won't tell you anything valuable in most cases.

---

### Post by linuxyogi on 2010-07-19
Then I guess there is nothing to be done at my end.

Thanks a lot for your replies.:D

---


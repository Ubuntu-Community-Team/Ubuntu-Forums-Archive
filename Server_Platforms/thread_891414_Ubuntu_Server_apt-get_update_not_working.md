---
title: "Ubuntu Server: apt-get update not working"
date: 2008-08-16
forum: Server Platforms
---

### Post by gatlin on 2008-08-16
I am running Ubuntu Server 8.04.1 on my home network.  I have a Netgear router, and I connect with dhcp (I'm not heavy into networking and server administration, hence my choice of the wonderful Ubuntu).  Ubuntu really is great, but lately, when I type "sudo apt-get update," I get the following:

```

Err http://archive.ubuntu.com hardy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

I don't know where to begin; I did once erroneously edit /etc/hosts (I put it back in place but of course will paste it on demand), but I don't recall that triggering the problem.  The server's hostname is "deuteronomy."  I am completely and utterly lost in the world of networking, so type slowly for me :)

---

### Post by windependence on 2008-08-16
Post the output of :

```
cat /etc/resolv.conf
```


-Tim

---

### Post by gatlin on 2008-08-16
cat /etc/resolv.conf is 
```
nameserver 192.168.1.1

```

Maybe it would also help to know the server's IP address is 192.168.1.3.  Grazie!

---

### Post by fjgaude on 2008-08-16
You can't update if you are not connected to the Internet, to the repositories, or am I wrong?

---

### Post by gatlin on 2008-08-16
The server is connected to the internet, and I know this because I am SSHing in from my other computer across town :) So I am connected to the internet, and I can ping "archive.ubuntu.com" and "security.ubuntu.com" from the server and that's all fine and dandy, but aptitude for some reason has trouble resolving those domains.  That's my best guess: aptitude configuration issue, but I would have no clue.  So, as I said earlier, anything you need pasted here, I won't question it.  Thanks!

[Edit]
Here are some commands I've run at the behest of knowledgeable friends (who are stumped but had some insights)
```
gatlin@deuteronomy:~$ nslookup security.ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   security.ubuntu.com
Address: 91.189.88.37
```

```

gatlin@deuteronomy:~$ cat /etc/hosts

127.0.0.1       localhost
127.0.1.1       deuteronomy

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I readily admit I once edited /etc/hosts but I think I put it back together right. But that might be the issue here.  

And then also, I believe (will verify when I get to the house and the router) that the router's IP address 192.168.1.1

Again, thank you for your time.

---

### Post by fjgaude on 2008-08-16
Here's what I get:

frank@sunshine:~$ nslookup security.ubuntu.com
Server:		68.94.156.1
Address:	68.94.156.1#53

Non-authoritative answer:
Name:	security.ubuntu.com
Address: 91.189.88.37

The 68 addresses are my DNS IPs. 

It's like your router is not passing your DNS to your server, or something like that. Maybe Tim will come on and show the way. <smile>

Here's my hosts file:

127.0.0.1 localhost
127.0.1.1 sunshine

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.101 moonlight
192.168.45.128 happystar
192.168.1.104 stardust

---

### Post by windependence on 2008-08-16
OK, make your /etc/resolv.conf look like this:

nameserver 192.168.1.1
nameserver 208.67.222.222
nameserver 208.67.220.220

Save the file and restart the network. Then try it.

I have another idea if that doesn't work.

-Tim

---

### Post by gatlin on 2008-08-16
Thank you windependence (and fj!).  I will be at the house soon to actually restart the network.  I assume that restarting the network means unplugging the router briefly, and if it doesn't I don't have remote access to it, so I guess what I'm saying is: don't unsubscribe yet because if it's not the solution I won't know for a while.  But thank you muchly!

---

### Post by fjgaude on 2008-08-16
Should not the namesever for the DNS come from the router? If it doesn't that means the router is not set for DHCP, right? Likely not, but the ISP should supply it, yes!

frank

---

### Post by gatlin on 2008-08-16
I tried both of your ideas (using the IP addresses that windependence gave, and then fjgaude's idea of using the nameservers from my router), and neither worked.  For the sake of clarity, I'm using the ones from windependence.  I changed /etc/resolv.conf and restarted the network both times, to no avail.  

So, windependence, what was your other idea?  I'm all ears!

---

### Post by gatlin on 2008-08-16
I recently followed a tutorial that enabled netatalk on my server (to use Apple Time Machine), and this is what my /etc/nsswitch.conf file looks like ... might be worth it to someone.  Right now the updates working is more important than Time Machine, so maybe this can be diagnosed

```
gatlin@deuteronomy:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

The reason I point this out is because even though netatalk is running, Deuteronomy does not show up as an AFP (Apple networking) share.  Time Machine/AFP had actually been working, but someone recommended I change nsswitch to its current configuration for various performance reasons (I promise in the future to be better about backups, as well as taking advice at face value).  I believe it was pretty much factory default until then, so I can take anyone's.

---

### Post by fjgaude on 2008-08-16
I know nothing about Time Machine. Questions: do you have an ISP and did they give you two IPs for the DNS?

If they did, then that is likely what should be used as nameserver in /etc/resolv.conf file.

Here's the ones I use:

nameserver 68.94.156.1
nameserver 68.94.157.1

And I'm with AT&T as ISP.

---

### Post by jerome1232 on 2008-08-16
> **gatlin said:**
> The server is connected to the internet, and I know this because I am SSHing in from my other computer across town :) So I am connected to the internet, and I can ping "archive.ubuntu.com" and "security.ubuntu.com" from the server and that's all fine and dandy, but aptitude for some reason has trouble resolving those domains.  That's my best guess: aptitude configuration issue, but I would have no clue.  So, as I said earlier, anything you need pasted here, I won't question it.  Thanks!

[Edit]
Here are some commands I've run at the behest of knowledgeable friends (who are stumped but had some insights)
```
gatlin@deuteronomy:~$ nslookup security.ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   security.ubuntu.com
Address: 91.189.88.37
```

```

gatlin@deuteronomy:~$ cat /etc/hosts

127.0.0.1       localhost
127.0.1.1       deuteronomy

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I readily admit I once edited /etc/hosts but I think I put it back together right. But that might be the issue here.  

And then also, I believe (will verify when I get to the house and the router) that the router's IP address 192.168.1.1

Again, thank you for your time.

I think the wrong tree is being barked up, I'm stumped as to what is happening but names are resolving just fine to ip's. It doesnt' look like a dns issue.

---

### Post by fjgaude on 2008-08-16
As as a potential work-around put into your hosts file the name

Name:   security.ubuntu.com
Address: 91.189.88.37

and then maybe apt-get update might work. <smile>

---

### Post by jerome1232 on 2008-08-16
Can you try and ping security.ubuntu.com and post the output of route?

(if the above solution doesn't fix it)

---

### Post by gatlin on 2008-08-16
> **fjgaude said:**
> As as a potential work-around put into your hosts file the name

Name:   security.ubuntu.com
Address: 91.189.88.37

and then maybe apt-get update might work. <smile>

I did that, as well as put archive.ubuntu.com in there, and now it works.  But this is a temporary fix; it's not a DNS issue, so what else could it be?  Windependence said he might have another idea, so maybe that could be it.  Since the hosts thing worked, maybe that's a clue? 

Thank you everybody for your tenacity.

---

### Post by gatlin on 2008-08-16
> **jerome1232 said:**
> Can you try and ping security.ubuntu.com and post the output of route?

(if the above solution doesn't fix it)

```
gatlin@deuteronomy:/etc$ ping security.ubuntu.com
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=1 ttl=44 time=152 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=2 ttl=44 time=155 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=3 ttl=44 time=153 ms
64 bytes from security.ubuntu.com (91.189.88.37): icmp_seq=4 ttl=44 time=153 ms
...
--- security.ubuntu.com ping statistics ---
139 packets transmitted, 139 received, 0% packet loss, time 137995ms
rtt min/avg/max/mdev = 151.535/154.303/164.299/2.043 ms


```

---

### Post by jerome1232 on 2008-08-16
Actually the ping doesn't matter anymore since the host thing fixed it, I was more looking to see if maybe the default route wasn't correct or possibly port 80 outbound had been blocked, but since editing /etc/hosts fixed it, well I'm stumped because that points to DNS was screwed up yet nslookup was working fine :S

so I have no clue as to why it wasn't working :)

---

### Post by fjgaude on 2008-08-16
One more time: Questions: do you have an ISP and did they give you two IPs for the DNS?

---

### Post by gatlin on 2008-08-16
> **fjgaude said:**
> One more time: Questions: do you have an ISP and did they give you two IPs for the DNS?

Sorry, sorry.  Yes, my ISP is Time Warner, and the two IPs they gave me for DNS are 24.93.41.127 and 24.93.41.128 and they are now set in my /etc/resolv.conf

---

### Post by fjgaude on 2008-08-16
You might try commenting out the ubuntu address in your hosts file and see if the DNS is working.

---

### Post by gatlin on 2008-08-16
I'm actually just going to format it, and if the same thing happens again after I reconfigure it (which takes about 20 minutes, I only need a few services on it), I will notify.  Otherwise, I fear I messed around where I shouldn't have so that could be the problem.  Thanks anyway!

---

### Post by windependence on 2008-08-17
> **gatlin said:**
> I did that, as well as put archive.ubuntu.com in there, and now it works.  But this is a temporary fix; it's not a DNS issue, so what else could it be?  Windependence said he might have another idea, so maybe that could be it.  Since the hosts thing worked, maybe that's a clue? 

Thank you everybody for your tenacity.

Aaaaaahhhh please don't re-install yet again. That is so , well, Windoze. You have a perfectly good install, none of rthe ings we have done will mess you up.

That WAS my other idea to put the entries for ALL the repositories in your hosts file. This is actually a good idea anyway because it eliminates a DNS lookup from the outside. When Linux needs to do a DNS query, the first place it looks is the hosts file, then the gateway, and then the outside DNS you provide OR whatever it resolves from DHCP as the DNS server.

Just a bit on DNS since veryone here seems confused about ISP servers etc.

You can use WHATEVER DNS servers you want in your resolv.conf. DNS does not have to go through your router, it will check that address anyway (the gateway). You should pick DNS servers that are fast and that will speed up any query you make to the outside including web browsing. the DNS servers I gave you were from OpenDNS. They are great because even if the response is a few miliseconds slower, because they are so popular, they have a lot of cached information. The way DNS works is that all DNS servers on the web are aware of all the other DNS servers. When a query is made, it will query the DNS server you specified and if the name isn't cached in that server, then that server will query other servers until it finds the name and resolves the IP address. As you can imagine, if the information is not cached, it can take a alot longer to resolve the name. This doesn't just happen for the domain you are surfing but for every picture, and every file on the site, it has to do a DNS query. Speed can be very important here. If each query takes 100ms and you have 10 queries there is a full second. Doesn't seem long but it is.

Putting DNS entries into your hosts file for sites you visit regularly is a really good idea if you like speed.

-Tim

---

### Post by gatlin on 2008-08-17
It is a little Windows, but it's over and done now.  What's more is, I now know what every file SHOULD look like.  I think my issue was related to netatalk because it wasn't showing up in my Apple network list, either.  I know the /etc/hosts thing works but that is treating the symptom, not the disease.

*Don't get me wrong --* thank you very much!! Really! But Ubuntu takes like 10 minutes to install and I had /home on a separate partition anyway for exactly this situation (I routinely test out other distros on the empty space, and keep my /home in all of them).  Thank you, though, really!

---

### Post by windependence on 2008-08-17
If you're running OSX, you shouldn't need netatalk at all. :)

Glad to help. I am quite sure it was some sort of DNS issue, but we had made so many changes that something probably got lost in the sauce. The DNS info was mainly for the rest of the forum because DNS and DHCP is something a lot of people just don't understand. Once you understand it, it's pretty simple. I would try the Open DNS servers if you get the chance, they are great. Good luck!

-Tim

---

### Post by jerome1232 on 2008-08-17
I just didn't understand why when the names were resolving correctly you guys jump to editing /etc/hosts and looking at /etc/resolv.conf (which would only solve dns woes), I've seen your posts before and I know you know your stuff. Seemed backwards to me. I was wrong lol cheers!

---

### Post by windependence on 2008-08-17
Well we kind of shotgunned this one. We were making so many changes I think we lost track. You should always do one thing at a time and then test. In some cases we didn't adhere to that. 

Actually, even though it seemd like the names were resolving, I think there was still a routing issue in there somewhere. Lots of confusion on this one, LOL. 

-Tim

---

### Post by gatlin on 2008-08-17
Hey, thanks! And, strictly speaking, Ubuntu needs netatalk + avahi to communicate with the Mac, but you're right, the Mac doesn't need it.  

But yes, I hope this thread serves to help out with DNS problems in the future.  Onward!

---

### Post by vertigo23 on 2008-08-29
I just had the identical problem and found this thread (thanks Google!).  I have a solution.

Replace this line in /etc/nsswitch.conf

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

with this

hosts:          files dns mdns4

And aptitude/apt-get start working perfectly.  This is in Ubuntu 8.04.1 Server, totally fresh install.

---

### Post by gatlin on 2008-08-30
Just to be clear, does that require any sort of restarting of services?  I mean, I fixed it with the Windoze (R) method, but for posterity it might be something to clear up.

Anyway, thanks!  Considering I reinstalled my system and set it up EXACTLY as it had been before, this problem might very well crop up again :)

I had edited that line to get mdns and netatalk working; is your suggestion what the default line is?

---

### Post by windependence on 2008-08-30
> **vertigo23 said:**
> I just had the identical problem and found this thread (thanks Google!).  I have a solution.

Replace this line in /etc/nsswitch.conf

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

with this

hosts:          files dns mdns4

And aptitude/apt-get start working perfectly.  This is in Ubuntu 8.04.1 Server, totally fresh install.

This bug:

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940)

Was supposed to have been fixed following Feisty. Maybe it still exists?

Also, you may want to explain to the forum just what the /etc/nsswitch.conf file is for.

-Tim

---


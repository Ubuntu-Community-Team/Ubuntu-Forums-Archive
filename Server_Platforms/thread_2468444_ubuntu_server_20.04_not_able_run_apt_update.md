---
title: "ubuntu server 20.04 not able run apt update"
date: 2021-10-29
forum: Server Platforms
---

### Post by kvstudio6 on 2021-10-29
hi expert, 
I using ubuntu server 20.04 and I running error when running apt-get update. 
how I can solve it ? thanks help.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289392&stc=1[/IMG]

---

### Post by TheFu on 2021-10-30
The repos there may be down for any number of reasons. Bad hardware, end of a contract, key person on vacation, some govts filter ... hard to know.
Wait a few days for it to solve itself or try a different set of repos - perhaps located in a different country.
If you've already waited a few days, you'll definitely want to find a different source for repos.
I was able to ping the IP above and when I point a web browser at [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/), it seems fine.

---

### Post by MAFoElffen on 2021-10-31
Looking at it... Where does "[COLOR=#ff0000]my.[/COLOR]archive.ubuntu.com" point to?

I can ping it... But just curious. Which brings up the diagnosics of network connection issues like this...

If you get an nw connect issue, like this on update the apt cache, the first thing to do is use ping to see if you can ping the address.
```

ping my.archive.ubuntu.com

```
if it is good, then apt update should work. If not, then try to ping the host domain...
```

ping ubuntu.com

```
If that worked, but the previous didn't, that tells you the repo itself is down. 
If that doesn't work, then see if your see yourself and your own network... If any of these fail, you can stop right there (no need to go on to the next step in this section until the previous failure is corrected).
```

ip addr     # get your own address (and gateway info), if not assigned or in the 167.xxx.xxx.xxx range (this would mean your dhcp server is down), there is a problem...
ping 127.0.0.1     # ping the link local/home/yourself. This is the 'inside' addr of your NIC. If fails, then your have a hardware or driver problem.
ping <the_same_IP_addr_of_yourself_from_above>     # see if you can ping the outside of your device's NIC, If fails this is a hardware, or drive problem
ping <gateway_address>     # can you see your way out of your Local LAN segment. This may be various problems.

```
If you get that far, then try to ping something that should always be up, such as google.
```

ping www.google.com

```
if that does not work, then
```

ping 8.8.8.8 # google's open DNS's IP address...

```
If you failed to ping the google named address, but can ping the numeric IP address of, then you have a DNS problem...

  * This is assuming you are hardwire connected to your Local LAN, and assuming that you first confirmed that you had a green link light status on your NIC. If wireless, then a few other steps thrown in...

*** The thing is, the "ping" utility is a network tool that is basic, included universally between almost all operating systems, and is so useful, if you understand how to use it and the reasoning behind what to do with it. That is why it IS included universally as a utility.

---

### Post by MAFoElffen on 2021-10-31
Looking at it... Where does "[COLOR=#ff0000]my.[/COLOR]archive.ubuntu.com" point to?

I can ping it... But just curious. Which brings up the diagnosics of network connection issues like this...

If you get an nw connect issue, like this on update the apt cache, the first thing to do is use ping to see if you can ping the address.
```

ping my.archive.ubuntu.com

```
if it is good, then apt update should work. If not, then try to ping the host domain...
```

ping ubuntu.com

```
If that worked, but the previous didn't, that tells you the repo itself is down. 
If that doesn't work, then see if your see yourself and your own network... If any of these fail, you can stop right there (no need to go on until corrected).
```

ip addr # get your own address (and gateway info), if not assigned or in the 169.254.xxx.xxx range, there is a problem with dhcp...
ping 127.0.0.1 # ping the link local/home/yourself
ping <the_same_addr_of_yourself_from_above>
ping <gateway_address>
[code]
If you get that far, then try to ping something that should always be up, such as google.
[code]
ping www.google.com

```
if that does not work, then
```

ping 8.8.8.8 # google's open DNS's IP address...

```
If you failed to ping the google named address, but can ping the numeric IP address of, then you have a DNS problem...

---


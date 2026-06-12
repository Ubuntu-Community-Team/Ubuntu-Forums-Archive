---
title: "server download speed"
date: 2017-02-16
forum: Server Platforms
---

### Post by mrjk990 on 2017-02-16
hello
i have vps ubuntu 14.04 location canada 
connection speed 1000mb /s
but when use wget download speed about 800kb /s
i want use my vps for rapidleech script
how i can solve this problem 
any help please 

```

ethtool eth0
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off (auto)
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes


```

---

### Post by darkod on 2017-02-16
If your server has a network connection of 1Gb/s that doesn't mean the provider is giving you that speed. You should check with them what speed you should expect from the VPS, unless you already know as part of the package you contracted.

Then, you tried wget getting a file from where? The speed will also depends on the setup and speed of the origin from where you tried getting the test file.

If your VPS provider is good, for most connections to the same country (where the datacentre is) you should expect high speeds.

---

### Post by mrjk990 on 2017-02-16
> **darkod said:**
> If your server has a network connection of 1Gb/s that doesn't mean the provider is giving you that speed. You should check with them what speed you should expect from the VPS, unless you already know as part of the package you contracted.

Then, you tried wget getting a file from where? The speed will also depends on the setup and speed of the origin from where you tried getting the test file.

If your VPS provider is good, for most connections to the same country (where the datacentre is) you should expect high speeds.

thank you for reply
vps company say "All servers are connected to our network using a 1 gbps connection" 
i do not want download the file at 1gb /s speed
at least 30mb - 40mb /s
when i test "wget"
```
http://ca.releases.ubuntu.com/ubuntu/dists/trusty/Contents-i386.gz
2017-02-16 09:58:40 (2.80 MB/s) - ‘Contents-i386.gz’
```
i get 2mb/s !! file from canada and vps from canada !! 
this not good speed

---

### Post by darkod on 2017-02-16
2.80 MB/s are not the same as 2.80 Mb/s.

B - byte = 8 bits
b - single bit

Your 2.80 MB/s are 2.80*8 Mb/s = almost 24 Mb/s... not so bad

PS. Yes, your provider says all servers are connected by 1Gb/s network and that's fine. But they probably "limit" the speed you can take on a single VPS. Otherwise, imagine how much bandwidth they need if all their VPSs can take up to 1Gb/s real speed towards the internet... :)

---

### Post by mrjk990 on 2017-02-16
> **darkod said:**
> 2.80 MB/s are not the same as 2.80 Mb/s.

B - byte = 8 bits
b - single bit

Your 2.80 MB/s are 2.80*8 Mb/s = almost 24 Mb/s... not so bad

PS. Yes, your provider says all servers are connected by 1Gb/s network and that's fine. But they probably "limit" the speed you can take on a single VPS. Otherwise, imagine how much bandwidth they need if all their VPSs can take up to 1Gb/s real speed towards the internet... :)

thank you darkod :)
my vps company give me unlimited bandwidth :D
i test same file on windows vps in same company and get 21mb /s !!
why in ubuntu just 2mb :(

---

### Post by darkod on 2017-02-16
I already explained it. Looks to me like you are getting 21 Mb/s in windows which is the same as 2.80 MB/s in linux. It only differs how they report the speed.

Post a screenshot image of the windows test. You can attach an image to your post. Be careful which unit it says, because that's the important part.

---

### Post by mrjk990 on 2017-02-16
[ATTACH=CONFIG]273754[/ATTACH]
you can see i get 16mb/s
ubuntu just 2mb/s
also many of website use rapidleech script aanf get 50-100mb/s
thank you for help

---

### Post by lisati on 2017-02-16
Sorry if I come across a tad pedantic, but when discussing internet speeds, the way the speed is written can make a difference to how to interpret the results. Mb/s is not the same thing as MB/s. Your screenshot shows MB/s.

---

### Post by dudumomo on 2017-02-17
I'm a bit lost as well...
On Linux, can you run a speedtest?

```
sudo apt-get install speedtest-cli
```

and run it
```
speedtest-cli
```

Then, for Gigabit VPS, it is always the same thing...
"All servers are connected to our network using a 1 gbps connection" = 1 server with 1G network card and 1G cable to local infra.
If they have 100 servers, so 100G should go through their local network, but may be they are not so well connected and only have 50G for outside connection (I summarize). However, usually this is not the bottleneck.

1st bottleneck, you don't have a server with 1G but a VPS that is on a server with 1G...if there is 10 VPS on the same server, you won't get 1G. And others users might use a lot of bandwidth ("taking yours")
2nd bottleneck, as it is a VPS, the resources of the server is also shared and you may be you are limited by the CPU or I/O disk.
3rd bottleneck, might be the server you are using or way to download, etc...

If you can share the speedtest, this might help.

Another way to further test, could be to download an ISO on a robust server near you, but using some download accelerator (Aria2 for Linux for example)
We use it like this if I remember well:
```
aria2 -x16 https://xxx
```

---

### Post by darkod on 2017-02-17
First, a file of 31MB is too small for any relevant speed comparisons... Then, some windows apps might be saying MB/s when actually referring to Mb/s, it all depends how they designed the app and many people simply do not pay attention to this.

Try downloading the ubuntu desktop 16.04.1 iso on both machines (on windows you can simply click on the link in [http://releases.ubuntu.com]("https://releases.ubuntu.com") and on linux you can use wget). The file is over 1GB and would be good for comparison. Then actually measure the time for each download, don't rely only on the result on screen. That will give you a way to compare the speed since it matters that much to you.

I think it works OK and it's only question how windows and linux report the speed.

PS. I see 16.04.2 has actually been posted in the releases so you can use that for testing. The desktop version is 1.4-1.5GB (64bit/32bit).

---


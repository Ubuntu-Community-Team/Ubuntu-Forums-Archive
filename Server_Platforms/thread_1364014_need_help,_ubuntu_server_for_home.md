---
title: "need help, ubuntu server for home"
date: 2009-12-25
forum: Server Platforms
---

### Post by raidspirit on 2009-12-25
hi there, i'm new in ubuntu so i'm pretty newbie in ubuntu...

i've been searching for solution over a week, but still no progress...here goes,
i have 5 computer at home, i wanted to make 1 of my computer as data server that is by using ubuntu of course, where all 4 computer (windows OS) can connect to the server.
i've download the 8.04LTS and have it install, i try to install desktop GUI for it because all i can see is cmd-like thingy which i dunno how-to, but it cannot connect to internet...i've check the /etc/network/interfaces and there's nothing wrong with the setting...i guess, here's my setting by the way...

auto eth0
iface eth0 inet static
address 192.168.0.128
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

i don't see any problem by it but...what's network and broadcast does?
do i need to delete them?
and again, i'm using D-LINK DIR-300 router, perhaps it was because of the router that i can't connect it to internet?

---

### Post by BkkBonanza on 2009-12-25
Well, the first thing is to check what network settings your router (or other computers) are using. This new machine needs to be on the same network and use the same gateway. So if your router is at 192.168.0.1 and is how you get to the net, then you likely have valis settings. If not, then you need to change the settings.

Most routers are set up to do DHCP. If so, then at first you may want to remove all the lines except the "auto" ones and change static to dhcp for eth0. This should cause your machine to get an ip assigned by the router and is likely to be functional right from the start.

Later you can change back to static or set your router to assign a "static lease" to that machine so that it always gets the same ip. You will want it to be static for server purposes at some point.

---

### Post by Iowan on 2009-12-25
> **raidspirit said:**
> what's network and broadcast does?
do i need to delete them?They/re a bit redundant anymore - not necessarily required, but shouldn't hurt, either. From "cmd-like thingy", check **ifconfig -a** to see if interface has the address (it should). Whilst there, check **ping -c5 192.168.0.1**. If that works, the next step might be to see if */etc/resolv.conf* has valid nameservers. (One advantage to DHCP is that the DHCP server usually provides its clients with DNS addresses).

As mentioned - setting it up for DHCP first will be a simple(r) way to get it going.

---

### Post by CharlesA on 2009-12-25
Check the /etc/resolve.conf file.

Second Iowan in that setting up with DHCP is way easier. All my machines have static IP addresses assigned based on their MAC by DHCP.

---

### Post by Iowan on 2009-12-26
> **CharlesA said:**
> All my machines have static IP addresses assigned based on their MAC by DHCP. I prefer that method, as well (also called a static lease). OP's choice - it does require some additional setup on DHCP server (router?).

---

### Post by garfonzo on 2009-12-26
For what it's worth, my Ubuntu server often looses its internet connection even though all the settings are correct and it has been online for months. Whenever I do a new update, or even sometimes when I do a power cycle, the server can only see the local network, and not the whole inter-tubes. My fix is like so:

```
ifconfig eth0 down
ifconfig eth0 up
```

For whatever reason, the network cards needs to be flipped off, then on to get things back in order. Don't know why.

Not sure if that will help, but it's worth a try.

---

### Post by raidspirit on 2009-12-28
i somehow manage to get my ubuntu online, it seem the problem lies on the router... i need to enable "DCHP server" on my router...although i set my ubuntu to static ip...
and thanks alot guys, hope ya all can help me again if i got any trouble...

---

### Post by msw on 2009-12-28
> **raidspirit said:**
> i somehow manage to get my ubuntu online, it seem the problem lies on the router... i need to enable "DCHP server" on my router...although i set my ubuntu to static ip...
and thanks alot guys, hope ya all can help me again if i got any trouble...

I would surmise the reason you had to set the router to dhcp is caused by your /etc/resolve.conf having the router's DNS settings which are unavailable when DHCP is flagged off. You can put your ISP's DNS IP"s in /etc/resolve.conf or better yet use [OpenDNS]("http://www.google.ca/url?sa=t&source=web&ct=res&cd=1&ved=0CAgQFjAA&url=http%3A%2F%2Fwww.opendns.com%2F&rct=j&q=opendns&ei=tt44S5G7E4yyswPsjODOBA&usg=AFQjCNGZBTf_WvewXCrhQ8oMPd2P82l7lQ"). If after a successful test, you can then disable the DHCP server in the router.

---

### Post by CharlesA on 2009-12-28
> **msw said:**
> I would surmise the reason you had to set the router to dhcp is caused by your /etc/resolve.conf having the router's DNS settings which are unavailable when DHCP is flagged off. You can put your ISP's DNS IP"s in /etc/resolve.conf or better yet use [OpenDNS]("http://www.google.ca/url?sa=t&source=web&ct=res&cd=1&ved=0CAgQFjAA&url=http%3A%2F%2Fwww.opendns.com%2F&rct=j&q=opendns&ei=tt44S5G7E4yyswPsjODOBA&usg=AFQjCNGZBTf_WvewXCrhQ8oMPd2P82l7lQ"). If after a successful test, you can then disable the DHCP server in the router.

This, more then likely.

---

### Post by ReverendKnoxville on 2009-12-30
I think since as you said you are a newbie, reinstall from a live CD or alternate CD. You're going to need GUI tools unless you plan to be a sysadmin and have significant time and patience to devote to becoming a command line guru (don't get me wrong, I LOVE the command line but most IT guys can't work without a GUI these days, which is why all my new IT staff have to go through a hell month consisting of nothing but a bash prompt, trust me you don't want to do that unless it's your job or a passion/hobby of yours).

If you only need to share data then a NAS distro might also suit your needs. If you want authentication then look into ebox, fedora directory server, or miru/ocean.

---

### Post by raidspirit on 2009-12-31
> **msw said:**
> I would surmise the reason you had to set the router to dhcp is caused by your /etc/resolve.conf having the router's DNS settings which are unavailable when DHCP is flagged off. You can put your ISP's DNS IP"s in /etc/resolve.conf or better yet use OpenDNS. If after a successful test, you can then disable the DHCP server in the router.

 ah i see, edited the /etc/resolv.conf and of course i'm using opendns and always been using it, i disabled dhcp server... and it works, thanks alot, i've learn new things in ubuntu.  all about manual work huh...

---


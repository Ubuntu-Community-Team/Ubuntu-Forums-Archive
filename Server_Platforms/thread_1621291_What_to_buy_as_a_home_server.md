---
title: "What to buy as a home server"
date: 2010-11-14
forum: Server Platforms
---

### Post by stefangr1 on 2010-11-14
So I've decided to buy or build a server / NAS.

It's purposes are as follows:
- NAS
- Apache
- Webdavs
- Samba
- NFS
- Time Machine
- PXE-boot server
- DHCP server
- Nameserver
- Router
- Usenet
- Torrents
- Future home automation (with a Velleman USB card).

For hardware, my considerations are the following:
- 2 Gigabit LAN ports: obviously they have to work in Linux,
  one is going to connect to the ADSL modem, the other to a Linksys WRT320N router and AP
- 4 harddisk bays (I'm starting with 3x2TB, but I'd like it to be future proof)
- Very low energy consumption
- Not unnecesarily expensive

So I can do two things: build my own system based on an Atom board (but I can't seem to find the right hardware), or buy a NAS that you can install linux on.

I've been looking at something like the QNAP TS-410 Turbo NAS. But does anyone know whether you can install your own OS on it? Apparently it comes with a custom linux OS, so am I right to assume that all hardware should work in Ubuntu?

What other options do you suggest?

---

### Post by SeijiSensei on 2010-11-14
I priced a Dell T310 with 3x2TB; it comes in around $2,300.

You do realize that you'll never need Gigabit ethernet to connect to the Internet anytime in the next decade (or two) especially if you live in the US.

In a home setting, you could probably run all those services on an old P4 box without it breaking a sweat.

---

### Post by stefangr1 on 2010-11-14
> **SeijiSensei said:**
> I priced a Dell T310 with 3x2TB; it comes in around $2,300.

You do realize that you'll never need Gigabit ethernet to connect to the Internet anytime in the next decade (or two) especially if you live in the US.

In a home setting, you could probably run all those services on an old P4 box without it breaking a sweat.

Do you realize how much energy an old P4 box consumes? This could easily be 70W, adding 150 euros per year to my energy bill. I don't have an old computer, and buying a cheap one is probably suboptimal for several reasons: no Gigabit lan, not enough SATA ports on an old IO-board, not enough hdd-brackets + sata power cables in the system.

I need the Gigabit LAN for the internal network, I agree that it doesn't matter for the link with the ADSL modem.

An Atom board + 2GB RAM + extra 2TB disk + NIC are less than 200 euro's. I can't figure out what case to buy though. What I really like is the Chenbro ES34069. It has 4 hot swappable bays, and it has a very efficient PSU. But it costs 200 euros, which seems a bit expensive. On the other hand, normal cases usually have inefficient PSU's, and they're either very big (I'd prefer a small case), or have only a few hdd-bays. So I'm wondering whether anyone knows a good case...

As the hardware is going to cost me 250 (cheap case) to 400 euros, I was thinking about buying a dedicated solution. The QNAP NAS costs 320 euros (getting me also at 400 euros with additional 2GB hdd), it has 2 Gigabit NIC's, 256mb of RAM and a 800Mhz Marvell CPU. So I was hoping to get some opinions on whether it's a good idea to buy something like this and put Ubuntu server on it...

---

### Post by SeijiSensei on 2010-11-14
> **stefangr1 said:**
> Do you realize how much energy an old P4 box consumes? This could easily be 70W, adding 150 euros per year to my energy bill.

Living here in the profligate US, it would be a lot cheaper.  I just checked my residential electric rates: At just under 8 cents/kWh, running 70W full-time for a year would cost me less than $50. 

One reason I made this suggestion is that I often see postings from people who believe, wrongly, that servers require much more horsepower than do desktops.  I've run Linux servers for years that do more or less everything on your list.  The earliest ones I built ran on 386 platforms; the last batch I built were running on Celerons.  

For servers, it's memory and hard drives that matter most.  Even a pretty wimpy box by modern desktop standards makes a fine server for the tasks you list.

---

### Post by stefangr1 on 2010-11-14
> **SeijiSensei said:**
> Living here in the profligate US, it would be a lot cheaper.  I just checked my residential electric rates: At just under 8 cents/kWh, running 70W full-time for a year would cost me less than $50. 

Yeah, we have energy taxes that are ridiculously high, electricity actually costs US$0.28 per kWh here :(, and I'll probably keep it for about 4 years, so It'll pay off to keep energy consumption in mind.

---

### Post by WinstonChurchill on 2010-11-14
> **stefangr1 said:**
> Yeah, we have energy taxes that are ridiculously high, electricity actually costs US$0.28 per kWh here :(, and I'll probably keep it for about 4 years, so It'll pay off to keep energy consumption in mind.
I've run just as many if not more (Add TOR and Freenet routing a ton of traffic) services as you want on an ancient 2Ghz P4 with 2GB of RAM and a stone age 9GB IDE HDD - you do NOT need nearly as much computing power as you're considering buying...

If you're really concerned about energy, use a cheap laptop with some sort of external hard drive setup (with eSATA, it could be very fast). You also get the added bonus of a built-in UPS.

For example, this could easily handle what you want: (In fact, you could go cheaper if you wanted)
[COLOR=RoyalBlue][http://www.newegg.com/Product/Product.aspx?Item=N82E16834115854](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115854)[/COLOR]

There are several USB-Gigabit adapters that work with Linux - obviously, you're limited by the USB bandwidth (480mbps), but, as SeijiSensei observes, it will be a very long time before your internet connection will be better than 480mbps. Put the USB ethernet on the internet side, hook up the onboard gigabit to your LAN, and you'll be in business. Plus, you have the added bonus of being able to set up a wireless network using hostapd and the laptop's integrated card. (Acer's hardware is usually supported, I think...)

If your server is indeed going to be acting as your router, just use your Linksys as the AP (if you don't go with the laptop solution), and get a gigabit switch for your wired LAN - very good 8-port ones run for ~$40.

**EDIT: **Apologies for the USD prices - I don't have any idea what the current euro conversion is...

---

### Post by volkswagner on 2010-11-14
I would sure be looking at an Intel Atom based board.  For power savings and quiet operation.  I did some basic comparisons of my Intel Atom 330 machine with one 3.5" HD vs. a few old Pentium 4 socket 478... Results showed nearly 100watts at idle for the P4 and 40 Watts for the 330.  The Atom based boards not running the Intel 945Video see even a lower power consumption.  I believe the GPU uses more power than the CPU!

May I ask why would you put the server before the Router?  Most folks would argue it is an unnecessary security risk to have your file server act as the firewall appliance.

New hardware such as [this D525]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128452") based board gets you in the game at a nice price for current hardware with DDR3 and 4 SATA Ports.  I would probably throw this in a micro atx case for added cooling running large slow moving fans.

I did a quick search on Newegg for Atom Server and [here]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=atom+server&x=0&y=0") is what comes up... Some interesting choices.  The [Sans Digital]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816111134&cm_re=atom_server-_-16-111-134-_-Product") is a little pricey for my liking but has a nice platform and Two Giga LAN ports. 

All the reviewers on [this board]("http://www.newegg.com/Product/Product.aspx?Item=13-182-205&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux#scrollFullInfo") were running Linux, none specific to Ubuntu/Debian but I think It is a great contender for your wish list.

---

### Post by stefangr1 on 2010-11-14
> **volkswagner said:**
> 
May I ask why would you put the server before the Router?  Most folks would argue it is an unnecessary security risk to have your file server act as the firewall appliance.

The only service that needs dual NICs is iptables, which I'll use mostly for prioritizing traffic. To my knowledge, this can be only done on a system with 2 NICS... The server will be between the ADSL modem (which acts as a firewall to the outside), and the WRT320N router and AP. I'll configure the WRT320N as a router (firewall off, dhcp off, etc.).

>  All the reviewers on [this board]("http://www.newegg.com/Product/Product.aspx?Item=13-182-205&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=linux#scrollFullInfo") were running Linux, none specific to Ubuntu/Debian but I think It is a great contender for your wish list.

An Atom board will definately run Linux. The only "danger" is that some NICS may not work at speeds above 100Mbit (no Gbit LAN). 

My question was about some dedicated NAS solutions that are on the market. They usually use some sort of trimmed down linux, and are very energy efficient. But I don't know if you can install your own OS on them. The system I was referring to earlier had 256mb of ram and a 800Mhz Marvell processor (I think thats what they also use in some smartphones). Synology has also some solutions, with uncommon CPU's. The reason why I'd like to run my own OS is that I want to be able to use some software that is not provided with the customized OS provided with these NAS boxes.

---

### Post by bitscarre on 2010-11-15
What about this baby right here: 

```
http://www.qnap.com/pro_detail_feature.asp?p_id=163
```

---

### Post by stefangr1 on 2010-11-15
> **bitscarre said:**
> What about this baby right here: 

```
http://www.qnap.com/pro_detail_feature.asp?p_id=163
```

I just read [this](http://www.qnap.com/PressRelease_detail.asp?pr_id=121) information about the QNAP hardware. It says that all their systems support Debian. I suppoze this means that Ubuntu would also work. So I find [this one](http://azerty.nl/8-1972-238550/qnap-ts-410-turbo-nas-nas-.html) quite an attractive option, it costs 320 euro.

However, getting back to the "you do NOT need nearly as much computing power as you're considering buying" argument of WinstonChurchill: I'm not quite convinced yet. Is 256mb RAM and a 800Mhz Marvell CPU really enough for the tasks I'm considering? The most CPU intensive task will be extracting RAR archives downloaded from usenet (which may be >10GB).

---

### Post by stefangr1 on 2010-11-16
So does anyone know whether a 800Mhz Marvell CPU and 256MB of ram are sufficient to run an Ubuntu home server?

---

### Post by SeijiSensei on 2010-11-17
Yes, though you might be happier with twice the memory.  I have a server sitting in the back room of my house running CentOS 5.5 in 256M.  It's runs a mail server, file service via NFS and Samba, and a mailing list manager.  I've also hosted a web site or two on it before I bought myself a virtual server a linode.com.  It's a 2.8GHz P4, though.  It would bog down running MailScanner if there was a lot of mail traffic through it, though mail scanning is a pretty intensive task. I think doubling its memory would solve that problem, but I'm no longer scanning mail locally.

---

### Post by CharlesA on 2010-11-17
> **SeijiSensei said:**
> Yes, though you might be happier with twice the memory.  I have a server sitting in the back room of my house running CentOS 5.5 in 256M.  It's runs a mail server, file service via NFS and Samba, and a mailing list manager.  I've also hosted a web site or two on it before I bought myself a virtual server a linode.com.  It's a 2.8GHz P4, though.  It would bog down running MailScanner if there was a lot of mail traffic through it, though mail scanning is a pretty intensive task. I think doubling its memory would solve that problem, but I'm no longer scanning mail locally.

+1 for that.

Granted I haven't actually ran a "bare metal" install of Ubuntu on a machine with only 256MB of RAM, my main server at home uses around 400 MB of RAM with everything running except virtual machines.

A clean install on a VM (non virtual kernel) uses around 40MB of RAM.

The newer atom boards have gigabit ethernet with a PCI expansion slot, so that might be an idea if you want a super low power box.

---


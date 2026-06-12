---
title: "Good dual band Wireless 'N' routers?"
date: 2011-06-29
forum: The Cafe
---

### Post by catlover2 on 2011-06-29
Hello, I am looking at a few wireless routers, 
[Linksys E3000]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124388&cm_re=e3000-_-33-124-388-_-Product")
[BUFFALO WZR-HP-AG300H]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833162047")
[D-link DIR 825]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127258")
If anyone has any comments on these routers, of suggestion of others, please let me know.

I like the looks of the DIR-825 because of the possibility of an antenna upgrade.
I will only consider routers that are compatible with dd-wrt.
Thanks, catlover:)

---

### Post by KiwiNZ on 2011-06-29
I cannot speak about the Buffalo or the D-Link but I have just recently experienced the LinkSYS  E3000 and it was terrible. I purchased it new had it for two weeks and smashed it with a hammer.

In that fortnight I had more dropouts disconnects........... than any other time networking.If you google just about any LinkSYS model and you will find similar experiences.

After that two weeks I took the router outside and smashed it with a hammer.

I purchased an Apple Airport Extreme and have had a rock solid network and internet since.

---

### Post by haqking on 2011-06-29
> **catlover2 said:**
> Hello, I am looking at a few wireless routers, 
[Linksys E3000]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124388&cm_re=e3000-_-33-124-388-_-Product")
[BUFFALO WZR-HP-AG300H]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833162047")
[D-link DIR 825]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127258")
If anyone has any comments on these routers, of suggestion of others, please let me know.

I like the looks of the DIR-825 because of the possibility of an antenna upgrade.
I will only consider routers that are compatible with dd-wrt.
Thanks, catlover:)

I recently upgraded a D-Link DIR 825 which had failed twice with replacements brought in for a friends small business.
I replaced it with the Netgear DGND3700 and is a great bit of kit IMO.

I use  NG DGDN3300 at home and that 2 is great, very configurable and wireless strength etc is very good.

---

### Post by catlover2 on 2011-06-29
I'll have a look at the Netgear one, I'm assuming that you mean [Netgear WN[COLOR=Red]_**D**_[COLOR=Black]R3700](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122326)

[/COLOR][/COLOR]

---

### Post by haqking on 2011-06-29
> **catlover2 said:**
> I'll have a look at the Netgear one, I'm assuming that you mean [Netgear WN[COLOR=Red]_**D**_[COLOR=Black]R3700[/COLOR][/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833122326")[COLOR=Red][COLOR=Black]

[/COLOR][/COLOR]

yeah i had edited my post actually i think at same time.  I meant the DGND3700.

but anything in that range i have always had good experience with for home/small business nothing much above that of course

---

### Post by ratcheer on 2011-06-29
I am using a Netgear WNDR3300. I would not consider it a "good" dual band router. It is my understanding that it can only actually use one band at a time, so that is not really dual band, is it? With dd-wrt, it is using 96% of its memory. It does not have ip6tables (but, that is a shortcoming of dd-wrt).

On the good side, it works and it is stable. Just feature bare.

I want an Apple AirPort Extreme.

Tim

---

### Post by haqking on 2011-06-29
> **ratcheer said:**
> I am using a Netgear WNDR3300. I would not consider it a "good" dual band router. It is my understanding that it can only actually use one band at a time, so that is not really dual band, is it? With dd-wrt, it is using 96% of its memory. It does not have ip6tables (but, that is a shortcoming of dd-wrt).

On the good side, it works and it is stable. Just feature bare.

I want an Apple AirPort Extreme.

Tim

My Netgear DGDN3300 is dual band and both work at same time no problem i think the next onme up from yours the WNDR3400 supports simultaneous

actually come to think of it my buddy round the corner runs a WNDR3300 and he is simultaneous ? mmmmm

---

### Post by wizard10000 on 2011-06-29
I had a couple of Buffalo dd-wrt dual band routers and eventually relegated both of them to wireless bridge duty as they were just terrible.  I've been using these -

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320038](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320038)

for the past few months and have been very happy with them.  I put dd-wrt on both of them, use one as master and one as a WDS node and they work flawlessly.  Highly recommended.

edit:

```
wizard@wizard-netbook:~$ ssh root@192.168.1.1
DD-WRT v24-sp2 big (c) 2010 NewMedia-NET GmbH
Release: 12/24/10 (SVN revision: 15962)
root@192.168.1.1's password: 
==========================================================
 
 ____  ___    __        ______ _____         ____  _  _ 
 | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | 
 || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ 
 ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| 
 |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| 
 
                       DD-WRT v24-sp2
                   http://www.dd-wrt.com
 
==========================================================


BusyBox v1.13.4 (2010-12-24 03:02:49 CET) built-in shell (ash)
Enter 'help' for a list of built-in commands.

root@DD-WRT:~# free
              total         used         free       shared      buffers
  Mem:       124628        12796       111832            0         1340
 Swap:            0            0            0
Total:       124628        12796       111832
root@DD-WRT:~# top

Mem: 12916K used, 111712K free, 0K shrd, 1340K buff, 3732K cached
CPU:  0.3% usr  0.1% sys  0.0% nic 99.2% idle  0.0% io  0.0% irq  0.1% sirq
Load average: 0.00 0.00 0.00 2/25 6931

```

---

### Post by ratcheer on 2011-06-30
> **haqking said:**
> My Netgear DGDN3300 is dual band and both work at same time no problem i think the next onme up from yours the WNDR3400 supports simultaneous

actually come to think of it my buddy round the corner runs a WNDR3300 and he is simultaneous ? mmmmm

Reviews I have read of this product say that the inability to use both bands simultaneously is its major shortcoming. E.g.,

[http://reviews.cnet.com/routers/netgear-rangemax-dual-band/4505-3319_7-32863752.html](http://reviews.cnet.com/routers/netgear-rangemax-dual-band/4505-3319_7-32863752.html)


Tim

---

### Post by haqking on 2011-06-30
> **ratcheer said:**
> Reviews I have read of this product say that the inability to use both bands simultaneously is its major shortcoming. E.g.,

[http://reviews.cnet.com/routers/netgear-rangemax-dual-band/4505-3319_7-32863752.html](http://reviews.cnet.com/routers/netgear-rangemax-dual-band/4505-3319_7-32863752.html)


Tim

ahh ok he probably has a diff version then.

My DGDN3300 is definately dual as i am using them both right now.  Also i have read many reviews about my one not having dual band, that it wont hide the SSID and signal is weak.

I am guessing they dont know what they are doing or a different firmware (which is easy to update ;-)

I would buy another one at twice the price...(well maybe ;-)

---

### Post by drmrgd on 2011-06-30
I have that Netgear WNDR3700 (not the 3300) router and I love it!  It's super stable and handles traffic quite well for a much larger range than I would have expected (I can still get a decent enough WiFi signal on my iPhone way out at the end of my 0.25 acre yard).  I stream Netflix wirelessly over it in HD (when Netflix isn't acting up that is!), and have had no problems.  I'd definitely recommend that one over the lot that you listed.

---

### Post by Lucradia on 2011-06-30
I had a WRT54G, it was epic. But newer linksys routers often would disconnect from the modem, off and on. I won't trust them.

---


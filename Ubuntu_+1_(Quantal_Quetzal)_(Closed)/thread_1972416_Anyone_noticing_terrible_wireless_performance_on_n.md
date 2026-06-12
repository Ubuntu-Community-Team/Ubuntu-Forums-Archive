---
title: "Anyone noticing terrible wireless performance on new 3.4 kernel"
date: 2012-05-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by vikrant82 on 2012-05-03
Just checking if someone is noticing wireless issues with iwlwifi on latest kernel 3.4 in quantal repos.

I have filed a bug on the same. For more details see - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994104")

---

### Post by 3vi1 on 2012-05-03
> **vikrant82 said:**
> Just checking if someone is noticing wireless issues with iwlwifi on latest kernel 3.4 in quantal repos.

I have filed a bug on the same. For more details see - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994104")

I've not seen any notable change, but I've only used wifi under 3.4 on one machine (a CR-48 ).  So, I'm using a different chipset than you are.

---

### Post by Starks on 2012-05-04
I've linked the upstream bug on the report.

---

### Post by Dlambert on 2012-05-04
I have not as well.

---

### Post by VinDSL on 2012-05-05
The only "terrible performance" I've noticed is when doing apt updates & upgrades, but I think this is due to the Ubu servers being overloaded with excessive traffic.

I've been experiencing 56K dialup speeds, on my 7MB ADSL2+ connection.  LoL!  :D

Everything else is normal...

---

### Post by ronacc on 2012-05-11
I just did a comparison between my updated ( to quantal at repo open )fresh install of precise and a fresh install of quantal from the daily live .the updated precise is almost twice as fast as the daily live install .

note: the updated precise also has the 3.4 kernel . maybe a config glitch with the daily live .

---

### Post by Starks on 2012-05-11
If you have a newish Intel wireless card, try modprobing with 11n_disable=1

N speed rate control for anything released in the past few years is garbage.

---

### Post by ronacc on 2012-06-09
whatever was trashing wireless on the livecd's is now affecting my updated from precise quantal , direct test dowmloading debian sid  with quantal then with suse 11  same box , same source , same router within minutes of each other  , suse yielded more than 3 times the download speed , tests with mangy moose on a different box show the same 3x faster than quantal .

---

### Post by fjgaude on 2012-06-09
I'm getting 6Mb/s on my 802.11b/n link with Dell mini-10, the usual speed when the net is not overloaded. Nothing different from 12.04.

---

### Post by TurbofanDude on 2012-06-10
I have noticed improved performance in 12.04 versus 11.10, but I don't think I've tried the 3.4 kernels on my laptop yet. I did notice  that when I wasn't plugged in, my speeds dropped horrendously.

---

### Post by jerrylamos on 2012-06-10
> **VinDSL said:**
> The only "terrible performance" I've noticed is when doing apt updates & upgrades, but I think this is due to the Ubu servers being overloaded with excessive traffic.
We've got 1.5 MB DSL service here, at a good price (we're retired), so 180 kb/s is max we get wired or wireless.  For me usable for internet videos example BBC news etc.

quantal update/upgrade erratically will sometimes reach 180 typically a fraction of that.  Judging from the forum (in)activity there aren't that many people using quantal.  I have no clue on the makeup of ubuntu servers.

? haven't seen much quantal activity anyway, and testing quantal kernel on precise don't notice much difference between quantal and precise for what I do.

Famous last words, "let the breakage begin..."

Actually, Quantal Quetzal is busted big time on my wide screen notebook with external monitor (bug written, straces, backtraces, etc) stuck on 1024x768 no matter what.  The wide screen should be 1366x768 (I think that's right) and the external 1280x1024.

Does run O.K. on my 1440x900 tower and this 1024x600 netbook.

Jerry

---

### Post by ronacc on 2012-06-10
i'm not sure its the 3.4 kernel , it started for me with some update many days after I had installed the 3.4 kernel on my updated to quantal precise install but affected the dailys from the start .

---

### Post by kaldor on 2012-06-10
Gave it a try on a live session. Everything seems fine out of the box. No difference from 12.04.

```
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
```

---

### Post by ronacc on 2012-06-10
I have tried almost every live cd since the first , same result as far as wireless goes , only difference I've seen is all the early ones found my network and made it available by rt clicking in the notifier , the for a couple last week I had to manually enter my ssid to get it made available , now its back to finding it on its own . dosen't matter still runs at about 1/3 the speed it ought to .

---


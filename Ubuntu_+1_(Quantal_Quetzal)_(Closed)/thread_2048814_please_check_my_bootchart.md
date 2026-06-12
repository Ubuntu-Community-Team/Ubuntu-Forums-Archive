---
title: "please check my bootchart"
date: 2012-08-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by drou on 2012-08-27
I need almost 2 minutes to login to my desktop. it's disappointing when i read everywhere about quantal's bootup times.
Any help speeding things up is much appreciated. Here is what bootchart created

[Click ME]("https://www.dropbox.com/s/in917pm5kdmix7p/drou-quantal-20120827-2.png")

PS. Don't try to see it inside dropbox. It has a Download button at the upper right corner

---

### Post by terry_gardener on 2012-08-28
That seems a long time. 

do you get the same when booting into unity. 

or just gnome shell

---

### Post by effenberg0x0 on 2012-08-28
> **drou said:**
> I need almost 2 minutes to login to my desktop. it's disappointing when i read everywhere about quantal's bootup times.
Any help speeding things up is much appreciated. Here is what bootchart created

[Click ME]("https://www.dropbox.com/s/in917pm5kdmix7p/drou-quantal-20120827-2.png")

PS. Don't try to see it inside dropbox. It has a Download button at the upper right corner

Hi, my desktop is booting up-to-date QQ in exactly 30s. Here are the specs:
**- MB:** ASUS M4A89GTD Pro USB3
**- CPU:** AMD Phenom II X6 1100T BE @ 3.8/4.0GHz (4GHz only on the turbo-something thing*). The six cores are manually enabled in BIOS.
**- HDD:** Corsair Force 3 SATA 3.0 90GB SSD (/dev/sda), WD Caviar Black SATA 3.0 1TB HDD (WD1002FAEX-00Y9A0).
**- RAM:** Corsair 4 x 4GB 1.333@1400MHz
[COLOR="Silver"][SIZE="2"](*) Which should kick in eventually and does not, despite what AMD Kernel people have already explained to me, I have never seen it happen.

[/SIZE][/COLOR]Here's the bootchart:
[ATTACH]223294[/ATTACH]

- I have removed network-manager, modem-manager, dnsmasq because they're of no use to me. I was not thinking of boot time when I removed then, but network-manager and modem-manager have been related to long boot times in the 2 previous development cycles.

- I did nothing to manually change or optimize the boot process, except for the above info it should be default unless I'm forgetting something. Maybe by comparing your bootchart to mine you can see what is taking long to load.

I don't boot too often and expected it to be up in 20-25s. With a little tweaking I believe there's room for improvement here...

Regards,
Effenberg

---

### Post by fjgaude on 2012-08-28
Boot time, depends on many things, like CPU and memory speed, BIOS and if it is UEFI, and the boot drive.

I get boot and resume times of five (5) seconds on my main box:

MB ASRock 68M-ITX/HT, Z68 chip set
CPU Intel i5-2405S, quad core, 1.6-3.6MHz
RAM 8GB at 2133MHz
SSD Plextor 128MHz

```
frank@cutie:~$ sudo **hdparm** -tT /dev/sda
/dev/sda:
 Timing cached reads:   22464 MB in  2.00 seconds = 11244.69 MB/sec
 Timing buffered disk reads: 1258 MB in  3.00 seconds = 419.30 MB/sec
```

The **gtkperf** for 12.04 is 4.56; for 12.10, 2.76 presently.

I do believe the UEFI BIOS cuts over five seconds from the boot.

---

### Post by effenberg0x0 on 2012-08-28
> **fjgaude said:**
> Boot time, depends on many things, like CPU and memory speed, BIOS and if it is UEFI, and the boot drive.

I get boot and resume times of five (5) seconds on my main box:

MB ASRock 68M-ITX/HT, Z68 chip set
CPU Intel i5-2405S, quad core, 1.6-3.6MHz
RAM 8GB at 2133MHz
SSD Plextor 128MHz

```
frank@cutie:~$ sudo **hdparm** -tT /dev/sda
/dev/sda:
 Timing cached reads:   22464 MB in  2.00 seconds = 11244.69 MB/sec
 Timing buffered disk reads: 1258 MB in  3.00 seconds = 419.30 MB/sec
```

The **gtkperf** for 12.04 is 4.56; for 12.10, 2.76 presently.

I do believe the UEFI BIOS cuts over five seconds from the boot.

Hi fjgaude, 

<OT>
I'm curious about your hdparm -T results. Here are mine for the specs I mentioned in a post above:
```

[14:01:40] ahsl@AL-DESK01:[~/downloads]: sudo hdparm -tT /dev/sda
[sudo] password for ahsl: 

/dev/sda:
 Timing cached reads:   6788 MB in  2.00 seconds = 3394.81 MB/sec
 Timing buffered disk reads: 1060 MB in  3.00 seconds = 352.89 MB/sec

```

Your cached reads are 3 times+ greater than mine. Are you, by any chance, running SSD in some RAID level? What SSD is that?
</OT>

I agree with you about UEFI. My laptop boots in about 10 seconds or so. Still a 5s boot is impressive for me, I don't think I ever had it in any hardware. Feel free to share some tips :)

Regards,
Effenberg

---

### Post by fjgaude on 2012-08-28
The boot SSD is made by **Plextor** PX128M3 with its **Marvell** controller the way to go; and even OCZ recognizes that now. I have an old Corsair Force3 like you but its write speed has gone way down since new, even with **discard** and using **fstrim** not helping much. No **RAID** here!

You remember Plextor, they built the best floppy drives in those days.

---

### Post by effenberg0x0 on 2012-08-28
> **fjgaude said:**
> The boot SSD is made by **Plextor** PX128M3 with its **Marvell** controller the way to go; and even OCZ recognizes that now. I have an old Corsair 3 like you but its write speed has gone way done since new, even with **discard** and using **fstrim** not helping much. No RAID here!

You remember Plextor, they built the best floppy drives in those days.

I do remember, I was not aware we had Plextor in SSD.

I gotta look into this. To tell you the truth, I have wasted a lot of time making this thing OC stable and cool and completely forgot about the SSD speed. I was looking at this Corsair specs (Force 3, which is Sata 3.0 6.0Gbps, thus supposed to be fast) and I think it's completely off the expected speeds... I found some benchmarks (like [this]("http://www.anandtech.com/show/2973/6gbps-sata-performance-amd-890gx-vs-intel-x58-p55")), I think SB850/AMD890GX is not a good performer.

Regards,
Effenberg

---

### Post by fjgaude on 2012-08-28
> **effenberg0x0 said:**
> I do remember, I was not aware we had Plextor in SSD.

I gotta look into this. To tell you the truth, I have wasted a lot of time making this thing OC stable and cool and completely forgot about the SSD speed. I was looking at this Corsair specs (Force 3, which is Sata 3.0 6.0Gbps, thus supposed to be fast) and I think it's completely off the expected speeds... I found some benchmarks (like [this]("http://www.anandtech.com/show/2973/6gbps-sata-performance-amd-890gx-vs-intel-x58-p55")), I think SB850/AMD890GX is not a good performer.

Regards,
Effenberg

I'm not overclocking at all, very low power box, using only HD3000 integated graphics. Using my Force 3 SSD I get this:

```
frank@cutie:~$ sudo hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   20776 MB in  2.00 seconds = 10399.05 MB/sec
 Timing buffered disk reads: 700 MB in  3.00 seconds = 233.12 MB/sec
```

Also look at my RAM clocking! My fans run slowly at just about a level you can't hear any noise from my little box, mini-ITX, setting on desktop, actually. <smile>

---


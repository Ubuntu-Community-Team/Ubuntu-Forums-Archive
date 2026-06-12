---
title: "How to perform a thorough scan using ClamTK?"
date: 2008-11-18
forum: Security
---

### Post by indiapavan on 2008-11-18
Hi. I used clamTK to scan windows files and folders. But the subfolders are being excluded in each scan. How can I scan an entire Windows partition and all the files and sub-folders present in it?

---

### Post by cariboo on 2008-11-19
I not sure how to do it using the gui, but from the command line:

```
sudo clamscan -r /dir to be scanned
```

Check:

```
man clamscan
```

For more info.

Jim

---

### Post by indiapavan on 2008-11-20
> **cariboo907 said:**
> I not sure how to do it using the gui, but from the command line:

```
sudo clamscan -r /dir to be scanned
```

Check:

```
man clamscan
```

For more info.

Jim

That helped. But the thing is, it still is not detecting Windows viruses. I know some of the .exe files are infected. But it is still not detecting it. Does it detect only Linux based viruses?

---

### Post by cariboo on 2008-11-20
You have to have your windows partition mounted in order to scan it. Clamav will scan for goth Linux and Windows viruses.

Jim

---

### Post by dvdcupgo339 on 2008-11-22
[font=Arial][size=10pt][font=Times New Roman][size=3][/size][/font][font=Times New Roman][size=3]**where can i[[color=#0000ff] buy cheap videos or dvds Online[/color]](http://www.dvdcup.com/catalog_15.html) **[/size][/font][size=3][font=Times New Roman]In other words, the following sources can help you buy DVDs at a time, and often pay less than even the wholesale price.[/font][/size][/size][/font][font=Times New Roman][size=3][/size][/font][font=Times New Roman][size=3][/size][/font][size=3][font=Times New Roman]DVD #1[/font][/size][font=Times New Roman][size=3][/size][/font][size=3][font=Times New Roman][color=#800080]eBay.com[/color] [/font][/size][font=Verdana][size=9pt]An obvious choice, but definitely the place where you can always score some really great deals on both new and used movies.[/size][/font][size=3][font=Times New Roman]While it might not simple to return a DVD bought on eBay, you can verify the condition and get a good feeling about the seller by checking out his feedback.[/font][/size][font=Times New Roman][size=3][/size][/font][size=3][font=Times New Roman]DVD #2[/font][/size][font=Times New Roman][size=3][/size][/font][size=3][font=Times New Roman][color=#0000ff]Amazon.com[/color][/font][/size][font=Verdana][size=9pt]One of the most popular places to buy DVDs online, of course, but there are often many bargains to be found here &#8212; sales, discounts, etc.[/size][/font][size=3][font=Times New Roman][/font][/size][size=3][font=Times New Roman]DVD #3[/font][/size][size=3][font=Times New Roman][/font][/size][size=3][font=Times New Roman][[color=#0000ff]dvdstrom.com[/color]](http://www.dvdstrom.com/)[/font][/size][font=Verdana][size=9pt][color=#0000ff][/color][/size][/font][font=Verdana][size=9pt]The DVD section of this complete online store  is top-quality,[/size][/font][size=3][font=Times New Roman][/font][/size][size=3][font=Times New Roman]DVD #4[/font][/size][font=Times New Roman][size=3][/size][/font][size=3][font=Times New Roman][[color=#800080]dvdcup.com[/color]](http://www.dvdcup.com/)[/font][/size][font=Times New Roman][size=3][/size][/font][font=Times New Roman][size=3]A good website to shop for the latest and popular DVDs online, free shipping,[/size][/font][size=3][font=Times New Roman]good quality,pay less than even the wholesale price, you can find all DVDs you need, [[color=#800080]dvd wholesaler and dropshipper[/color]](http://www.dvdcup.com/)[/font][/size]

---

### Post by erwall on 2008-11-23
> **indiapavan said:**
> That helped. But the thing is, it still is not detecting Windows viruses. I know some of the .exe files are infected. But it is still not detecting it. Does it detect only Linux based viruses?
Have you updated the virus database?  Through the gui, you can do Help --> Update Signatures or freshclam -v in the command line.  Then File --> Recursive Scan or the command line someone mentioned earlier.  It will definitely find windows viruses, I've done so several times.

---


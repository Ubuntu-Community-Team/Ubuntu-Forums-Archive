---
title: "how old can the hardware be inorder to run ubuntu server"
date: 2010-03-05
forum: Server Platforms
---

### Post by 411hacker on 2010-03-05
I would like to build a home server from some old computer parts that I  have had laying around for about a year. I would like to use Ubuntu  server for it but i don't know if my system can handle it. this is what i  have.

[LIST]
[*]pentium III 450MHz processor
[*]384MB's of RAM
[*]32MB graphics card
[*]20GB boot drive
[/LIST]
Heres what I will be adding later 

[LIST]
[*]PCI RAID card [http://www.newegg.com/Product/ProductReview.aspx?Item=15-124-022&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux](http://www.newegg.com/Product/ProductReview.aspx?Item=15-124-022&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux)
[*]x2 500GB hard drives running on mirror RAID [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073)
[/LIST]
Also what websites have the best guides for setting up ubuntu server as a home server?

---

### Post by DasEi on 2010-03-05
that will work for a server, you might consider using the minimal installer and only install what you need, maybe use icewm or another thinner windowmanager, though gnome will run, too

---

### Post by 411hacker on 2010-03-05
ok that sounds good thanks. do you know of any online guides that i can follow for setting up the server?

---

### Post by DasEi on 2010-03-05
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

for a server also check dyndns (google) or another service, there are few free ones, so server can be found by domain rather then ip, unless you have a static ip.

the following link I just googled, got to look yourself if that's usefull, haven't tested it :

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

---

### Post by NullHead on 2010-03-05
You can use this command to help you install the services you need```
sudo tasksel
```

You'll be greeted with a CLI GUI (ncurses) with checkboxes and what not. It will help you configure the packages you need. If you want a web server, select the LAMP option, and you'll get Apache (web server), mysql and php scripting language support.

---

### Post by Iowan on 2010-03-05
[http://howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") has several "perfect server" articles - sometimes a bit more that necessary for basic server. [Here]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is another (somewhat dated) guide.

---

### Post by cdenley on 2010-03-05
> **DasEi said:**
> that will work for a server, you might consider using the minimal installer and only install what you need, maybe use icewm or another thinner windowmanager, though gnome will run, too

A GUI doesn't belong on a server, and isn't installed on the "server edition" by default.

---


---
title: "Selecting a mother board"
date: 2006-06-25
forum: Server Platforms
---

### Post by rtcary on 2006-06-25
Though I have a couple of Linux servers running in my home office, I do not qualify as a Linux guru; I just know enough to get my FTP, HTTP, PHP, Interbase and MySQL up and running.  Once running, I forget about it (the main reason I love Linux) other than backups.

One of my servers is using an ABIT BE7 board with bios RAID and the new kernels are not compatible with it, so I need to replace the mother board before installing Linux.  Granted, asking for a mother board is like asking for a wine recommendation (I live in the wine country :-) ), however here are my broad requirements:

* Performance is not an issue (DSL WAN).
* Like to stay main stream with a processor (e.g. Intel P4).
* Will use software RAID to maintain a mirror of the data.
* Reliabily is important (put it online and forget).

Suggestions welcomed....

Todd

---

### Post by mips on 2006-06-25
If you are only interested in P4 and not AMD then maybe consider a genuine Intel board.

---

### Post by rtcary on 2006-06-25
[QUOTE=mips]If you are only interested in P4 and not AMD then maybe consider a genuine Intel board.[/QUOTE]

The only reason I specified an Itel board is because I have been "branded"!  That is, I started out with an Intel MDS 800 system in 1973 that used an 8080, but I am open to any CPU that has a good record.  One of the philosophies that seems to give a godd return for the dollar is use use what was the state of the art a year or two ago.

When I look at the list of Intel (or ASUS or ABIT) mother boards, I am over whelmed since I do not know what to look for.  Any suggestions are encouraged...

Todd

---

### Post by mips on 2006-06-25
AMD will give you more bang for buck and run cooler. Maybe have a look at the hardware compatibility list.

What type of server is this, mission critical stuff ?

What is your budget ? What do you need to buy out of this budget (MB,CPU,RAM etc)  ?

---

### Post by rtcary on 2006-06-25
[QUOTE=mips]AMD will give you more bang for buck and run cooler. Maybe have a look at the hardware compatibility list.

What type of server is this, mission critical stuff ?

What is your budget ? What do you need to buy out of this budget (MB,CPU,RAM etc)  ?[/QUOTE]

<<< Maybe have a look at the hardware compatibility list. >>> Do you have a suggestion for a good list?

The budget is not important and as described in previous messages, the server's main use is working as an FTP site so my clients can download updates to their software applications and to display local community photos so the newspaper can select the ones they want to run.  I keep a backup server ready that is kept in sync with rsync, so I just want a reliable work horse; not a Ferrari.

Todd

---

### Post by mips on 2006-06-25
[http://doc.gwos.org/index.php/Mainboard](http://doc.gwos.org/index.php/Mainboard)
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)

These are desktop boards and have a lot of stuff you would not need for a server. Then again server boards are usually more expensive.

I personally have a gigabyte board with zero hassles, others are happy with asus. I suspect a server board from the major players should be ok.

Alternative look at a few boards that interest you and come back with a shortlist and we'll provide input.

[http://shop.amd.com/us-en/platforms/4.aspx?sid=txtlnk](http://shop.amd.com/us-en/platforms/4.aspx?sid=txtlnk)
[http://www.intel.com/products/server/index.htm?iid=prod_nav+server&](http://www.intel.com/products/server/index.htm?iid=prod_nav+server&)
[http://www.giga-byte.com/products/Networking/Products_List.aspx?ClassID=17](http://www.giga-byte.com/products/Networking/Products_List.aspx?ClassID=17)
[http://usa.asus.com/products2.aspx?l1=9&l2=39](http://usa.asus.com/products2.aspx?l1=9&l2=39)
[http://www.tyan.com/products/html/systemboards.html](http://www.tyan.com/products/html/systemboards.html)
[http://www.supermicro.com/Aplus/motherboard/](http://www.supermicro.com/Aplus/motherboard/)

Another option is to simply buy a blade server from a well know company.

Just looked at the shop.amd.com site and a single cpu Sun Fire X2100 Server with 512MB ram, no storage can be had for US$745 !!! Do a sort low to high on price and look at Sun/IBM/HP and the prices are not bad if you want a "real" server which should be pretty reliable as they build them better than desktops and warranty is usually 3yrs plus.

I would honestly just get one of the sun boxes and populate it to my liking, [http://www.sun.com/servers/entry/x2100/index.jsp](http://www.sun.com/servers/entry/x2100/index.jsp)

---


---
title: "Low energy server"
date: 2010-04-21
forum: Server Platforms
---

### Post by rubenverweij on 2010-04-21
Hi all,
I have a long standing wish to have my own webserver.
So, I got an old pc, installed ubuntu server on it and it all worked fine - except for my parents. :P
They apparently thought it wasn't necessary to leave my server on day and night, and said that if I wanted to do just that, I'd have to pay for it myself.
As I've already said, the pc is quite old and uses a lot of power (somewhere around 80 W on average) and I can't afford it to pay ~€140,- a year for the server.
Are there any other solutions I can try? Are there any low energy servers out there that aren't too expensive for a poor student to install ubuntu on?
I also wondered whether ithere are any NAS devices on which I could install ubuntu server?
I hope someone can help me!
Thanks in advance,
Ruben

---

### Post by CheresZabor on 2010-04-21
i would suggest some sort of Intel Atom box, i had one running as a NAS and for a short time even a VMware Server under Ubuntu Server, so it should be more then enough to push Apache or something light

Oops almost forgot, i had a Atom 330 with 2GB of ram

---

### Post by volkswagner on 2010-04-21
80 watts is not terrible.

You could try an older pentium2 box maybe even pentium 3.  I have seen those running at ~40watts.

You could look into the Linkstation NAS devices as they have deals on refurbs.

You can hack them with a Debian install or other lightweight distro.

Check out the [Buffalo NAS wiki]("http://buffalo.nas-central.org/index.php/Main_Page").


You could also hunt down a lower power Notebook/netbook, or build an Intel Atom based server.

---

### Post by Bachstelze on 2010-04-21
You could get a [Soekris](http://soekris.com/) box. In addition to making for a reliable, low-power server, it can be an interesting experience to use that kind of hardware.

---

### Post by dudumomo on 2010-04-21
80W is indeed not that bad.
You can build your ITX machine instead. (Or buy a second hand one)

Otherwise, taking an old P2 is not bad either.

In my case I have a E5200 with an intel ITX MB +2gb + 250GB 2.5. (I don't use more than 10% of the CPU, and 1go would have been enough too)
But I like having a good CPU (As I'm doing grid computing)

An Atom would be nice too.

Actually, it really depends on your budget.

As I guess you cannot afford a new machine, so finding an old laptop or P2 P3 would be good to.
(Such spare components shouldn't be expensive at all)

Where are you from ?

---

### Post by snowpine on 2010-04-21
SheevaPlug... uses 5 watts and costs just US$99.

[http://gizmodo.com/5159399/sheevaplug-a-99-linux-pc-crammed-inside-a-wall-plug](http://gizmodo.com/5159399/sheevaplug-a-99-linux-pc-crammed-inside-a-wall-plug)

---

### Post by dudumomo on 2010-04-21
Wow...very nice.
Very interesting.
More info: [http://www.plugcomputer.org/](http://www.plugcomputer.org/)

Not bad: [http://www.globalscaletechnologies.com/p-31-guruplug-server-standard.aspx](http://www.globalscaletechnologies.com/p-31-guruplug-server-standard.aspx) 75&#8364;

---

### Post by rubenverweij on 2010-04-21
Thank you all for your quick replies.
Great tips, I will definitely look into this tomorrow.
The SheevaPlug looks nice, but 512 mb is too little storage for me.
I'll keep you updated on my choice!

---

### Post by dudumomo on 2010-04-22
You can add a usb key or hard drive if the space is the problem.

---

### Post by rubenverweij on 2010-04-22
Okay, thanks for all the tips.
I'm considering to buy one of the plug servers, but I still have a few questions:
The plug server uses flash storage, right? So wouldn't it were out quickly if I use it as a webserver?
And if it does wear out, can it be replaced or should I then buy a new one?
One last question, so please bear with me :) : what is the difference between this one: [http://www.newit.co.uk/shop/proddetail.php?prod=GuruPlug-Server](http://www.newit.co.uk/shop/proddetail.php?prod=GuruPlug-Server) and this one: [http://www.newit.co.uk/shop/proddetail.php?prod=SheevaPlug](http://www.newit.co.uk/shop/proddetail.php?prod=SheevaPlug).
Which one should I buy? :D
Thanks for your patience and help!
Ruben

---

### Post by HermanAB on 2010-04-22
My current home server is an old Eee PC 701 with three USB memory sticks plugged into it.

---

### Post by Bachstelze on 2010-04-22
> **HermanAB said:**
> My current home server is an old Eee PC 701 with three USB memory sticks plugged into it.

Does it also serve as a frying pan? :p My 701 gets very hot after just an hour of usage, it would probably melt if I left it always on.

---

### Post by CannibalZerg on 2010-04-23
My home Ubuntu Server is based on mini-ITX VIA-Epia with VIA-C3@600MHz processor (TDP 6W) [http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?productLine=1&id=81&tabs=1](http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?productLine=1&id=81&tabs=1)
and 1TB eco-green HDD. It consumes ~15-20W and almost silent (there is no cooler fans, except one for power supply unit)

---

### Post by TitanusEramius on 2010-04-23
Like suggested in the beginning of the thread, a second-hand Pentium is a very good choice for running a server. I got mine Pentium3 for free, it has a 1000mhz cpu, 256mb ram & 2*40gb hdd. All of that is using ~25 watt of power if one of the hdd's is spun down.

In my opinion a NAS would be a perfect alternative to a "normal" computer:
[http://www.synology.com/enu/products/DS110j/index.php](http://www.synology.com/enu/products/DS110j/index.php)
They are cheap, fast and very easy to setup and use.

Good luck

---


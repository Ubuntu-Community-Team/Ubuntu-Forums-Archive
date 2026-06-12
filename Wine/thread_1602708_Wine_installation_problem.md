---
title: "Wine installation problem"
date: 2010-10-21
forum: Wine
---

### Post by mawene_san on 2010-10-21
I have just installed Ubuntu on my laptop and to connect to the internet I need to install Wine so i can install the Virgin Broadband disc.

I have tried multiple versions of wine and I have not managed to install any of them and obviously cannot use the software centre as I have no internet connection.

In fact when going on software centre and typing in wine I am given two options which both say "Wine 1.2 is not available with this type of computer (1386).

Is there a specific package of wine I should use?

My laptop an Intel Core Duo T2080 1.73GHz on an Intel 943GML Calistoga motherboard

Any help would be muchly appreciated, Thanks.

---

### Post by gufide on 2010-10-22
just type in a terminal:

```
[I]sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update

sudo apt-get install wine1.3[/I]
```

---

### Post by bobwyajnr on 2010-10-22
@Op

Something like this might be more appropriate:
[Virgin Media Wireless Router Installation Without CD]("http://community.virginmedia.com/t5/Wireless/Wirless-Router-Installation-Without-CD/m-p/29643")

Do you have a working internet connection on the laptop (e.g. a Windows partition) / on another computer in your house?? Because the Ubuntu Software Centre / Synaptic / apt-get aren't going to work without one!!

I wouldn't bother trying to get the Virgin Media software working on Ubuntu. You shouldn't need it... WINE isn't going to help anyway - as you can't install it without a working internet connection...

Bob

---


---
title: "Ubuntu 10 cannot regconize wireless connections"
date: 2011-02-21
forum: Ubuntu Studio
---

### Post by sikhungtan on 2011-02-21
In Ubuntu 10.10, I can't find any wireless connection while Windows 7 finds 2 and connect easily. I clicked on Internet connection button in Ubutu, then selected Connect to hidden wireless connection, and type the name of the recent wifi connection but it said: You cannot connect to internet. You're now offline :confused:. So what I should do to connect to the Internet. Help me please!

---

### Post by JC Cheloven on 2011-02-21
This post belongs to the "networking and wireless" forum, but anyway.

Are you sure your wireless card is supported and working under ubuntu?
When you click on the network manager icon, it hsould show a list of wireless networks, or at least not saying anything like "device not ready". 

To find out the model of your wireless card, in a terminal type
```
lspci |grep Network
```
Then you can do a search for example [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see whether your card is supported or not. 

If in doubt, please post again in the "networking and wireless" forum. You'll have more chances of getting an useful answer.

---

### Post by sikhungtan on 2011-02-21
Thank for your reply! I clicked on Internet connection but the list show Wireless Network Disconnect, and when I try to connect to one, system says sthing as ...disconnect, you're now offline. I 'll check my network card again. Thank you very much! ;)

---


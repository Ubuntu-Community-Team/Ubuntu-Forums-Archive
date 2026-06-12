---
title: "Is Wireless-N sortof a marketing gimmick?"
date: 2013-01-11
forum: The Cafe
---

### Post by user1397 on 2013-01-11
So I hadn't even thought about this til a co worker of mine brought it to my attention today.  I was asking him what router he has at his house and he told me just a wireless G.  The ISP in our city, Cox Communications, has a max download rate of 5mbps, but I don't usually get anywhere above 2mbps max.  

A wireless-G router is advertised at max speeds of 54mbps, a full 52mbps more than what is bottlenecked by my ISP.

Wireless-N routers boast 300mbps.

Is there a point to any of this until the ISP's start giving us more bandwith?

Also a question, if I get a wireless-N router at my house, and if I have a lot of devices connected to wifi at any given moment (let's say around 10), will the max speed distribute itself more evenly around the devices than if I were using a wireless-G router?  Also do wireless-N routers really have THAT much better range than wireless-G's?

---

### Post by pqwoerituytrueiwoq on 2013-01-11
the point is local network, you can stream video from your computer to the wireless raspberry pi mounted on the back of your tv for example, or copy your linux disk images from your desktop to your laptop via wireless lan
wireless n is supposed to have a larger range, but my wtr54gl (running tomato) has a huge range

---

### Post by bogustrumper on 2013-01-11
In my experience, Wireless-N routers are indeed more powerful. In my in-laws' house (older construction, but not exactly huge), I could get nice strong Wireless-N signals everywhere, but the 802.11G router they were using left noticeable dead spots.

But, you're right in principle: Using DSL getting 5mbps with a Wireless-N router getting 300mbps isn't going to be much different than a 50mbps 802.11G router. Adding security such as WPA or WEP or what-have you will add some overhead, but probably not enough to notice compared to DSL.

Where you will notice a difference is any streaming on the local network. For example, a lot of modern TVs or stereos or blu-ray players can stream media from your PC over your wifi  network. That could run a lot better over Wireless-N than 802.11G.

---

### Post by Bandit on 2013-01-11
Wireless N is how all wireless networks should be. Seem to have better signal strength at times and over al much faster internal network speed with slower latency for mmo games. If I was to have to buy a new router, wireless N would be my only option. But make sure you get a dual band. Keep in mind if you get a single band and someone hops on your network on a older protocol say, b or g. Then all your networked devices will slow down to that speed. But if you get dual band router, then it will switch slower people to the 2.4ghz band and keep the faster nics on the 5ghz (ish) band.

---

### Post by Jakin on 2013-01-11
I can say with experience, that Wireless-N range is quite abit better for the in-home wireless network, over Wireless-G.

Perhaps your incoming WWW speeds aren't as fast to take advantage, but certainly when sharing files from within your own wireless network, even when you are quite abit aways from the router/access point... Im in quite a big house.. Wireless-G won't reach the room im in (that is, its not stable), thats where N range comes in handy :)

Dual Band routers... i have one, im not really sure if its helping me or not..

---

### Post by forrestcupp on 2013-01-11
> **pqwoerituytrueiwoq said:**
> the point is local network, you can stream video from your computer to the wireless raspberry pi mounted on the back of your tv for example, or copy your linux disk images from your desktop to your laptop via wireless lan
wireless n is supposed to have a larger range, but my wtr54gl (running tomato) has a huge range

This is the main thing for people with slower internet connection. If you have more than one computer on your wireless network, and you need to transfer files or stream media from one computer to another, or print to a network printer, that type of thing isn't limited by your internet connection. You want that to be fast.

One practical example is if you're using something like PlayOn on a computer to stream Hulu to your Xbox 360 wirelessly, then your router is going to be used first to stream Hulu from the internet, and then at the same time to send the converted Hulu stream to your 360. 

Unless you just have really fast internet, and some people do now, the router speed is mainly for all the devices that interact with each other on the local network.

---

### Post by ssam on 2013-01-11
you will only get the rated speeds over wireless ( eg, G getting 54mbps) under optimum conditions. compare [http://www.speedtest.net/](http://www.speedtest.net/) with ethernet and wireless or data transfer between 2 machines.

so just because your wireless is in theory faster than your broadband it does not mean its not the bottleneck.

---

### Post by haqking on 2013-01-11
worthy to note that I have fixed a few peoples "speed" as they were implementing WEP or WPA/TKIP on Wireless N which will severely reduce the speed.

To get the full speed available you need WPA2/AES as it is part of the specification and certification

Don't channel bond.

And if you connect G devices to a N router which is also connecting N devices this can bottleneck the routers bandwidth overall to the N devices.

Peace

---

### Post by lz1dsb on 2013-01-11
Most of the people in this thread mention the rated speeds 54Mpbs for G, 300Mbps...
In reality one seldom gets a utilization on a wireless network above 50%, even if the conditions are perfect. It's how WiFi works, the same channel is used for Uplink and Downlink. So on a 54Mbps link one should be able to utilize about 25Mbps data speed, assuming that there aren't other user associated to the same beacon or any other deteriorating factors... There's a lot of signaling overhead associated with WiFi which reduces the capacity for user data.
Regarding the main topic. Like already mentioned, the biggest advantage with N WiFi routers is in the local network. The concept is that most of your home appliances in the not so distant future will be connected, and the most convenient way is to have some sort of wireless connectivity. For the multimedia devices, the advantage is, that you could stream over wireless multimedia content directly. Not that you can't do that now with the G specification, but it should be more efficient with N...

---

